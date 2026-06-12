---
title: "Vista Ubuntu &amp; XP Triple boot"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by slinkydonkey on 2008-11-09
Hello All

I am trying to get my laptop to triple boot with Vista, Ubuntu & XP.

So far I have got dual boot to work with Vista & Ubuntu 8.10 but next I want to install XP.  I have created another partition for XP but when I boot off the XP CD it says it can't find the harddisk.

I have looked [here ]("http://ubuntuforums.org/showthread.php?t=327781&highlight=triple+boot") & [here ]("http://ubuntuforums.org/showthread.php?t=724817") but to be honest its just confused me.  

I guess I need to reenable the VISTA boot loader as the Grub loader can't be seen by the XP install setup?

Anytips? ](*,)

---

### Post by And6ate9 on 2008-11-18
when triple booting windows you have to start with the oldest operating system first. 

Try doing Winxp - Vista - Ubuntu. That's may work.  

You can search for the reason why this must be done in the forums

---

### Post by Mikeyp926 on 2008-11-18
Yes, I'm currently triple-booting, and I installed xp first, then vista, then ubuntu.  When you turn on your machine grub will give you the option to boot ubuntu or to enter the vista boot loader.  The vista boot loader will then give you the option to boot vista or xp.  This method has worked perfectly so far for me.

---

