---
title: "Will Not Boot from External SSD drive, Please help"
date: 2016-03-04
forum: Installation &amp; Upgrades
---

### Post by rob312 on 2016-03-04
Hello, this is my first experience trying to use ubuntu. I first installed ubuntu onto a usb flash drive and I was able to boot from it. Then I thought I would try using an external hard drive to speed things up. I cannot get it to boot from it, please help! It is a pny ssd hard drive. It has a sata connection, so I used a cable that connects from sata to usb 3.0. I made 3 partitions on it. The first is fat32 for file storage that I can use with windows, the second is ext4 where I installed ubuntu, and the 3rd is the swap space. I told it to install the boot to the 2nd partition just like I did when I installed it on the flash drive, however it just gives me a black screen with a blinking cursor when I try to  boot from the drive. 

Please Help!

Thanks.

---

### Post by Bucky Ball on 2016-03-04
Welcome. Did you use the 'Something Else' option during install and do you remember where you put grub if so?

If you install and launch[ Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"), it gives the option to run a bootinfo script. Run that and post the output back here between code tags, please (see link in my signature for how).

Make sure that drive is in an on when you run it.

---

### Post by grahammechanical on 2016-03-04
> I told it to install the boot to the 2nd partition

Install again and this time make sure that Grub is being installed into the MBR of the Drive.

Regards

---

### Post by sudodus on 2016-03-05
Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Is the computer running in BIOS or UEFI mode?

Knowing this makes it easier for us to help.

---

### Post by rob312 on 2016-03-05
Hello, I tried installing grub to a different location using: 
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

It now boots up fine, but I have an additional question. I read in a post that now whenever grub is updated, it will still remember the old location of grub. Will this cause problems, and how can I change that or get rid of the old location? Thanks

---

### Post by oldfred on 2016-03-05
#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short  
    sudo grub-probe -t device /boot/grub 
   #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

