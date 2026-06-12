---
title: "grub reinstall problems, exit code 20"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by tim67 on 2006-07-29
Hi

I have winxp on one hd and ubunto on anouther . I had a working
system, but due to windows re-install i can only boot windows.

i tried the live-cd, but it hangs up on keyboard detection, 

i then tried the installation disk in rescue mode. i tried to 
re-install grub, but the installation program gave a 
"grub-reinstall failed with exit code 20" message

is there something i could try before re-installing ubuntu ?

-timo

---

### Post by marcher on 2006-08-27
I get its problem . How to ? Help me Please

---

### Post by tim67 on 2006-09-17
I got it working now :)
somehow the MBR got write-protected, possibly when i tried 
GAG boot manager. I un-installed it, so the MBR was fixed
( or restored ? ) .

Then I ran the dapper drake 6.06 install cd in rescue mode, 
and i managed to write grub to 1st hard disk. 

now it seems that the data & user accounts etc. are ok, 
and I can use grub to boot to linux / Xp

-Timo

---

