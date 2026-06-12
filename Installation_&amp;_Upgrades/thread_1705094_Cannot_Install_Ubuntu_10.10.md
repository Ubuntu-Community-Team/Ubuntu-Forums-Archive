---
title: "Cannot Install Ubuntu 10.10"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by apodictic on 2011-03-11
Hello. I have been trying to install Ubuntu 10.10 on my laptop. Every time I boot from my USB and I select install, loops on an error message that seems like a DRDY error. Any ideas? The specs of my laptop are below:

Brand: MSI
Intel Core 2 Duo 2.0GHz processor
BIOS: A1674IMS Ver 1.0L
RAM: 4GB
Video: ATI Mobility Radeon HD 3400 Series
Current OS: Windows 7 Ultimate 32bit (just a note here, I reinstalled windows 7 over Windows Vista, but I am pretty sure vista is out of my computer. However, whenever I boot, I load into Windows Boot Manager and get the choice to select either Vista or 7, but both choices boot Windows 7)

Thanks for the help.

---

### Post by Hedgehog1 on 2011-03-11
Welcome to the Fourms!

We need to get a look at your disk partition layout.

Please boot  off the LiveCD/LiveUSB, select 'TRY' and then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

I expect with a little clean up of unused partitions we can get you rolling.

***The Hedge***

:KS

---

### Post by apodictic on 2011-03-12
Hi. Thank you. If you mean "Run Ubuntu from this USB," I tried that and it does the same error as when I hit "Install Ubuntu on a Hard Disk"

---

### Post by Hedgehog1 on 2011-03-12
> **apodictic said:**
> Hi. Thank you. If you mean "Run Ubuntu from this USB," I tried that and it does the same error as when I hit "Install Ubuntu on a Hard Disk"

apodictic,

When you boot of the Ubuntu USB, do you see this screen before you press any keys:
[IMG]http://www.ubuntu.com/sites/default/files/active/maverick/trial_01_medium.jpg[/IMG]

If you are seeing a different screen, you are not using the LiveCD/LiveUSB iso, but the 'Alternate Installer' iso that does not offer the 'TRY' option.

Are you seeing this screen?  Or something else?

***The Hedge***

:KS

---

### Post by apodictic on 2011-03-12
@hedgehog1 I do not see that screen first. The first screen I see is shown below.


[IMG]http://img204.imageshack.us/i/img0752t.jpg/[/IMG]

---

### Post by Hedgehog1 on 2011-03-12
apodictic,

OK - we can still work with this.

The very first menu option select says '**Run Ubuntu from this USB**'.  Choose that, please.  When Ubuntu comes up, do this:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.


***The Hedge***

:KS

---

### Post by apodictic on 2011-03-12
Yea. That is what I hit. It still gave me the same problem with the DRDY loop error.

---

### Post by apodictic on 2011-03-14
So, any ideas?

---

### Post by apodictic on 2011-03-25
Results from the sudo fdisk -l command

---


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x437c30c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12768   102557696    7  HPFS/NTFS
/dev/sda2           12768       38914   210010112    7  HPFS/NTFS

---

### Post by Hedgehog1 on 2011-03-25
apodictic,

So, it looks like you were able to 'Run Ubuntu from this USB'.

[B]Device Boot Start End Blocks Id System
/dev/sda1 * 1 12768 102557696 7 HPFS/NTFS
/dev/sda2 12768 38914 210010112 7 HPFS/NTFS[/B]

Right now your hard drive has two partitions, the boot partition for Win7 and the main Win7 partition.  You also appear to have open space at the end of your drive.

The next logical step is to run gparted from the 'Run Ubuntu from this USB' option, and create the partitions you will want for Ubuntu to use.

The layout will be:

/dev/sda3 Logical Partition to the end of the drive, filling all space left
__/dev/sda5 ext4 logical drive, taking all but the swap space your want
__/dev/sda6 Linux Swap  (make it the size of your RAM, plus a tiny bit more).

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-25
When you get to here on the install:

[IMG]http://img705.imageshack.us/img705/2588/hp4partitions09.png[/IMG]

It will get you to here:

[IMG]http://img849.imageshack.us/img849/9937/hp4partitions10.png[/IMG]

Setup **/dev/sda5** this way (your partition size will be different):

[IMG]http://img861.imageshack.us/img861/5274/hp4partitions11.png[/IMG]

Setup **/dev/sda6** this way (your swap partition size may be different):

[IMG]http://img26.imageshack.us/img26/4934/hp4partitions12.png[/IMG]

Make sure your Device for boot loader installation is **/dev/sda** , not /dev/sda1 or /dev/sda3 - just **/dev/sda**

[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG]

And you should be ready to press "INSTALL" and go!

***The Hedge***

:KS

---

### Post by apodictic on 2011-03-27
Thank you for the instructions. I have followed your instructions and after I perform the first restart I get an this screen after selecting ubuntu from grub load:

---
Gave up waiting for root device. Common problems:
   - Boot args (cat /proc/cmdline)
      -Check rootdelay= (did the system wait long enough?)
      -Check root= (did the system wait for the right device?)
   -Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/ecaffac9-9043-43f8-bcde-5c7c0269dedc does not exist.
Dropping to a shell!


BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

---

### Post by apodictic on 2011-03-29
Any solution to this problem?

---

### Post by collisionystm on 2011-03-29
are you trying to dual boot ubuntu and windows? Or replace windows with ubuntu?

---

