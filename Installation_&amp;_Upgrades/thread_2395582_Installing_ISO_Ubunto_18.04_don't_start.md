---
title: "Installing ISO Ubunto 18.04 don't start"
date: 2018-07-03
forum: Installation &amp; Upgrades
---

### Post by altagracience on 2018-07-03
I'm trying to install Ubuntu 18.04 from usb stick but that is impossible. The instalation doesn't begin. I only can select lenguage and then than freeze every. 
I did download the iso two time and checked that.
Computer: new HP pavilion power 15, whitout OS
I can move the mouse but can't select anything

---

### Post by kansasnoob on 2018-07-04
Probably GeForce GTX 1050 graphics? You might try running the live session with the nomodeset boot parameter. Do you know how to do that? Then after installing probably install the nVidia drivers.

---

### Post by altagracience on 2018-07-04
Can you explain please?

---

### Post by The Cog on 2018-07-04
[https://www.youtube.com/watch?v=fA9Kw8jqaP8](https://www.youtube.com/watch?v=fA9Kw8jqaP8)
Nomodeset tells it not to try to change the graphics mode, which is probably what's going wrong.

---

### Post by altagracience on 2018-07-04
Love you!!!!! Thanks, that works

---

