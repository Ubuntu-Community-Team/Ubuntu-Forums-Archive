---
title: "Running Ubuntu off Thumbdrive"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by DanMan_7 on 2010-03-26
I would like to make an active copy of Ubuntu on a USB.  Making it so I can plug into any computer and have all my files/settings/programs and be able to change those settings and have them saved.  I am looking for a completely portable OS that actively remembers and can keep changes dynamically.  I'm not a programmer (obviously) but I'm pretty adept at negotiating instructions, Can anyone help? 

 I would be happy with either Ubuntu 9.10, or the Ubuntu for netbooks, which might be a little faster to boot and run on USB?

 Appreciate your help, Thank You Kindly, Dan :)

---

### Post by Fafler on 2010-03-26
Just boot from the installation CD with flash drive connected and choose to partition and install to it. Piece of cake. I think don't it makes any difference if you choose netbook remix or the normal version. Netbook remix is AFAIK just optimized for smaller displays.

If you don't already have the flash drive, i suggest you go out and spend a bit more on one of the faster models. I use a 8 gb Kingston Datatraveler, and it works great but is a bit slow from time to time. Also, if you know how to use the partition manager during the installation, go without swap if you're going to use it on systems with more than, say, 1 gb memory. For various reasons, flash memory is not very suitable for swap.

---

### Post by garvinrick4 on 2010-03-26
Just make sure on about page 8 or so of gparted installation you hit advanced and put your
grub on your own device it defaults to sda.
 And even then in different machines I have seen them look for grub and put it in place of
the Windows grub4dos and owner of machine will freak. 
 Better off getting a 8 gig or so flash partition in gparted into 2 seperate 4 gig partitions 1 for a fat32 USB 4 gig persistence which is plenty to make a nice system and the other 4 gig
for your home stuff. The Ubuntu USB creator has 4 gig persistence Unetbootin has no persistence (will not retain changes). Makes a nice Live USB drive for repairs, a nice system with all the goodies and a seperate 4 gig for music, notes and downloads. If you need more home space get a 16 gig and have a 4 gig and a 12 gig partition. 
 It sounds nice to have a ext4 with a /boot and a /root and a swap but it is just frills and the way with USB creator with casper will never change anyones grub for sure 100% not
a chance. 4 gig is plenty of room to make a nice system.
 Once you get flash the way you like it and downloaded all you need go to software sources and turn off downloads say never.
Leave kernel the one installed with USB creater  and do not upgrade, screws up the install.

---

### Post by stevecs on 2010-03-26
I use ubuntu full and several small mini-ubuntu (xbmc custom installs) off of flash thumb drives.   A couple pointers, get an SLC based flash drive, the MLC flash (cheap ones) die way too quickly under use.   Also use EXT2 as the file system.   EXT3 doubles, sometimes more than that the number of writes which is a killer for flash (I've gone through 3 SLC sticks, different vendors, due to wearing out the stick with other file systems).    You will still wear it out as with all NAND based technology but you'll get more use out of the drive for longer.   Also NO SWAPFILE!  this is the worst thing to put on a nand device.   (keep laughing at the idiots who buy the SSD's for a pagefiles/swapfiles).

---

### Post by the yawner on 2010-03-26
On a related note, there is a program installed by default in Karmic which lets you create a startup disks thingie (which is a misnomer since you actually use a flash drive). Long as you have an iso copy of the installer, you can use the program to create the persistent thumbdrive OS.

---

### Post by zepita on 2010-03-26
there's a tool called live usb creator made by fedora team that works for putting isos into pendrives and use them as boot device.  Additionally, you can specify space to use for files and to save data.

---

### Post by DanMan_7 on 2010-03-26
The ubuntu community is awesome as always :KS

Thank you everyone, I will combine all these tips, maybe try to create an article for others to follow if they desire the same. (credit will be given)   Thanks again

---

### Post by C.S.Cameron on 2010-03-26
If you choose to use usb-creator for a persistent install and need more space than the 4 GB allowed by FAT32 you can make an ext2,3 or 4 partition and name it casper-rw.
I would not worry about burning the drive out using ext3 or 4 for the FS, I have been booting Ubuntu with an ext3 casper-rw partition from a 2GB drive since 2 GB drives first came out. If you do the math a flash drive should last over a year if you use it to run Ubuntu eight hours a day.

---

