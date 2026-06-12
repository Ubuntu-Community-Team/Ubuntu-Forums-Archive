---
title: "Xubuntu and Windows XP not booting anymore"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by aevirex on 2007-12-31
Hi all,
I just installed Xubuntu on my desktop PC and like previously on my notebook GRUB was configured correctly to boot Windows (XP). However when I want to boot Windows I get an error about hal.dll being missing.
The information I gathered was that Linux changed something with the names of the partitions so boot.ini directs to a wrong partition (Windows is not installed on "C:"). Anyways I wanted to ask if someone knows who my boot.ini has to look like so it can boot Windows again?

boot.ini:
```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn /usepmtimer
multi(0)disk(0)rdisk(0)partition(3)\FUTURAMA\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /bootlogo

```

Also, I have hda1 ("C:" with boot.ini being on it) and hda6 ("F:" if I remember correctly with my Windows installation).

So, has anyone an idea what to change in the boot.ini so I can boot Windows again or is this even impossible?

Thanks in advance,
aevirex

EDIT: Just noticed that the thread title is a little wrong... Xubuntu boots very well :) (Just Windows XP not)

---

### Post by markharding557 on 2007-12-31
you can restore access to windows using the recovery console on your winxp disc
load recovery console up and select fixmbr on the other hand you could reinstall grub
see links below[http://www.practicalpc.co.uk/computing/windows/xprepair4.htm]("http://www.practicalpc.co.uk/computing/windows/xprepair4.htm")
this link is for reinstalling grub
[http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")

---

### Post by logos34 on 2007-12-31
You might want to post you fdisk:

sudo fdisk -l

According to you boot.ini, windows is on hda4.  But if boot.ini and other boot files are on C:  hda1, then that's where the menu.lst windows entry needs to point:

gksudo gedit /boot/grub/menu.lst

> title Windows XP
root (hd0,**0**)
...

---

### Post by aevirex on 2008-01-06
Sorry for the late reply!

Here is what I get when writing fdisk -l in the console:
```

/dev/hda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/hda2            7650       19928    98631067+   f  W95 Ext'd (LBA)
/dev/hda5            7650       15298    61440561    7  HPFS/NTFS
/dev/hda6           16709       19928    25864618+   7  HPFS/NTFS
/dev/hda7           15299       15602     2441848+  82  Linux swap / Solaris
/dev/hda8           15603       16708     8883913+  83  Linux

```

Ok, Windows is on hda6, former C: is hda1...

Here is the /boot/grub/menu.lst part about Windows:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Sorry, I still don't get it... Can someone please tell me what to do?

Thanks in advance,
aevirex

---

### Post by aevirex on 2008-01-08
Anyone? :<

---

