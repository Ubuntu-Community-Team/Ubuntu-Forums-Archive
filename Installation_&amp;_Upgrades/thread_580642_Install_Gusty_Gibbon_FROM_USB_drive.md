---
title: "Install Gusty Gibbon FROM USB drive?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Skootles on 2007-10-18
So I have a new box arriving soon that I plan to install gusty gibbon on, however I just realized, I need another way to install gusty on it. It's a DVD drive-less machine, so I was wondering if it's possible to install over a network or from a USB hard drive I have?

If not I'll have to borrow the CD drive from another pc of mine, but I'd rather not.

---

### Post by DavidTruesdale on 2007-10-19
Hi, I attempted to install Ubuntu 7.10 on a USB pendrive last night. I found a very good tutorial at [http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar). The installation does not work perfectly. I cannot get the persistent mode to work yet, but the install functions perfectly as a Live image. Although I haven't done so, it should work for installing to a hard drive through the gui.

Hope this helps.

---

### Post by HostFat on 2007-10-19
I have the same problem. I want to install Gusty Gibbon **FROM** USB drive.
I DON'T want to install it ON a USB drive, it's different.

---

### Post by shad0w_walker on 2007-10-19
[http://mywheel.net/blog/index.php/ubuntu-network-install/](http://mywheel.net/blog/index.php/ubuntu-network-install/) 

That link might help you out. Not installing from USB but it should help you setup a network boot server.

---

### Post by bliffle on 2007-10-19
I think you can do it with a CLI "mount" command. Here's one that another guy was using:

```
mount -o loop -t iso9660 ubuntu-7.10-alternate-i386.iso  /media/cdrom0
```

That's for an iso on a CD so you have to adapt it for USB.

---

### Post by shad0w_walker on 2007-10-19
Not to bash your idea, but how is that going to work on a system with out an OS on it? He can't mount a ISO to install an OS from with no OS. Not to mention he would have to reboot and kill of that OS to do an install. It's a good idea for installing just about anything else, but I'm afraid that isn't gonna work for installing an OS.

---

### Post by Skootles on 2007-10-19
> **shad0w_walker said:**
> Not to bash your idea, but how is that going to work on a system with out an OS on it? He can't mount a ISO to install an OS from with no OS. Not to mention he would have to reboot and kill of that OS to do an install. It's a good idea for installing just about anything else, but I'm afraid that isn't gonna work for installing an OS.
Yeah, looks like I'll have to borrow my CD drive from my other PC..   or, actually, I think I saw one in my roommate's spare bedroom that's been there for a few months..  :D

And so I don't have to start another thread, I'm going to need a wireless card, and I was wondering if [this D-Link WDA-1320]("http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10076869&catid=") will be fully compatible with Gusty?

---

### Post by pssturges on 2007-10-19
Hi,

It should definitely be possible using this guide: [Preparing Files for USB Memory Stick Booting]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=3565717")

You need to use the 'Flexible' version and then put the iso on the flashdrive. Also, make sure you get your files from the gutsy archive.

However, I have been trying this for several hours and it all goes well until the installer tries to find the ISO. It scans all the hard drives but does not seem to search the flashdrive. So of course it doesn't find it!

Any ideas?

Thanks
Phil

BTW, it actually fails because it's trying to find files on the cdrom, which is broken in this system.

---

### Post by pssturges on 2007-10-20
Anyone?

---

### Post by sicofante on 2007-10-20
Check these threads:

[http://ubuntuforums.org/showthread.php?t=579654](http://ubuntuforums.org/showthread.php?t=579654)
[http://ubuntuforums.org/showthread.php?t=568609](http://ubuntuforums.org/showthread.php?t=568609)
[http://ubuntuforums.org/showthread.php?t=563411](http://ubuntuforums.org/showthread.php?t=563411)
[http://ubuntuforums.org/showthread.php?t=503787](http://ubuntuforums.org/showthread.php?t=503787)

---

### Post by murak on 2007-10-20
I also want to install Ubuntu from and usb stick. I know its possible since this exists: [http://www.dragontechnology.com/ubuntu_usb.php](http://www.dragontechnology.com/ubuntu_usb.php)
It would be nice to just download the files from that one and put them on my own usb stick. Anyone know where I can download it? Or is that ileagal?:confused:

---

### Post by Matt Yun on 2007-10-20
I know that the original poster was asking about installing from a USB external hard drive; but this would be the same as installing from a USB pen drive as well.  Essentially, you want the USB drive (whether hard drive or pen drive) to act like a CD-ROM, so you can run the ubiquity installer to do a proper hard drive installation on the primary disk.

I actually installed Gutsy from a USB pen drive to my hard disk.  This article was very helpful:  [How-to:  Installing Ubuntu Linux on a USB Pen Drive]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2").  Summary of what I did (assuming that your USB drive is /dev/sdb):

Download the Gutsy CD ISO file (e.g. to ~/ubuntu.iso) and verify MD5 etc.

In a terminal, do this:

```
$ sudo apt-get update && sudo apt-get install lilo

$ sudo mkdir /mnt/tmp

$ sudo mount -t iso9660 -o loop ~/ubuntu.iso /mnt/tmp

$ cd /mnt/tmp

$ sudo cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz install/mt86plus /media/USBstick

$ cd /media/USBstick

$ sudo mv isolinux.cfg syslinux.cfg

```

Edit syslinux.cfg [cf. debuntu.org article].  Contents of syslinux.cfg:

```
DEFAULT persistent
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL persistent
  menu label ^Start Ubuntu in persistent mode
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper persistent initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL live
  menu label ^Start or install Ubuntu
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL xforcevesa
  menu label Start Ubuntu in safe ^graphics mode
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper xforcevesa initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel vmlinuz
  append  boot=casper integrity-check initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

```

Continue in terminal:
```
$ sudo umount /media/USBstick

$ sudo syslinux -f /dev/sdb1

$ sudo lilo -M /dev/sdb

```

Re-boot with your USB drive.

---

### Post by bellawood on 2007-10-20
Hi, I migth have one idea, would it work if we copied all the cd iso stuff to a pen drive and insert in it a disk boot? there is any way to do aomething like that??

---

### Post by bellawood on 2007-10-20
Anyway to do that in windows platform Matt, Trying to install ubuntu without the cd drive too, but dont have any linux installed.

---

### Post by pssturges on 2007-10-20
Matt Yun,

That looks very different to the guide  was using unsuccessfully. I'll give it a go. Thanks very much for your help

Phil

---

### Post by HostFat on 2007-10-21
Great guide, but is there something to make this from windows?

---

### Post by pssturges on 2007-10-21
OK,

I gave it a go. All seemed to go well with putting all the bits & pieces on the flash drive. I can boot from the flash drive and get the first splash screen, but then I get the following error:

'Could not find kernel image: linux'
:mad:

I don't know if it makes any difference, but I trying to install Kubuntu.

Any ideas where I might be going wrong?

Thanks
Phil

---

### Post by spud42 on 2007-10-21
did you change the references to ubuntu to kubuntu with the relevant correct file names and iso names?

---

### Post by pssturges on 2007-10-21
Yeah, I did. I couldn't say with 100% certainty that I did them all though. I might have to try again and pay particular attention to that?

Thanks
Phil

---

### Post by Matt Yun on 2007-10-22
> **HostFat said:**
> Great guide, but is there something to make this from windows?

I don't know how to install Ubuntu from Windows, but I've read that [Wubi ]("http://wubi-installer.org/")can do it.  

From their website:  "Wubi is an unofficial Ubuntu installer for Windows users that will bring you into the Linux world with a single click. Wubi allows you to install and uninstall Ubuntu as any other application. If you heard about Linux and Ubuntu, if you wanted to try them but you were afraid, this is for you.  Wubi is Safe: It does not require you to modify the partitions of your PC, or to use a different bootloader.  
Wubi is Simple:  Just run the installer, no need to burn a CD."

---

### Post by Matt Yun on 2007-10-22
> **bellawood said:**
> Hi, I migth have one idea, would it work if we copied all the cd iso stuff to a pen drive and insert in it a disk boot? there is any way to do aomething like that??

It is insufficient to copy the contents of the Ubuntu iso file to the pen drive; you need to install a bootloader on the pen drive too.

See my earlier post; all the stuff about syslinux and lilo is to get a bootloader on the USB pen drive.  You would need to do the same for an external USB hard drive.

---

### Post by pssturges on 2007-10-22
Matt,

Many many thanks! I'm typing this on my fresh gutsy install\\:D/. I just kept it simple and installed Ubuntu rather than Kubuntu. Went smooth as silk.:)

Thanks again
Phil

---

