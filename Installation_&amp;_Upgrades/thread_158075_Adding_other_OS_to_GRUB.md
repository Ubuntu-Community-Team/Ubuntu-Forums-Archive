---
title: "Adding other OS to GRUB"
date: 2006-04-10
forum: Installation &amp; Upgrades
---

### Post by DeadMazzay on 2006-04-10
Hello.

I have Ubuntu on IDE drive and WinXP on SATA. They were installeed independently, and just switched to win using BIOS, when needed.

So I want to:
1) add win drive to fstab to be able to mount NTFS partitions
2) add win drive to GRUB to enable dual-boot.

The question is:
Will it makesome modificatios on win hdd I'm going to add? Does GRUB (installed on Ubuntu drive) write something on another HDD, its file table or boot records?
I just have very important data on my winXP drive I don't want to loose in vase of some problem.

---

### Post by super on 2006-04-10
ya this should be relatively easy and won't write anything to your winxp drive so no need worry.

1. to add the drive to the fstab just follow the instuctions [here]("http://www.ubuntuguide.org/#automountntfs"). but change /dev/hd*x*# to /dev/sd*x*# since your drive is sata

2. as for grub, the config file is in /boot/grub/menu.lst open this file as root:
```
sudo gedit /boot/grub/menu.lst
```
and add this to the bottom:
```
title		Microsoft Windows XP Home Edition
root		(sd*x*,*y*)
savedefault
chainloader	+1
```
change the *x* and *y* to the appropriate disk assignment and partition number (eg sd0,1)

---

### Post by DeadMazzay on 2006-04-10
Thanks. 

But what are my *X* and *Y* in a case if I my win boot partition is "sda1":
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7139    57343986    7  HPFS/NTFS
/dev/sda2            7140       19456    98936302+   f  W95 Ext'd (LBA)
/dev/sda5            7140       19456    98936271    7  HPFS/NTFS
```

---

### Post by PriceChild on 2006-04-10
sd0,1 i think :)

Just had an experience changing my list from a command line today for an hour trying to get grub to load ubuntu again, so i'll be annoyed if i haven't learnt it and this is wrong :)

---

### Post by lha on 2006-04-11
title 		Windows XP
map		(hd0) (hd1)
map		(hd1) (hd0)
root		(hd1,0)
chainloader +1
makeactive

---

### Post by Blarion on 2006-04-11
You can re-install GRUB using Super Grub Disk, and it'll autodetect your OS'es.
[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

---

### Post by DeadMazzay on 2006-04-11
I've digged a little bit, found nothing interesting and I've understood that "x" in this case does not depend of place device plugged in. This is a number of device  as it BIOS understands. So if I set (in BIOS) that master IDE is primary boot device, and my first SATA drive is a second, then for grub they are hd0 and hd1 respectively.
So I've set this config for my GRUB and it works well:

```

title           Windows XP
root            (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
# savedefault
chainloader     +1

```

**lha:** what *makeactive* does? actually if both drives/partitions are active and primary boot partition is set in BIOS do I need this? (it works without it). So I don't need to activate or hide partitions, right?

**Blarion:** Thanks a lot, but I like to dig such things myself to understand and to learn for my own experience ;) so I will do in in future in some minutes :)

---

### Post by dcstar on 2006-04-11
[QUOTE=super]
......
2. as for grub, the config file is in /boot/grub/menu.lst open this file as root:
```
sudo gedit /boot/grub/menu.lst
```
and add this to the bottom:
......[/QUOTE]
Which means add it after the part of the menu.lst file that says:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
```
because:
```
### BEGIN AUTOMAGIC KERNELS LIST
## [B]lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script[/B] except for the default options below
```

---

### Post by lha on 2006-04-12
[QUOTE=DeadMazzay]**lha:** what *makeactive* does? actually if both drives/partitions are active and primary boot partition is set in BIOS do I need this? (it works without it). So I don't need to activate or hide partitions, right?[/QUOTE]

From grub's manual:
"4.1.2 Load another boot loader to boot unsupported operating systems

If you want to boot an unsupported operating system (e.g. Windows 95), chain-load a boot loader for the operating system. Normally, the boot loader is embedded in the boot sector of the partition on which the operating system is installed.

   1. Set GRUB's root device to the partition by the command rootnoverify (see rootnoverify):

          grub> rootnoverify (hd0,0)
     

   2. Set the active flag in the partition using the command makeactive6 (see makeactive):

          grub> makeactive
     

   3. Load the boot loader with the command chainloader (see chainloader):

          grub> chainloader +1
     

      `+1' indicates that GRUB should read one sector from the start of the partition. The complete description about this syntax can be found in Block list syntax.
   4. Run the command boot (see boot). "

Active != not hidden. I guess makeactive is only needed if you have multiple os'es that grub can't boot directly. There's no need to hide/unhide either. If you had more than one Windows installed, you might need to use hide to prevent Windows' from seeing each other. (Atleast older Windows' had problems with multiple primary partitions on one disk.)

---

### Post by adrian15 on 2006-04-24
[QUOTE=Blarion]You can re-install GRUB using Super Grub Disk, and it'll autodetect your OS'es.
[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)[/QUOTE]

Hey. What you're saying is not true. Super Grub Disk is for reinstalling/restoring Grub. (Usually when you cannot boot windows.) And it does restore your former menu.lst but it does not add any entry to your former menu.lst.

That means that you cannot use Super Grub Disk for adding a Windows boot entry for your system.

But there's a thing you can do from inside Super Grub Disk: Boot Windows. But of course you do need to boot from Super Grub Disk.

adrian15

---

### Post by ableape on 2007-08-29
I have had success using GAG ([http://gag.sourceforge.net/](http://gag.sourceforge.net/)) when the GRUB goes awry.  

Things at the boot level can get very confusing and new users can make some pretty time consuming mistakes.  Before you decide you need to reload everything, try managing the booting across different OS's with GAG.  Often when GRUB gets discombobulated, the original OS's are still in tack and usable.  Its not likely that  a novice user will be able to reinstall GRUB on their first try, so have GAG handy.


Many of the examples in this post are on IDE drives, hd1, for example.  Most people are using SATA which borrows the "sd" name.  So sd0, sd1, etc...

---

### Post by maybeway36 on 2007-08-29
If you only use IDE drives, Ubuntu calls them sda, sdb, etc. even though they're not SCSI.

---

