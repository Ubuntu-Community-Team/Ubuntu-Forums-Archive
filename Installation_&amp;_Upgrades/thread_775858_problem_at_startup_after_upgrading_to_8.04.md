---
title: "problem at startup after upgrading to 8.04"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by il-mArCi0 on 2008-04-30
i have a computer with Ubuntu and Windows XP.
after the upgrade of Ubuntu to the new version (8.04) i can't load Ubuntu e and Windows XP.
when i try to run Win Xp the system reboot automatically.

when i run Ubuntu i got like "Terminal" program.
the UUID on vol_id and fstab are the same.
what can i do?

thanks

---

### Post by frodon on 2008-04-30
I would boot a liveCD and check your menu.lst file, more likely the references are wrong.
If you need assitance with this please post your menu.lst file, the output of "sudo fdisk -l" and "ls -l /dev/disk/by-uuid/"

---

### Post by il-mArCi0 on 2008-04-30
> **frodon said:**
> I would boot a liveCD and check your menu.lst file, more likely the references are wrong.
If you need assitance with this please post your menu.lst file, the output of "sudo fdisk -l" and "ls -l /dev/disk/by-uuid/"

sudo fdisk -l
```
/dev/sda1   *   1   14377   115483221   7   HPFS/NTFS
/dev/sda2     14378   19243   39086145  83  LINUX
/dev/sda3     19244   19457   1718955   f   W95 ESTESO (LBA)
/dev/sda5     19244   19457   1718923+  82  LINUX SWAP / SOLARIS
```

ls -l /dev/disk/by-uuid/
```
lrwxrwxrwx 1 root root 10 2008-04-30 19:12  "UUID" -> /../../sda2
lrwxrwxrwx 1 root root 10 2008-04-30 19:12  "UUID" -> /../../sda5
lrwxrwxrwx 1 root root 10 2008-04-30 19:12  "UUID" -> /../../sda1
```

where *"UUID"* is a list of numbers and letters

---

### Post by El King on 2008-04-30
```
sudo gedit /boot/grub/menu.lst
```
and post back

---

### Post by il-mArCi0 on 2008-04-30
> **El King said:**
> ```
sudo gedit /boot/grub/menu.lst
```
and post back

i got
```
title ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,1)
kernel /boot/vmlinux-2.6.24-16-generic root=UUID=... ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet
```

*...then the recovery mode and the memtest*

after there is:

```
title Windows XP Professional
root  (hd0,0)
savedefault
makeactive
chainloader +1
```

---

### Post by frodon on 2008-04-30
Could you post your /boot/grub/device.map file too, thanks.

---

### Post by il-mArCi0 on 2008-04-30
> **frodon said:**
> Could you post your /boot/grub/device.map file too, thanks.

sudo nano /boot/grub/device.map 
```
(hd0) /dev/sda/

```

---

### Post by frodon on 2008-04-30
If your UUID in your 2.6.24-16-generic kernel line well match your sda2 UUID then it looks good from what i see.

I really wonder what could cause this, sorry i have no accurate answer to give you.

One thing you can try if you are willing to test is to reinstall GRUB from liveCD :
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4)

---

### Post by il-mArCi0 on 2008-04-30
anyone knows other solutions?

---

### Post by dstew on 2008-04-30
Do you get the grub menu when you boot?
EDIT: I notice in the Ubuntu menu item the term "quiet" at the end.```
title ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,1)
kernel /boot/vmlinux-2.6.24-16-generic root=UUID=... ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
[COLOR="Red"]quiet[/COLOR]
``` What is this? I did not find it as a menu command in the [Gnu grub manual]("http://www.gnu.org/software/grub/manual/grub.html"). Remove it and see if anything changes.

---

### Post by il-mArCi0 on 2008-04-30
> **dstew said:**
> Do you get the grub menu when you boot?
EDIT: I notice in the Ubuntu menu item the term "quiet" at the end.```
title ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,1)
kernel /boot/vmlinux-2.6.24-16-generic root=UUID=... ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
[COLOR="Red"]quiet[/COLOR]
``` What is this? I did not find it as a menu command in the [Gnu grub manual]("http://www.gnu.org/software/grub/manual/grub.html"). Remove it and see if anything changes.

