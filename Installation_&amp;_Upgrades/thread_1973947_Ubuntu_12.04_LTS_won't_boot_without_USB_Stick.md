---
title: "Ubuntu 12.04 LTS won't boot without USB Stick"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by bkosh84 on 2012-05-05
Hello all-

I am looking for help with an issue I'm having with Ubuntu 12.04 LTS 64bit.. I installed Ubuntu and erased my Windows 7 (intentionally) and now I cannot boot Ubuntu unless my Installation USB Stick is inserted into the computer and I first boot it through the USB stick.. But after I boot into Ubuntu, I can remove the stick and it will work just fine.. Until I restart my computer and need to boot Ubuntu again.. Anyone know what's up? I installed it on a HP Pavilion g4 Laptop.

---

### Post by oldfred on 2012-05-05
When you install Ubuntu with the auto install options, the grub2 boot loader is normally installed to sda. Some computers make the flash drive sda by default so you may have installed grub to the flash drive?

Post this to see which drive your install is in.

sudo fdisk -l

if your full install in in sda once booted.

sudo grub-install /dev/sda

but if it is sdb

sudo grub-install /dev/sdb

That should overwrite the boot loader in the MBR.

But grub2 remembers where to reinstall on major grub updates.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

If it is not the hard drive we will need to reset that.

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by Pablo W on 2012-05-05
Hi,

I had the same problem as bkosh. In my case, the problem appeared after a fresh install of Ubuntu 12.04 in a mini HP 5101 solid-state netbook.
I followed oldfred instructions to the letter. Now I don't need to plug the installation usb stick for the netbook to boot. It's such a relief! 

I found also that grub2 still had the usb drive as a reference for major updates, so following oldfred post, I managed to change that as well.

Thank you very much, oldfred. I think this is the first time I get something fixed through a single answer... and without even the need to post the question myself! 

Today, I believe in Ubuntu again :)

Cheers.

---

### Post by ka386 on 2012-05-12
I had exactly the same problems and corrected them as in the topic.
Thank you oldfred!

---

### Post by Action Jackson on 2012-05-22
Hi, I've been having the same problem (word on the street is that there was a bug with the v12.04 installer that installs grub on the USB drive by default). I must be missing something, have tried to install to both sda and sdb but I still can't boot up without the usb in the drive.

Will copy in my terminal details to see if you guys can figure out what's going on:

[FONT=Courier New]sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000df64c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   304343039   152170496   83  Linux
/dev/sda2       304345086   312580095     4117505    5  Extended
/dev/sda5       304345088   312580095     4117504   82  Linux swap / Solaris

Disk /dev/sdb: 4009 MB, 4009754624 bytes
23 heads, 23 sectors/track, 14804 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7831551     3911744    c  W95 FAT32 (LBA)

Disk /dev/mapper/cryptswap1: 4216 MB, 4216324096 bytes
255 heads, 63 sectors/track, 512 cylinders, total 8235008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa242e58b

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table[/FONT]

It looks like sdb's marked as the boot device (I presume that's what the asterisk means) but I can't seem to change it to sda where ubutu's actually installed...

---

### Post by wilee-nilee on 2012-05-22
> **Action Jackson said:**
> Hi, I've been having the same problem (word on the street is that there was a bug with the v12.04 installer that installs grub on the USB drive by default). I must be missing something, have tried to install to both sda and sdb but I still can't boot up without the usb in the drive.

Will copy in my terminal details to see if you guys can figure out what's going on:

[FONT=Courier New]sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000df64c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   304343039   152170496   83  Linux
/dev/sda2       304345086   312580095     4117505    5  Extended
/dev/sda5       304345088   312580095     4117504   82  Linux swap / Solaris

Disk /dev/sdb: 4009 MB, 4009754624 bytes
23 heads, 23 sectors/track, 14804 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7831551     3911744    c  W95 FAT32 (LBA)

Disk /dev/mapper/cryptswap1: 4216 MB, 4216324096 bytes
255 heads, 63 sectors/track, 512 cylinders, total 8235008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa242e58b

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table[/FONT]

It looks like sdb's marked as the boot device (I presume that's what the asterisk means) but I can't seem to change it to sda where ubutu's actually installed...

In the ubuntu install run in the terminal.

```
sudo grub-install /dev/sda
```Then

```
sudo update-grub
```Shut the computer down and remove the usb, and power on and see if you get the grub menu now.

If you continue to have this problem start a thread and run these commands in the ubuntu install, and go to the home and find the results.txt. Copy and paste all the text from that results.txt to a new thread, when you start the thread hit the # in the panel and paste all the text between them. 

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
``` ```
chmod a+x bootinfoscript
``````
sudo bash bootinfoscript
```The asterisk on the sdb1 is just a bootflag you do not need this on the sda HD with the ubuntu install.

---

### Post by Action Jackson on 2012-05-22
Thanks for the tips wilee-nilee, unfortunately it still won't boot without the usb. See my new thread with boot info [http://ubuntuforums.org/showthread.php?p=11957939#post11957939](http://ubuntuforums.org/showthread.php?p=11957939#post11957939)

EDIT > Turns out it was the bootflag (apparently some boards look for it). I used Gpart to change flag to spa1 and now it's booting without usb!

---

### Post by mijalis on 2012-09-18
If you begin a fresh install, another solution to this problem is to choose grub's location during the installation process.
Full procedure is described here: [http://ourlife01.blogspot.gr/2012/09/step-by-step-installation-of-lubuntu-on.html](http://ourlife01.blogspot.gr/2012/09/step-by-step-installation-of-lubuntu-on.html)

---

### Post by SteveGeemaggio on 2013-01-18
Hello,

I use Trisquel 6.0 32bit (which is based on Ubuntu 12.04) and I have it dual booted with Windows 7. I had this exact problem and was Completely baffled until I found this forum. Grub seemed to install into my usb key and Refused to boot any operating system without the usb key inserted. So I simply followed wilee-nilee's instructions:

#sudo grub-install /dev/sda

Then
     
     #sudo update-grub
 
Then shut down the computer, removed usb key, turned on the computer and problem solved!

Thank You!

---

### Post by eriknorthrop on 2013-02-20
I am also having the same problem, I cannot boot from my SSD with a fresh in stall of 12.04 LTS. I tried to boot from the flash drive and copy the grub file to the proper location on the SSD and reboot.. no luck. 

Since i cannot boot from the SSD at all, I cannot run grub-install. Is there any ways around this?

Thanks

---

