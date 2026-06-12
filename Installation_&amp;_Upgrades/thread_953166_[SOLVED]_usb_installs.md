---
title: "[SOLVED] usb installs"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by xphlo on 2008-10-19
I am looking to install ubuntu,gentoo,and slackware on a usb. I see many tutorials on doing similar to what i want, but they nearly always say 'Live' usb, or live persistent. 

My real desire is to have full installs on an 8Gb usb, with four ext3 partitions and a swap. (when I say full, I dont mean every package on earth, just not "Live", or slax, etc)

can I just partition/format my usb, run the installer for each distro, and make sure it is installed to the desired locale on the usb. (I had also planned to use extlinux)

Is there a particular reason why most tutorials do not speak of standard installs (size comes to mind, but is there another reason?)

Thanks.

---

### Post by caljohnsmith on 2008-10-20
> **xphlo said:**
> 
can I just partition/format my usb, run the installer for each distro, and make sure it is installed to the desired locale on the usb. (I had also planned to use extlinux)

Is there a particular reason why most tutorials do not speak of standard installs (size comes to mind, but is there another reason?)

Thanks.
Yes, as long as your BIOS supports booting your USB drive, you should be able to simply treat the USB drive like any other drive and go through the normal installation process. I think the reason the tutorials don't speak about it is because it doesn't take any special steps to do it. :)

---

### Post by C.S.Cameron on 2008-10-20
Probably best to disable your HDD first.
Then from Live CD, (or one of those Live USB's), run install.
When you get to partitioning select manual.
I generally reduce the size of the FAT32 partition so I can still use it on a windows machine.
To the right of this I create a ext2 or ext3 partition with a mount point '/home'.
to the right of this, an ext3 partition for the file system with a mount point '/'.
To the right of this you can create a swap partition.
Maximum number of partitions is 4.
The root and swap can be placed in an extended partition if you need more.
complete the install and Ubuntu should work just like from a hard drive but a little slower at writing.

---

### Post by snowpine on 2008-10-20
C.S. Cameron has really good advice. I'll just add that you are going to want at least 4gb just for Ubuntu if you use this method. That's the main reason most people use the "Live USB" method; to fit the OS plus still have room for your data. Also I am not sure there's any performance advantage to a swap partition given the slow speed of most flash devices.

---

### Post by 22flames on 2008-10-20
Un plug the hdd than just put in usb live cd find the usb on the partition menu and when you get to the end of the install click advanced than put the boot manager on your usb partition. DO NOT ACCIDENTLY PUT ON HARD DRIVE TURN IT OFF OR UNPLUG OR BE CAREFULL:)

22FLAMES

---

### Post by Herman on 2008-10-20
If you use the Reiser File System instead of the standard Ext3, your operating system will perform as fast as a normal hard drive installation with some kinds of flash memory controllers.

I like to give all my file systems a label or volume name, they'll be mounted with that name and show up in Gnome Partition Editor with that label.
You can set a volume Label from the right-click menu from modern versions of GParted.

From the command line, you can give any ReiserFS partitions in your USB a volume name with something like, ```
sudo reiserfstune /dev/sdb2 -l "UBUNTU"
```Where: your USB is seen by Linux as '/dev/sdb', and your Ubuntu partition is partition number 2 in the USB disk.

---

### Post by xphlo on 2008-10-20
Thank you all.

Ubuntu went on with no problems. Slack goes on tomorrow.

I went with a 350mb swap. Most of the systems I boot on will have  RAM > 1Gb. May or may not of needed it. Ill pay extra attention to the logs and see how much it really helps.

I went the partitioning scheme as suggested by C.S.Cameron.
 
pri boot 200Mb FAT32     # has extlinux / free space for windows
pri 1.0Gb ReiserFS       # for /home
pri 350Mb Swap
ext 4.0Gb Ext3           # / for ubuntu
ext ~1.2Gb Ext3         # / for slackware
ext ~1.2Gb Ext3         # / for gentoo

Thanks again.

---

### Post by caljohnsmith on 2008-10-20
Just one small caveat: for each new distro that you install, usually by default they install their own boot loader and take over the HDD's MBR (Master Boot Record). So if you want to use Ubuntu to handle booting all your OSes, then usually the easiest way is to have each distro install its boot loader to the boot sector of its partition, and not the MBR, which then makes it really easy to boot them. In other words, you would tell the installer to put Grub/Lilo in say /dev/sdb2 rather than /dev/sdb if sdb is your USB drive, and if sdb2 is the partition of that particular distro. Then you can easily "chain load" or boot the distro from Ubuntu's Grub menu using the following notation:
```
title Other Distro
root (hd0,X)
chainloader +1
```
If you would like more specifics, let me know, but that gives the general idea.

---

