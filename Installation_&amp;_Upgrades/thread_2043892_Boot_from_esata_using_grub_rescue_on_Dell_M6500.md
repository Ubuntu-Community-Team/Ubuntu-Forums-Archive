---
title: "Boot from esata using grub rescue on Dell M6500"
date: 2012-08-17
forum: Installation &amp; Upgrades
---

### Post by ecsedy on 2012-08-17
I have a laptop provided by my company, one implication of which is that I do not have the option of overwriting the MBR on sda or sdb without getting grief. I would like the ability to boot an Ubuntu environment off an eSata drive. The BIOS is locked down so I can't change it. I think the best option is using a rescue grub CD image. When I run the 12.04 live CD I can look at dmesg and see the ahci driver loads and recognizes the eSata drive. I created a rescue iso and it boots fine but does not see the eSata hd2 drive. I tried doing insmod raid but that does not help and the is no ahci.mod available to load. Ideas?

Thanks.

---

### Post by gordintoronto on 2012-08-17
If you can boot from CD, a Grub script might work.

If you can boot from a flash drive, it would make experimenting a lot cheaper. [smile]

---

### Post by ecsedy on 2012-08-18
Trying to do a grub-mkconfig which doesn't work since I am running a live CD. Apparently you can make it work if you do a chroot.

---

### Post by ecsedy on 2012-08-18
So rather than playing around with the live CD I scrounged up an old USB  enclosure with a 60 GB hard drive in it. I installed Ubuntu 12.04 with  no problem. I had to install the xorriso package to do a grub-mkrescue  but that was no problem. The interesting thing was that after I  installed the OS the grub menu came up and it showed the eSata drive in  the menu options (I have an old Windows install on it). I did a  grub-mkconfig and followed by a grub-mkrescue. After booting with the  rescue iso I created there was the eSata drive listed where it should  be. When I tried booting to it I got some message about the UUID of the  drive not being found. The script looks like it is trying to do a search  based on the fs-uuid and it is not working. Of course if I do a blkid  in Ubuntu the drive is there and the fs-uuid is there and correct for  the partition. Right now it seems like booting into Ubuntu works because  it loads some driver that grub does not and that's why grub does not  see the eSata drive. Grub sees USB drives just fine, though. The chip in  the laptop is an Intel Series 5 SATA chip set to RAID, not AHCI. Ideas?

---

### Post by ecsedy on 2012-08-19
So I built and installed the latest grub 2.00 from source because it does have an ahci module. When I get the grub command prompt and load the ahci module the ls command returns a blank line. Any other command returns a message saying device hd2 can't be found.

---

