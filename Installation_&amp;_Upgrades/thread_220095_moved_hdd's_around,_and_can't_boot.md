---
title: "moved hdd's around, and can't boot"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by jlgoolsbee on 2006-07-20
Ok.  Just helped my younger brother build his new rig, and he wanted to do a WinXP/Ubuntu dual boot - which I've had plenty of experience with, because that's my setup at work.  He had 2 hdd's; wanted one to be OS'es, and the other be personal data, so to start off, we installed only the primary hd and cdrom.  Installed WinXP, installed Ubuntu, had grub configured correctly and had the machine stable for a week or so.  Now, he went to reconfigure the internal drives to add in his secondary drive, and while grub and WinXP are fine, Ubuntu is not.  Ubuntu gets as far as mounting the root filesystem, and halts for a couple minutes, and then dumps to a shell, with an error that says it can't find hda3 (which used to be '/').

We started up with the Ubuntu Live Disk, and ran 'fdisk -l'...
```
root@ubuntu:~# fdisk -l

Disk /dev/hde: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1           2       16033+  12  Compaq diagnostics
/dev/hde2   *           3        5876    47182905    7  HPFS/NTFS
/dev/hde3            5877        7181    10482412+  83  Linux
/dev/hde4            7182        7476     2369587+   f  W95 Ext'd (LBA)
/dev/hde5            7182        7476     2369556   82  Linux swap / Solaris

Disk /dev/hdf: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1       36483   293049666    7  HPFS/NTFS

```
Now, what it appears has happened is that it replaced 'hda' with 'hde', and also (not shown) has moved the cdrom (which used to be 'hdc') to be 'hda'.  I've found a couple threads that speak of Dapper doing this, but most of those threads end with no real resolution.

The next step was to try just replacing the relevant values in '/boot/grub/menu.lst' and '/etc/fstab'...
```
FROM MENU.LST

title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hde3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hde3 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot
```

