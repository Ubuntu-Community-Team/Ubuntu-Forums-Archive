---
title: "LUBUNTU 11.10 No screens found"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by deepak115 on 2012-02-12
I have recently installed lubuntu 11.10 on my netbook.
Benq Joybook lite  U121 Eco

I find the error no screens found after I try to startx

the X.org  log shows these too
No screen section
No layout section
Screen-- "default screen section " (0)


I also tried nomodeset, but the same problem persisted. 
Please suggest me. The earlier version 10.4 worked well. But this one refuses as X
I can login via tty and updated the system too.
Please help me out,
thanq

deepak

---

### Post by Rodney9 on 2012-02-12
Did you have this problem using the Live CD ?

Help on installing Lubuntu - 

[https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu)




For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Rex Bouwense on 2012-02-12
I think Rodney9 is on the right track.  If everything worked when you tried the live CD, that would be one thing.  However, if you didn't try it before you installed you could have had a bad download or even a bad burn.  Try creating a bootable flash drive after you check the MD5Sum.  If the hash doesn't check out you may have to download again.

---

### Post by deepak115 on 2012-03-14
Hi,
Thanq. I figured that out atlast. That was due to the X refusing to startup. Just installed the emgd ppa and emgd-xorg-conf and it started the x automatically. BTW, the tty worked for me with the wireless out of the box. Thats what helped me. Downloaded ~60MB of the dependencies and finally DONE. Thanq

deepak

---

