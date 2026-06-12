---
title: "Loading UBUNTU on 2nd New hard drive?"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by guntherfurlong on 2008-05-24
Recently purchased a second Western Digital Hard drive 160Gb. I'm running Win XP on my main hard drive.

I managed to install Ubuntu 7.04 on the new second drive but I am unable to get it to find a proper article that will give me the menu to dual boot btw the two..  

Sorry if this has been posted before.. but I'm very new to Linux and wish to explore it...

Thank u in advance..

---

### Post by cdtech on 2008-05-24
Within Ubuntu, bring up a terminal and type:
sudo grub

This will give you the grub shell >

To install the GRUB bootloader on the primary disk, type:
setup (hd0)

This will install the GRUB bootloader code within the MBR of the primary drive.

Type quit to exit the GRUB shell.

When you reboot you will be presented the GRUB bootloader.

---

### Post by guntherfurlong on 2008-05-24
Thanksfor your prompt reply. I can't get ubunto to load up in the first place. Should I try loading it again via the Ubuntu CD and install GRUB from there?

---

### Post by animefan82 on 2008-05-24
yes

---

### Post by guntherfurlong on 2008-05-24
Loaded up the Ubuntu Live CD

Loaded Grub

Got the error message ...
[COLOR=Red]
[/COLOR][COLOR=Red][I]grub> setup(hd0)

Error 27: Unrecognized command

grub> 


[/I][/COLOR]

---

### Post by cdtech on 2008-05-24
> **guntherfurlong said:**
> Loaded up the Ubuntu Live CD

Loaded Grub

Got the error message ...
[COLOR=Red]
[/COLOR][COLOR=Red][I]grub> setup(hd0)

Error 27: Unrecognized command

grub> 


[/I][/COLOR]

You should have a space between "setup (hd0)"

---

### Post by guntherfurlong on 2008-05-24
setup (hd0) gets me this... (a space is there)

[COLOR=Red]Error 12: Invalid device requested[/COLOR]

---

### Post by cdtech on 2008-05-24
what do you get with:
sudo fdisk -l

---

### Post by guntherfurlong on 2008-05-24
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18719   150360336   83  Linux
/dev/sda2           18720       19452     5887822+   5  Extended
/dev/sda5           18720       19452     5887791   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sdb2            7650       19456    94839727+   f  W95 Ext'd (LBA)
/dev/sdb5            7650       13386    46082421    7  HPFS/NTFS
/dev/sdb6           13387       19456    48757243+   7  HPFS/NTFS

Disk /dev/sdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7295    58597056    7  HPFS/NTFS

---

### Post by cdtech on 2008-05-24
OK

Boot into the live Ubuntu cd.

When you get to the desktop open a terminal and enter.

```
sudo grub
```

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

```
grub >find /boot/grub/stage1
```

Whatever was returned for the find command use it in the next step (you are still at grub>.

```
grub >root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```
grub >setup (hd0)
```

Then exit the grub shell

```
grub> quit
```

I just think the root was not set properly.
The hd0 is the proper device though....

---

### Post by guntherfurlong on 2008-05-24
Ok.. that worked the charm. Will test it out and get back to ya.. thanks alot again :)

---

### Post by cdtech on 2008-05-24
Yu welcome.

Good luck.

You should also see the other selectable OS's now as well in the GRUB menu.

---

### Post by guntherfurlong on 2008-05-24
Hmmm.. unfortunately it didn't work... the WinXp kept booting again... the grub interface didn't even load up...

---

### Post by cdtech on 2008-05-24
> **guntherfurlong said:**
> Hmmm.. unfortunately it didn't work... the WinXp kept booting again... the grub interface didn't even load up...

Then it's your boot order within your bios setup. Booting the secondary drive as default.

---

### Post by guntherfurlong on 2008-05-25
Got it sorted out.. :) My BIOS was a problem.. finally got the right drive to load..and the GRUB came on... thanks...

---

### Post by guntherfurlong on 2008-05-26
Hello friend..

A friend gave me UBUNTU 8.04  to install instead.... but following the steps as mentioned above in the thread, for some reason I cannot get the Grub to load... 

Once booted up... it says...

Grub loading stage1.5
Grub Loading, please wait
Error 15

My fdisk -l reveals (at the Ubuntu LIVE terminal)


Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd6a9bb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18719   150360336   83  Linux
/dev/sda2           18720       19452     5887822+   5  Extended
/dev/sda5           18720       19452     5887791   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa1c20ebc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sdb2            7650       19456    94839727+   f  W95 Ext'd (LBA)
/dev/sdb5            7650       13386    46082421    7  HPFS/NTFS
/dev/sdb6           13387       19456    48757243+   7  HPFS/NTFS


Can u help me... tried the following
sudo grub 
grub >find /boot/grub/stage1

but got this error instead "Error 27: Unrecognized command"

---

### Post by cdtech on 2008-05-26
There is no stage 1 looking at your fdisk return (no MBR on sda).

It looks as though your GRUB bootloader was not installed during the setup. Try this from the CD:

grub> root (hd0,0)
grub> setup (hd0)
grub> quit

Then reboot and see if that corrects the problem.

---

