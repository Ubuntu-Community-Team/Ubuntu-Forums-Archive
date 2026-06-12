---
title: "Boot problem with Hardy -"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by Coppper on 2008-08-30
Hello  , 

 I have just upgrade to hardy and i think there are some problems with it.
  
  I have problems  when booting with the latest version of the kernel (black screen) but it's fine when booting with the previous one .
Is there a solution for that .

If i want to go back to Gutsy , how can i do that ?

---

### Post by Pumalite on 2008-08-30
See if you can get into Recovery Mode of the latest kernel and there try 'xfix' (fix broken packages first and if that doesn't work; try fix xserver.

---

### Post by linux_tech on 2008-08-30
what are your system specs?
Are you able to boot into recovery mode and use the command startx?
at the blinking curser black screen can you press ctrl+alt+f1
to go to a command prompt 
then try typing in-  startx

---

### Post by Coppper on 2008-08-31
I haven't tried to boot on recovery mode , but i noticed that when booting
with the second option(an older version of kernel) everything is ok.

This is the one that works

 Ubuntu 8.04, kernel 2.6.22-15-generic

So , i just modify /boot/grub/menu.lst to change the order and set the 
default option to kernel 2.6.22-15-generic

Should i try what you comment to try to fix it up ? 
I don't know if i'm going to have problems because of using an older version

---

### Post by Pumalite on 2008-08-31
Trying what I suggested you loose nothing except time. Your second kernel is there to boot if you need it.

---

