---
title: "[SOLVED] 231GB Partion Ubuntu reporting 100Gb free"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by acdcfan on 2008-09-29
Just as title says..... 
I have installed Ubuntu on 231Gb partition but Ubuntu is reporting 100Gb free. I have gone through all the folders and maximum amount I could come up with, by looking at all the folders under device /dev/sdc1 is around 20GB
Screen shot below shows file system 
[http://img297.imageshack.us/img297/5444/screenshotqk1.png](http://img297.imageshack.us/img297/5444/screenshotqk1.png) 

Where does second dvfs-fuse-daemon coming from and why do I have such incorrect reporting of a free space. 

On another note How do I stop file check or whatever it is at the start up? 

Thanks upfront

---

### Post by Bakon Jarser on 2008-09-29
Applications > Accessories > Disk Usage Analyzer

---

### Post by acdcfan on 2008-09-29
> **Bakon Jarser said:**
> Applications > Accessories > Disk Usage Analyzer 

Got it sorted...thanks for pointing me the right direction 
It was virtual Mac OSX I created but could not get to work.. 
I deleted and got 100GB back not showing as 200.4Gb available :)

---

### Post by acdcfan on 2008-09-29
What about stopping file or whatever it is checking at logo screen. By pressing Esc button you cancel it, but can it be stopped all together through a command line

---

### Post by Bakon Jarser on 2008-09-29
I think there are ways to stop it but it's good for the system to check it.  It only does it I think once every thirty boots.  I know I read somewhere that somebody figured out how to move it to shutdown instead of startup.  You'll have to do your own googling though.

---

