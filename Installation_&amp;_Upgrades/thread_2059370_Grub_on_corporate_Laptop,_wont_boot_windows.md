---
title: "Grub on corporate Laptop, wont boot windows"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by RubenRybnik on 2012-09-17
Hey all... I'm a pretty seasoned Linux user for the most part, but this one has be a pretty stumped, and my experience with grub/burg is dealing mostly with the normal "I installed Windows and now can't get into Linux" and vice-versa.  

I installed Ubuntu 12.04 last night on my corporate laptop, done this before and everything worked ok, however just got a new laptop and suspect the HD is encrypted or something along those lines.

Grub correctly picked up the Windows Partition, which is labeled "System Reserved", however this partition is much smaller than my Windows partition ( See command output below ).  Also in the commands below and in GParted the drive I suspected Windows to boot for isn't seen in some instances, and GParted thinks it may be defective somehow.  I'm almost sure this isn't the case since this all happened immediately after my install of Ubuntu, before everything was running fine in Windows.

Any solutions to try here? How can I know it's encrypted, corrupt or something else?  Really hoping it's not encryption, only dang reason I need Windows is for VPN( Linux isn't supported at all I tried lol )

fdisk -l showing /dev/sda2(What I suspected should be my main Win OS Partition) as being shown

```

# /boot/burg$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x85bf8bca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1808383      903168    7  HPFS/NTFS/exFAT
/dev/sda2         1808384   399860399   199026008    7  HPFS/NTFS/exFAT
/dev/sda3       399861760   625139711   112638976   83  Linux

```

blkid output NOT showing /dev/sda2

```

# /boot/burg$ sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="26A48C0BA48BDBA5" TYPE="ntfs" 
/dev/sda3: UUID="22ff2930-9eb9-4951-b4ae-1826969c8732" TYPE="ext4"

```

burg.cfg excerpt for Windows entry

```

### BEGIN /etc/burg.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
        insmod ntfs
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 26a48c0ba48bdba5
        chainloader +1
}
### END /etc/burg.d/30_os-prober ###

```

GParted Screenies:

[IMG]http://imageshack.us/a/img38/9097/gpartedscreenshot.png[/IMG]

---

### Post by RubenRybnik on 2012-09-17
Ahhh... Forgot the error when I choose the Windows boot option, get the windows(Dos?) black screen with text indicating that an expected resource is unavailable.  Also I had to install linux by shrinking the Win partition in Windows, as GParted obviously has problems with that partition and didn't have options to shrink it during setup of Ubuntu( During install I mean )

---

### Post by oldfred on 2012-09-19
Always best to shrink the Windows partition with Windows tools. Windows always wants to run chkdsk after a resize, so you need to reboot several times after the resize.

If it has not run chkdsk you need to do that.

The 100MB boot/repair partition is how Windows 7 installs. That gives the option to encrypt the main install and you should be able to get to the Windows recovery or repair in that partition. Some have posted that it is difficult as you just about have to hit the f8 (is it f8?, have not used Windows for ages) almost at the same time as you press enter in grub on the Windows boot entry. Some said try several times.

Always best to have a repairCD or liveCD for the current version of every system installed.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Mark Phelps on 2012-09-19
Windows WAS on sda2; only the Win7 boot loader was on sda1.  With what is seen in the gparted screenshot, looks like you may have wiped out Win7.  

GRUB will still think it's there because it sees the boot loader files in sda1.

Since there appears to be no Recovery partition, if you have no Win7 backup, you would have to reinstall it to get it back.

---

### Post by YannBuntu on 2012-09-20
> **Mark Phelps said:**
> Windows WAS on sda2

+1
But before reinstalling Windows, he can try fixing the partition, or recovering documents via TestDisk.

---

