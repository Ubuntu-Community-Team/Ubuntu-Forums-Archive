---
title: "Big boot problem with 6.10"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by clucas on 2006-12-26
Installed Ubuntu 6.10 on a machine that had Windows XP as well as Suse 10.1. During installation I set it up to replace the hard disk area that had Suse with the Ubuntu install. I thought all went well until I rebooted and got the Grub error 17. I then rebooted with the Win XP CD and after going to the repair menu I did a "fixmbr". Then when I rebooted I got a operating system error and nothing happens. Now, I have to put in a blank disk into the CD ROM and have it boot from the CD ROM. That gets me into Ubuntu. I mounted the area where the existing Windows folders are so I can access them. At least I can see them. What I want to do is copy them to a disk, then reformat the disk, reinstall Windows and then reinstall Ubuntu. Can I save this system without reformating?

---

### Post by bulldog on 2006-12-26
Lets try.
Can you boot into ubuntu and give me the output of ```
sudo fdisk -l (l as in like)
```

---

### Post by clucas on 2006-12-26
I really, really appreciate the quick response! I wasn't expecting such a fast reply. Unfortunately, I am at work so will not be able to respond until this evening. So thanks and I'll get back as soon as I can.

---

### Post by clucas on 2006-12-26
For some clarification first: When it boots up with no disk in the drive I get "Diskette drive 0 seek failure...Error loading operating system". So When I then reboot from the cd drive with a blank cd in it Ubuntu boots up.

From running the command:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14401   115676001   83  Linux
/dev/sda2           14402       14589     1510110    5  Extended
/dev/sda5           14402       14589     1510078+  82  Linux swap / Solaris

---

### Post by juff on 2006-12-26
Hi, I'm a newbie and am having a similar problem to [COLOR="RoyalBlue"]slucas.[/COLOR]  I have two hard drives on my computer with Win XP on hda.  When I recently installed Ubuntu Edgy on my second drive (hdb) over a previous Suse10.1, the grub loader shows my Ubuntu installation, but doesn't give me any option to start my Win XP on hda.  Here is my output of fdisk -l

[FONT="Courier New"]Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3956    31776538+   7  HPFS/NTFS
/dev/hda2            3957        7475    28266367+   7  HPFS/NTFS

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7169    57584961   83  Linux
/dev/hdb2            7170        7476     2465977+   5  Extended
/dev/hdb5            7170        7476     2465946   82  Linux swap / Solaris
[/FONT]

How do I get the grub to recognise my win XP installation?  I had previously loaded an Acronis boot loader before the Ubuntu installation - don't know if that makes a difference?

---

### Post by Oqsy on 2006-12-26
similar issues, except no error messages...
my dilemma (i hope the OP doesn't mind me piling on here, but i just registered at this site and this thread was exactly the kind of help i'm seeking as well) is that I have 2 hard drives, one with ubuntu 6.10 and a swap part., and the other that's just a single part. with NTFS/winxp.  I get the grub bootloader at startup, but when I press ESC, my winxp doesn't show up as an option.  any hints?  btw, brand new to linux and my apologies up front for the newb questions.

Oqsy

---

### Post by bulldog on 2006-12-27
> **clucas said:**
> For some clarification first: When it boots up with no disk in the drive I get "Diskette drive 0 seek failure...Error loading operating system". So When I then reboot from the cd drive with a blank cd in it Ubuntu boots up.

From running the command:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14401   115676001   83  Linux
/dev/sda2           14402       14589     1510110    5  Extended
/dev/sda5           14402       14589     1510078+  82  Linux swap / Solaris

Check your diskette station in the BIOS if it's properly recognized.
If so give us the output of your menu.lst```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by bulldog on 2006-12-27
> **juff said:**
> Hi, I'm a newbie and am having a similar problem to [COLOR="RoyalBlue"]slucas.[/COLOR]  I have two hard drives on my computer with Win XP on hda.  When I recently installed Ubuntu Edgy on my second drive (hdb) over a previous Suse10.1, the grub loader shows my Ubuntu installation, but doesn't give me any option to start my Win XP on hda.  Here is my output of fdisk -l

[FONT="Courier New"]Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3956    31776538+   7  HPFS/NTFS
/dev/hda2            3957        7475    28266367+   7  HPFS/NTFS

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7169    57584961   83  Linux
/dev/hdb2            7170        7476     2465977+   5  Extended
/dev/hdb5            7170        7476     2465946   82  Linux swap / Solaris
[/FONT]

How do I get the grub to recognise my win XP installation?  I had previously loaded an Acronis boot loader before the Ubuntu installation - don't know if that makes a difference?

Add this entry to your menu.lst and save the file.
Are you booting from the ubuntu disk?
If so we have to map your windows,I put two extra lines for the mapping in it to be save.
To open your menu.lst```
gksudo gedit /boot/grub/menu.lst
```
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1
```

