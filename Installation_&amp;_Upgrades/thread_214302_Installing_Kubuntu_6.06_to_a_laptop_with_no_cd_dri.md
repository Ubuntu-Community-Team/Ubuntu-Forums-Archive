---
title: "Installing Kubuntu 6.06 to a laptop with no cd drive"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by ikkejw on 2006-07-12
Hey,

Let me tell you the whole story:
I have a laptop and it used to run Kubuntu 5.10 which I had installed from the cd drive. Now I wanted to install 6.06 from the cd's that had just arrived. I booted from the cd (which was really difficult, because the cd drive was near the end of its life. Sometimes it worked, but usually not), clicked the Install icon on the desktop, reformatted the drive etc, and let it install. The install progress was at around 50%, when I heard loud noise coming from the cd drive. It appeared the lens had fallen off the laser, into the cd. The cd is still usable, although the cd drive is not. And, whenever I boot the laptop, GRUB gives me an error 15.

Now, I think you can almost guess my question:
**Is it possible to install Kubuntu 6.06 using only a floppy drive and a network connection to my other pc's and the internet?**

If it isn't:
When I buy an external cd drive (I probably will, not sure), can I boot to a floppy and then install from cd? (Assuming I can not directly boot from an external drive)

---

### Post by sethmahoney on 2006-07-12
I think a few people on the forum have had success installing from one of those USB key drives.  You might do a search and see if that is an option for you.

---

### Post by ikkejw on 2006-07-13
Well, my laptop can not boot from USB drives, only from floppy, cd or harddisk drives. Besides, I only have a 128MB USB drive so I can't install many packages.

Isn't there a way to create a bootable floppy that installs a very simple Debian system (with apt) from the USB drive? If I had that, I think I could add the Dapper repositories to the sources.list and just do an apt-get dist-upgrade. Right?

---

### Post by Afishionado on 2006-07-13
Debian can do it:

[http://www.debian.org/distrib/floppyinst](http://www.debian.org/distrib/floppyinst)

But I don't know of an easy way for Ubuntu to do this, off the top of my head.

Maybe boot from SBM:

[http://btmgr.webframe.org/](http://btmgr.webframe.org/)

and then install from a USB key?

---

### Post by ButteBlues on 2006-07-13
I'm having a similar issue.

BIOS doesn't boot from CDROM (Bios is current version), A:\ (floppy) drive is dead, and SBM won't install on my harddisk (the DOS installer closes everytime I open it).

Any other ideas?

---

### Post by ikkejw on 2006-07-13
> **Afishionado said:**
> Maybe boot from SBM:

[http://btmgr.webframe.org/](http://btmgr.webframe.org/)

and then install from a USB key?

I installed SBM on a floppy but it doesn't detect the USB drive, it only shows the harddisk, floppy and cdrom drives :(

edit:
The USB drive did contain bootable files, I put the contents of [http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/netboot.tar.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/netboot.tar.gz) on it.

---

### Post by ikkejw on 2006-07-14
All right, I did some googles and I found out 2 things:
USB can be accessed from DOS using DUSE.
and Loadlin can be used from DOS or Windows to boot the Linux Kernel and create an initial ramdisk.
I'll them this afternoon (GMT+1), stay tuned!

a simple façade, you could try running Loadlin from windows (from the command line, cmd) to start the installer.

---

### Post by ButteBlues on 2006-07-14
> **ikkejw said:**
> a simple façade, you could try running Loadlin from windows (from the command line, cmd) to start the installer.

If I could get instructions for doing this, that'd be swell (I can be something of a computer noob sometimes). :)

---

### Post by ikkejw on 2006-07-14
> **a simple façade said:**
> If I could get instructions for doing this, that'd be swell (I can be something of a computer noob sometimes). :)

Well, normally you would download netboot.tar.gz, untar it somewhere on your harddisk together with loadlin, then go to start --> run --> type "cmd" and hit enter, and navigate to the directory where you installed the files. Once there, run
```
loadlin linux initrd=initrd.gz vga=normal ramdisk_size=14332 root=/dev/rd/0 rw --
```
if you want to install Ubuntu, or
```
loadlin linux initrd=initrd.gz vga=normal ramdisk_size=14332 root=/dev/rd/0 rw -- preseed/url=http://people.ubuntu.com/~cjwatson/bzr/debian-cd/ubuntu/data/dapper/preseed/kubuntu/kubuntu.seed
```
if you want to install Kubuntu.

HOWEVER, When I do this I get a kernel panic saying the ramdrive can't be mounted :( :
```

RAMDISK: ran out of compressed data
invalid compressed format (err=1)
VFS: Cannot open root device "rd/0" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```

Anyone knows what to do now?


Besides, the DUSE drivers didn't work for me. I am now using the Moto Hairu drivers, or whatever they're called.


edit:
I changed /dev/rd/0 with /dev/ram, and now I get this output:
```

RAMDISK: Incomplete write (28672 != 32768) 14647296
RAMDISK: Ran out of compressed data
invalid compressed format (err=1)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)

```

---

### Post by ButteBlues on 2006-07-15
Thank you for your effort, however, I was able to manually fix (by opening up and tweaking) the CDROM drive and am using the Dapper Kubuntu Live CD to install. Hopefully everything suggested here will be useful to someone in the future though. :)

---

### Post by ikkejw on 2006-07-16
I'm glad you found a way to install Kubuntu. :D

But, my laptop still crashes with a kernel panic. Anyone knows what to do now?

---

### Post by Sable683 on 2006-07-16
I am having a similar problem. I have an older HP Pavilion laptop with no working CD Rom or 3.5" floppy. I have the Ubunut ISO image saved on my hard drive (both ISO image and Extracted), but can't seem to get it installed on an unallocated (37 GB) partition. I tried grub, but that didn't work. I also tried instlux, which also didn't work for me. If you can connect to the internet from the grub command line, you can install using instlux. I can't connect to the internet outside of windows for some reason. Thus my most recent frusteration ](*,) 

~Sable

---

### Post by ikkejw on 2006-07-17
Well, I installed GRUB on a floppy and tried to boot from the harddrive... And guess what? It worked! Seems like the installer installed enough to boot from before it crashed. Now I've got to install GRUB, do an apt-get dist-upgrade just to be on the safe side, and it's running again. :D

BUT, it seems it didn't set the correct password (or I just forgot it :) ). Is there any way to reset it?

edit: I reset the user and root passwords but now sudo doesn't work anymore (just doesn't do anything) and anywhere I need to give my root password (not in the console but in kde, for example when I start adept) it tells me my root password is invalid :k

---

