---
title: "Computer reboots when I try to install"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by red96gsr on 2006-12-06
I am new to Ubuntu, and to linux. When I try to run Ubuntu from the disk or install it I get a message that says "UNCOMPRESSING LINUX...OK, BOOTING THE KERNEL", then my computer reboots itself. I  am using the DVD that comes with the Official Ubuntu book, and I have tried the following options:
  START OR INSTALL UBUNTU
  START UBUNTU IN SAFE GRAPHICS MODE
  INSTALL IN TEXT MODE
  INSTALL IN OEM MODE
  INSTALL A SERVER
  CHECK CD FOR DEFECTS
I get the same results every time. I am running Windows XP, but i tried doing a fresh install on an empty hard drive. Still the same thing, any idea what is wrong? I have tried two other disks as well, I have used both to install Ubuntu on two other computers.

My specs:
Compaq Presario
Celeron 2.7GHZ
768MB RAM
NVIDIA GeForce FX5200
Sound Blaster Live

---

### Post by pay on 2006-12-07
I don't think that you're doing anything wrong. Your hardware may not be playing nice with the install cd so you can try the alternate installation cd which installs in a text mode. Also the cd maybe corrupted so you might need to try to download that. Or you can try dapper which seems to be more hardware friendly.

---

### Post by red96gsr on 2006-12-08
I tried to install using the text mode, it does the same thing. I know the disk is good, i used to install on another computer. The disks I am using are Dapper Drake.

---

### Post by OzzyFrank on 2006-12-08
Hiya. OK, in my experience with installing with a corrupt CD is that it got as far as an OK one, but when installing and configuring apps, some of the .debs were listed as corrupt. While a CD fault could be anywhere and so have corrupted a vital install file, that has already been ruled out by use of the CD on another PC.

And with me, I couldn't get the install to go past errors stating I had no maths coprocessor, and using certain boot options made it worse, like rebooting the PC. In the end, it turned out to be a faulty memory module, which Windows was apparently OK with (for the time being) but was stopping Xubuntu in its tracks. After having to dump a 128Mb chip, and dropping the total RAM from 288Mb to 160Mb, the old P2 (or AMD K6-2 400, to be exact) not only could install from the "alternate CD" (the text-based install better for older PCs), but even run the Live CDs of both Xubuntu and Ubuntu. I suggest run the memtest86+ utility available in the install, and if an error comes up, pull out modules (if you have more than one) and run the test till you isolate which one it is. Then turf it.

Don't know if that will be of help, but it solved my installation woes, and that was on a pretty ancient PC too. (And in case you end up successfully installing, then your monitor turns off just before the login screen, it's a video card issue, hehe... jeez that was fun!).

OzzyFrank

---

### Post by altonbr on 2006-12-18
I had the same problem, and I posted it over here: [http://www.ubuntuforums.org/showthread.php?p=1902874#post1902874](http://www.ubuntuforums.org/showthread.php?p=1902874#post1902874). Seems to be a hardware issue, but it's too early to tell what's the specific component.

---

### Post by altonbr on 2006-12-18
I answered in that thread above that the answer MAY BE adding 

```
acpi=off
```

Has a flag when booting. Hit "F6" before trying to install in text mode, and enter the above command at the end of the line, before the "--". That should work.

---

### Post by red96gsr on 2006-12-28
Thanks, I will try that tonight.

---

