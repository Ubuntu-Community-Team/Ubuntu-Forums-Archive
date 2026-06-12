---
title: "Booting ISO from HD"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by sande87 on 2008-07-10
Hi, Iv recently tried to boot ISOs from the harddrive. I want to do this to save some time when I try other distros, save some CDs and to have a rescue LiveCD on the harddrive.I also have no CD or DVD burner, and I hate to go ask my MacBook wielding little brother to burn for ISOs for me because I have an old craptop that I got for free. Iv searched for ways to this and have found a couple of ways to do this both here in this forum and on other forums. 

There is a lot of different approaches to this, and I have tried quite a few of them. The problem is that there seldom is someone that posts what worked for them, and just exactly how they did it. So I want to find out which solutions you people have come up with and just how you got it to work. 

Mostly Iv tried to use grub. The way I went about it was to create a 5gig partition, format it to ext2 and extract the files from the ISO onto that partition. And then edit /boot/grub/menu.lst to get it to boot from that partition using the distributions cheatcodes found in isolinux.cfg. I tried this for Ubuntu, PCLinuxOS and Knoppix, Ubuntu and PCLinuxOS both didnt work. 

my edit to boot/grub/menu.lst:
title		Ubuntu LiveCD from HD
root		(hd0,5)
kernel		/boot/vmlinuz "I dont remember the exact cheatcodes"
initrd		/boot/initrd

In Ubuntu the kernel loaded, but after a while I got a lot of errors, some about fd0 and some about the filesystem that it was booted from. The kernel loaded in PCLinuxOS too, but it didnt find the *.sqashfs image, so it just reverted to a limited command prompt. In Knoppix it worked just fine, but I suspect that is because of the nature of Knoppix. So Iv been successful at fulfilling my need to have a rescue LiveCD bootable from the harddrive.

Now, I dont want to troubleshoot my approaches to booting a LiveCD or ISO from the harddrive. I want to know how you guys did it, and if there are some solutions that will work for LiveCDs in general and not just one specific distribution. Well, if theres a good solution for doing this with Ubuntu, Ill be a little happier cus my current box is almost fubared due to mye trail and error approach to learning Linux. What Im ultimately after is a solution that works with most LiveCDs.

Thanks in advance :)

EDIT:

Iv stumbled over some interesting projects trying to get LiveCD/ISO boot from the harddrive:

MoviX: 

A small 32mb(!!) Linux distro that is all about playing movies, watching TV (if you have a TVcard), and listening to music. I find this interesting because with I can hopefully sqeeze some extra battertime out of my 4 year old laptop. It should also let you watch movies and such on ancient computers, as its commandline only and uses little resources. There are included scripts for USBstick and Compact Flash installs, you can boot it from CD and run it completely from RAM, and you can also install it on the harddrive. You can either give MoviX its own partition, or you can run it from an already existing partition with another OS on. That partition being ext?, FAT?? or NTFS. Theres instructions on how to do all these things in the MoviX readme. Theres also instructions on how to run it over the net and network. 
[http://movix.sourceforge.net/](http://movix.sourceforge.net/)

---

### Post by logos34 on 2008-07-10
Here's how I boot my Parted Magic rescue cd and Gparted from HDD:

Mount the parted Magic 1.8 .iso and copy contents (isolinux folder and pmagic) to your partition.

Add this entry to /boot/grub/menu.lst:

> title Parted Magic 1.8
root (hd0,3)  -->substitute your actual partition
kernel /isolinux/bzImage root=/dev/ram0 initrd=initrd init=/linuxrc ramdisk_size=100000
initrd /isolinux/initrd.gz

For Gparted (0.3.3) I did basically the same thing...menu.lst looks like this:

> title Gparted 0.3.3-0
root (hd0,3)
kernel /isolinux2/linux root=/dev/ram0 initrd=initrd.gz init=/linuxrc ramdisk_size=65000
initrd /isolinux2/initrd.gz

(*I had to rename the folder 'isolinux**2**' on account of the existing P-M folder)

I can't seem to find a way to boot the latest version of Parted Magic or Gparted.  The former used to have a tut page for hdd boot but I can't seem to find it anymore

---

### Post by sande87 on 2008-07-10
Nice, thanks for the input. I think im going to set up a Gparted partition, you never know when youll be in need for some partitioning :P

Thanks :)

---

