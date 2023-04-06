# Learn refatoring

👋 สวัสดี, repo นี้จะเป็นการฝึก refactor React คับ เหมาะสำหรับคนที่เขียน React มาสักพัก

- จำเป็นต้องมีความรู้ React มาหน่อย (แต่จริงๆมือใหม่ก็ลองทำได้)
- ไม่จำเป็นต้องมีความรู้ CSS

## Introduction

ผมตั้งใจสร้าง repo นี้ขึ้นมาเนื่องจากเป็นโค้ดที่ผ่านการใช้งานมาจริงๆ และเป็น business requirement ที่เกิดขึ้นจริง เหมาะสำหรับการฝึกฝนมากๆ หวังว่าจะเป็นประโยชน์กับทุกๆท่านที่ผ่านมาเห็นนะครับ

โค้ดทั้งหมดผมได้มาจาก [MUI repository](https://github.com/mui/material-ui/blob/master/docs/src/components/productCore/CoreStyling.tsx#L75)

หลังจาก clone โปรเจคแล้วลองรัน `yarn && yarn dev`

จะได้หน้าจอแบบนี้ขึ้นมา

<img width="1605" alt="image" src="https://user-images.githubusercontent.com/18292247/230282137-f6269f4f-9de9-4fcd-9323-41b250d9e6df.png">

## How to practice

เพื่อให้เสมือนจริงมากที่สุด ให้เริ่มทำความเข้าใจโค้ดเองทั้งหมดว่า application นี้เกี่ยวกับอะไร ทำงานอย่างไร

ไฟล์ที่เกี่ยวข้อง

- `src/App.tsx`
- `src/useResizeHandle.js`

### TypeScript

สำหรับใครที่ต้องการฝึกฝนด้วย TypeScript ด้วย ให้ใช้ branch `typescript`.

## Challenges

### 1. Adjust width with arrow left and right key

เริ่มต้นตัวปุ่มรองรับเม้าส์และการสัมผัส เมื่อลากไปทางซ้ายจะเห็นว่ากล่องสีเทาจะมีความกว้างลดลง และเมื่อลากกลับมาทางขวากล่องสีเทาจะมีความกว้างมากขึ้น

โจทย์คือ เมื่อโฟกัสไปที่ปุ่ม (ด้วยการกด Tab) แล้วกดลูกศรซ้าย-ขวาที่คีย์บอร์ด ความกว้างต้องเปลี่ยนไปที่ละ 1px

### 2. Adjustable key press width diff and support SHIFT, ALT key

จากข้อ 1, ทำให้สามารถ custom ระยะที่เปลี่ยนแปลงเวลากด ลูกศร 1 ครั้ง

- ถ้ากด SHIFT ค้างไว้ด้วย ให้ เอาระยะนั้น คูณ 10
- ถ้ากด ALT ค้าง ระยะจะเป็น 1px เสมอ

### 3. Support hold

ถ้ากดลูกศรค้าง ความกว้างจะเปลี่ยนไปเรื่อยๆ แต่ต้องไม่เกิน `maxWidth` ที่กำหนดไว้
