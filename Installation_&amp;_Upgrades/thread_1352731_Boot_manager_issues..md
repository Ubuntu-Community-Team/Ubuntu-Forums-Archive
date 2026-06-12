---
title: "Boot manager issues."
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by rsvr85 on 2009-12-11
Hey guys, i do hope someone can help.  I'm completely lost :(

Some background for you;

I have Windows 7 Ultimate installed on the first partition of my first hard drive.

I booted into the Karmic desktop edition CD and went ahead and installed Ubuntu onto an external USB hard drive i have.  The installation went fine, Ubuntu is working perfect :)

I restart the machine with the USB external hard drive plugged in and GRUB loads up and i'm able to boot into either Windows or Ubuntu.
However, if i remove the drive and boot the computer, GRUB starts to load but i get a "No such disk" error.  

This has me stumped, surely GRUB shouldn't be loading without the external hard drive plugged in a Windows boot loader should load up??

I tried a startup repair for Windows (without the external plugged in) and Windows said that there were no problems......well, sorry Stevie.....there is, there's no bootloader!!

Can someone kick in the right direction please.  This really is not good as i cannot use this PC without the USB external drive plugged in (which of course defeated the object of installing in on the external in the first place).

Any help is greatly appreciated and i thank you in advance for your precious time :) 

If you need any additional info i will be more than willing to help.

EDIT:

Here's the output of ```
sudo update-grub
```

```
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
```

---

### Post by oldfred on 2009-12-12
IF you have the internal hard drive set as first in BIOS that is what the computer boots. When you had the external plugged in grub automatically installed to the internal as that was the boot drive. 

I would reinstall grub to the external drive. You will have to check to make sure it installs to the correct drive. It will depend on which drive is sda and sdb.

I would then recover the Win7 boot loader on the internal drive. If you switch the BIOS to boot the external first then grub will boot. If not plugged in the the win loader should boot. 

There seem to be some issues on drive order in grub and you may need to make sure it knows the new drive order so on an update it does not overwrite windows again.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Someone had this comment that may help
Reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/apt/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. After an update you should manually rerun it so it stays in-sync.

---

### Post by rsvr85 on 2009-12-12
Thanks for the speedy response Fred :)

I went through the commands for GRUB as shown in the tutorial.  No errors were shown.

I then went into BIOS changed the boot priority to internal, booted off my W7 DVD and fixed the Windows boot manager, all fine and dandy there.

Now it seems that GRUB wasn't re-installed.  I can now boot into Windows fine but with the external plugged in and set to priority in BIOS i get the same error as before; "no such disk"

Should i boot into my Karmic CD and run the terminal commands again?

I'm in Windows atm with no way into my Karmic install.

EDIT:
i booted into the LiveCD and ran this in the terminal

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xb7e61057

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10937    82680832    7  HPFS/NTFS
/dev/sda2           10938       41345   229884480    7  HPFS/NTFS

Disk /dev/sdd: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbea2b0fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        7296    58605088+  83  Linux
ubuntu@ubuntu:~$ sudo mkdir /media/sdd1
ubuntu@ubuntu:~$ sudo mount /dev/sdd1 /media/sdd1
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sdd1 /dev/sdd1
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly
ubuntu@ubuntu:~$

```

---

### Post by rsvr85 on 2009-12-12
I went ahead and reinstalled Karmic on the external.  I couldn't figure how to reinstall GRUB on my own :(
This time i disabled my main hard drive in the BIOS and in the advanced installation options made sure that the boot manager was installed on the external drive (i missed that option last time;) ).

---

