# การทดลอง พื้นฐาน JavaScript และการใช้งานร่วมกับ HTML/CSS
## การทดลองที่ 1 : ทำความรู้จักกับ JavaScript
###  การเพิ่ม JavaScript ลงในเว็บเพจ

JavaScript สามารถเพิ่มลงในเว็บเพจได้ 3 วิธี:

1. แบบ Inline: แทรก scipt ในแต่ละบรรทัดของ HTML Element
```html
<button onclick="alert('สวัสดี!')">คลิกที่นี่</button>
```

2. แบบ Internal Script: เขียน script ใน block   <script> </script>
```html
<script>
    alert('สวัสดี!');
</script>
```

3. แบบ External Script: เขียน script ในไฟล์แล้วเรียกใช้ใน HTML
   ไฟล์ script.js มีข้อมูลดังนี้
```javascript
    alert('สวัสดี!');
```
   ไฟล์ HTML มีการเรียกใช้ script ดังนี้
```html
<script src="script.js"></script>
```

### การทดลองที่ 1.1 : สร้างไฟล์ HTML และทดลองใช้ JavaScript ทั้ง 3 แบบ

สร้างไฟล์ `index.html`:
```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>ทดลอง JavaScript</title>
</head>
<body>
    <!-- Inline JavaScript -->
    <button onclick="alert('คลิกปุ่มที่ 1!')">ปุ่มที่ 1</button>

    <!-- ทดสอบ Internal JavaScript -->
    <button id="btn2">ปุ่มที่ 2</button>

    <!-- ทดสอบ External JavaScript -->
    <button id="btn3" onclick="hello3();">ปุ่มที่ 3</button>

    <!-- Internal JavaScript -->
    <script>
        document.getElementById('btn2').onclick = function() {
            alert('คลิกปุ่มที่ 2!');
        };
    </script>

    <!-- External JavaScript -->
  <!-- ต้องสร้างไฟล์ script.js มีโค้ดโปรแกรมในไฟล์ดังนี้
   function hello3(){
    alert('คลิกปุ่มที่ 3!');
    }
 -->
    <script src="script.js"></script>
</body>
</html>
```

### แบบฝึกปฏิบัติที่ 1: การใช้งาน JavaScript เบื้องต้น

1. สร้างหน้าเว็บที่มีปุ่ม 3 ปุ่ม:
   - ปุ่มที่ 1: ใช้ Inline JavaScript แสดงชื่อนักศึกษา
   - ปุ่มที่ 2: ใช้ Internal JavaScript แสดงวันที่ปัจจุบัน
   - ปุ่มที่ 3: ใช้ External JavaScript แสดงเวลาปัจจุบัน

2. เพิ่มกล่องข้อความและปุ่มสำหรับแสดงผล:
   - มีช่องกรอกข้อความ
   - มีปุ่มเมื่อคลิกแล้วจะแสดงข้อความที่กรอกในช่องข้อความ  (สามารถใช้ document.getElementById('id ของ textbox').value เพื่อดึงข้อมูลในช่อง)
