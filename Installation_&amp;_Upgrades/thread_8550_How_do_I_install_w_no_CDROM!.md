---
title: "How do I install w/ no CDROM?!"
date: 2004-12-18
forum: Installation &amp; Upgrades
---

### Post by ming0 on 2004-12-18
I've got a notebook that has no built in floppy (I have a bootable USB FDD) and no CDROM. It's a panasonic R1.

I can get loadlin to run (by using a windows boot floppy), and I have my HDD partitioned as follows:
     hda1           Boot           Primary      Linux ReiserFS                            5996.23
     hda2                          Primary      Linux swap                                 509.97
     hda3                          Primary      Linux ReiserFS                           13473.01
     hda4                          Primary      W95 FAT16 (LBA)      [EMERG      ]          24.68

If I put the .iso files onto hda3, can I install it to hda1 from a loadlin prompt? Any hints on how to make this happen?

Thanks!
Dean ;)

---

### Post by gny on 2004-12-18
Here is a page that probably will help you alot,

[https://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-11-26.2137127791](https://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-11-26.2137127791)

se also:

[http://troja.ath.cx/~zond/knoppix_net/](http://troja.ath.cx/~zond/knoppix_net/)

Ask me if you have any more questions.

---

### Post by sbfisher on 2004-12-18
I have the same problem.  I have a notebook with a broken CD-rom and it's a crappy old computer.  I just want to install ubuntu to take notes and things for class.

I have an extra partition that I can copy the ubuntu ISO or ubutu files to.  The links above weren't much help because the ubuntu install wouldn't start from the network.  It won't detect my (pcmcia) network card and start installing.

I tried copying my ubuntu files to a FAT partition since I can copy files to the drive across the network in Win98.  Copied all the files over and tried booting it with a utility called linld which is like loadlin.  linld image=vmlinuz cl=root=/dev/hda4 .  Get kernel panic or something and it will not boot since I guess it doesn't like trying to boot from a FAT partition.

I downloaded the debian floppy boot that had 6 disks (4 disks of drivers).  It started and got my network working.  I then installed a very basic debian install from network (no x-windows or anything).  The instructions were here: _[http://www.ubuntulinux.org/wiki/WartyUpgradeNotes](http://www.ubuntulinux.org/wiki/WartyUpgradeNotes)_  about how to supposedly upgrade.  I switched the sources list to point to ubuntu.  I tried "adding desktop users to the standard groups" as it explains.  That part didn't work right.  I just got a weird > prompt when I tried it.  I'm not sure what that part was supposed to do.

I did the apt-get installs to supposedly get ubuntu and install it, but it doesn't work.  x-Windows tries starting, but just exits.  Tried startx manually and get errors about "no symbols found."  The install is totally hosed and is basically worthless after all that work and waiting.

I'd be very, very happy if anyone can give me better instructions or tips about how to get this actually working.

Thanks!!!

---

### Post by ming0 on 2004-12-19
The netboot guides are convoluted and disjointed--I can't seem to get it working  #-o 

I'm trying to serve the tftp file from an ubuntu box--but I have no way of knowing what is the problem... I've tried searching google for guides on how to set it up, but i've not found anything too helpful yet  :confused: 

Anyone have any sane, step by step instructions that will work w/ warty?!

Thanks :)

---

### Post by ming0 on 2004-12-19
Okay, I found some pretty nice instructions on doing the pxe boot:
[http://wiki.koeln.ccc.de/Ubuntu_PXE_Install](http://wiki.koeln.ccc.de/Ubuntu_PXE_Install) 

But I still feel pretty deficient :cry: 

I've gotten to the installer, but I don't know what to do (The instructions say 'marvel as ubuntu is installed over the net') but when I choose the defaults, nothing really happens.

I've not found a working mirror? It has a great britain mirror, but it doesn't work for me--I'm not sure if the packets aren't actually making it onto the internet, or if the mirror is gone...

Thanks for the help thus far

---

### Post by sbfisher on 2004-12-20
Ok, my latest fun.  I really wanted to install ubuntu, but I got Knoppix to install.  Still trying to install ubuntu.  I copied the install files to a ext2 partition from the CD.  Trying to figure out how to start the install.  My partitions (may be useful later):

/dev/hda1=Windows 98
/dev/hda2=Linux swap
/dev/hda5=Knoppix
/dev/hda6=Extra partition for copying install files to (750 megs)


**How I got Knoppix to install so I could copy the ubuntu CD to my drive:**
1. Copied the *knoppix* file off the 3.6 CD.  Also copied *linux24* and *minirt24.gz*.  Put them all into my FAT partition that i could get to across the network from Windows 98.  Made a folder called *Knoppix*.  Be sure to put them there.

2. Downloaded *Loadlin 1.6c* and extracted the exe file to this same folder.

3. Created a batch file called *runit.bat* to start loadlin since I had to keep experimenting to get knoppix to load correctly.  In this file I put:

*loadlin linux24 fromhd=/dev/hda6 ramdisk_size=50000 knoppix_dir=KNOPPIX init=/etc/init initrd=minirt24.gz noapic noapm nodma lang=en*

Ran it, booted to Knoppix (as though running off a cd) and then installed it to my hard drive.

4. Got samba to work after many problems, created an ext2 partition in */dev/hda6* and copied the contents of my ubuntu install CD to it.  chmoded all the files to read, write, execute for everyone (777) since I figured access would be assured.

**How to get ubuntu install to load?**

1. Copied *vmlinuz* and *initrd.gz* from my ubuntu cd to a folder on my windows98 partition (/dev/hda1).  Also copied loadlin there.

2. Created a runit.bat file similar to the one I made for knoppix to (I hoped) start the install from /dev/hda6.  It contained the line

*loadlin vmlinuz DEBCONF_PRIORITY=critical vga=normal initrd=initrd.gz ramdisk_size=10240 root=/dev/hda6 init=/linuxrc devfs=mount,dall rw --*

I wasn't sure about some of the codes.  I run it and get a bunch of things loading quickly and then get (the last few lines):

[i]RAMDISK: Compressed image found at block 0
VFS: Mounted root (ext2 filesystem).
Mounted devfs on /dev
NET: Registered protocol family 1
VFS: Cannot open root device "hda6" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic: VFS: Unable to mount root fs on unknown-block(0,0)[/i]

Can anyone give me tips on how to do this or is it just impossible?

Thanks.

---

### Post by sbfisher on 2004-12-22
Ok, latest update.  I got my ubuntu install to (more or less) work on my notebook without the working CD-rom.  Remind me not to waste my life trying to get something like this to work.  He's is how I worked around the multitude of install problems:

1. Installed ubuntu to a desktop computer.
2. Imaged the ubuntu partition.
3. Restored it to the notebook by copying image over network in Win98.
4. Created grub boot disk on floppy.
5. Booted the newly copied partition with grub on floppy.
6. Followed the instructions here:  [http://www.ubuntulinux.org/support/documentation/faq/RreprobeMonitor/talkback/1101679952/view?searchterm=monitor](http://www.ubuntulinux.org/support/documentation/faq/RreprobeMonitor/talkback/1101679952/view?searchterm=monitor) and it seems to go into X-Windows now since I had much different hardware on my desktop.

UPDATE:  This install is very unstable on my notebook so I have to try a different way.

---

### Post by sbfisher on 2004-12-22
Installer ALMOST Works:

1. Copied install CD to /dev/hda7.
2. I have grub installed

At grub boot menu, I changed the lines to the following the then tried to boot:
 
root (hd0,6)

kernel /install/vmlinuz  DEBCONF_PRIORITY=low vga=normal initrd=/install/initrd.gz ramdisk_size=10240 root=/dev/rd/0 init=/linuxrc devfs=mount,dall rw --

initrd /install/initrd.gz

savedefault

boot


After doing this, I get the installer, but when I get to DETECT AND MOUNT CD ROM, I get errors--although it seems to find much of my other hardware ok.  I keep getting told to insert my cd-rom. (The files are on /dev/hda7--leave me alone you idiotic installer, you should know where the files are since you booted off them).  About the only choice I have at this point is to "Execute a shell"  I looked around to see if I could mount /dev/hda7 to the cdrom folder to fool the @#$# installer to use it.

mount /dev/hda7 /cdrom
mounting /dev/hda7 on /cdrom failed: No such file or directory

aaaargh.  If anyone can help me get the derailed installer to install from the hard drive copy of the files at this point it would be huge.

Otherwise I'll go back to Windoze--which I was trying to get away from after my notebook crashed in the middle of a midterm exam (the final straw).  Oh well, maybe ubuntu is just not ready to be used by mere mortals. ;-)

---

### Post by Steve Quezadas on 2006-06-11
Guys,

I have a solution of what worked for me. First, I created a partition (fat32 for me) on a hard disk and I copied the contents of the ubuntu cdrom into a "ubuntu" folder on that partition.

Then I created a grub disk:
cd /boot/grub
dd if=stage1 of=/dev/fd0 bs=512 count=1
dd if=stage2 of=/dev/fd0 bs=512 seek=1

I booted off the disk until I got to the grub prompt. Then I typed:
root (hd0,0)
kernel /ubuntu/install/vmlinuz preseed/file=/cdrom/preseed/server.seed vga=normal ramdisk_size=16384 root=/dev/rd/0 rw --
initrd /ubuntu/install/initrd.gz

Then I booted ubuntu! From there, it tried to detect the CDROM (but couldn't). I got into the shell by pressing alt-f2 . then I did a:
rm -rf /cdrom
mkdir /mnt
mount /dev/hda1 /mnt 
ln -s /mnt/ubuntu /cdrom

Then I press F1, let the detection of the CDROM driver fail, and move on with the installation. I am not sure if this works, because my laptop ended up not having enough RAM, but it should at least get people here farther.

- Steve

PS Give me a shoutout if this helped (--steve {atsign} thestever {dot} net--)

---

### Post by crot4103 on 2007-05-15
> **sbfisher said:**
> Ok, latest update.  I got my ubuntu install to (more or less) work on my notebook without the working CD-rom.  Remind me not to waste my life trying to get something like this to work.  He's is how I worked around the multitude of install problems:

1. Installed ubuntu to a desktop computer.
2. Imaged the ubuntu partition.
3. Restored it to the notebook by copying image over network in Win98.
4. Created grub boot disk on floppy.
5. Booted the newly copied partition with grub on floppy.
6. Followed the instructions here:  [http://www.ubuntulinux.org/support/documentation/faq/RreprobeMonitor/talkback/1101679952/view?searchterm=monitor](http://www.ubuntulinux.org/support/documentation/faq/RreprobeMonitor/talkback/1101679952/view?searchterm=monitor) and it seems to go into X-Windows now since I had much different hardware on my desktop.

UPDATE:  This install is very unstable on my notebook so I have to try a different way.


[weather Ebay caffeine Cash Advance Equity Loans](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/index.php)

---