and...
```
FROM FSTAB:

proc            /proc           proc    defaults        0       0
/dev/hde3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

However, this did not fix things, and Ubuntu still hangs trying to mount the root filesystem.  The only value that I can think might have changed would be the value in 'menu.lst' that says...
```
root            (hd0,2)
```
... but I can't find any info about how to determine this number.

The machine itself is built on an Asus P5WD2 Premium mobo, which has 2 IDE channels.  When we did the install, the main drive was on the 'blue' IDE (IDE), and now we have moved the main to the 'red' IDE (actually, ITE IDE), for space/layout issues inside.  Maybe this is our problem; neither me or my brother have ever had a board with ITE IDE, and really know nothing about it.

Despite all of this, WinXP still boots fine, and shows no issues whatsoever... so I have to figure the issue lies somewhere in one of these files I've posted above.  If there's any other info that would be of use, just let me know, and I'll post it asap.

Thanks in advance for your help.

---

### Post by confused57 on 2006-07-21
Here's an excellent grub tutorial:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

May help you troubleshoot your problem.

---

### Post by jlgoolsbee on 2006-07-21
> **confused57 said:**
> Here's an excellent grub tutorial:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

May help you troubleshoot your problem.

That's an excellent article; it at least answers my question about hd(0,2) being the correct value for this situation, and I believe it is (esp. since WinXP still boots correctly using hd(0,1), and the Ubuntu '/' partition is the very next partition on that same drive)... and yet Ubuntu still can't find the root file system.

What's next?

---

### Post by jayemef on 2006-07-21
Did you only switch your IDE cabling at the motherboard level, or did you swap the ends too? Ie, is hda now hdb/hd0 now hd1, etc.? Also, I am assuming that you are getting into grub and selecting Windows from there, or are you using system rescue to bring it up?

---

### Post by jlgoolsbee on 2006-07-21
The original configuration:
ITE IDE: Nothing
IDE: HDD1 as Master, CDROM as Slave

New configuration:
ITE IDE: HDD1 as Master, HDD2 as Slave, both on Primary Channel
IDE: CDROM as Master on Primary (only) Channel

I hope that makes sense.

Here is a screen grab from after boot-up (when it dumps to busybox after not finding root fs):
[IMG]http://s93111428.onlinehome.us/temp/img_1274.jpg[/IMG]

This is strange, because utilities on both the Ubuntu Live Disk and the Linux SysRescue Disk identify the partition tables as:
```
/dev/hde1               1           2       16033+  12  Compaq diagnostics
/dev/hde2   *           3        5876    47182905    7  HPFS/NTFS
/dev/hde3            5877        7181    10482412+  83  Linux
/dev/hde4            7182        7476     2369587+   f  W95 Ext'd (LBA)
/dev/hde5            7182        7476     2369556   82  Linux swap / Solaris
```

So I'm really confused.

---

### Post by jlgoolsbee on 2006-07-21
Still no luck here.

---

### Post by SkyNet2029 on 2006-07-22
At the Grub boot menu, press ESC then toss this at grub:

```
# find /boot/vmlinuz-2.6.15-26-386
```

that should give you the correct directory/partition to 
specify grub to load from.

---

### Post by jlgoolsbee on 2006-07-22
No dice.  The command:
```
# find /boot/vmlinuz-2.6.15-26-386
```
... returns a value of '(hd0,2)' which means (I think) that the configuration is correct.  And yet Ubuntu still can't find '/dev/hde3' on boot-up.  I even tried passing the boot commands through grub's command line manually and watching the boot process.  There was a point where it stalled on some USB stuff (I hope I don't have the problems listed [here]("http://ubuntuforums.org/showthread.php?t=186115"), since all was fine before we swapped the drives around), but I'm hoping that's not it.

Is it possible grub is identifying my 'hde3' as something else?  How can I tell?

Would reinstalling grub help?

---

### Post by jlgoolsbee on 2006-07-22
Any fresh ideas?

---

### Post by Herman on 2006-07-23
Okay, what about giving GAG Boot Manager a try? 
GAG is a Graphical boot manager, which is very good for those of us who enjoy switching drives around and/or installing/uninstalling operating systems frequently, because it isvery quick and easy to reconfigure. 

GAG Boot Manager will find boot Windows for you no problems, if Windows is bootable. [*Click Here*]("http://users.bigpond.net.au/hermanzone/p12.htm#Install_Lilo_from_terminal") for a GAG Boot Manager How-to.

To boot Ubuntu or any Linux, we need to install either GRUB or LILO to the first sector of the Linux (Ubuntu) parition. (Rather than to MBR)
This can be done easiest by using the Dapper Drake 'Alternate' Install CD's new 'Rescue a broken system' mode. You will need to know the partition number first. [Click here]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub") to see an illustrated how-to. Remember, install to a partition number, eg (hd0,2) rather than to MBR, eg (hd0).

If you have the Dapper 'Desktop Live/Install CD, you can also install GRUB to your Ubuntu partition, [click here]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")
 sililarly, replace  root (hd0, 1) with whatever hard disk and partition number will be correct for your setup, and replace setup (hd0)  with setup (hdx,x) where hdx,x ia the right drive and partition number.

Hopefully that will at least get you booting again, if Ubuntu is bootable.
I can't understand why GRUB won't boot it from the command line though. If it's bootable, you should be able to boot it from Grub's command Line. Even if you need to edit /etc/fstab, it should at least boot.

Well, that's my suggestion for now, give it a try and see if it gets you anywhere, I hope it will. Regards, Herman. :D

---

### Post by Herman on 2006-07-23
> The machine itself is built on an Asus P5WD2 Premium mobo, which has 2 IDE channels. When we did the install, the main drive was on the 'blue' IDE (IDE), and now we have moved the main to the 'red' IDE (actually, ITE IDE), for space/layout issues inside. Maybe this is our problem; neither me or my brother have ever had a board with ITE IDE, and really know nothing about it. Yup, after some googling, it seem like others with the same error message have either had their hard disks plugged in differently form expected, jumpered differently, or configured in thier BIOS differently, or didn't know what was different.
But if you had space limitations maybe you have to have it plugged in like that, and besides, we probably don't want to have to risk changing it back again now, in case it does something to Windows this time.
I wonder how all your Ubuntu files got changed? Oh well, the fact is they appear to be changed anyway , I guess it doesn't matter how.
 	Code:
 	[LEFT]FROM FSTAB:

proc            /proc           proc    defaults        0       0
/dev/hde3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0[/LEFT]
 
 That's really weird, your cdrom dirve is /dev/hda now? Wow! :D

If you use GAG to chainload GRUB and GRUB still loads Ubuntu, you might gain something just by the fact that you are re-installing GRUB. Grub is a better bootloader than Lilo, because it updates itself when we get an new kernel during an update. However, maybe you''l be right back where you started again too, after all that, and still get the same error message.

GAG/Lilo might work if GAG/GRUB doesn't.
You should be able to install Lilo to your Ubuntu partition by the 'Alternate' CD method already described by using your 'Tab' key to select <Go Back> instead of installing Grub, and <Go Back> a second time if necessary, to get back to the Ubuntu installer Main Menu. From there you should something like this, (see fig 12 MBR and below that), [*Click Here*]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_Go_Back__to_Install_LILO_Boot_Loader").
You should be able to install Lilo that way. Well, that's one way, if you have the 'Alternate' CD. 

If you don't have the 'Alternate' CD, you can use the 'Desktop' CD to install Lilo with. that's a little more explaining, I'll wait until you ask me before I go into the details of that.

If even that doesn't work you'll have to decide whether it will be easier to just re-install Ubuntu or play around with your hard drive jumpers, wires/motherboard connections, and BIOS settings some more.  Hopefully one or the other will fix it, but you might even need to do both. Save those ideas 'till last probably.
Regards, Herman :D

---

### Post by CamB on 2006-08-18
> New configuration:
ITE IDE: HDD1 as Master, HDD2 as Slave, both on Primary Channel
IDE: CDROM as Master on Primary (only) Channel

Sorry to thread dig on this...

I'm in exactly this position now - I've installed 6.06 on my Asus P5WD2 in the same configuration. The DVD has to go on the Master, so the HDD's I'm using for Ubuntu go on the ITE controller.

It seems the controller is the problem - I boot and run fine by connecting the 2 HDDs to the master ide controller and disconnecting the DVD.

So - does anyone know a workaround to get grub to successfully boot from a drive which is connected to the ITE controller on one of these mobos?

---

### Post by jlgoolsbee on 2006-08-25
> **Herman said:**
> 
I wonder how all your Ubuntu files got changed? Oh well, the fact is they appear to be changed anyway , I guess it doesn't matter how.
```

[LEFT]FROM FSTAB:
proc            /proc           proc    defaults        0       0
/dev/hde3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0[/LEFT]
```
 
 That's really weird, your cdrom dirve is /dev/hda now? Wow! :D


Well, actually I changed those values by editing them myself (when I booted the LiveCD), because theorhetically, those are the correct values according to the various commands I ran while using the LiveCD.

The reversed IDE assigning is a documented bug in Dapper... see here:
[http://ubuntuforums.org/showthread.php?t=192002](http://ubuntuforums.org/showthread.php?t=192002)
[http://ubuntuforums.org/showpost.php?p=1392432&postcount=5](http://ubuntuforums.org/showpost.php?p=1392432&postcount=5)

Still, no dice here... any fresh ideas (that don't involve re-installing something)?

---

### Post by CamB on 2006-08-26
> **jlgoolsbee said:**
> Still, no dice here... any fresh ideas (that don't involve re-installing something)?

Kinda... I ended up installing it on a HDD attached to the ITE controller, then swapping the HDD to the main IDE channel and sticking the DVD on the ITE channel.

I had to change a couple of references in the grub menu.

---

