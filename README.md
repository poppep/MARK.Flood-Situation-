# ติดตั้งระบบรายงานอุทกภัยเป็นแอปมือถือ (PWA)

แอปนี้เป็น "เปลือก" ที่เปิดเว็บแอป Apps Script เต็มจอ มีไอคอนบนหน้าจอหลัก
เปิดแล้วไม่มีแถบเบราว์เซอร์ ข้อมูลทั้งหมดยังอยู่ที่ Apps Script / Google Sheets เหมือนเดิม

## ขั้นที่ 1: ตั้งค่า Apps Script
1. Deploy > Manage deployments > แก้ไข (ไอคอนดินสอ)
2. Execute as: **Me** / Who has access: **Anyone**
3. Deploy แล้วคัดลอก Web app URL (ลงท้าย `/exec`)

## ขั้นที่ 2: ใส่ URL
เปิดไฟล์ `config.js` แล้วแทนค่า `APP_URL` ด้วย URL ข้างบน

## ขั้นที่ 3: นำขึ้นโฮสต์ HTTPS (ฟรี)
PWA ต้องอยู่บน HTTPS เลือกอย่างใดอย่างหนึ่ง
- **GitHub Pages**: สร้าง repo → อัปโหลดไฟล์ทั้งโฟลเดอร์นี้ → Settings > Pages > Branch: main
- **Netlify Drop**: ลากโฟลเดอร์นี้ไปวางที่ app.netlify.com/drop
- **Cloudflare Pages / Firebase Hosting** ก็ใช้ได้

## ขั้นที่ 4: ติดตั้งบนมือถือ
- **Android (Chrome)**: เปิดลิงก์ → เมนู ⋮ → "ติดตั้งแอป" / "เพิ่มลงในหน้าจอหลัก"
- **iPhone (Safari)**: เปิดลิงก์ → ปุ่มแชร์ → "เพิ่มไปยังหน้าจอโฮม"

## ต้องการไฟล์ .apk (Android)
เข้า https://www.pwabuilder.com ใส่ลิงก์ของขั้นที่ 3 → Package for stores → Android
จะได้ไฟล์ .apk / .aab สำหรับแจกตรงหรือขึ้น Play Store

## หมายเหตุ
- ต้องมีอินเทอร์เน็ตเสมอ (ออฟไลน์จะเห็นหน้า "ลองอีกครั้ง")
- GPS: ครั้งแรกจะมีป๊อปอัปขออนุญาตตำแหน่ง ให้กด "อนุญาต"
- ถ้าแก้โค้ด Apps Script ต้อง Deploy เป็น version ใหม่ (URL เดิมใช้ต่อได้)
- เปลี่ยนไอคอนได้โดยแทนไฟล์ใน `icons/` (192, 512, maskable-512)
