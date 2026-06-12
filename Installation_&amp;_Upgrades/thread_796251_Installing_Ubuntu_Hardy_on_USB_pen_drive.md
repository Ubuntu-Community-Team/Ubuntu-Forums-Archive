---
title: "Installing Ubuntu Hardy on USB pen drive"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by Spanky2k5 on 2008-05-16
Hey Guys,
 I'm pretty intrigued by the idea of having a portable installation of Ubuntu around with me so I bought myself a Patriot Xporter XT 8gb pen drive and found a tutorial to install Hardy here;[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

Couple of questions though if anyone can help me.
First, when I'm using the OS from a USB and want to install an app like, Envy...for example....will I be able to do this or can I only work with what is packaged into the installation by default?

Secondly, not really Ubuntu related but I use a KN9 SLI motherboard and am not sure if this allows me to boot from a USB pen drive, although I am given the option to boot from USB CD-ROM and USB Floppy Disk and stuff like that. Anyone familiar with this m/board and able to help me out here?

Thanks all!

---

### Post by dstew on 2008-05-16
To your first question, the tutorial you used is to create a persistent installation, which means that it will retain your installed software.

The second question I can't help you with, but I think if the mobo can boot a USB CD-ROM or floppy, it should boot the USB pen drive.

---

### Post by Spanky2k5 on 2008-05-16
Thanks for the reply, so just to clarify. After I've made the bootable USB and I'm running Ubuntu from it, if I choose to install additional software from a repository then it will install correctly and work next time I use the USB.
I ask because I'm finishing up my dissertation on WLAN Security Protocols and a lot of the tools I've researched are Linux based so I wanna install a few of these and use them with a USB Wireless NIC.

I tried booting from USB earlier choosing USB-LLD (or something like that) for all three boot options but that didn't work. KN9 has got to be the worst m/board series ever manufactured. It barely works with anything.

---

### Post by reacocard on 2008-05-16
That method of booting is rather roundabout. A better way is to just install ubuntu directly. You'll need to use the alternate install CD and be careful to put grub on the flash drive instead of your main drive, but aside from that it works without tweaking. I've done this myself and it works great (though the 1GB stick I chose is a little cramped).

---

### Post by Spanky2k5 on 2008-05-16
I wish I even knew where to begin doing that but I'm completely new to Ubuntu and Linux in general.
I'm following the tutorial in my first post and have just finished, only thing I'm worried about is when I typed this;

cp -rfv casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz /media/ubuntu8/

I got a few messages saying 'cannot stat 'unbuntu.ico' No such file or directory
and 'Cannot stat 'disctree' No such file or directory.

I also got a few 'Cannot create symbolic link' errors but I'm pretty sure I can ignore these

---

### Post by Spanky2k5 on 2008-05-16
Ok, now I got another problem, when booting to the USB drive I get an error with the syslinux saying there's an unknown command or something like that.
I followed the tutorial to the letter so I'm not sure why it doesn't like that

---

### Post by ppeterb on 2008-05-31
Used Xubuntu live CD to install to an 8GB OCZ Rally2 flash drive.  $25 from Tiger.com.  Used about 3GB leaving 5GB free.  The system now boots in less than 30 seconds.  I'm really pleased with result.

Caution.  When doing install pay attention to which disk the boot record gets installed on.  This is in an early menu.  The process will default to the system hard drive - which is a modest-to-huge disaster.  Select the sda for the flash drive.  (To be safe unplug power to internal hard drive(s) and floppy.)

Install takes about 45 minutes.  A "huge" update takes much longer first time system finds the internet.  Added Adobe flash to Firefox "automatically" via talkingpointsmemo.com.  (Not adobe.com or youtube.com.)

---