### บันทึกผลการทดลอง 
```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>แสดงข้อมูลด้วย JavaScript</title>
</head>
<body>
    <h2>ทดสอบ JavaScript</h2>

    <!-- ปุ่มที่ 1: Inline JavaScript -->
    <button onclick="alert('นายวสุรัตน์ มณีรัตนะพร')">ปุ่มที่ 1</button>

    <!-- ปุ่มที่ 2: Internal JavaScript -->
    <button id="btn2">ปุ่มที่ 2</button>

    <!-- ปุ่มที่ 3: External JavaScript -->
    <button id="btn3">ปุ่มที่ 3</button>

    <br><br>
    <!-- กล่องข้อความและปุ่มแสดงผล -->
    <input type="text" id="textbox" placeholder="กรอกข้อความที่นี่">
    <button onclick="showText()">แสดงข้อความ</button>
    <p id="display"></p>

    <script>
        // Internal JavaScript สำหรับแสดงวันที่ปัจจุบันในรูปแบบไทย
        document.getElementById('btn2').onclick = function() {
            let options = { year: 'numeric', month: 'numeric', day: 'numeric' };
            let thaiDate = new Date().toLocaleDateString('th-TH', options);
            alert('วันที่ปัจจุบัน: ' + thaiDate);
        };

        // Function สำหรับแสดงข้อความจากช่อง input
        function showText() {
            let text = document.getElementById('textbox').value;
            document.getElementById('display').innerText = 'ข้อความ: ' + text;
        }
    </script>

    <!-- External JavaScript -->
    <script src="/js/index.js"></script>
</body>
</html>
```
```js
// External JavaScript สำหรับแสดงเวลาปัจจุบันในไทย
document.getElementById('btn3').onclick = function() {
    let options = { hour: '2-digit', minute: '2-digit', second: '2-digit', timeZone: 'Asia/Bangkok' };
    let thaiTime = new Date().toLocaleTimeString('th-TH', options);
    alert('เวลาปัจจุบัน: ' + thaiTime);
};
```
[รูปผลการทดลองที่ 1]
![image](https://github.com/user-attachments/assets/a2d3e4c9-39ef-4966-b501-d63ef5408082)
![image](https://github.com/user-attachments/assets/58a2e60b-1f46-4530-a359-6aa02df797a6)
![image](https://github.com/user-attachments/assets/05ab93c4-2992-40cb-b73d-3cca2afb7ef6)
![image](https://github.com/user-attachments/assets/a7ef54d4-96f6-46fc-a5e6-d5e8c92dcaac)

  
## การทดลองที่ 2: พื้นฐาน JavaScript
### 2.1 การประกาศตัวแปรและชนิดข้อมูล

JavaScript มีวิธีการประกาศตัวแปร 3 แบบ:
- `var`: ประกาศตัวแปรแบบเดิม (legacy) - ไม่แนะนำให้ใช้ในโค้ดสมัยใหม่
- `let`: ประกาศตัวแปรที่สามารถเปลี่ยนแปลงค่าได้ - เหมาะสำหรับค่าที่ต้องการเปลี่ยนแปลงในภายหลัง
- `const`: ประกาศตัวแปรที่ไม่สามารถเปลี่ยนแปลงค่าได้ - เหมาะสำหรับค่าคงที่

ชนิดข้อมูลพื้นฐานใน JavaScript:
1. Number: ตัวเลขทั้งจำนวนเต็มและทศนิยม
2. String: ข้อความ ใช้เครื่องหมาย '' หรือ ""
3. Boolean: ค่าความจริง true/false
4. Undefined: ตัวแปรที่ยังไม่ได้กำหนดค่า
5. Null: ตัวแปรที่ไม่มีค่า (ต่างจาก undefined)
6. Array
7. Object
   
### ตัวอย่าง การประกาศตัวแปรแต่ละแบบ
```javascript
// ประกาศตัวแปรแบบ let - สามารถเปลี่ยนแปลงค่าได้ในภายหลัง
let name = "สมชาย";     // String เก็บข้อความ
let age = 25;           // Number เก็บตัวเลข
let isStudent = true;   // Boolean เก็บค่าจริง/เท็จ

// ประกาศตัวแปรแบบ const - ไม่สามารถเปลี่ยนแปลงค่าได้หลังจากประกาศ
const PI = 3.14;            // ค่าคงที่ทางคณิตศาสตร์
const DAYS_IN_WEEK = 7;     // ค่าคงที่ที่ไม่ควรเปลี่ยนแปลง

// การเปลี่ยนแปลงค่าตัวแปร
name = "สมหญิง";   // ทำได้เพราะประกาศด้วย let
age = 26;          // สามารถเปลี่ยนค่าได้
// PI = 3.15;      // Error! ไม่สามารถเปลี่ยนค่า const ได้

// ตัวอย่างการใช้งาน undefined และ null
let uninitializedVar;           // มีค่าเป็น undefined โดยอัตโนมัติ
let emptyValue = null;          // กำหนดค่า null อย่างชัดเจน

// ตัวอย่างการประกาศ Array
let fruits = ["แอปเปิ้ล", "กล้วย", "ส้ม"];

// ตัวอย่างการประกาศ Object
let person = {
    name: "สมชาย",
    age: 25,
    isStudent: true
};
```

### 📝 แบบทดสอบที่ 2.1: การทดลองประกาศตัวแปร
1. สร้างตัวแปรเก็บข้อมูล รหัสนักศึกษา ชื่อนักศึกษา คะแนนสอบกลางภาค, คะแนนสอบปลายภาค โดยเลือกใช้ let หรือ const 
2. สร้าง Object สำหรับเก็บข้อมูลนักศึกษา  ประกอบด้วยข้อมูล รหัสนักศึกษา, ชื่อ, สาขาวิชา, เกรดเฉลี่ย

### บันทึกผลการทดลอง 2.1
```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ข้อมูลนักศึกษา</title>
</head>
<body>
    <h1>ข้อมูลนักศึกษา</h1>
    <div id="student-info"></div> <!-- สถานที่แสดงข้อมูลนักศึกษา -->

    <script src="script.js"></script> <!-- เชื่อมต่อไฟล์ JavaScript -->
</body>
</html>
```
```js
// ประกาศตัวแปรสำหรับเก็บข้อมูลนักศึกษา
let studentId = "67030344";          // รหัสนักศึกษา
let studentName = "วสุรัตน์ มณีรัตนะพร";          // ชื่อนักศึกษา
let midtermScore = 67;               // คะแนนสอบกลางภาค
let finalScore = 72;                 // คะแนนสอบปลายภาค

// สร้าง Object สำหรับเก็บข้อมูลนักศึกษา
const student = {
    id: studentId,                   // รหัสนักศึกษา
    name: studentName,               // ชื่อ
    major: "เทคโนโลยีคอมพิวเตอร์",    // สาขาวิชา
    gpa: 3.75 // เกรดเฉลี่ย
};

// แสดงข้อมูลนักศึกษาใน HTML
const studentInfoDiv = document.getElementById("student-info");
studentInfoDiv.innerHTML = 
    "<p>รหัสนักศึกษา: " + student.id + "</p>" +
    "<p>ชื่อ: " + student.name + "</p>" +
    "<p>คะแนนสอบกลางภาค: " + midtermScore + "</p>" +
    "<p>คะแนนสอบปลายภาค: " + finalScore + "</p>" +
    "<p>สาขาวิชา: " + student.major + "</p>" +
    "<p>เกรดเฉลี่ย: " + student.gpa + "</p>";
```
[รูปผลการทดลองที่ 2.1]
![image](https://github.com/user-attachments/assets/668f2499-4cef-45ea-98c1-f810cfe07434)


### 2.2 การดำเนินการทางคณิตศาสตร์

JavaScript มีตัวดำเนินการทางคณิตศาสตร์พื้นฐานดังนี้:
- `+` การบวก
- `-` การลบ
- `*` การคูณ
- `/` การหาร
- `%` การหารเอาเศษ (modulo)
- `**` การยกกำลัง (exponentiation)
- `++` การเพิ่มค่าทีละ 1 (increment)
- `--` การลดค่าทีละ 1 (decrement)

### แบบฝึกหัด 2.2: ทดลองใช้ตัวดำเนินการทางคณิตศาสตร์
```javascript
// กำหนดค่าตัวแปรเริ่มต้น
let x = 10;
let y = 5;

// การดำเนินการพื้นฐาน
let sum = x + y;      // บวก: 10 + 5 = 15
let diff = x - y;     // ลบ: 10 - 5 = 5
let product = x * y;  // คูณ: 10 * 5 = 50
let quotient = x / y; // หาร: 10 / 5 = 2
let remainder = x % y; // หารเอาเศษ: 10 % 5 = 0 (หาร 5 ลงตัว)

// การเพิ่ม/ลดค่าทีละ 1
let counter = 1;
counter++;            // เพิ่มค่าทีละ 1: counter = 2
counter--;            // ลดค่าทีละ 1: counter = 1

// การยกกำลัง
let squared = x ** 2;  // 10 ยกกำลัง 2 = 100
let cubed = x ** 3;    // 10 ยกกำลัง 3 = 1000

// การใช้ตัวดำเนินการร่วมกับการกำหนดค่า
let number = 5;
number += 3;          // เท่ากับ number = number + 3
number -= 2;          // เท่ากับ number = number - 2
number *= 4;          // เท่ากับ number = number * 4
number /= 2;          // เท่ากับ number = number / 2

```

### 📝 แบบทดสอบที่ 2.2: การคำนวณพื้นฐาน
1. เขียนโปรแกรม กำหนดคะแนน  3 วิชา แล้วหาค่าคะแนนเฉลี่ย แล้วแสดงผลการคำนวณ
2. เขียนโปรแกรม กำหนดชื่อสินค้า ราคาสินค้า คำนวณราคาสินค้าที่รวม VAT 7% แล้วแสดงผลการคำนวณ

### บันทึกผลการทดลอง 2.2
```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>คำนวณคะแนนเฉลี่ยและราคาสินค้า</title>
</head>
<body>
    <h1>คำนวณคะแนนเฉลี่ย</h1>
    <form id="score-form">
        <label for="score1">คะแนนวิชาที่ 1:</label>
        <input type="number" id="score1" required><br>
        <label for="score2">คะแนนวิชาที่ 2:</label>
        <input type="number" id="score2" required><br>
        <label for="score3">คะแนนวิชาที่ 3:</label>
        <input type="number" id="score3" required><br>
        <button type="submit">คำนวณคะแนนเฉลี่ย</button>
    </form>
    <div id="average-score"></div> <!-- แสดงคะแนนเฉลี่ย -->

    <h1>คำนวณราคาสินค้าพร้อม VAT</h1>
    <form id="product-form">
        <label for="productName">ชื่อสินค้า:</label>
        <input type="text" id="productName" required><br>
        <label for="productPrice">ราคาสินค้า:</label>
        <input type="number" id="productPrice" required><br>
        <button type="submit">คำนวณราคาสินค้าพร้อม VAT</button>
    </form>
    <div id="product-price"></div> <!-- แสดงราคาสินค้าพร้อม VAT -->

    <script src="script.js"></script> <!-- เชื่อมต่อไฟล์ JavaScript -->
</body>
</html>
```
```js
// คำนวณคะแนนเฉลี่ย
const scoreForm = document.getElementById("score-form");
const averageScoreDiv = document.getElementById("average-score");

scoreForm.addEventListener("submit", function(event) {
    event.preventDefault(); // ป้องกันการรีเฟรชหน้า

    // รับค่าจาก input
    let score1 = parseFloat(document.getElementById("score1").value);
    let score2 = parseFloat(document.getElementById("score2").value);
    let score3 = parseFloat(document.getElementById("score3").value);

    // คำนวณคะแนนเฉลี่ย
    let averageScore = (score1 + score2 + score3) / 3;

    // แสดงผลคะแนนเฉลี่ยใน HTML
    averageScoreDiv.innerHTML = "คะแนนเฉลี่ย: " + averageScore.toFixed(2);
});

// คำนวณราคาสินค้าพร้อม VAT
const productForm = document.getElementById("product-form");
const productPriceDiv = document.getElementById("product-price");

productForm.addEventListener("submit", function(event) {
    event.preventDefault(); // ป้องกันการรีเฟรชหน้า

    // รับค่าจาก input
    let productName = document.getElementById("productName").value;
    let productPrice = parseFloat(document.getElementById("productPrice").value);

    // คำนวณราคาสินค้าที่รวม VAT 7%
    let vatRate = 0.07; // อัตรา VAT 7%
    let totalPrice = productPrice + (productPrice * vatRate);

    // แสดงผลการคำนวณใน HTML
    productPriceDiv.innerHTML = "ชื่อสินค้า: " + productName + "<br>" +
                                 "ราคาสินค้าพร้อม VAT 7%: " + totalPrice.toFixed(2) + " บาท";
});
```
[รูปผลการทดลองที่ 2.2]
![image](https://github.com/user-attachments/assets/fef0aa0e-071d-4169-9154-f5aaafb2ad56)



### 2.3 การควบคุมการทำงาน

JavaScript มีโครงสร้างควบคุมการทำงานหลักๆ ดังนี้:

1. เงื่อนไข (Conditionals):
   - `if`: ตรวจสอบเงื่อนไขเดียว
   - `if...else`: ตรวจสอบเงื่อนไขและมีทางเลือก
   - `if...else if...else`: ตรวจสอบหลายเงื่อนไข
   - `switch`: เลือกทำงานตามค่าที่กำหนด

2. การวนซ้ำ (Loops):
   - `for`: วนซ้ำตามจำนวนรอบที่กำหนด
   - `while`: วนซ้ำตราบใดที่เงื่อนไขเป็นจริง
   - `do...while`: ทำงานอย่างน้อย 1 ครั้ง แล้ววนซ้ำตามเงื่อนไข
   - `for...of`: วนซ้ำสำหรับข้อมูลแบบ iterable
   - `for...in`: วนซ้ำสำหรับ properties ใน object


```javascript
// 1. การใช้ if-else
let score = 75;

// ตรวจสอบเงื่อนไขตามลำดับ
if (score >= 80) {         // ถ้าคะแนน >= 80
    console.log("เกรด A");
} else if (score >= 70) {  // ถ้าคะแนน >= 70 แต่ < 80
    console.log("เกรด B");
} else {                   // ถ้าไม่ตรงเงื่อนไขใดเลย
    console.log("เกรด C");
}

// 2. การใช้ switch
let day = 1;
switch (day) {
    case 1:
        console.log("วันจันทร์");
        break;              // break เพื่อออกจาก switch
    case 2:
        console.log("วันอังคาร");
        break;
    default:               // ค่าเริ่มต้นถ้าไม่ตรงกับ case ใดๆ
        console.log("วันอื่นๆ");
}

// 3. การใช้ for loop
// วนซ้ำ 5 รอบ: เริ่มที่ 1, ทำจนถึง 5, เพิ่มค่าทีละ 1
for (let i = 1; i <= 5; i++) {
    console.log("รอบที่", i);
}

// 4. การใช้ while loop
// วนซ้ำตราบใดที่เงื่อนไขเป็นจริง
let count = 1;
while (count <= 3) {      // ทำซ้ำตราบใดที่ count <= 3
    console.log("นับ:", count);
    count++;              // เพิ่มค่า count ทีละ 1
}

// 5. การใช้ do...while loop
// ทำงานอย่างน้อย 1 ครั้ง แล้วค่อยตรวจสอบเงื่อนไข
let num = 1;
do {
    console.log("ตัวเลข:", num);
    num++;
} while (num <= 3);

// 6. การใช้ for...of loop กับ array
let fruits = ['แอปเปิ้ล', 'กล้วย', 'ส้ม'];
for (let fruit of fruits) {
    console.log("ผลไม้:", fruit);
}

// 7. การใช้ for...in loop กับ object
let person = {
    name: 'สมชาย',
    age: 25,
    job: 'โปรแกรมเมอร์'
};
for (let key in person) {
    console.log(key + ":", person[key]);
}

// 8. การใช้เงื่อนไขซ้อน (Nested Conditions)
let age = 18;
let hasPermission = true;

if (age >= 18) {
    if (hasPermission) {
        console.log("สามารถเข้าใช้งานได้");
    } else {
        console.log("ต้องได้รับอนุญาตก่อน");
    }
} else {
    console.log("อายุไม่ถึงเกณฑ์");
}

// 9. การใช้ตัวดำเนินการลอจิคัล (Logical Operators)
let isStudent = true;
let isMember = false;

if (isStudent && isMember) {           // AND (&&)
    console.log("เป็นทั้งนักเรียนและสมาชิก");
} else if (isStudent || isMember) {    // OR (||)
    console.log("เป็นอย่างใดอย่างหนึ่ง");
} else {
    console.log("ไม่เป็นทั้งสองอย่าง");
}

// 10. การใช้ break และ continue
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        continue;    // ข้ามการทำงานที่เหลือในรอบนี้
    }
    if (i === 4) {
        break;       // ออกจาก loop ทันที
    }
    console.log("ตัวเลข:", i);
}
```


### 📝 แบบทดสอบที่ 2.3: การควบคุมการทำงาน
1. กำหนดตัวเลข และตรวจสอบว่าตัวเลขที่กำหนดเป็นเลขคู่หรือเลขคี่
2. สร้าง loop แบบ for แสดงตารางสูตรคูณ แม่ 2 และ loop แบบ while แสดงสูตรคูณ แม่ 3
3. เขียนโปรแกรมนับถอยหลังจาก 10 ถึง 1
4. เขียนโปรแกรมกำหนดอายุ และตรวจสอบช่วงวัยตามอายุที่กำหนด (กำหนดอายุแต่ละช่วงวัย วัยเด็ก วัยรุ่น วัยผู้ใหญ่)

### บันทึกผลการทดลอง 2.3
```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>โปรแกรมต่าง ๆ</title>
</head>
<body>
    <h1>โปรแกรมตรวจสอบเลขคู่หรือเลขคี่</h1>
    <input type="number" id="number" placeholder="กรอกตัวเลข" required>
    <button id="checkNumberBtn">ตรวจสอบ</button>
    <div id="numberResult"></div>

    <h1>ตารางสูตรคูณแม่ 2</h1>
    <div id="multiplicationTable2"></div>

    <h1>ตารางสูตรคูณแม่ 3 (ใช้ while loop)</h1>
    <div id="multiplicationTable3"></div>

    <h1>โปรแกรมนับถอยหลัง</h1>
    <button id="countdownBtn">นับถอยหลัง</button>
    <div id="countdownResult"></div>

    <h1>ตรวจสอบช่วงวัย</h1>
    <input type="number" id="age" placeholder="กรอกอายุ" required>
    <button id="checkAgeBtn">ตรวจสอบช่วงวัย</button>
    <div id="ageResult"></div>

    <script src="script.js"></script> <!-- เชื่อมต่อไฟล์ JavaScript -->
</body>
</html>
```
```js
// โปรแกรมตรวจสอบเลขคู่หรือเลขคี่
document.getElementById("checkNumberBtn").addEventListener("click", function() {
    const number = parseInt(document.getElementById("number").value);
    const numberResultDiv = document.getElementById("numberResult");

    if (number % 2 === 0) {
        numberResultDiv.innerHTML = number + " เป็นเลขคู่";
    } else {
        numberResultDiv.innerHTML = number + " เป็นเลขคี่";
    }
});

// ตารางสูตรคูณแม่ 2
const multiplicationTable2Div = document.getElementById("multiplicationTable2");
for (let i = 1; i <= 12; i++) {
    multiplicationTable2Div.innerHTML += "2 x " + i + " = " + (2 * i) + "<br>";
}

// ตารางสูตรคูณแม่ 3 (ใช้ while loop)
const multiplicationTable3Div = document.getElementById("multiplicationTable3");
let i = 1;
while (i <= 12) {
    multiplicationTable3Div.innerHTML += "3 x " + i + " = " + (3 * i) + "<br>";
    i++;
}

// โปรแกรมนับถอยหลัง
document.getElementById("countdownBtn").addEventListener("click", function() {
    const countdownResultDiv = document.getElementById("countdownResult");
    countdownResultDiv.innerHTML = ""; // ล้างผลลัพธ์ก่อน

    for (let j = 10; j >= 1; j--) {
        countdownResultDiv.innerHTML += j + "<br>";
    }
});

// ตรวจสอบช่วงวัย
document.getElementById("checkAgeBtn").addEventListener("click", function() {
    const age = parseInt(document.getElementById("age").value);
    const ageResultDiv = document.getElementById("ageResult");

    if (age < 13) {
        ageResultDiv.innerHTML = "วัยเด็ก";
    } else if (age >= 13 && age < 20) {
        ageResultDiv.innerHTML = "วัยรุ่น";
    } else {
        ageResultDiv.innerHTML = "วัยผู้ใหญ่";
    }
});
```
[รูปผลการทดลองที่ 2.3]
![image](https://github.com/user-attachments/assets/ecbebfa7-10f7-49e8-b817-14e027967aac)


### 2.4 Functions และ Arrow Functions

Functions คือกลุ่มคำสั่งที่สามารถนำมาใช้ซ้ำได้ ใน JavaScript มีวิธีการเขียน function 2 แบบหลักๆ:

1. Function แบบปกติ (Regular Functions):
   - ใช้คำสั่ง `function` ในการประกาศ
   - สามารถมีหรือไม่มีพารามิเตอร์ก็ได้
   - สามารถ return ค่ากลับหรือไม่ก็ได้
   - มี `this` context ของตัวเอง

2. Arrow Functions:
   - เป็นวิธีเขียนแบบสั้นที่มาใน ES6
   - ไม่มี `this` context ของตัวเอง
   - เหมาะสำหรับ function สั้นๆ
   - มักใช้ใน callback functions

#### ตัวอย่างการสร้างและเรียกใช้ Function 

```javascript
// 1. Function พื้นฐาน - ไม่มีพารามิเตอร์และไม่ return ค่า
function sayHello() {
    console.log("สวัสดี!");
}
sayHello();  // เรียกใช้ function: แสดง "สวัสดี!"

// 2. Function ที่รับพารามิเตอร์
function greet(name) {
    console.log("สวัสดี " + name);
}
greet("สมชาย");  // แสดง: "สวัสดี สมชาย"

// 3. Function ที่ return ค่า
function add(a, b) {
    return a + b;  // ส่งค่าผลบวกกลับ
}
let sum = add(5, 3);  // sum = 8

// 4. Function ที่มีค่าเริ่มต้นของพารามิเตอร์
function greetWithTitle(name, title = "คุณ") {
    console.log("สวัสดี " + title + " " + name);
}
greetWithTitle("สมชาย");          // แสดง: "สวัสดี คุณ สมชาย"
greetWithTitle("สมชาย", "ดร.");   // แสดง: "สวัสดี ดร. สมชาย"

// 5. Function ที่รับหลายพารามิเตอร์ (Rest Parameters)
function sum(...numbers) {
    let total = 0;
    for (let num of numbers) {
        total += num;
    }
    return total;
}
console.log(sum(1, 2, 3, 4));  // แสดง: 10

// 6. Function ที่ return หลายค่าโดยใช้ Object
function getPersonInfo() {
    return {
        name: "สมชาย",
        age: 25,
        job: "โปรแกรมเมอร์"
    };
}
let person = getPersonInfo();
console.log(person.name);  // แสดง: "สมชาย"

// 7. Function ที่เป็น Method ใน Object
let calculator = {
    add: function(a, b) {
        return a + b;
    },
    subtract: function(a, b) {
        return a - b;
    }
};
console.log(calculator.add(5, 3));      // แสดง: 8
console.log(calculator.subtract(5, 3));  // แสดง: 2

// 8. Nested Function (Function ซ้อน Function)
function outer(x) {
    function inner(y) {
        return x + y;  // inner function สามารถเข้าถึงตัวแปรของ outer function
    }
    return inner;
}
let addFive = outer(5);
console.log(addFive(3));  // แสดง: 8

// 9. Callback Function
function process(callback) {
    console.log("กำลังประมวลผล...");
    callback();  // เรียกใช้ function ที่ส่งเข้ามา
}
process(function() {
    console.log("เสร็จสิ้น!");
});

// 10. Immediately Invoked Function Expression (IIFE)
(function() {
    console.log("Function นี้ทำงานทันทีที่ถูกประกาศ");
})();
```


### 📝 แบบทดสอบที่ 2.4.1: Functions
1. สร้าง function คำนวณค่า BMI (ดัชนีมวลกาย) จากน้ำหนักและส่วนสูง
2. สร้าง function ที่รับชื่อและอายุ แล้วแสดงข้อความทักทายที่เหมาะสมกับอายุ
3. เขียน function ตรวจสอบรหัสผ่านว่ามีความยาวมากกว่า 8 ตัวอักษรหรือไม่

### บันทึกผลการทดลอง 2.4.1
```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>โปรแกรมฟังก์ชันต่าง ๆ</title>
</head>
<body>
    <h1>คำนวณค่า BMI</h1>
    <input type="number" id="weight" placeholder="น้ำหนัก (กิโลกรัม)" required>
    <input type="number" id="height" placeholder="ส่วนสูง (เมตร)" required>
    <button id="calculateBMI">คำนวณ BMI</button>
    <div id="bmiResult"></div>

    <h1>ทักทายตามอายุ</h1>
    <input type="text" id="name" placeholder="กรอกชื่อ" required>
    <input type="number" id="age" placeholder="กรอกอายุ" required>
    <button id="greetBtn">ทักทาย</button>
    <div id="greetingResult"></div>

    <h1>ตรวจสอบรหัสผ่าน</h1>
    <input type="text" id="password" placeholder="กรอกรหัสผ่าน" required>
    <button id="checkPasswordBtn">ตรวจสอบรหัสผ่าน</button>
    <div id="passwordResult"></div>

    <script src="script.js"></script> <!-- เชื่อมต่อไฟล์ JavaScript -->
</body>
</html>
```
```js
// ฟังก์ชันคำนวณค่า BMI
function calculateBMI(weight, height) {
    return weight / (height * height); // BMI = น้ำหนัก / (ส่วนสูง^2)
}

// ฟังก์ชันที่ทักทายตามอายุ
function greetByAge(name, age) {
    let greeting;
    if (age < 13) {
        greeting = "สวัสดีคุณ " + name + " คุณยังเด็กอยู่เลย";
    } else if (age < 20) {
        greeting = "สวัสดีคุณ " + name + " คุณยังเป็นวัยรุ่นอยู่";
    } else {
        greeting = "สวัสดีคุณ " + name + " คุณเป็นผู้ใหญ่แล้ว";
    }
    return greeting;
}

// ฟังก์ชันตรวจสอบรหัสผ่าน
function isPasswordValid(password) {
    return password.length > 8; // ตรวจสอบความยาวของรหัสผ่าน
}

// ฟังก์ชันจัดการการคำนวณ BMI
document.getElementById("calculateBMI").addEventListener("click", function() {
    const weight = parseFloat(document.getElementById("weight").value);
    const height = parseFloat(document.getElementById("height").value)/100;
    const bmiResultDiv = document.getElementById("bmiResult");

    if (weight > 0 && height > 0) {
        const bmi = calculateBMI(weight, height);
        bmiResultDiv.innerHTML = "ค่า BMI ของคุณคือ: " + bmi.toFixed(2);
    } else {
        bmiResultDiv.innerHTML = "กรุณากรอกน้ำหนักและส่วนสูงให้ถูกต้อง";
    }
});

// ฟังก์ชันจัดการการทักทายตามอายุ
document.getElementById("greetBtn").addEventListener("click", function() {
    const name = document.getElementById("name").value;
    const age = parseInt(document.getElementById("age").value);
    const greetingResultDiv = document.getElementById("greetingResult");

    greetingResultDiv.innerHTML = greetByAge(name, age);
});

// ฟังก์ชันจัดการการตรวจสอบรหัสผ่าน
document.getElementById("checkPasswordBtn").addEventListener("click", function() {
    const password = document.getElementById("password").value;
    const passwordResultDiv = document.getElementById("passwordResult");

    if (isPasswordValid(password)) {
        passwordResultDiv.innerHTML = "รหัสผ่านปลอดภัย";
    } else {
        passwordResultDiv.innerHTML = "รหัสผ่านต้องมีความยาวมากกว่า 8 ตัวอักษร";
    }
});
```
[รูปผลการทดลองที่ 2.4.1]
![image](https://github.com/user-attachments/assets/370f6c58-0f6f-46f3-ad0c-cd890b4899d1)



#### 2.4.2 Arrow Function
Arrow Function เป็นวิธีการเขียน function แบบสั้นๆ ที่มาพร้อมกับ JavaScript เวอร์ชัน ES6

### ตัวอย่างการใช้ Arrow Function
```javascript
// Arrow Function แบบพื้นฐาน
const greet = (name) => {
    return "สวัสดี " + name;
};

// Arrow Function แบบย่อ (ถ้ามีคำสั่งเดียว)
const greetShort = name => "สวัสดี " + name;

// Arrow Function ที่มีหลายพารามิเตอร์
const multiply = (a, b) => a * b;

// Arrow Function ที่ไม่มีพารามิเตอร์
const getRandomNumber = () => Math.random();

// ตัวอย่างการใช้ Arrow Function กับ Array
const numbers = [1, 2, 3, 4, 5];

// การใช้ map กับ Arrow Function
const doubled = numbers.map(num => num * 2);
console.log("เลขคูณ 2:", doubled); // [2, 4, 6, 8, 10]

// การใช้ filter กับ Arrow Function
const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log("เลขคู่:", evenNumbers); // [2, 4]
```
### แบบทดสอบ 2.4.2 เขียนฟังก์ชันต่อไปนี้ในรูปแบบ Arrow function
1. สร้าง function คำนวณค่า BMI (ดัชนีมวลกาย) จากน้ำหนักและส่วนสูง
2. สร้าง function ที่รับชื่อและอายุ แล้วแสดงข้อความทักทายที่เหมาะสมกับอายุ
3. เขียน function ตรวจสอบรหัสผ่านว่ามีความยาวมากกว่า 8 ตัวอักษรหรือไม่

### บันทึกผลการทดลอง 2.4.2
```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>โปรแกรมฟังก์ชัน Arrow</title>
</head>
<body>
    <h1>คำนวณค่า BMI</h1>
    <input type="number" id="weight" placeholder="น้ำหนัก (กิโลกรัม)">
    <input type="number" id="height" placeholder="ส่วนสูง (เมตร)">
    <button id="calculateBMI">คำนวณ BMI</button>
    <div id="bmiResult"></div>

    <h1>ทักทายตามอายุ</h1>
    <input type="text" id="name" placeholder="กรอกชื่อ">
    <input type="number" id="age" placeholder="กรอกอายุ">
    <button id="greetBtn">ทักทาย</button>
    <div id="greetingResult"></div>

    <h1>ตรวจสอบรหัสผ่าน</h1>
    <input type="text" id="password" placeholder="กรอกรหัสผ่าน">
    <button id="checkPasswordBtn">ตรวจสอบรหัสผ่าน</button>
    <div id="passwordResult"></div>

    <script src="script.js"></script> <!-- เชื่อมต่อไฟล์ JavaScript -->
</body>
</html>
```
```js
// ฟังก์ชันคำนวณค่า BMI (Arrow Function)
const calculateBMI = (weight, height) => weight / (height * height);

// ฟังก์ชันที่ทักทายตามอายุ (Arrow Function)
const greetByAge = (name, age) => {
    if (age < 13) return `สวัสดีคุณ ${name} คุณยังเด็กอยู่เลย`;
    if (age < 20) return `สวัสดีคุณ ${name} คุณยังเป็นวัยรุ่นอยู่`;
    return `สวัสดีคุณ ${name} คุณเป็นผู้ใหญ่แล้ว`;
};

// ฟังก์ชันตรวจสอบรหัสผ่าน (Arrow Function)
const isPasswordValid = password => password.length > 8;

// จัดการการคำนวณ BMI
document.getElementById("calculateBMI").addEventListener("click", () => {
    const weight = parseFloat(document.getElementById("weight").value);
    const height = parseFloat(document.getElementById("height").value)/100;
    const bmiResultDiv = document.getElementById("bmiResult");

    if (weight > 0 && height > 0) {
        const bmi = calculateBMI(weight, height);
        bmiResultDiv.innerHTML = `ค่า BMI ของคุณคือ: ${bmi.toFixed(2)}`;
    } else {
        bmiResultDiv.innerHTML = "กรุณากรอกน้ำหนักและส่วนสูงให้ถูกต้อง";
    }
});

// จัดการการทักทายตามอายุ
document.getElementById("greetBtn").addEventListener("click", () => {
    const name = document.getElementById("name").value;
    const age = parseInt(document.getElementById("age").value);
    document.getElementById("greetingResult").innerHTML = greetByAge(name, age);
});

// จัดการการตรวจสอบรหัสผ่าน
document.getElementById("checkPasswordBtn").addEventListener("click", () => {
    const password = document.getElementById("password").value;
    const passwordResultDiv = document.getElementById("passwordResult");

    passwordResultDiv.innerHTML = isPasswordValid(password) 
        ? "รหัสผ่านปลอดภัย" 
        : "รหัสผ่านต้องมีความยาวมากกว่า 8 ตัวอักษร";
});
```
[รูปผลการทดลองที่ 2.4.2]
![image](https://github.com/user-attachments/assets/636e6663-2b68-41d1-9cda-b01531509392)


## การทดลองที่ 3 : การใช้ JavaScript กับ HTML และ CSS
### การทดลองที่ 3.1 การสร้างปุ่มและจัดการ Event ด้วย JavaScript
### ตัวอย่างที่ 1 
```html
<!DOCTYPE html>
<html>
<head>
    <title>Event Handling</title>
</head>
<body>
    <button onclick="showMessage()">คลิกที่นี่</button>
    
    <script>
    function showMessage() {
        alert("สวัสดีครับ/ค่ะ!");
    }
    </script>
</body>
</html>
```
### ตัวอย่างที่ 2
```html
<!DOCTYPE html>
<html>
<head>
    <title>Event Handling</title>
</head>
<body>
    Enter name<input type="text" id="name">
    <button onclick="showMessage(document.getElementById('name').value)">คลิกที่นี่</button>
    
    <script>
    function showMessage(name) {
        alert("สวัสดีครับ/ค่ะ คุณ :",name);
    }
    </script>
</body>
</html>
```
### ตัวอย่างที่ 3 
```html
<!DOCTYPE html>
<html>
<head>
    <title>Event Handling</title>
</head>
<body>
    Enter name<input type="text" id="name">
    <p id="output_value"></p>
    <button onclick="showMessage(document.getElementById('name').value)">คลิกที่นี่</button>
    
    <script>
    function showMessage(name) {
        document.getElementById('output_value').innerHTML='Hello' + name;
    }
    </script>
</body>
</html>
```

### แบบทดสอบ 3.1 
1. เขียนเว็บ รับค่าน้ำหนักและส่วนสูง ทำการ คำนวณค่า BMI (ดัชนีมวลกาย) แล้วแสดงผลว่า อ้วน, ผอม หรือ สมส่วน โดยเขียนฟังก์ชันแบบ Arrow function

### บันทึกผลการทดลอง 3.1
```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>คำนวณค่า BMI</title>
</head>
<body>

    <h1>คำนวณค่า BMI</h1>
    <input type="number" id="weight" placeholder="น้ำหนัก (กิโลกรัม)">
    <input type="number" id="height" placeholder="ส่วนสูง (เซนติเมตร)">
    <button id="calculateBMI">คำนวณ BMI</button>

    <div id="result"></div>

    <script src="script.js"></script> <!-- เชื่อมต่อไฟล์ JavaScript -->
</body>
</html>
```
```js
// ฟังก์ชันคำนวณ BMI (Arrow Function)
const calculateBMI = (weight, height) => weight / ((height / 100) ** 2);

// ฟังก์ชันแสดงผลลัพธ์ว่า อ้วน, ผอม หรือ สมส่วน (Arrow Function)
const getBMICategory = bmi => {
    if (bmi < 18.5) return "ผอม";
    if (bmi >= 18.5 && bmi < 25) return "สมส่วน";
    return "อ้วน";
};

// จัดการการคลิกปุ่มคำนวณ
document.getElementById("calculateBMI").addEventListener("click", () => {
    const weight = parseFloat(document.getElementById("weight").value);
    const height = parseFloat(document.getElementById("height").value);
    const resultDiv = document.getElementById("result");

    if (weight > 0 && height > 0) {
        const bmi = calculateBMI(weight, height);
        const category = getBMICategory(bmi);
        resultDiv.innerHTML = `ค่า BMI ของคุณคือ: ${bmi.toFixed(2)} (${category})`;
    } else {
        resultDiv.innerHTML = "กรุณากรอกน้ำหนักและส่วนสูงให้ถูกต้อง";
    }
});
```
[รูปผลการทดลองที่ 3.1]
![image](https://github.com/user-attachments/assets/eb5731d1-5c02-4c62-bd5c-81199b93ae40)


## การทดลองที่ 3.2 : การสร้างฟอร์มสำหรับจองห้องพัก
การสร้างฟอร์มลงทะเบียนเพื่อรวบรวมข้อมูลที่จำเป็นสำหรับการจองห้องพัก

### ขั้นตอนที่ 3.2.1: สร้างโครงสร้าง HTML พื้นฐาน

สร้างไฟล์ `index.html` และใส่โค้ดต่อไปนี้:

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ระบบจองห้องพักออนไลน์</title>
</head>
<body>
    <h1>แบบฟอร์มจองห้องพัก</h1>
    
    <form id="bookingForm">
        <div>
            <label for="fullname">ชื่อ-นามสกุล:</label>
            <input type="text" id="fullname" name="fullname" required>
        </div>

        <div>
            <label for="email">อีเมล:</label>
            <input type="email" id="email" name="email" required>
        </div>

        <div>
            <label for="phone">เบอร์โทรศัพท์:</label>
            <input type="tel" id="phone" name="phone" required>
        </div>

        <div>
            <label for="checkin">วันที่เช็คอิน:</label>
            <input type="date" id="checkin" name="checkin" required>
        </div>

        <div>
            <label for="checkout">วันที่เช็คเอาท์:</label>
            <input type="date" id="checkout" name="checkout" required>
        </div>

        <div>
            <label for="roomtype">ประเภทห้องพัก:</label>
            <select id="roomtype" name="roomtype" required>
                <option value="">กรุณาเลือกประเภทห้องพัก</option>
                <option value="standard">ห้องมาตรฐาน</option>
                <option value="deluxe">ห้องดีลักซ์</option>
                <option value="suite">ห้องสวีท</option>
            </select>
        </div>

        <div>
            <label for="guests">จำนวนผู้เข้าพัก:</label>
            <input type="number" id="guests" name="guests" min="1" max="4" required>
        </div>

        <button type="submit">จองห้องพัก</button>
    </form>
</body>
</html>
```

### ขั้นตอนที่ 3.2.2 : การปรับแต่งด้วย CSS

เพิ่มความสวยงามให้กับฟอร์มด้วย CSS โดยเพิ่ม `<style>` ในส่วน `<head>` ของไฟล์ HTML:

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ระบบจองห้องพักออนไลน์</title>
    <style>
        body {
            font-family: 'Sarabun', sans-serif;
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f5f5f5;
        }

        h1 {
            color: #2c3e50;
            text-align: center;
            margin-bottom: 30px;
        }

        form {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }

        div {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            color: #34495e;
            font-weight: bold;
        }

        input, select {
            width: 100%;
            padding: 8px;
            border: 1px solid #ddd;
            border-radius: 4px;
            box-sizing: border-box;
        }

        input:focus, select:focus {
            outline: none;
            border-color: #3498db;
            box-shadow: 0 0 5px rgba(52,152,219,0.3);
        }

        button {
            background-color: #2980b9;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
        }

        button:hover {
            background-color: #3498db;
        }

        @media (max-width: 480px) {
            body {
                padding: 10px;
            }
        }
    </style>
</head>
```

### คำอธิบาย CSS:

1. ใช้ `max-width` และ `margin: 0 auto` เพื่อจัดกึ่งกลางฟอร์ม
2. จัดการ layout ด้วย `display: block` และ `width: 100%`
3. เพิ่มเอฟเฟกต์ `hover` และ `focus`
4. ใช้ `box-shadow` เพื่อเพิ่มมิติการแสดงผล
5. รองรับการแสดงผลบนมือถือด้วย `@media`

### ผลการทดลอง
ทดสอบปรับแต่ง CSS ในแต่ละส่วน แล้วเขียน สรุปผลการทดลองว่าได้ทดลองเปลี่ยนส่วนใด แล้วผลเป็นอย่างไร พร้อมแนบรูปประกอบการทดลอง

### บันทึกผลการทดลอง 3.2.2
```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ระบบจองห้องพักออนไลน์</title>
    <link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@400&display=swap" rel="stylesheet"> <!-- เชื่อมต่อฟอนต์ -->
    <link rel="stylesheet" href="styles.css"> <!-- เชื่อมต่อ CSS -->
</head>
<body>
    <h1>แบบฟอร์มจองห้องพัก</h1>
    
    <form id="bookingForm">
        <div>
            <label for="fullname">ชื่อ-นามสกุล:</label>
            <input type="text" id="fullname" name="fullname" required>
        </div>

        <div>
            <label for="email">อีเมล:</label>
            <input type="email" id="email" name="email" required>
        </div>

        <div>
            <label for="phone">เบอร์โทรศัพท์:</label>
            <input type="tel" id="phone" name="phone" required>
        </div>

        <div>
            <label for="checkin">วันที่เช็คอิน:</label>
            <input type="date" id="checkin" name="checkin" required>
        </div>

        <div>
            <label for="checkout">วันที่เช็คเอาท์:</label>
            <input type="date" id="checkout" name="checkout" required>
        </div>

        <div>
            <label for="roomtype">ประเภทห้องพัก:</label>
            <select id="roomtype" name="roomtype" required>
                <option value="">กรุณาเลือกประเภทห้องพัก</option>
                <option value="standard">ห้องมาตรฐาน</option>
                <option value="deluxe">ห้องดีลักซ์</option>
                <option value="suite">ห้องสวีท</option>
            </select>
        </div>

        <div>
            <label for="guests">จำนวนผู้เข้าพัก:</label>
            <input type="number" id="guests" name="guests" min="1" max="4" required>
        </div>

        <button type="submit">จองห้องพัก</button>
    </form>
</body>
</html>
```
```css
body {
    font-family: 'Sarabun', sans-serif;
    max-width: 600px; /* กำหนดความกว้างสูงสุดของฟอร์ม */
    margin: 0 auto; /* จัดกลาง */
    padding: 20px;
    background-color: #f5f5f5;
}

h1 {
    color: #2c3e50;
    text-align: center;
    margin-bottom: 30px;
}

form {
    background-color: white;
    padding: 20px;
    border-radius: 8px; /* มุมโค้ง */
    box-shadow: 0 2px 4px rgba(0,0,0,0.1); /* เงา */
}

div {
    margin-bottom: 15px; /* ระยะห่างระหว่าง div */
}

label {
    display: block; /* แสดง label เป็นบล็อก */
    margin-bottom: 5px;
    color: #34495e;
    font-weight: bold;
}

input, select {
    display: block; /* แสดงเป็นบล็อก */
    width: 100%; /* ความกว้าง 100% */
    padding: 10px; /* เพิ่มระยะห่างภายใน */
    border: 1px solid #ddd;
    border-radius: 4px; /* มุมโค้ง */
    box-sizing: border-box; /* คำนวณขนาดของกล่อง */
    transition: border-color 0.3s, box-shadow 0.3s; /* เอฟเฟกต์การเปลี่ยนสีขอบ */
}

input:hover, select:hover,
input:focus, select:focus {
    outline: none; /* ไม่ให้มีขอบเมื่อ focus */
    border-color: #3498db; /* เปลี่ยนสีขอบเมื่อ focus */
    box-shadow: 0 0 5px rgba(52,152,219,0.3); /* เงาเมื่อ focus */
}

button {
    background-color: #2980b9;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 4px; /* มุมโค้ง */
    cursor: pointer;
    width: 100%; /* ความกว้าง 100% */
    font-size: 16px;
    transition: background-color 0.3s; /* เอฟเฟกต์การเปลี่ยนสี */
}

button:hover {
    background-color: #3498db; /* เปลี่ยนสีเมื่อ hover */
}

@media (max-width: 480px) {
    body {
        padding: 10px; /* ลดระยะห่างในมือถือ */
    }

    h1 {
        font-size: 24px; /* ขนาดฟอนต์หัวข้อในมือถือ */
    }
}
```
[รูปผลการทดลองที่ 3.2.2]
![image](https://github.com/user-attachments/assets/709cbecc-43ae-4355-8b85-a9dbb6ba7c5c)


## ขั้นตอนที่ 3.2.3: การเพิ่มฟังก์ชันด้วย JavaScript

เพิ่มโค้ด JavaScript ก่อนปิด `</body>`:

```html
<script>
    document.getElementById('bookingForm').addEventListener('submit', function(e) {
        e.preventDefault();
        
        // ตรวจสอบวันที่
        const checkin = new Date(document.getElementById('checkin').value);
        const checkout = new Date(document.getElementById('checkout').value);
        const today = new Date();
        
        if (checkin < today) {
            alert('กรุณาเลือกวันเช็คอินที่ยังไม่ผ่านมา');
            return;
        }
        
        if (checkout <= checkin) {
            alert('วันเช็คเอาท์ต้องมาหลังวันเช็คอิน');
            return;
        }
        
        // ตรวจสอบรูปแบบเบอร์โทร
        const phone = document.getElementById('phone').value;
        const phoneRegex = /^[0-9]{10}$/;
        if (!phoneRegex.test(phone)) {
            alert('กรุณากรอกเบอร์โทรศัพท์ให้ถูกต้อง (10 หลัก)');
            return;
        }
        
        // คำนวณจำนวนวันที่พัก
        const days = Math.ceil((checkout - checkin) / (1000 * 60 * 60 * 24));
        
        // แสดงสรุปการจอง
        const roomtype = document.getElementById('roomtype');
        const roomtypeText = roomtype.options[roomtype.selectedIndex].text;
        
        const summary = `
            สรุปการจอง:
            - ชื่อผู้จอง: ${document.getElementById('fullname').value}
            - ประเภทห้อง: ${roomtypeText}
            - วันที่เข้าพัก: ${checkin.toLocaleDateString('th-TH')}
            - วันที่ออก: ${checkout.toLocaleDateString('th-TH')}
            - จำนวนวันที่พัก: ${days} วัน
            - จำนวนผู้เข้าพัก: ${document.getElementById('guests').value} ท่าน
        `;
        
        if (confirm(summary + '\n\nยืนยันการจองห้องพัก?')) {
            alert('จองห้องพักเรียบร้อยแล้ว');
            this.reset();
        }
    });

    // เพิ่มการตรวจสอบวันที่แบบ Real-time
    document.getElementById('checkin').addEventListener('change', function() {
        document.getElementById('checkout').min = this.value;
    });

    // จำกัดจำนวนผู้เข้าพักตามประเภทห้อง
    document.getElementById('roomtype').addEventListener('change', function() {
        const guestsInput = document.getElementById('guests');
        if (this.value === 'standard') {
            guestsInput.max = 2;
        } else if (this.value === 'deluxe') {
            guestsInput.max = 3;
        } else if (this.value === 'suite') {
            guestsInput.max = 4;
        }
        
        if (guestsInput.value > guestsInput.max) {
            guestsInput.value = guestsInput.max;
        }
    });
</script>
```

### คำอธิบาย JavaScript:

1. ตรวจสอบความถูกต้องของข้อมูล:
   - วันที่เช็คอินต้องไม่เป็นวันที่ผ่านมาแล้ว
   - วันที่เช็คเอาท์ต้องมาหลังวันเช็คอิน
   - เบอร์โทรศัพท์ต้องมี 10 หลัก

2. เพิ่มฟังก์ชันการโต้ตอบ:
   - แสดงสรุปการจองก่อนยืนยัน
   - รีเซ็ตฟอร์มหลังการจอง
   - ปรับจำนวนผู้เข้าพักตามประเภทห้อง

3. การตรวจสอบแบบ Real-time:
   - ตรวจสอบวันที่เช็คอิน-เช็คเอาท์
   - ปรับจำนวนผู้เข้าพักสูงสุดตามประเภทห้อง
</body>
</html>
```

### ผลการทดลอง
ทดสอบปรับแต่ง JavaScript ในแต่ละส่วน แล้วอธิบายโค้ดในแต่ละส่วน เขียนสรุปผลการทดลองว่าได้ทดลองเปลี่ยนส่วนใด แล้วผลเป็นอย่างไร พร้อมแนบรูปประกอบการทดลอง

### บันทึกผลการทดลอง 3.2.3
```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ระบบจองห้องพักออนไลน์</title>
    <link rel="stylesheet" href="styles.css"> <!-- ลิงก์ไปยัง CSS -->
</head>
<body>
    <h1>แบบฟอร์มจองห้องพัก</h1>
    
    <form id="bookingForm">
        <div>
            <label for="fullname">ชื่อ-นามสกุล:</label>
            <input type="text" id="fullname" name="fullname" required>
        </div>

        <div>
            <label for="email">อีเมล:</label>
            <input type="email" id="email" name="email" required>
        </div>

        <div>
            <label for="phone">เบอร์โทรศัพท์:</label>
            <input type="tel" id="phone" name="phone" required>
        </div>

        <div>
            <label for="checkin">วันที่เช็คอิน:</label>
            <input type="date" id="checkin" name="checkin" required>
        </div>

        <div>
            <label for="checkout">วันที่เช็คเอาท์:</label>
            <input type="date" id="checkout" name="checkout" required>
        </div>

        <div>
            <label for="roomtype">ประเภทห้องพัก:</label>
            <select id="roomtype" name="roomtype" required>
                <option value="">กรุณาเลือกประเภทห้องพัก</option>
                <option value="standard">ห้องมาตรฐาน</option>
                <option value="deluxe">ห้องดีลักซ์</option>
                <option value="suite">ห้องสวีท</option>
            </select>
        </div>

        <div>
            <label for="guests">จำนวนผู้เข้าพัก:</label>
            <input type="number" id="guests" name="guests" min="1" max="4" required>
        </div>

        <button type="submit">จองห้องพัก</button>
    </form>

    <script src="script.js"></script> <!-- ลิงก์ไปยัง JavaScript -->
</body>
</html>
```
```js
document.getElementById('bookingForm').addEventListener('submit', function(e) {
    e.preventDefault();
    
    // ตรวจสอบวันที่
    const checkin = new Date(document.getElementById('checkin').value);
    const checkout = new Date(document.getElementById('checkout').value);
    const today = new Date();
    
    if (checkin < today) {
        alert('กรุณาเลือกวันเช็คอินที่ยังไม่ผ่านมา');
        return;
    }
    
    if (checkout <= checkin) {
        alert('วันเช็คเอาท์ต้องมาหลังวันเช็คอิน');
        return;
    }
    
    // ตรวจสอบรูปแบบเบอร์โทร
    const phone = document.getElementById('phone').value;
    const phoneRegex = /^[0-9]{10}$/;
    if (!phoneRegex.test(phone)) {
        alert('กรุณากรอกเบอร์โทรศัพท์ให้ถูกต้อง (10 หลัก)');
        return;
    }
    
    // คำนวณจำนวนวันที่พัก
    const days = Math.ceil((checkout - checkin) / (1000 * 60 * 60 * 24));
    
    // แสดงสรุปการจอง
    const roomtype = document.getElementById('roomtype');
    const roomtypeText = roomtype.options[roomtype.selectedIndex].text;
    
    const summary = `
        สรุปการจอง:
        - ชื่อผู้จอง: ${document.getElementById('fullname').value}
        - ประเภทห้อง: ${roomtypeText}
        - วันที่เข้าพัก: ${checkin.toLocaleDateString('th-TH')}
        - วันที่ออก: ${checkout.toLocaleDateString('th-TH')}
        - จำนวนวันที่พัก: ${days} วัน
        - จำนวนผู้เข้าพัก: ${document.getElementById('guests').value} ท่าน
    `;
    
    if (confirm(summary + '\n\nยืนยันการจองห้องพัก?')) {
        alert('จองห้องพักเรียบร้อยแล้ว');
        this.reset(); // รีเซ็ตฟอร์มหลังการจอง
    }
});

// เพิ่มการตรวจสอบวันที่แบบ Real-time
document.getElementById('checkin').addEventListener('change', function() {
    document.getElementById('checkout').min = this.value; // ตั้งค่าวันที่เช็คเอาท์ให้มากกว่าหรือเท่ากับวันที่เช็คอิน
});

// จำกัดจำนวนผู้เข้าพักตามประเภทห้อง
document.getElementById('roomtype').addEventListener('change', function() {
    const guestsInput = document.getElementById('guests');
    if (this.value === 'standard') {
        guestsInput.max = 2; // ห้องมาตรฐานสูงสุด 2 ท่าน
    } else if (this.value === 'deluxe') {
        guestsInput.max = 3; // ห้องดีลักซ์สูงสุด 3 ท่าน
    } else if (this.value === 'suite') {
        guestsInput.max = 4; // ห้องสวีทสูงสุด 4 ท่าน
    }
    
    if (guestsInput.value > guestsInput.max) {
        guestsInput.value = guestsInput.max; // ปรับจำนวนผู้เข้าพักถ้าจำนวนเกินสูงสุด
    }
});
```
[รูปผลการทดลองที่ 3.2.3]
![image](https://github.com/user-attachments/assets/48aaec2b-5ffd-43ac-be56-496bd5410ab1)


## คำแนะนำเพิ่มเติม
- ทดลองเขียนโค้ดทุกตัวอย่างด้วยตัวเอง
- ลองปรับเปลี่ยนค่าต่างๆ เพื่อดูผลลัพธ์ที่เปลี่ยนไป
- ใช้ Console ใน Developer Tools ของเบราว์เซอร์เพื่อดูผลลัพธ์และแก้ไขข้อผิดพลาด
- ทำความเข้าใจแต่ละบรรทัดของโค้ดก่อนที่จะไปศึกษาหัวข้อถัดไป (ใช้ GenAI เพื่อช่วยในการอธิบายได้)

## แหล่งเรียนรู้เพิ่มเติม
- MDN Web Docs: https://developer.mozilla.org/th/docs/Web/JavaScript
- W3Schools: https://www.w3schools.com/js/
- JavaScript.info: https://javascript.info/
