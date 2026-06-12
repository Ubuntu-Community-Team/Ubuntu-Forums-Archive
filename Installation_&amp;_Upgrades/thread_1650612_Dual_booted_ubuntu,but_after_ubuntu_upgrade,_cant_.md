---
title: "Dual booted ubuntu,but after ubuntu upgrade, cant boot windows or ubuntu"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by Aubrey42 on 2010-12-21
Well i have two hard drives, i used wubi on windows (which is on my c: drive) to put ubuntu 10.10 on my d: drive. Everything was running smoothly until the update manager uptated ubuntu. When the installation  was completed, i was told to restart. So i did. When it restarted, nothing happened. My computer froze and i cant access wondows or ubuntu, and i cant change anything.

Please help!!! :confused:

---

### Post by garvinrick4 on 2010-12-21
What disks do you have:
Ubuntu install Cd
Windows recovery Cd
and which do you want to try to boot first?
Run this script in Ubuntu live cd (install cd with try ubuntu)
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
download to desktop and then run this below in terminal will put a file Called results
on desktop capy and paste in this thread, after copied to Message box highlight whole
thing and hit the # in upper right of message box. Puts it in nice little box to read in.

```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by Aubrey42 on 2010-12-21
I used wubi to put it on so i dont have the live cd and i cant get onto anything. After the system option screen shows when i turn the pc on, nothing boots and i cant even get to the boot menu. and i figured that using the windows cd would work but i was hoping to find another way where i didnt lose everything

---

### Post by garvinrick4 on 2010-12-21
> **Aubrey42 said:**
> I used wubi to put it on so i dont have the live cd and i cant get onto anything. After the system option screen shows when i turn the pc on, nothing boots and i cant even get to the boot menu. and i figured that using the windows cd would work but i was hoping to find another way where i didnt lose everything
Ok lets get windows booting so you can get a live cd and fix WUBI. Use the xp/vista/7 link below.
[WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?") 
[[wubi] Wubi megathread - ]("http://ubuntuforums.org/showthread.php?t=1639198")
[Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1639198")[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by garvinrick4 on 2010-12-21
Wubi is a folder in C: drive right next to Users that says Ubuntu. It is formatted in ext which Windows cannot read. It also attaches itself to Windows boot manager to boot so it
has its own special procedures to fix as you can see in the links I gave you.
Put WUBI in your title so Wubi users can see and chime in.

---

### Post by Aubrey42 on 2010-12-21
awesome thx ill try it tomorrow

---

### Post by bcbc on 2010-12-22
+1 to garvinrick4's advice.

Reinstall the windows bootloader (you don't need to worry about the bootsector).

This assumes that when you boot you are getting a grub rescue> prompt. If you are, then likely you actually installed 10.04.1 Ubuntu (not 10.10). The ubuntu.com website doesn't state this, but the windows-installer (wubi) option is still set at release 10.04.1.

In future, try to avoid updating packages grub-pc and grub-common.

---

### Post by Aubrey42 on 2010-12-23
because my ubuntu was on my d drive, i just ended up putting it in my brothers old computer which has xp running, then i booted the windows, and then just formatted the drive that had ubuntu on it. But thanks for the advice because i still need that other hd to run windows... Also, im thinking about trying ubuntu one more time but with my brothers old cpu so it wont matter if it crashes. If i do, is it really necessary that i install the updates with the update manager? Or do i need them?

---

### Post by bcbc on 2010-12-23
those grub updates are actually designed for people upgrading to from an older release (e.g. 9.10) to 10.04 (upgrades always take the latest copy). The fix was supposed to be cosmetic and addressed a bug that had been waiting around since May this year.

So there is no reason why a user running 10.04 would need to update grub. There's not a lot of testing on these updates that I could see from the [bug report]("https://bugs.launchpad.net/wubi/+bug/581760")

In general, you should review all updates. Click on it and read what they are fixing. For security updates, it's a good idea to install them, but for Recommended updates (like grub) it's not important unless it addresses a problem you have. (But update-manager will keep bugging you to update them, unless you lock the version in Synaptic - there's nothing in Update manager that you can click on and select "don't prompt me again").

PS formatting your D: drive is fine, but you still need to fix your bootloader in the MBR on your windows drive. I wasn't sure from your description whether you'd done it.

---

