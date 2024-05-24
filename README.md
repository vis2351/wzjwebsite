<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>个人信息和成绩单</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-image: url('新建文件夹（2）/背景.jpg'); 
            background-size: cover;
            background-position: center; 
        }
        .container {
            width: 80%;
            margin: 20px auto;
            padding: 20px;
            opacity: 0.9; 
            /* 添加以下两行样式 */
            border: none;
            background-color: transparent;
        }
        .personal-info {
            margin-bottom: 20px;
        }
        .grades-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        .grades-table th, .grades-table td {
            border: 1px solid #ccc;
            padding: 8px;
            text-align: center;
        }
        .grades-table input {
            width: 50px;
            text-align: center;
        }
        img {
            float: right;
            max-width: 150px;
			max-height: 200px; 
        }
        p {
            font-size: 16px; 
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="personal-info">
            <h2>个人基本信息</h2>
			<img src="新建文件夹（2）/照片.jpg" alt="照片" style="max-width: 200px;">
            <p><strong>姓名：</strong> 王子嘉</p>
            <p><strong>学号：</strong> U202214941</p>
            <p><strong>班级：</strong> 自动化2202班</p>
            <p><strong>出生年月：</strong> 2004年5月3日</p>
            <p><strong>兴趣爱好：</strong> 听音乐、骑行</p>
            <p><a href="http://aia.hust.edu.cn">华中科技大学人工智能与自动化学院</a></p>
        </div>

        <h2>部分成绩</h2>
        <table class="grades-table">
            <thead>
                <tr>
                    <th>课程名称</th>
                    <th>学时</th>
                    <th>成绩</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>互联网技术与应用</td>
                    <td>32</td>
                    <td><input type="number" value="90" oninput="calculateAverageGrade()"></td>
                </tr>
                <tr>
                    <td>自动控制原理</td>
                    <td>56</td>
                    <td><input type="number" value="90" oninput="calculateAverageGrade()"></td>
                </tr>
                <tr>
                    <td>微机原理</td>
                    <td>64</td>
                    <td><input type="number" value="90" oninput="calculateAverageGrade()"></td>
                </tr>
                <tr>
                    <td>计算方法</td>
                    <td>40</td>
                    <td><input type="number" value="90" oninput="calculateAverageGrade()"></td>
                </tr>
                <tr>
                    <td>人工智能导论</td>
                    <td>40</td>
                    <td><input type="number" value="90" oninput="calculateAverageGrade()"></td>
                </tr>
            </tbody>
            <tfoot>
                <tr>
                    <td colspan="2">加权平均分</td>
                    <td id="averageGrade"></td>
                </tr>
            </tfoot>
        </table>
    </div>

    <script>
        function calculateAverageGrade() {
            const inputFields = document.querySelectorAll('.grades-table input');
            const averageGradeElement = document.getElementById("averageGrade");
            let totalCredit = 0;
            let weightedSum = 0;

            inputFields.forEach(inputField => {
                const credit = parseInt(inputField.parentNode.previousElementSibling.textContent);
                const score = parseInt(inputField.value);

                if (!isNaN(credit) && !isNaN(score)) {
                    totalCredit += credit;
                    weightedSum += credit * score;
                }
            });

            const averageGrade = weightedSum / totalCredit || 0;
            averageGradeElement.textContent = averageGrade.toFixed(2);
        }

        calculateAverageGrade();
    </script>
</body>
</html>
