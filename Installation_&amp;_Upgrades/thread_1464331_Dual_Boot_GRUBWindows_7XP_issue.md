---
title: "Dual Boot GRUB/Windows 7/XP issue"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by jrd1760 on 2010-04-28
Hello Everyone, been a while since I've been here. So I did something that is probably rather stupid and I would be glad for some help. I have two HDDs in my computer. One has Win XP only and the other had Win 7 RC and OpenSolaris tri-booting, I was testing them both. Since I hadn't used either in quite a while I decided to just install Ubuntu 8.10 over them both. Well I forgot about GRUB. So now my choice for booting into XP involves choosing the Win 7 bootloader from Grub and then choosing XP rather than the two now dead OS's in the Win 7 bootloader. How exactly can I get this back to just choosing between Ubuntu and XP? I assume it involves fix mbr from Win XP disc, but at this point I would rather leave my dual-booting days behind and just get back to straight up XP for now. Also, if this is more of a Windows forum question I apologize but if anyone could help it will be greatly appreciated. Been looking for hrs. and it's 2am where I am at. Thanks in advance

---

### Post by wilee-nilee on 2010-04-28
This link tells you how to load the XP boot back to the mbr, do this 1st make sure XP is booting as you want then use a live Ubuntu CD and use gparted too remove Ubuntu.
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
This seems like the way to do it if you just want XP.
I would make sure you have a backup of XP and a install disc before doing anything. If you want a link to a legit XP home here it is, it says drivers included but I have used this ISO to load several computers much older then the acer I own and different manufacturers, with no problems.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

---

### Post by max-power2717 on 2010-04-28
You will likely be able to fix the problem via grub's configuration from within ubuntu without needing to update the MBR. 

Just to make sure I understand your situation: you installed ubuntu on one entire disk (over windows 7 and Solaris), and simply allowed it to install grub to the MBR, and now ubuntu (grub) loads up by default. Windows XP is on the other disk (untouched by the ubuntu installation). From the grub boot menu, there's an option to boot windows, which brings the windows 7 boot loader up. The windows 7 boot loader has options for windows xp (which boots) as well as windows 7 and solaris (which fail to boot since you wrote over them). ... Is that correct?

If so, what I reckon has happened is the ubuntu installer overwrote the MBR on the window's XP disk, but for some reason didn't give an option by default to boot windows XP. While you were experimenting you got the windows 7 boot loader installed onto the other disk, and that wasn't affected at all during the ubuntu install (hence, it can still boot windows xp).

If I'm correct, the solution will simply be to update your grub boot configuration (found at /boot/grub/menu.lst by default). 

There'll be an entry which boots windows 7, you want to change it to boot windows xp instead.

Very few changes will likely need to be made in that file. You'll probably have an entry something like:
```

title        windows 7 
root        (hd1,0)
savedefault
makeactive
chainloader    +1

```You'll want to change it to something like:
```

title windows XP
root (hd0,0)
chainloader +1

```If you post the current contents of your menu.lst file here, I can give you more information about it can be edited to boot windows xp properly. Also, if the file /boot/grub/device.map is present and not empty, post it's contents as well (as this affects the order that your disks are seen by grub and the OS - can cause major booting headaches when not set up correctly for your system).

---

