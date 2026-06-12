---
title: "Dual Boot Help Please"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by Poisond on 2007-02-06
[FONT="Century Gothic"]Hi Guys,

I wanna make the switch to linux but as a long time windows user I had problems the first time I tried Ubuntu. 

I was able to install Ubuntu successfully but failed in configuring the boot file to allow my already existing windows xp installation to show up as an option to select. So I uninstalled Ubuntu and fixed the windows boot file.

Anyway I would try to try Ubuntu again and was hoping someone may be able to help me configure dual boot successfully this time. I am currently using Ubuntu via VMware but its very slow.

::MY COMPUTER::

I have three harddrives currently, no raid setup. I am willing to format one of them to devote to ubuntu only to hopefully make things easier. I remember the first time I installed Ubuntu, even though I had a separate partition it overwrote my windows boot file. Is there a way to add ubuntu to the existing windows boot file? I am a total linux newb and wanna go about this the easiest way.

I have currently: ubuntu-6.06-desktop-i386.iso

If I need to post more information please let me know what else is needed.

If anyone can help or suggest another version of Ubuntu I should use it would be greatly appreciated, thanks.

[/FONT]

---

### Post by confused57 on 2007-02-06
Since you'll be using separate hard drives for Ubuntu & Windows, you might want to consider this:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Disconnecting your Windows hard drive probably isn't mandatory(it's just a safety precaution), I just described how to do this to someone else without disconnecting:
[http://www.ubuntuforums.org/showthread.php?t=355019](http://www.ubuntuforums.org/showthread.php?t=355019)

---

### Post by Moulton on 2007-02-06
> **Poisond said:**
> Is there a way to add ubuntu to the existing windows boot file?
Here's how I did it...

Edit the Boot.Ini file on your Windows boot disk.  It's probably hidden and read-only, so unprotect it so you can edit it.
```

[boot loader]
timeout=12
default=C:\bootsect.grb
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINNT="Microsoft Windows 2000 Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
C:\bootsect.lnx="Red Hat Linux"
C:\bootsect.grb="Ubuntu Grub Loader"

```
The two BootSect files are 512-byte copies of the bootsectors that my two Linux installations had written to the MBR.  I used 'dd' to capture them into files in the C: drive.  The rest of the Boot.Ini file is pretty much the way Windows left it, except that I changed my default.

The above boot menu lets me boot either Win2K, WinXP, Red Hat (LILO), or Ubuntu (Grub).  What's more, my Grub menu has a an entry that lets me go back to the NT Loader menu.

---

### Post by Poisond on 2007-02-07
Thanks for the reply guys, I will definitely check out the link.

I'll try your suggestion also Moulton after I install Ubuntu.

Thanks guys.

---

### Post by Poisond on 2007-02-19
I finally got around to installing Ubuntu 6.06, my SATA drive was corrupted but I just got a new one today and the install went through fine.

Grub added my xp to the boot loader and everything works grand. Thank you Ubuntu! I will just edit the Grub file to hopefully move xp to the top of the list since its working fine.

Having problems getting Ubuntu to detect my monitor resolution and graphics card I think but I just downloaded the linux drivers from ati so hopefully that'll be fixed soon.

Thanks guys!

---

