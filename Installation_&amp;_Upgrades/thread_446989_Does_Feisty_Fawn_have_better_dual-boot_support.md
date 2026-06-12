---
title: "Does Feisty Fawn have better dual-boot support?"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by Robert A. Morin on 2007-05-17
I was wondering if Feisty Fawn had better support for dual-booting with Vista than Dapper Drake did. 
Was this one of the issues that Ubuntu tackled, or hasn't this been perfected yet?

---

### Post by tgm4883 on 2007-05-17
What do you mean by better dual boot support?  Isn't that controlled by grub?

---

### Post by 24x30cl on 2007-05-17
Dapper didnt pose any problems at all when i installed it next to my XP Pro install. Took some time for me to figure out how to make windows the first choice on bootup though.

But im sure that if you have a specific problem the nice people here can help ;)

---

### Post by Robert A. Morin on 2007-05-17
Yes, I knew about GRUB, but if you remember, that if you didn't partition correctly, Vista would not be recognized, and GRUB would only list Ubuntu.  I'm not too sure if THAT'S been corrected, is where I was getting at.

---

### Post by tgm4883 on 2007-05-17
> **Robert A. Morin said:**
> Yes, I knew about GRUB, but if you remember, that if you didn't partition correctly, Vista would not be recognized, and GRUB would only list Ubuntu.  I'm not too sure if THAT'S been corrected, is where I was getting at.

If that's the problem, it is a real easy fix

---

### Post by Grogger on 2007-05-28
tgm, 

So what is that easy fix?  I'm having that exact problem.  I have a vaio laptop with Vista preinstalled.  I installed ubuntu dapper in the free space and found that vista wasn't listed in the grub boot menu when I rebooted.  I  attempted to add the first listing to my /boot/grub/menu.lst file with gedit that says: 
"title  Windows Vista
root  (hd0,1)
makeactive
chainloader +1"

However when I try to boot grub to that listing I receive an error message:
"Filesystem type unknown, partition type 0x7
makeactive
chainloader +1

Error 13: Invalid or unsupported executable format"

I'm not really sure where to go from here.  My hope is to be able to dual boot vista and ubuntu.  

btw:  I have only one 80gb hard drive that is sata.  

Thanks for the help.

---

### Post by Grogger on 2007-05-28
One other complication.  There is a restore partition that came preinstalled with my vista laptop too.  I found that this is located at root (hd0,0) in my grub file.  I think the regular vista install is in root (hd0,1) but doesn't load properly from grub and then the ubuntu install is located at root (hd0,2).  ;)   I'm finding this isn't the simplest install yet.  :?

---

