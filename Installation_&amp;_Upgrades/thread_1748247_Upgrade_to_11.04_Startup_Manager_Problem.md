---
title: "Upgrade to 11.04 Startup Manager Problem"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by fredberry on 2011-05-03
I successfully upgraded my dual boot system from 10.10 to 11.04. Prior to the upgrade startup manager would allow me to set which OS to boot as default. After the upgrade I am unable to set XP as my default boot. It seems as if startup manager is accessing a previous 'boot text file' (don't know what you call it) rather than the one created w/11.04. How do I solve this?

Thanks in advance.

Fred

---

### Post by Epek12 on 2011-05-04
Yes, I have similar problem, only I have Windows7 in dual boot with ubuntu 11.04. After the upgrade from 10.10 it will not set up win7 as the default system. How do I fix this, since I'm not the only one using this computer, and other users need win7?

Thanks in advance.

---

### Post by Epek12 on 2011-05-04
> **fredberry said:**
> I successfully upgraded my dual boot system from 10.10 to 11.04. Prior to the upgrade startup manager would allow me to set which OS to boot as default. After the upgrade I am unable to set XP as my default boot. It seems as if startup manager is accessing a previous 'boot text file' (don't know what you call it) rather than the one created w/11.04. How do I solve this?

Thanks in advance.

Fred

Hy Fred,

try this [http://ubuntuforums.org/showthread.php?p=10645791](http://ubuntuforums.org/showthread.php?p=10645791)

so basiclly, in startup manager just set to the option before last, that's what I did, and now it boots win7. As "hari-home" says, it's probably bug in startup manager. 

If somebody has a better solution, please say so.

---

### Post by robertj20112 on 2011-08-29
> **fredberry said:**
> I successfully upgraded my dual boot system from 10.10 to 11.04. Prior to the upgrade startup manager would allow me to set which OS to boot as default. After the upgrade I am unable to set XP as my default boot. It seems as if startup manager is accessing a previous 'boot text file' (don't know what you call it) rather than the one created w/11.04. How do I solve this?

Thanks in advance.

Fred

Here's what worked for me: During the boot process, I counted down the (shortened) list of choices, including the submenu "previous ubuntu version" as one, to the line of the desired default.  If that was number 5, for example, then in Startup Manager, I selected the fifth item in the drop-down list, NO MATTER WHAT THE NAME OF THAT ITEM WAS.  Upon reboot, my desired default was highlighted and chosen.  (This may be the same process as described by Epek12, but I was not sure, thus this response.)

---

### Post by jerrrys on 2011-08-29
[http://ubuntuforums.org/showthread.php?t=1794689](http://ubuntuforums.org/showthread.php?t=1794689)

---

### Post by ovicious on 2012-01-03
I configured startup manager as following--
Changed Resolution


After that whenever I boot, in the Grub menu I cannot select any other OS. The menu has become frozen.

---

