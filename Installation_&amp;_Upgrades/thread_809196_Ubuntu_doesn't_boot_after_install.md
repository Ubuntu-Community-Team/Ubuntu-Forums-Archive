---
title: "Ubuntu doesn't boot after install"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by BlueMonkMN on 2008-05-27
I just finished installing Ubuntu on a multiple hard drive system (I have a SATA and ... another older kind of drive, and my system seems to boot off the SATA drive if the CMOS has all the drives enabled).  I installed Ubuntu to the unused space on the SATA (newer) drive.  When it was done, it said to reboot in order to complete the process and just booted into Windows XP instead.  How do I configure the boot loader after the install has completed?  I tried booting from the live CD and using the partition editor, but I don't see any options for configuring the boot loader there.  Another interesting piece of information: the installer says it was going to install the boot loader to hd0, but I don't seem to have an hd0.  I have sda and sdb which seem to represent my two drives.  sdb has sdb1 and sdb2, and sdb2 contains sdb5 (ext3) and sdb6 (linux-swap). sdb1 is ntfs.  Surely the solution here must be simple, but I can't find it myself.

---

### Post by Dan++ on 2008-05-27
What does the file /boot/grub/menu.lst look like?

You can find it by first mounting sbd5 in the from the live CD, navigate to it in terminal (using cd <whatever the mount point is> and then in terminal type:

```
sudo gedit /boot/grub/menu.lst
```

It should show all the options for the GRUB boot loader including operating systems and general display options. If you want options when it loads, there should be a part of the file which looks something like this:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

Notice hiddenmenu is commented out, and timeout is 10.

---

### Post by Patb on 2008-05-27
Bluemonk, first try Catlett's "How to restore Grub from a live Ubuntu cd":
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

The terminology differs for different programs.  Grub numbering starts at 0 whereas Ubuntu numbering starts at 1.  So, what grub sees as (hd0,0), ubuntu may see as /dev/sda1.  I usually just install grub to the MBR and all goes okay.  

In your case, the sata drive with linux appears to be sdb.  If you post your more detailed partition information, someone should be able to give more specific advice. Please post the output of:
```
sudo fdisk -l
```

Cheers, Pat.

---

### Post by BlueMonkMN on 2008-05-27
OK, I got a bit more info.  First of all, here's the text returned by sudo fdisk -l:
```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x(omitted)

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        9725    78075900    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x(omitted)

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16709   134215011    7  HPFS/NTFS
/dev/sdb2           16710       38913   178353630    5  Extended
/dev/sdb5           16710       28182    92156841   83  Linux
/dev/sdb6           38726       38913     1510078+  82  Linux swap / Solaris

```

Secondly, I tried disabling the SATA drive and confirmed that GRUB installed onto the wrong drive.  When I do so I at least see some hint that GRUB is trying to run, but I get error 21.  Presumably this is because it's looking for the drive that I disabled (which I disabled in order to force the system to boot onto the old drive).  So I need 2 things now.  1) Can I configure the GRUB installed on the old drive to boot into the old Windows XP installation on it (the only OS on that drive), and 2) How do I install grub on the new drive.  This is after I followed the procedure mentioned in the linked article.  Apparently the procedure doesn't account for the possibility that the system might not boot from the first drive.  And oddly, I can't seem to find any way to boot off the first drive when the second (SATA) drive is enabled.  It seems I have to disable the second drive in order to boot off the first drive (strange CMOS shortcoming?).  So at the moment I have no way to boot to the first (old) drive.

---

### Post by BlueMonkMN on 2008-05-27
BTW, I don't seem to have a /boot/grub directory.  What is the grub from hd0 using?  There's no linux partition on hd0, and the only linux partition I have on the system doesn't have /boot/grub.  Yet, when I type find /boot/grub/stage1 it returns (hd1,4)

---

### Post by BlueMonkMN on 2008-05-28
OK, without any replies, I decided to try this (if I recall correctly):
root (hd1,4)
setup (hd0,1)
(or was it setup (hd1,0) -- I don't remember)

That got grub set up on the correct hard drive so that when I boot, it runs.  But somehow it's gotten terribly confused and won't boot any of the 3 bootable partitions I have on two drives!

When I try to boot to any of the Ubuntu installations, it says that the partition doesn't exist.  When I try to boot to the Windows XP installation, I think I get Error 17, and when I try to boot to the other Windows XP installation, I get the Dell recovery utility.  The only way to boot to Ubuntu is to manually edit the root command before booting.  How did it get so terribly confused?  I finally found my /boot/grub directory (I didn't realize I had to look in a different place when running from the live CD).  Here's what it's got:

```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fedafd25-fade-4a6a-b080-3e096a00baa5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fedafd25-fade-4a6a-b080-3e096a00baa5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

Please help, things are going downhill fast.

Edit: 1) I discovered that it's error 12: Invalid Device, not error 17 that I get when I try to boot to the first Windows XP partition.
2) I just discovered that I can boot into the old Windows XP installation from the old/first drive if I use that last configuration (with the "map" lines) and change root (hd1,0) to root(hd1,1)

Edit2: To boot to Ubuntu I have to change root(hd1,4) to root(hd0,4).

---

### Post by BlueMonkMN on 2008-05-29
When I boot into the Ubuntu partition now, it seems that it doesn't even recognize that there's an NTFS partition on the same drive (it does see the NTFS partition on the first drive), which might help explain why I can't find any way to boot into that XP partition.  When I boot into the first drive's XP partition, it can't see the contents of the second drive either (it sees a drive with no capacity).  When I installed grub on the second drive, did it overwrite some partition information or what?  Shall I try using Windows XP's FIXMBR to try to restore the second drive's Windows XP partition and boot ability?  How are grub and Windows XP supposed to interact as far as the boot sequence?

I did use FIXMBR on the first drive to make that drive directly bootable again (because the grub that was installed there was failing).  I did this as kind of a test to see if FIXMBR would help.  I had to copy NTLDR and NTDETECT.COM from the Windows XP CD in order to make it boot after using FIXMBR because it was giving "NTLDR not found" messages.  But after that it was able to boot.  I'm still nervous about doing this to the second drive, though.  I'm nervous that this NTLDR and NTDETECT are different than the files that were there before.  Do I need to re-apply some update?

---

### Post by BlueMonkMN on 2008-05-29
I finally had to disable the old hard drive so nothing could see it, then boot from the Windows XP install CD and use FIXBOOT to re-install the boot sector on the other (SATA) drive.  So now I can finally boot into the new Windows XP partition again.  Dare I try a different GRUB configuration to see if I can set up booting to multiple systems?  How do I do that without overwriting the Windows XP boot sector in a way that makes the XP partition unrecognizable?

---

### Post by meierfra. on 2008-05-30
Just to make sure: You are currently able to boot into the XP on you 500 GB drive, but you are not able to boot into Ubuntu? And you 80GB drive is disabled?

 So I suggest to leave out your old 80GB drive for now.

 This should allow you to Boot in Windows and Ubuntu on your 500GB drive (with the 80 GB disabled)


Boot from the Ubuntu Live CD. Open a terminal and  type

```
 sudo grub
```
and at the "grub>" prompt

```
find /boot/grub/menu.lst
```

Since you internal drive is detached this should return  "(hd0,4)".

```
root (hd0,4)
setup (hd0)
quit
```

You now have Grub installed on the MBR your 500GB drive.

Next we will edit "menu.lst"


```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda5 /ubuntu
cd /ubuntu/boot/grub
sudo cp menu.lst menu.lst.bu
gksudo gedit menu.lst
```


Change  "#groot (hd1,4)" to "#groot (hd0,4)"

Change "root (hd1,4)" to "root (hd0,4)" (three times in ubuntu items)

Change

title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


to 

title	XP on old drive
root		(hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader	+1

Add

title		XP on new drive
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Save the file.

Reboot and you should get  a Grub Menu which allows you to boot into Ubuntu and your new XP.


If this worked, add the Old Drive into the systems. But make sure that the bios are set to boot into the new 500GB drive (You might have to switch  switch the boot order in the bios  or plug your drives in differently.)

Then you should be able to boot into all of your OS.

---

### Post by BlueMonkMN on 2008-05-31
Thanks!  Now I can boot to Ubuntu or XP on the SATA (320 GB) drive or XP on the old (80 GB) drive.  I can't boot to the Dell utility partition any more, but I've only found that useful once since I got the system 5 years ago (in diagnosing the fact that the old drive had a bad sector), so I don't really care about that.  If I use the BIOS' boot menu feature, I can also boot to the old drive instead of the new drive, which gets me into the old XP.  The BIOS boot menu also has an option to boot into the utility partition, but that just launches GRUB now, so GRUB must have overwritten the utility partition's boot sector or something.  When I try to use the menu item in GRUB that used to boot into the utility partition, now it just says NTLDR is missing.  If you have any ideas I'd be curious/interested to try them out, but like I said, I don't think I'll be needing that partition.

---

### Post by meierfra. on 2008-05-31
Use this in menu.lst:

title		Dell Utility
root		(hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader	+1

But I'm not sure that it will work.

---

### Post by BlueMonkMN on 2008-06-18
I don't know what happened.  Everything was working fine, but now when I try to boot into Windows XP (the new one on (hd0,0)) it starts bootong and then reboots.  Next time I try to boot into it it says that an error was encountered starting windows last time and asks if I want to start in safe mode.  Could this have anything to do with the fact that I installed Wine in Ubuntu and temporarily configured it to use that partition as the C drive?  I un-installed wine now in case that had something to do with it, but I don't expect this to help.  Now how do I diagnose this problem (the same thing happened trying to boot in safe mode... a few lines of log and then it reboots to Grub).

I tried rebooting again and it looks like the last line that was displayed in safe mode before rebooting had something to do with agp440.sys (it was only there for half a second so I couldn't see it very well)

---

### Post by meierfra. on 2008-06-18
Sorry, I know nothing about that. I suggest to start a new thread .

P.S. I just edited my post on the "Dell Utility" partition. I must have been sleeping, when I  wrote that  2 weeks ago.

---

