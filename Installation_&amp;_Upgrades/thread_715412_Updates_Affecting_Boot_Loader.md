---
title: "Updates Affecting Boot Loader"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by UChris on 2008-03-04
Hello,
I have Ubuntu 7.10 installed on a Toshiba Satellite laptop.  I installed three or so months ago to try out Ubuntu, and (up until very recently) was dual booting with Windows XP.  I say very recently because, as of my last restart, grub no longer shows the Windows XP option.
I haven't actually used my Ubuntu partition for a couple months as school has taken the most of my time, so, when I chose to see how it was doing tonight, I thought downloading updates would be a good idea.  After the updates were downloaded and installed, I restarted as suggested by Ubuntu.  Upon restarting, I noticed that the (previously default) choice of Windows XP in my grub bootloader was absent.

Any ideas as to why this happened, and how I could fix it?

---

### Post by overdrank on 2008-03-04
> **UChris said:**
> Hello,
I have Ubuntu 7.10 installed on a Toshiba Satellite laptop.  I installed three or so months ago to try out Ubuntu, and (up until very recently) was dual booting with Windows XP.  I say very recently because, as of my last restart, grub no longer shows the Windows XP option.
I haven't actually used my Ubuntu partition for a couple months as school has taken the most of my time, so, when I chose to see how it was doing tonight, I thought downloading updates would be a good idea.  After the updates were downloaded and installed, I restarted as suggested by Ubuntu.  Upon restarting, I noticed that the (previously default) choice of Windows XP in my grub bootloader was absent.

Any ideas as to why this happened, and how I could fix it?

HI and you can change that by editing the gksudo gedit /boot/grub/menu.lst and this is a good link
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by kool_kat_os on 2008-03-04
> **UChris said:**
> Hello,
I have Ubuntu 7.10 installed on a Toshiba Satellite laptop.  I installed three or so months ago to try out Ubuntu, and (up until very recently) was dual booting with Windows XP.  I say very recently because, as of my last restart, grub no longer shows the Windows XP option.
I haven't actually used my Ubuntu partition for a couple months as school has taken the most of my time, so, when I chose to see how it was doing tonight, I thought downloading updates would be a good idea.  After the updates were downloaded and installed, I restarted as suggested by Ubuntu.  Upon restarting, I noticed that the (previously default) choice of Windows XP in my grub bootloader was absent.

Any ideas as to why this happened, and how I could fix it?

i didnt read your post.....but if it installed a new kernel it resets the /boot/grub/menu.lst

---

### Post by mikewhatever on 2008-03-05
> **UChris said:**
> Hello,
I have Ubuntu 7.10 installed on a Toshiba Satellite laptop.  I installed three or so months ago to try out Ubuntu, and (up until very recently) was dual booting with Windows XP.  I say very recently because, as of my last restart, grub no longer shows the Windows XP option.
I haven't actually used my Ubuntu partition for a couple months as school has taken the most of my time, so, when I chose to see how it was doing tonight, I thought downloading updates would be a good idea.  After the updates were downloaded and installed, I restarted as suggested by Ubuntu.  Upon restarting, I noticed that the (previously default) choice of Windows XP in my grub bootloader was absent.

Any ideas as to why this happened, and how I could fix it?

You should move the Windows entry to the very end of the file.
[http://ubuntuforums.org/showthread.php?t=712662](http://ubuntuforums.org/showthread.php?t=712662)

---

