# ตารางเรียน & กิจกรรมมหาลัย

เว็บ static + Vercel Function ตัวเดียว (`api/calendar.js`) ที่สร้างไฟล์ปฏิทิน .ics จาก `data.json`
ไม่มี dependency ไม่ต้อง build

## Deploy
1. อัปโฟลเดอร์นี้ขึ้น GitHub แล้ว Import ใน Vercel (Framework: Other, ไม่ต้องใส่ Build Command)
   หรือรัน `npx vercel --prod` ในโฟลเดอร์นี้
2. เปิดโดเมน production ที่ Vercel ให้ (เช่น https://ชื่อโปรเจกต์.vercel.app)

## แก้ข้อมูล (ฝั่งมหาลัย)
แก้ `data.json` ที่เดียว แล้ว push — หน้าเว็บและปฏิทินที่นักศึกษาสมัครรับไว้จะอัปเดตตาม
- `classes[].day`: 1=จันทร์ ... 7=อาทิตย์
- `events[]`: ใส่ `"allday": true` สำหรับกิจกรรมทั้งวัน (ใช้ `to` เป็นวันสุดท้ายถ้าหลายวัน)

## ลิงก์ปฏิทิน
- `/calendar.ics` ทั้งหมด · `/classes.ics` เฉพาะตารางเรียน · `/events.ics` เฉพาะกิจกรรม

## ข้อควรรู้
- ปฏิทินที่สมัครรับเป็นแบบอ่านอย่างเดียว และ Google Calendar อาจใช้เวลาหลายชั่วโมงในการซิงก์การแก้ไข
- ให้นักศึกษาใช้โดเมน production เท่านั้น เพราะ Preview Deployment อาจติด Deployment Protection ทำให้ปฏิทินดึงไฟล์ไม่ได้
- ปุ่ม "เพิ่มลง Google Calendar" ทีละรายการเป็นลิงก์สำเร็จรูป ไม่ต้องพึ่งเซิร์ฟเวอร์
