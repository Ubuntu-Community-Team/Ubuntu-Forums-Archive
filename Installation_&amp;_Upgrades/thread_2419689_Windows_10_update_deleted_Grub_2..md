---
title: "Windows 10 update deleted Grub 2."
date: 2019-05-24
forum: Installation &amp; Upgrades
---

### Post by 1488-based on 2019-05-24
May I please have some information on how I can restore my Grub boot loader. I am dual booting Windows 10 and Linux Ubuntu 19.04. I can still boot into Ubuntu but I have to go through the BIOS everytime. What is the best and easiest way I can restore Grub to my bootloader partition.?

Cheers.

---

### Post by RobGoss on 2019-05-25
Hello, Can you tell me why you need to restore the boot loader? was your system not booting correctly as a dual boot just wondering

You can take a look at this video it should help you with your grub loader problem
[https://www.youtube.com/watch?v=i97y5Y2nChs](https://www.youtube.com/watch?v=i97y5Y2nChs)


Boot repair 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Rubi1200 on 2019-05-25
Before making any changes, I recommend booting with a LiveUSB (should be same version as your installed version) and running the boot info summary (see link in my signature). Please do not repair anything, just choose to create a summary and post here so we can advise on the next steps.

Thanks.

---

### Post by yancek on 2019-05-25
You could try booting Ubuntu and from a terminal, run the command:  sudo efibootmgr and take a look at or post the output here if you don't understand it.  Might have changed the priority from Ubuntu to windows.  Best thing to do which will provide more information is to run boot repair with the Create BootInfo Summary option suggested above.

---

### Post by pablosquared on 2019-05-26
Try Refind to re-establish boot control. Make a bootabe USB or CD/DVD disk with Refind on it. It'll allow you to boot Linux, from where you should be able to establish a permanent fix, with Refind as your boot manager.

[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by 1488-based on 2019-05-26
Cheers everyone for the information. I have managed to fix it by changing the boot order in my BIOS.

Cheers.

---

### Post by RobGoss on 2019-05-27
That's good to hear' you can mark this thread as **solved **if you have fixed the issue. Please use the Thread Tool tab at the top of this post

---

