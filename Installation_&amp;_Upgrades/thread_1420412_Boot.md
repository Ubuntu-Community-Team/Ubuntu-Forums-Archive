---
title: "Boot"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by ezrayst on 2010-03-03
Hey all
I just want some help in starting uBuntu

I installed Windows 7 First then give partition space of 25 GB for my Ubuntu
However, I prefer using Windows 7 BootLoader instead of using Ubuntu BootLoader
can anyone help me in changing that?

Thanks so much

---

### Post by sinurge on 2010-03-03
> **ezrayst said:**
> Hey all
I just want some help in starting uBuntu

I installed Windows 7 First then give partition space of 25 GB for my Ubuntu
However, I prefer using Windows 7 BootLoader instead of using Ubuntu BootLoader
can anyone help me in changing that?

Thanks so much
I do not think you can do a dual boot using the windows boot loader and it wont recognize the times when the linux kernals are updated.

You would be better suited by putting the new grub setup

---

### Post by ezrayst on 2010-03-03
I cant? i think i will be alrite
but since I use windows more frequently, i think it is essential to set the bootloader by windows :D

---

### Post by louieb on 2010-03-03
Take a look at [EasyBCD]("http://neosmart.net/dl.php?id=1")   -

---

### Post by presence1960 on 2010-03-03
> **ezrayst said:**
> I cant? i think i will be alrite
but since I use windows more frequently, i think it is essential to set the bootloader by windows :D

That does not matter. GRUB will allow you to boot into windows every time you boot and never use ubuntu if that is what you want to do. or it will let you boot windows 999 times out of 1,000 times. Your statement is incorrect. But if you want to use the windows bootloader try Easy BCD as louieb suggests (yuukkkk- I can't believe i just said that! GRUB is way more simple and way more versatile than windows or Easy BCD)

---

