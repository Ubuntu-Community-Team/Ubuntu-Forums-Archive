---
title: "grub mapping problem. Can't boot into windows"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by ubuntu_demon on 2006-08-09
Hi,

I'm helping someone with Ubuntu. One of his machines can't boot into windows anymore after we have installed Ubuntu.

I suspect grub has some kind of mapping problem.

We resized his windows partition with gparted using the livecd and we installed Ubuntu on his machine.

The partitions :
/dev/hda1 ntfs windows (primary partition)
/dev/hda2 ext3 ubuntu / (primary partition)
/dev/hda3 linux-swap (primary partition)
/dev/hda4 /home (primary partition)
/dev/hdb1 ntfs (data) (primary partition)

This is the error I get :
*Filesystem type unknown, partition type 0x7*

which is strange because AFAIK type 0x7 is regular ntfs.

The relevant part of /boot/grub/menu.1st
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

I tried adding the following lines to /boot/grub/menu.1st (between makeactive and chainloader+1) :
```

map (hd0) (hd1)
map (hd1) (hd0)

```

I also tried the other way around :
```

map (hd1) (hd0)
map (hd0) (hd1)

```

They both result in the following error (translated from dutch) :

[I]NTLDR missing
[/I]
lspci :
```

0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 11)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 11)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
0000:02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:03.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
0000:02:03.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
0000:02:03.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
0000:02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

```

Ubuntu has no problems with mounting /dev/hda1. Ubuntu boots without any problems.

I also tried reinstalling grub (from Ubuntu).

parted,gparted and fdisk showed no errors. fdisk confirmed the partition type for the windows partition is 7.

Here's another strange problem I have with the same pc :

Can't mount nor format floppy drive
[http://www.ubuntuforums.org/showthread.php?t=233003](http://www.ubuntuforums.org/showthread.php?t=233003)

We are going to try to flash the bios tomorrow.

Any suggestions ?

Thanks in advance,

ubuntu_demon

---

### Post by bensexson on 2006-08-09
When it is at the grub menu use e and then c to get to the grub command line.  Then try this: root (0,0)  What does this do?

---

### Post by Herman on 2006-08-09
Maybe try replacing 'root' with 'rootnoverify' and see if that will help ?
```
                       # This entry automatically added by the Debian installer for a non-linux OS
                      # on /dev/hda1
                      title        Microsoft Windows XP Professional
                      rootnoverify        (hd0,0)
                      savedefault
                      makeactive
                      chainloader    +1
``` Just a guess. When I read the grub manual about that command, it doesn't really seem logical that this will help, but it seems to help sometimes.I just wanted to throw that in anyway. Regards, Herman :D

---

### Post by bensexson on 2006-08-09
You know, forget whar I said.  I think Herman is onto it.

---

### Post by ubuntu_demon on 2006-08-09
> **bensexson said:**
> When it is at the grub menu use e and then c to get to the grub command line.  Then try this: root (0,0)  What does this do?

Thanks for the suggestion.

regards,

ubuntu_demon

---

### Post by ubuntu_demon on 2006-08-09
> **Herman said:**
> Maybe try replacing 'root' with 'rootnoverify' and see if that will help ?
```
                       # This entry automatically added by the Debian installer for a non-linux OS
                      # on /dev/hda1
                      title        Microsoft Windows XP Professional
                      rootnoverify        (hd0,0)
                      savedefault
                      makeactive
                      chainloader    +1
``` Just a guess. When I read the grub manual about that command, it doesn't really seem logical that this will help, but it seems to help sometimes.I just wanted to throw that in anyway. Regards, Herman :D
That seems like something I could try :). Thank you very much.

---

### Post by ubuntu_demon on 2006-08-09
> **bensexson said:**
> You know, forget whar I said.  I think Herman is onto it.
I'm currently not at over at his house. I will be there tomorrow again. I will try all suggestions.

The regular result (without trying anything) is :
*Filesystem type unknown, partition type 0x7*

---

### Post by ubuntu_demon on 2006-08-09
The reason why I think it might be a mapping problem is :

Problem 02
[http://www.ubuntuforums.org/showpost.php?p=1231460&postcount=62](http://www.ubuntuforums.org/showpost.php?p=1231460&postcount=62)

I can reproduce both these errors :

*Filesystem type unknown, partition type 0x7*

[I]NTLDR is missing
Press Ctrl+Alt+Del to restart
[/I]

(I believe I got both of them at the same time when I tried adding the mapping stuff)

---

### Post by ubuntu_demon on 2006-08-10
We removed the second harddrive (and we made sure the remaining harddrive is properly connected, the bios is detecting it properly). The problem still remains. So it wasn't a mapping problem between the two drives.

I'll update the first post later. No time right now.

---

### Post by confused57 on 2006-08-10
You guys are the experts, but wonder if doing a **fixmbr** for Windows, then reinstalling grub?  You've probably already thought of this...
Does he have SP2, here's someone who had a problem without having SP2 installed:
[http://www.ubuntuforums.org/showthread.php?t=223048&page=2](http://www.ubuntuforums.org/showthread.php?t=223048&page=2)

---

### Post by ubuntu_demon on 2006-08-10
> **confused57 said:**
> You guys are the experts, but wonder if doing a **fixmbr** for Windows, then reinstalling grub?  You've probably already thought of this...


Not tried that one yet because I was thinking (tunnel vision) it was a mapping problem. We are going to try it though :). 

Thanks for the suggestion.

> **confused57 said:**
> 
Does he have SP2, here's someone who had a problem without having SP2 installed:
[http://www.ubuntuforums.org/showthread.php?t=223048&page=2](http://www.ubuntuforums.org/showthread.php?t=223048&page=2)

He has SP 2 installed already.

---

