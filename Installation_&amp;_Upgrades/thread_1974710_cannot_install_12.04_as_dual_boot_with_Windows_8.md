---
title: "cannot install 12.04 as dual boot with Windows 8"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by pbpersson on 2012-05-06
This is part two of my first attempt at installing 12.04 with Windows 8 on my test machine.

Last weekend I tried installing it using the "specify your own partitions" option and when I rebooted the only thing to come up was Windows 8, no grub menu.

Today I re-installed Ubuntu using the "do you want to totally re-install 12.04 as a dual boot with Windows" or something like that.  When I reboot I still only get Windows 8.

I know there is some way to get into some special screen somewhere and type a special command to tell grub to reconfigure itself but I am a little foggy on that and not sure if this procedure has changed in 12.04.  Right now I am typing from the 64-bit 12.04 live CD on this machine.  Here is the fdisk -l output:

```
 ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bb3fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   312578047   155929600    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f3a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *        2046   136718335    68358145    5  Extended
/dev/sdb3       136718336   234440703    48861184   83  Linux
/dev/sdb5        97658880   136718335    19529728   82  Linux swap / Solaris
/dev/sdb6            2048    97658879    48828416   83  Linux

Partition table entries are not in disk order
 
```

Windows is on sda and Ubuntu is on sdb, sdb3 is root and sdb6 is home.


Phil

---

### Post by wilee-nilee on 2012-05-06
Try booting from the sdb drive first, change the bios to show it above  the sda. If you get to ubuntu run this command to update grub to add  windows to grub if not there already,

```
sudo update-grub
```

---

### Post by pbpersson on 2012-05-06
Thank you!  That was a faster fix than I ever could have hoped for!

\\:D/\\:D/\\:D/\\:D/

---

### Post by wilee-nilee on 2012-05-06
> **pbpersson said:**
> Thank you!  That was a faster fix than I ever could have hoped for!

\\:D/\\:D/\\:D/\\:D/

Your welcome, enjoy. :)

---

### Post by pbpersson on 2012-05-06
I guess I am not 100% solved.

Windows 8 was not working so I did the "sudo update-grub" and it is still not happy.

It tries to boot and for a while it is on a screen that says "Preparing automatic repair" but then it goes to this screen:

```

Your computer needs to reboot
Please hold down the power button
Error code: 0x00000050
Parameters:
0x85C00000
0x00000000
0x81DC4920
0x00000002

```

:(

---

### Post by wilee-nilee on 2012-05-06
I have had W7 and W8 and several Linux installs on a single HD all boot fine but I always custom install windows so no boot partition is made, two HD's should not be a problem. Lets get a closer look at your setup run the script from this download and post the results.txt that will appear with the command I give you.

Extract it to your desktop.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by pbpersson on 2012-05-06
> **wilee-nilee said:**
> I have had W7 and W8 and several Linux installs on a single HD all boot fine but I always custom install windows so no boot partition is made, two HD's should not be a problem. Lets get a closer look at your setup run the script from this download and post the results.txt that will appear with the command I give you.

Extract it to your desktop.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

I am going to attach it since it is rather long.

---

### Post by wilee-nilee on 2012-05-06
The script appears to be okay, it may be that a chkdsk run from W8 on its C partition might clean this up. Here is a link, be sure to boot into Ubuntu after this and run

```
sudo update-grub
```After the chkdsk in W8 to get grub reloaded for a retry at booting the W8 from grub.

[http://windows8themes.org/how-to-run-chkdsk-in-windows-8.html](http://windows8themes.org/how-to-run-chkdsk-in-windows-8.html)

Windows chkdsk command

```
chkdsk /r
```I assume you can still boot W8 from the sda drive.

---

### Post by pbpersson on 2012-05-06
I am in Ubuntu now and cannot boot into Windows 8.  You suggested that I boot into Windows 8 and run a checkdisk but I cannot get there to try this.

I might try booting from the Windows 8 CD to see if it can fix this.  I wonder if it has some tools like checkdisk?

---

### Post by oldfred on 2012-05-06
You should be able to change BIOS or one time boot key to boot Windows drive and directly boot Windows.

You may need to turn off fast boot.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by wilee-nilee on 2012-05-06
> **pbpersson said:**
> I am in Ubuntu now and cannot boot into Windows 8.  You suggested that I boot into Windows 8 and run a checkdisk but I cannot get there to try this.

I might try booting from the Windows 8 CD to see if it can fix this.  I wonder if it has some tools like checkdisk?

You should be able to boot to windows 8 by putting the sda drive first in the bios.

There is a per session boot from menu that can be triggered at powering on to choose the HD, cd, usb.. etc to boot from as well generally it is f12, tap it while you see the bios gui goes by, not actually opening the bios. It may say on the screen the key prompt for this menu as well. 

Also check the above post as well I just saw that it was there. :)

---

### Post by pbpersson on 2012-05-06
Tapping F12 during the system boot did not do anything.

I ran a chkdsk on C: and it did not find any problems.

I can get to Windows 8 and Unbuntu 12.04 by changing the disk drive boot order in the BIOS so it is an extra step but this is just a test machine.  I should not be bouncing between the operating systems that much.

Thank you!

---

### Post by wilee-nilee on 2012-05-06
> **pbpersson said:**
> Tapping F12 during the system boot did not do anything.

I ran a chkdsk on C: and it did not find any problems.

I can get to Windows 8 and Unbuntu 12.04 by changing the disk drive boot order in the BIOS so it is an extra step but this is just a test machine.  I should not be bouncing between the operating systems that much.

Thank you!

You have a good attitude about this, it can get frustrating for sure. All or most computers have a one time boot menu, if you look on line with that model and onetime boot or boot from menu or get the manual, you can get that key sequence so you can avoid having to open the bios every time. It might jsut be another f key or esc, some times it is two keys in sequence.
 
There may be a fix but yeah W8 is in development so sooner or later it will have to be purchased to run. Not a bad OS really, a little different with the metro setup but pretty easy to run and figure out.

---

### Post by Francewhoa on 2012-08-31
Have you tried to restart and press SHIFT key? This will display the grub screen. There you can select if you want to boot Windows or Ubuntu.

---