---

### Post by bulldog on 2006-12-27
> **Oqsy said:**
> similar issues, except no error messages...
my dilemma (i hope the OP doesn't mind me piling on here, but i just registered at this site and this thread was exactly the kind of help i'm seeking as well) is that I have 2 hard drives, one with ubuntu 6.10 and a swap part., and the other that's just a single part. with NTFS/winxp.  I get the grub bootloader at startup, but when I press ESC, my winxp doesn't show up as an option.  any hints?  btw, brand new to linux and my apologies up front for the newb questions.

Oqsy

Give us the output of```
sudo fdisk -l  (l as in like)
```

If I have this information I can make a entry for your windows as well.

---

### Post by clucas on 2006-12-27
I edited out the top portion of the file. Here is what I get. Unfortunately it doesn't have the Windows part. I must have hosed something.

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot


Also, I said in my original posting that I mounted the Windows part of my hard disk. (sudo mount /dev/hda1 /home/greg/test). When I look at that folder, not all the Windows folders are there. This is what is shown:

greg@greg-desktop:~$ sudo ls /home/greg/test
Alcohol Soft    MSOCache   RECYCLER                   WinMPG VideoConvert
BitTorrents     Music      SirGregurus                XFire
Download        N          System Volume Information
Gregs Computer  Photoshop  Video Cleaner Pro

---

### Post by juff on 2006-12-28
Thanks for the reply [COLOR="Navy"]Bulldog[/COLOR].  :KS 

However, before I saw your post, I decided to get Win XP booting again by running *fixmbr *and *fixboot *from the recovery console which you can load from the Win XP disk.  This worked (much to the satisfaction of my nagging 12 yo son), but I have consequently lost the grub loader and can't boot Ubuntu except from the CD.

So, I have a new question - how do I re-install the grub loader, hopefully in a way that guarantees recognition of Ubuntu on hdb *and *Win XP on hda?

---

### Post by bulldog on 2006-12-28
> **juff said:**
> Thanks for the reply [COLOR="Navy"]Bulldog[/COLOR].  :KS 

However, before I saw your post, I decided to get Win XP booting again by running *fixmbr *and *fixboot *from the recovery console which you can load from the Win XP disk.  This worked (much to the satisfaction of my nagging 12 yo son), but I have consequently lost the grub loader and can't boot Ubuntu except from the CD.

So, I have a new question - how do I re-install the grub loader, hopefully in a way that guarantees recognition of Ubuntu on hdb *and *Win XP on hda?

To reinstall grub you need to boot into the live cd,if you have one hard disk it's no problem,if you have more as one I need some extra info.
So if you have just one hard disk do the following.
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

---

### Post by bulldog on 2006-12-28
> **clucas said:**
> I edited out the top portion of the file. Here is what I get. Unfortunately it doesn't have the Windows part. I must have hosed something.

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot


Also, I said in my original posting that I mounted the Windows part of my hard disk. (sudo mount /dev/hda1 /home/greg/test). When I look at that folder, not all the Windows folders are there. This is what is shown:

greg@greg-desktop:~$ sudo ls /home/greg/test
Alcohol Soft    MSOCache   RECYCLER                   WinMPG VideoConvert
BitTorrents     Music      SirGregurus                XFire
Download        N          System Volume Information
Gregs Computer  Photoshop  Video Cleaner Pro

Well the problem you see not all the folders can be done later,first properly boot ubuntu and windows shall we?

You have to put the following entry in your menu.lst to boot windows.
You have grub on the windows disk as I can see,cause ubuntu is set to (hd1,0)
So windows is on (hd0,0)
```
gksudo gedit /boot/grub/menu.lst
```
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda
title		Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
chainloader	+1
```

You have the windows disk not partitioned,it's just one large disk.
This is not the optimal way to use your disk.
I would suggest to make some partitions,where you can store your data,so not everything is lost when you have to format for a reinstall.
To mount your windows it's best done in fstab,so it will be mounted every time you start ubuntu.
Info here,

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by clucas on 2006-12-28
No good with the edit of menu.lst.

I still have to have a blank CD in the drive and have to boot from that. When i get the grub menu and select Windows, I get "NTLDR is missing". I know that's a Windows loader file and have started to do some research on that unless you can help me out. I spoke with one of my company's MIS guys (who doesn't know Linux) and as a last resort I might take him the hard disk to copy off the files and then I'll reformat and start anew!

Thanks for your help.

---

### Post by clucas on 2006-12-30
I think I figured out what went wrong. I have 2 hard drives on that PC. When I was installing Ubuntu I thought I was setting it up on the drive that didn't have the operating system on it. I had formatted it for Linux and blew away the Windows files! So I am in the process of reinstalling Windows and then will reinstall Ubuntu.

Thanks for the help.

---

