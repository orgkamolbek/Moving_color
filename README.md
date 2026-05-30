# 🎆 Moving Colors: Interactive Particle Physics Engine

HTML5 Canvas API va zamonaviy JavaScript (ES6+ OOP) sinflari yordamida yaratilgan, sichqoncha harakatiga sezgir generativ zarrachalar tizimi (Particle System). Loyiha koordinatalar tizimida fizika qonuniyatlarini simulyatsiya qilish, obyektlarning hayot aylanish siklini boshqarish va real vaqt rejimida yuqori unumdorlikka ega animatsiyalarni render qilish mexanizmlarini namoyish etadi.

---

## 📝 Loyiha haqida

Ushbu veb-ilova foydalanuvchining kursor harakatlariga javob beruvchi interaktiv raqamli poligon hisoblanadi. Sichqoncha harakatlanganda kursor koordinatalaridan har tomonga tasodifiy tezlikda sochiluvchi va vaqt o'tishi bilan kichrayib so'nuvchi kamalak rangli mikro-zarralar oqimi generatsiya qilinadi. Tizim to'liq matematik va algoritmik asosda ishlaydi.

---

## 📐 Algoritmik Arxitektura va Zarralar Simulyatsiyasi (Kinematics Lifecycle)

Har bir zarracha (Particle) xotirada mustaqil obyekt sifatida shakllanadi va o'yin sikli (`requestAnimationFrame`) ichida quyidagi hayotiy bosqichlarni bosib o'tadi:

1. **Generatsiya (Spawning):** `mousemove` hodisasi har safar ishlaganda kursor nuqtasida 5 ta yangi `Particle` nusxasi yaratilib, `particlesArray` massiviga yuklanadi.
2. **Kinematik Harakat:** Har bir kadrda zarracha koordinatalari uning shaxsiy tezlik vektoriga mos ravishda siljiydi:
   $$X_{new} = X_{current} + SpeedX$$
   $$Y_{new} = Y_{current} + SpeedY$$
3. **Masshtab so'nishi (Fade Out):** Zarracha harakatlangani sayin uning radiusi (`size`) chiziqli ravishda kamaytirib boriladi.
4. **Xotirani Tozalash (Garbage Collection):** Agar zarracha o'lchami kritik nuqtadan (`size <= 0.3`) kichrayib ketsa, u `splice()` metodi orqali massivdan butunlay o'chiriladi.

---

## ⚡ Asosiy xususiyatlari (Features)

* 🎨 **Dynamic HSL Spectrum:** Ranglar generatorida `hsl(hue, 100%, 50%)` modelidan foydalanilgan bo'lib, bu yerda `hue` qiymati 0 dan 360 gacha tasodifiy tanlanishi orqali mukammal kiber-kamalak effekti hosil qilinadi.
* ⚛️ **Object-Oriented Physics (OOP):** Har bir zarrachaning o'z xususiyatlari (pozitsiya, o'lcham, rang, tezlik) va metodlariga (`update()`, `draw()`) ega bo'lgan klass tuzilmasida boshqarilishi.
* 🌀 **Customizable Motion Trail:** Kod tarkibida ekranni tozalashning muqobil varianti (iz qoldirish effekti) `rgba(0,0,0,0.1)` yarim shaffof qatlami bilan izoh holatida tayyor qoldirilgan.
* 📈 **High-Performance Rendering:** Brauzerning grafik quvvatini optimallashtiruvchi va silliq $60\text{ FPS}$ animatsiyani ta'minlovchi `requestAnimationFrame` tizimi.
* 🖥️ **Fluid Viewport Resize:** Oyna o'lchami o'zgarganda (`resize`) canvas o'lcham
