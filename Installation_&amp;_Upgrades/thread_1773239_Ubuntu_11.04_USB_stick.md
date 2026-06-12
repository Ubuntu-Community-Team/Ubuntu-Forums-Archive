---
title: "Ubuntu 11.04 USB stick"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by Cpierce on 2011-06-01
On previous versions of Ubuntu, in order to install on a USB stick, all I had to do was disconnect the hard drive, put the USB in, and run the Ubuntu installation disc. I wanted to install 11.04 on a 16GB stick, how ever the above didn't work. I got an error message saying it couldn't mount the USB drive. I formatted the drive and tried again, but still got the same message.

Could someone help me out, or point me in the right direction ?

---

### Post by garvinrick4 on 2011-06-01
Your first drive is sda then put your flash in a usb port and it is then sdb. As long as you do not
disconnect your internal drive  will always be sda.
So install your system to drive sdb  your usb flash. Remember when you install it says in /etc/fstab it was drive sdb at install. 
Do not want it to be sda at install want it to be sdb or will cause confusion with both thinking they are sda. (could happen disconnecting sda drive)
Put file system in sdb and grub make sure is in sdb very important to make sure sdb and not
sda. If you just make sure of that all else the same. Just keep focused installing.
Can see which is which by:
```
sudo fdisk -l 
```
(lower case L)

---

### Post by Cpierce on 2011-06-01
Thank you for the help. The problem I have had in the past is that if the main hard drive(ubuntu 10.04) is connected, and a USB is plugged in, Ubuntu doesn't see the USB as an install option. How do I make sure the USB is available as a target drive?

---

### Post by Cpierce on 2011-06-02
I tried connecting the internal HD, and booting up with the USB drive in to see if I could select where to install it. I got the same message I did when the HD was disconnected.

BusyBox v1.17.1 built in shell(ash)
enter help for a list of commands

(initramfs)mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error

cannot mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

---

### Post by Cpierce on 2011-06-02
GarvinRick4,
If I go ahead and boot up on lucid (internal drive), put the USB drive in and run fdisk -l, it does see the USB, and it is sdb. 

But if I try to boot up on the 11.04 live CD, I get the error message above before I ever get to the install menu

I really appreciate the help.

---

### Post by Cpierce on 2011-06-07
Help !

---

### Post by dforionstar on 2011-06-07
I'm not sure if this will help...

I am able to install from a Source USB flash drive onto a Target USB flash drive, on my laptop. What I did was turn the laptop OFF and temporarily remove the internal HDD altogether. Then when I attempt to install, the installer on the Source USB drive sees only one HDD: the Target USB HDD, and thats where it puts GRUB and installs Ubuntu.

I have not been able to use the Alternate ISO as it seems to have an issue running after I used LiLi USB Creator to put the ISO onto the Source USB drive. Same problem with Xubuntu Alternate ISO. 

You may also have an issue with how the Target drive was formatted.

I hope that helps.:)

---

### Post by linuxinstalledfromhdd on 2011-06-07
Try it with 10.10 this time...

You can get your 10.10 iso over here, and there is a guide to get everything perfect too:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

You can install Ubuntu 10.10 from a USB Flash Drive with the instructions from here:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Make sure you scroll down to option number two.  And create your Ubuntu 10.10 USB Flash Drive to boot your computer from, and install Ubuntu 10.10 to your hard drive. It only takes about 15 minutes after booting from your USB to install it to your hard drive that way. 

:guitar:

---

### Post by Cpierce on 2011-06-08
That solved it. Ubuntu 10.10 installed just fine to the USB when I disconnected the internal HD. Now I am upgrading 10.10 to 11.04. Don't expect any problems so I will mark this solved.

Thanks everyone.

---

### Post by Cpierce on 2011-06-08
Got it working but when I installed the nVidia driver, Unity disappeared. So I bailed, and will just stick to 10.04.

---

