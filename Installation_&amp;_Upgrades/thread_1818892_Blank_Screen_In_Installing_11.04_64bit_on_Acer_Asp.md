---
title: "Blank Screen In Installing 11.04 64bit on Acer Aspire 4750G"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by caveman7 on 2011-08-05
My friend and I recently bought **Acer Aspire 4750G** laptops with the following specifications:
[B]Intel Core i5 2410M
6GB DDR3 RAM
nVidia GT540M Graphic Card[/B]

After installing Windows 7, I decided to install **Ubuntu 11.04 64bit** alongside Windows (dual boot). Hence, I download the .iso from Ubuntu's website and checked the md5 to verify its integrity.
I then created a bootable USB flashdisk using the latest edition of **Universal USB Installer**. Note that the flashdisk is brand new.

I booted from the flashdisk successfully. I chose the **"Try Ubuntu without Installing"** option but the screen went blank, with only **_** in the uppermost left side. I could not type anything. I left it for a few minutes but the screen remained blank. I switched off the laptop, booted again and chose **"Install Ubuntu"**. The same thing happened.

I then erased the contents of the flashdisk and made it bootable again using **Unetbootin** to no avail.

My friend (using laptop which is the same model as mine) also downloaded the .iso, created bootable flashdisk and booted from it. The same thing occurred.

What should I do? :confused:

---

### Post by Toz on 2011-08-05
Have a look at: [http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/]("http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/")

and

[http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535")

for things to try. Post back if you run into further problems.

---

### Post by mcwood on 2011-08-07
had the same problem. so instead opted burning iso to a DVD. However, it went straight to windows boot. so I check the BIOS for boot order & the 1st boot order is called windows boot manager. so i changed it by putting it the last boot order. After that, everything installed normally.

---

