---
title: "Multi-Boot issues"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by TomDaBomb2u on 2008-11-21
Hello all,

I'm having trouble with Intrepid and Windows XP. I'm going to have XP, Ubuntu Intrepid, and Blag 90k on one drive and Mac OS X on another. 

I just started from scratch - scrapped my previous Ubuntu installation (Hardy) and installed Intrepid. Windows is on the first partition on the drive, but when I reinstalled Ubuntu, the bootloader did not update. It automatically loads Windows without presenting me with the OS list.

How do I access my Ubuntu installation?


Thanks!
-Thomas

P.S - I searched the forums for this problem and couldn't find it. Sorry if this is a duplicate...

---

### Post by taurus on 2008-11-21
Sounds like you need to reinstall GRUB to MBR.  Maybe this helps.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by TomDaBomb2u on 2008-11-22
Thanks Taurus!

This looks like exactly what I need. I'll try it now...

---

### Post by TomDaBomb2u on 2008-11-23
OK...it's been a rough day. I'm in Ubuntu now, but I can't get Windows to load. I looked at my /boot/grub/menu.lst file and the Windows entry looks like this

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I'm not sure what the "map" lines do, but the partition appears to be listed correctly (hd1,0).

I opened GPartEd, and my info is as follows:

Windows - /dev/sdb1 (With a Warming: Unable to read the contents of this filesystem! Because of this some operations may be unavailable)

Ubuntu - /dev/sdb2

Please help! I'm about to freak out; I NEED my Windows partition...

---

### Post by caljohnsmith on 2008-11-23
What error do you get when you boot Windows with that entry you are using? Do you boot the sda drive on start up or the sdb drive? How about opening a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like, so I can help you figure out how to boot Windows from Grub.

---

### Post by TomDaBomb2u on 2008-11-23
Hi caljohnsmith,

Thanks for the reply. Here's the info you asked. for. 

```
thomas@tomdabomb2u-desktop:~$ sudo fdisk -lu
[sudo] password for thomas: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98f598f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   965008484   482504211   83  Linux
/dev/sda2       965008485   976768064     5879790    5  Extended
/dev/sda5       965008548   976768064     5879758+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9fba9fba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   983033414   491516676    7  HPFS/NTFS
/dev/sdb2       983033415  1275994754   146480670   83  Linux
thomas@tomdabomb2u-desktop:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
thomas@tomdabomb2u-desktop:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
ff01

```


I booted with a live GPartEd disk and my Windows information is still there. Which it should be; I haven't done anything to compromise it, I'm just upset that I can't access it at the moment. 

Thanks for your help!
-Thomas

---

### Post by TomDaBomb2u on 2008-11-23
Oh, and the error I get is 

```
Error 13: Invalid or unsupported executable format.
```

---

### Post by caljohnsmith on 2008-11-23
OK, it appears you are probably booting from your sdb drive on start up; how about opening your menu.lst first:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to be:
```
title Windows XP
root (hd0,0)
chainloader +1
```
And let me know exactly what happens when you try it from the Grub menu. :)

---

### Post by TomDaBomb2u on 2008-11-23
YES!!! THANK YOU!!!

Also...what's the difference between gksudo and sudo?

---

### Post by caljohnsmith on 2008-11-23
> **TomDaBomb2u said:**
> YES!!! THANK YOU!!!

Also...what's the difference between gksudo and sudo?
Glad to hear it worked OK. About gksudo vs. sudo, gksudo is used to run any GUI application as root, while sudo is to run any command-line program as root. The difference is basically how they set up the environmental variables before running the program. Anyway, cheers and have fun with your OSes. :)

---

