---
title: "Ubuntu on USB hard drive and GRUB error 17"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by huckey on 2007-04-14
Hi all,
  I have a ASUS P4P800E-Deluxe based computer with a Seagate internal hard drive. On that hard drive I have Windows 2000 installed. 
  I have now bought a WD MyBook external USB drive and want to install Ubuntu there. What I also want is that GRUB is installed on that external drive and since there already is some data on that external drive I need to keep the existing FAT32 partition and add Ubuntu's partitions at the end of the drive.
  The internal drive is seen as First Hard Drive and the external one is seen as Second Hard Drive in by BIOS.
  The goal is to have Ubuntu totally transparent as the internal hard drive is the default to boot from and I want to boot Ubuntu only when I press F8 at startup to get boot devices list.

  I am a total newbie to Linux world.

  What I succeeded with so far was to:
- boot from Live CD
- during installation limit the existing FAT32 partition on the external drive and create (automatically by the installation program) partitions for Ubuntu
- install Ubuntu to the newly created partitions
- since the external USB drive is seen as the second drive, in the installation program I told it to install GRUB to (hd1).

  Now, when I try to boot from the external USB drive I can see that GRUB tries to load stage 1.5 and then displays Error 17 (no more text than just the error number) and it hangs (pressing keys does not result in anything).

  Looking into what Error 17 is I suppose there is something wrong with my GRUB configuration. I have tried numerous options with menu.lst but still got Error 17.
  Here is what my fdisk -l shows:
Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       28969   232693461    c  W95 FAT32 (LBA)
/dev/sdb2   *       28970       38506    76605952+  83  Linux
/dev/sdb3           38507       38913     3269227+   5  Extended
/dev/sdb5           38507       38913     3269196   82  Linux swap / Solaris


  Here is what I have in my menu.lst (an excerpt) - as you can see I have already played with the file trying to follow one of the hints I found on this forum to replace /dev/sdb with UUID of the drive but it did not help:
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=8e7b50db-a7ac-456f-91f5-1b54c3eb7575 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

  Can you help me with how I should install Ubuntu or change GRUB settings to get the desired setup?

  Thank you!

Huckey

---

### Post by andy gee on 2007-04-14
Herman's Super Grub Disk help page is great for grub problems - error 17 is here: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

So maybe check that the location of the root (hdx,y) as this is the most common reason for error 17 when booting Linux? You're booting from an external USB hard drive - will that still use the standard  root(hdx,y) system?

You could try using the Super Grub DIsk to reinstall Grub, but that might not explain why you had the problem.

---

### Post by pxwpxw on 2007-04-14
**huckey**

> 
Device Boot Start End Blocks Id System
/dev/sdb1 1 28969 232693461 c W95 FAT32 (LBA)
**/dev/sdb2** * 28970 38506 76605952+ 83 Linux
/dev/sdb3 38507 38913 3269227+ 5 Extended
/dev/sdb5 38507 38913 3269196 82 Linux swap / Solaris


Here is what I have in my menu.lst (an excerpt) - as you can see I have already played with the file trying to follow one of the hints I found on this forum to replace /dev/sdb with UUID of the drive but it did not help:
title Ubuntu, kernel 2.6.17-10-generic
**root (hd1,2)**
kernel /boot/vmlinuz-2.6.17-10-generic root=UUID=8e7b50db-a7ac-456f-91f5-1b54c3eb7575 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot


Hope you made a backup copy of the original menu.lst.

But if /dev/sdb2 is the linux root partition, with directory /boot, holding kernels and /boot/grub,
then menu.lst should show: root  (hd1,1)  - not (hd1,2)
 
assuming grub has mapped (hd1) /dev/sdb, in /boot/grub/device.map on the external drive root partition.

I think the Super Grub Disk would be a good insurance against further problems.

---

### Post by bulldog on 2007-04-14
Just open the menu.lst and you'll see it points to hd1.?,change the one into a zero and it boots fine.
The disk with GRUB installed is often revered to as hd0.
Leave the part behind the  ,  as it is.

---

### Post by huckey on 2007-04-14
Hi again,
  I have tried all the options provided in the replies to my original post. No success :-(

  I can not download Super Grub - the download site does not respond. Is there a mirror?

  In the meantime I have reinstalled Ubuntu (deleted Linux partitions and started everything over) and told it to install Grub to (hd1,1) instead of (hd1). I got to the same place: Error 17 and Grub hangs.

  This brings me to this question: doesn't the fact that no matter what changes I applied to menu.lst and that I reinstalled Ubuntu with changed place for Grub mean that it is not a problem with menu.lst but with Grub itself? I think it is since Grub hangs and I can not get further.

  Is it possible that my Linux partition lies too far away from "the beginning of the disc" which makes Grub hang because it can not address so far?

  What other options do I have? 

Huckey

---

### Post by confused57 on 2007-04-14
The Super Grub Disk website seems to be down at the moment, it'll probably be back up soon.
You might try the GAG boot manager:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)
you can make a boot floppy or cd 

You could be right about your Ubuntu root partition is too far from the beginning of the disk.  I was helping someone else with a grub error 17, but SGD reported a grub error 18(which indicates this).

See this for an explanation of grub errors:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_Errors](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_Errors)

Added:  I did a Google search & looks like you can download an older version of SGD(.9532) here:
[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)
scroll down a little bit & on the right side of the screen is an option for downloading this version

---

### Post by andy gee on 2007-04-15
Three System rescue tools, one with the **Super Grub Disk** included:

1. The Ultimate Boot CD at [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) is a boot disk with a bunch of tools that everyone should have, and it includes the **Super Grub Disk vers. 9575** (slightly older than current, but newer than 9532). It is free, but I don't know if it's open source. You'll find good clear instructions at the website.

The iso (116 Mb) for cd burning as well as the .zip (94MB) are at  [http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

The next two might or might not help, but they're good rescue cds to have generally:

2. the **gparted live CD** is useful for all sorts of partition work and you can get it at [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) I have vers 0.3.3 and it's only 29 Mb and fits on a minicd.

3. I have found the **System Rescue cd**  at [www.sysresccd.org/Download.en.php](www.sysresccd.org/Download.en.php) useful and it's handy to have, size=115 Mb.

Hope this helps.

---

### Post by huckey on 2007-04-15
Hi,
  thank you all for your tips and hints.

  I finally made it to work. 

  In my case the problem seem to have been caused by two factors:
- the fact that my Linux partition was located too far away from the beginning of the disc
- the fact that when I boot from my external hard drive it becomes hd0 although it was hd1 during install.

  The first factor I managed to overcame with GPartEd: I deleted the existing Linux partition and moved the existing FAT 32 partition to the end of the disc leaving the space unused so that the installer could use it.

  The second factor I overcame with booting via Super Grub Disk and then changing what I had in menu.lst from (hd1,1) to (hd0,1). This did the trick.

  Thanks again for help!

Huckey

---

### Post by pxwpxw on 2007-04-15
well done:D

---

