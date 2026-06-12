---
title: "Installing on external hard drive"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by blueysak on 2010-07-07
Hello I am new to linux and I would like to install linux on my external hard drive. The external hard drive is 250gb but i only want to use 50gb for ubuntu, any ideas how? Also my main consern is that i would like it so if I removed the external hard drive i can boot my windows xp. I've reading alot of problems about this and when people remove the external hard drive they get an error on something called the "GRUB"? I dont want this problem. Also if I removed the external hard drive and put it into my laptop (also running xp) I cud boot ubuntu from it? Is this possible and if i is could u give me a link to a tutorial or write it out please! Thank You

---

### Post by blueysak on 2010-07-08
anyone?

---

### Post by dabl on 2010-07-08
If your computer BIOS is able to boot from the external drive (I assume it is USB), then it should be possible to do what you are planning.  So the first thing to check is your BIOS -- look for a screen with "Boot Devices" and see if there is a "Boot from USB" option that you can check.  Also, look at the "Boot Device Sequence" -- probably your internal hard drive is at the top of the list.  After you have checked "Boot from USB", reboot your computer with your external drive plugged in, and go into BIOS and look at the "Boot Device Sequence", and see if it is possible to move your USB external drive up to the top of the list.  If you can, then all indications are that you can boot from it.

So, to deal with the partitioning issue, I personally like to use a Parted Magic Live CD for that:  [http://partedmagic.com/download.html](http://partedmagic.com/download.html)

In addition to partitioning, it has some nice benchmarking tools and other stuff on it.  The Ubuntu Live CD has GParted on it, and you can use that too.  Make a 50G partition, if that's what you want.  I would advise making it the first partition (to the left on the GParted graphic), and after it is made, you need to right-click on it and set the "boot" flag (in the "Manage Flags" menu).  If you have a lot of memory (more than 2G), you can try it without a swap partition, but personally I always make a swap partition so I don't have to worry about it. Make the swap partition 100MB larger than your installed memory, and you will be able to use "Suspend to Disk" if you want.

With your external drive partitioned, you can reboot a Ubuntu Live CD or a Ubuntu Alternate Install CD (my favorite) and proceed to install the OS on the external drive.  Because you are new, and because of the risk that you'll inadvertently install Grub on your internal hard drive, I would advise you to open your case and pull either the power plug or the data cable off your internal drive.  If it is a laptop or netbook and you can't open it, you'll just have to be very, very careful at the end of the Ubuntu installation process, and make sure that Grub is installed to the external drive.  From a running Live CD, you can run the command (in a terminal window) ```
sudo fdisk -lu
``` and observe the output and figure out which drive is the external one.  Supposing you learn that it is /dev/sdb, then at the end of the installation process you want to have it install Grub to /dev/sdb (to the master boot record on that drive).

With regard to your ability to take the external drive to any computer and successfully boot Ubuntu, that's not going to work as well as you imagine, because during installation it will undoubtedly make some configurations for the specific hardware that it is connected to.  To have a "universally bootable" Ubuntu OS on a USB device, you can simply (from a running Live CD) click "System > Administration > USB Startup Disk".  Also, make a search on "pendrive linux" or otherwise search on "bootable usb stick" and you will find techniques to put a "Live" version on a USB device, which will function the same as a Live CD.  You can do the same thing on a USB hard drive as on a USB removable memory device (aka "stick" or "thumb drive").

I hope this helps.  Links:

[http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/](http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/)

[http://kubuntuforums.net/forums/index.php?topic=3107512.0](http://kubuntuforums.net/forums/index.php?topic=3107512.0)

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by blueysak on 2010-07-08
I am pretty sure i can boot off a usb because i have a dell dimension and my friend told me he is pretty sure they can.

I am confused on the partitioning part. I was exploring the my computer setting and i found out if you right click my computer and click manage it brings up a window. In that window if you click disk management you could "Shrink" the disk. Does shrink mean make it into parts? If so would that work? I am also a confused on what this section of the partitioning mean 

" I would advise making it the first partition (to the left on the GParted graphic), and after it is made, you need to right-click on it and set the "boot" flag (in the "Manage Flags" menu). If you have a lot of memory (more than 2G), you can try it without a swap partition, but personally I always make a swap partition so I don't have to worry about it. Make the swap partition 100MB larger than your installed memory, and you will be able to use "Suspend to Disk" if you want."

Then only response to that is that I dont have a lot of memory i only have 512mb of ram.



I dont want to unplug the internal hard drive because i am not that great with technological stuff. I often break things... So i guess i will have to be careful at the end of the installation.

I think i get the grub part on the installation.

On the part if it takes too much of a hassle to make a universal boot up then I am okay. I just want the ability to unplug and run windows without having any problems.

Thank You

---

### Post by dabl on 2010-07-08
> **blueysak said:**
> 

" I would advise making it the first partition (to the left on the GParted graphic), and after it is made, you need to right-click on it and set the "boot" flag (in the "Manage Flags" menu). If you have a lot of memory (more than 2G), you can try it without a swap partition, but personally I always make a swap partition so I don't have to worry about it. Make the swap partition 100MB larger than your installed memory, and you will be able to use "Suspend to Disk" if you want."


That is referring to the graphic that you see when you run GParted (the partitioning program).

I don't think you want to use the "Disk and Partition" utility from the Ubuntu desktop for what you are trying to do.  It sounds like the best thing would be the System > Administration > USB Startup Disk or whatever that says. **Make sure you have a backup of any data that is currently on that external disk drive, because it will be reformatted during the process and all data will be wiped out.**

---

### Post by blueysak on 2010-07-08
"I don't think you want to use the "Disk and Partition" utility from the Ubuntu desktop for what you are trying to do. It sounds like the best thing would be the System > Administration > USB Startup Disk or whatever that says."

Oh i wasnt talking about from ubuntu i was talking about from xp.

"Make sure you have a backup of any data that is currently on that external disk drive, because it will be reformatted during the process and all data will be wiped out."

The hard drive is already clean it had too many viruses so i wiped it and the format now is NTFS.

By the way, thanks for you help and sorry if I am disturbing or confusing you with all these questions.

---

### Post by oldfred on 2010-07-08
On the last partition screen in the Ubuntu install is an advance button that controls where grub is installed, otherwise is defaults to sda (usually). IF you want to avoid the issues, you need to use the advance button and install grub to the external drive. If in BIOS you set the external first and internal second, then when the external is not plugged in it will still boot off the internal.

[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

Older verison but the install process is the same.
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by dabl on 2010-07-08
> **blueysak said:**
> 

The hard drive is already clean it had too many viruses so i wiped it and the format now is NTFS.



OK.  No, Win XP can't help you here.  And NTFS is not a Linux filesystem, so what will happen when you run the "USB Startup Disk" utility is that your external drive will be reformatted to ext3 or ext4, and then Ubuntu will be installed on it, configured to be a bootable disk.

---

### Post by blueysak on 2010-07-08
okay thank you

---

### Post by C.S.Cameron on 2010-07-08
If you disable your internal HDD before installing to the external drive you can't go wrong with grub.

---

