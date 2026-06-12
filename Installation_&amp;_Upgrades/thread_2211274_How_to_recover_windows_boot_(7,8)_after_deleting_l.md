---
title: "How to recover windows boot (7,8) after deleting linux partition (swap+ext4)?"
date: 2014-03-15
forum: Installation &amp; Upgrades
---

### Post by ajroxx16 on 2014-03-15
Hello in this post i will be telling you a method which i discovered just now on how to recover windows boot after deleting linux partition.

I did a mistake yesterday that i installed ubuntu studio 12 on my laptop alongside of windows 8.
Installation was easy but now i wanted to try kali linux i.e for web penetration testing, soh i read some threds on how to remove linux distros from dual boot.

They suggested to delete linux partition from windows partition manager and then run a recovery, I had window 8.
i wanted to do some experiment so i made a bootable kali-linux pendrive , deleted my ubuntu studio partition and did **not recover my windows, **that was a big mistake.

Soh i booted to kali live to see how it looks and installed it through "install kali" given in menu. It did not install and gave me error regarding bootloader
it cannot find any bootloader location.

I tried searching "bootable pendrive from ubuntu" but installation failed in kali and even it's software center was unable to give me results.
Unetbootin is a software which makes pendrive bootable and was pre installed in kali but it made only linux based live images bootable not windows. There are other apps too but they works only in ubuntu not kali, i guess.

Soh after various methods i tried creating a bootable pendrive or recovering boot loader, at 3am i was exausted.
So i decided to install ubuntu inorder to install **winusb** which makes windows image bootable through ubuntu.
So i installed ubuntu 12.10  and luckily it asked me weather to install alongside of windows 8 or not.
I installed and i recovered my window 8 too.
I am not dualbooting ubuntu and window 8. :)

Here is the solution to this problem.
[http://askubuntu.com/questions/149674/how-to-create-or-recover-windows-bootloader-after-deleting-ubuntu-boot-drive](http://askubuntu.com/questions/149674/how-to-create-or-recover-windows-bootloader-after-deleting-ubuntu-boot-drive)

---

