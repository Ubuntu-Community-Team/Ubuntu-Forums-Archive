---
title: "i need a bit of help :)"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by applesios on 2011-08-11
i have a lot of hard drives or whatever it's called 

here take a look :

[IMG]http://i51.tinypic.com/2vnmeyq.jpg[/IMG]

if you cant undetstand anything it's beacuse my windows is in hebrew

as you see F: drive is the one with the biggest GB available 

if i will install it there, will i be able to uninstall it later?

THANKS :guitar:

---

### Post by sanderd17 on 2011-08-11
> **applesios said:**
> 

if you cant undetstand anything it's beacuse my windows is in hebrew

as you see F: drive is the one with the biggest GB available 

if i will install it there, will i be able to uninstall it later?

THANKS :guitar:

If you install Ubuntu via Wubi (inside Windows), than you can uninstall it via the windows add/remove-software utility. 

If you install it as a pure dual boot (by booting from the Ubuntu CD), than it will create another new partition for Ubuntu. If you later want to uninstall Ubuntu, you will have to delete that partition, enlarge another one and repair the windows bootloader with a windows repair disk.

Wubi is very suited for "longer testing periods" of 1 to 6 months. If you use Ubuntu for a longer time, a wubi installation can become unstable because of problems with the Windows partition format.

---

### Post by haqking on 2011-08-11
LOL

well what are you trying to install to it ?

I assume you mean you want to Dual Boot Ubuntu with Windows and install it to that drive ?

---

### Post by lmarmisa on 2011-08-11
I recommend to install Ubuntu with Wubi. If you do not feel comfortable with Ubuntu, you will be able to uninstall it like any other windows program. 

This video could help you:

[http://www.youtube.com/watch?v=iW1V6TuZZmc](http://www.youtube.com/watch?v=iW1V6TuZZmc)

Do not forget to select the volume **F: **during the install process. About 15 GB could be a good size for your Ubuntu.

Best regards,

Luis

---

### Post by ~!geek!~ on 2011-08-11
You may install ubuntu using either wubi installer or by booting the live cd (or usb) having ubuntu and installing it in separate partition. I m assuming you intend to install ubuntu using wubi (i.e. logging into windows 7 and then trying to install ubuntu as another program). If its the case, you are installing ubuntu as any other program in windows. So you can uninstall it as any other program.

---

### Post by applesios on 2011-08-12
LOL people i meant installing it with WUBI on F: drive, will i be able to uninstall it later? :P

---

### Post by sanderd17 on 2011-08-12
> **sanderd17 said:**
> If you install Ubuntu via Wubi (inside Windows), than you can uninstall it via the windows add/remove-software utility. 


            ^^

---