quiet is not the problem
because is only a options for displaying messages
[https://answers.launchpad.net/ubuntu/+question/3944]("https://answers.launchpad.net/ubuntu/+question/3944")

---

### Post by frodon on 2008-04-30
You are right with the quiet functionality, i have never seen it used as last line though.
The word quiet at the end of the kernel line is enough AFAIK so i would remove the one in red just in case it creates troubles.

---

### Post by Denja on 2008-04-30
Hi Team,
I also have the same problem..
After upgrading Ubuntu 7.10 to the new version (8.04) 
i can't load Windows XP from my dualboot SATA harddisk
The grub load menu shows normally but
when i try to run Win Xp the system hangs at boot.

(Starting up..)

The only issue prior to this is that [COLOR="Red"]windows didnt shutdown properly ?!
before upgrading[/COLOR] cause i coudn't mount my second windows partition
(unable to mount volume error) even from gutsy 7.10
 
Here are my lists:

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3fee3fed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5737    46082421    7  HPFS/NTFS
/dev/sda2            5738       24859   153597465    f  W95 Ext'd (LBA)
/dev/sda3           24860       30272    43479922+  83  Linux
/dev/sda4           30273       30515     1951897+  82  Linux swap / Solaris
/dev/sda5            5738       24859   153597433+   7  HPFS/NTFS

------------------------------------------------------------------------
total 0
lrwxrwxrwx 1 root root 10 2008-04-30 23:23 2c2721b6-af0b-4a87-bf9b-b806247f13f0 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-04-30 23:23 B074A9FF74A9C884 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-04-30 23:23 DA60AEE660AEC919 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-04-30 23:23 dbb8b75e-7926-4f6b-8285-3240363668d2 -> ../../sda3
-------------------------------------------------------------------------
And GRUB menu list..

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dbb8b75e-7926-4f6b-8285-3240363668d2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dbb8b75e-7926-4f6b-8285-3240363668d2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify		(hd0,0)
makeactive
chainloader	+1
boot

Any advice would be great.thx :)

---

### Post by dstew on 2008-04-30
The menu item looks correct, except for the **boot** command, which is unnecessary in the menu. Delete it and see if that helps.

---

### Post by il-mArCi0 on 2008-04-30
> **frodon said:**
> If your UUID in your 2.6.24-16-generic kernel line well match your sda2 UUID then it looks good from what i see.

I really wonder what could cause this, sorry i have no accurate answer to give you.

One thing you can try if you are willing to test is to reinstall GRUB from liveCD :
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4)

i also tried to reinstall GRUB from the liveCD but i've still have the same problem :(

---

### Post by frodon on 2008-05-01
Ok for those who issue booting windows (only windows) here is a similar case and how the user solved his issue :
[http://ubuntuforums.org/showthread.php?t=773240&page=3](http://ubuntuforums.org/showthread.php?t=773240&page=3)

@Denja the above link should solve your problem,

@il-mArCi0, you said "when i run Ubuntu i got like "Terminal" program". This might just tell that ubuntu is booting fine but just isn't working correctly, try to boot it in recovert mode to see if you get any error message.

---

### Post by dstew on 2008-05-01
Frodon, the links in that thread are not active. Do you have an active link you can post to that fixntldriso.zip file? Thanks.

EDIT: I found this: [http://www.tinyempire.com/notes/ntldrismissing.htm](http://www.tinyempire.com/notes/ntldrismissing.htm)

---

### Post by il-mArCi0 on 2008-05-01
i've resolved my problem doing like this:

First, you need to know the name of your swap partition. Punch in this line:

    # fdisk -l | grep swap

This will spit out something like:

    /dev/sda2 4744 4868 1004062+ 82 Linux swap / Solaris

In this case, my device is /dev/sda2.
Then...

    # swapoff /dev/sda2
    # mkswap /dev/sda2

This will rebuild your swap partition. 
Now replace the new UUID in those files:

    # sudo nano /etc/fstab
    # sudo nano /etc/initramfs-tools/conf.d/resume

Update your bootup ramfs with the new swap information.

    # update-initramfs -u

Restart your system:

    # sudo shutdown -r now

If you still can't see gnome type (this was my case)
 
    # startx

---

### Post by frodon on 2008-05-01
So you are now able to boot linux and windows correctly now ?

So basically you fixed your wrong swap uuid and regenerate your init scripts (which was maybe your only issue with linux side).

Anyway i'm happy to know that you are back to normal.

---

### Post by il-mArCi0 on 2008-05-01
> **frodon said:**
> So you are now able to boot linux and windows correctly now ?

So basically you fixed your wrong swap uuid and regenerate your init scripts (which was maybe your only issue with linux side).

Anyway i'm happy to know that you are back to normal.

with windows i still have the same problem
it restart automatically...i have to check out some windows system repair....
thanks for the help!

---

### Post by frodon on 2008-05-01
The link i gave in post #16 should help you, this user solved his issue and will soon post detailled instruction for other users with the same problem.

---

### Post by Denja on 2008-05-09
Hi Team,
Sorry for the delay..its a friend fix
> The menu item looks correct, except for the boot command, which is unnecessary in the menu. Delete it and see if that helps.I changed that didnt help and from grub windows load still freeze

> Ok for those who issue booting windows (only windows) here is a similar case and how the user solved his issue :
[http://ubuntuforums.org/showthread.php?t=773240&page=3](http://ubuntuforums.org/showthread.php?t=773240&page=3)

@Denja the above link should solve your problem
@Dstew EDIT: I found this: [http://www.tinyempire.com/notes/ntldrismissing.htm](http://www.tinyempire.com/notes/ntldrismissing.htm)
Yes this fixed helped a lot i burned the iso cd
and now i can boot directly to windoaws..
But still cant boot properly from Grub..
So it seems that my problem now is Grub.I will learn more about grub configuration then.
Thanks to both for your advice:KS

---

