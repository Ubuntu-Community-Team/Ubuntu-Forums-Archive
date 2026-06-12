---
title: "Grub and HP Smart Array 5i+ RAID controller"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by MurphysLaw on 2006-08-02
Hello,

I am having trouble with Grub and a HP Smart Array 5i+ RAID controller.

I did a fresh install of Ubuntu 6.06 Server on a Compaq DL360 with the above RAID controller configured as RAID 1. The install works perfectly. I have a variety of partitions mounted off /dev/cciss/c0d0. The /boot directory is not a seperate partition.

Everything is great until I reboot. The BIOS hands off to the hard disk, but Grub never loads.

If I boot off the Ubuntu install CD, I can select "Boot off first hard disk". The CD will then call my locally installed Grub, and everything works.

I have even redone grub-install, but to no avail. Grub appears to be configured propery, and the proper parts seem to be loaded in the MBR.

Any ideas?

Thanks

---

### Post by MurphysLaw on 2006-08-02
Found the solution:
Somewhere else on these forums someone suggested changing the BIOS boot order to call the RAID controller before the CD-ROM.

I tried it and now Ubuntu boots perfectly.

---

### Post by JimLadd on 2006-08-02
I am having the same problem.  The only thing I can add is that the cciss reference is different when I go into restore mode from the install disk.

normally the first partition is /dev/cciss/c0d0p1

when I use restore mode I mount it from /dev/cciss_c0d0p1

I remember having a grub problem with the cciss driver a while back with Debian sarge.

-Jim

---

### Post by scdzaak on 2007-06-28
Dear MurphysLaw,

You write: 
I did a fresh install of Ubuntu 6.06 Server on a Compaq DL360 with the above RAID controller configured as RAID 1. The install works perfectly.

Is it possible that you give a hint how you did this final installation.
I have the same machine with the controler and 3 SCSI drive's , and I want tot make it as test server under Ubuntu 6 or 7 server.

Kind regards,

Eric

---

### Post by MurphysLaw on 2007-06-28
Hi,

Sorry, that was I long time ago. All I remember is:
A) Changing the boot order in the BIOS to make the RAID array #1.
B) I was brand new to this model family of HP servers. As a result, when I inserted the physical drives I initially didn't push them in hard enough. 

MurphysLaw

---

### Post by citybird on 2008-01-16
I am having the same problem with a ProLiant DL380 with a Smart Array 6i controller.

I am trying to install 7.10 server and start the install in expert mode and I blacklist 2 drivers:
```
sym53c8xx.blacklist=yes sym53c8xx_2.blacklist=yes
```

after the "installing the base system" step I switch to a console screen by pressing ALT F2
then I add the  to the cpqarray to the modules file with:
```
echo "cpqarray" >>/target/etc/mkinitramfs/modules
```

I continue the install till I reach installing grub and instead of taking the default value:
hd(0) i think
I specify the boot partition:
```
/dev/cciss/c0d0p1
```

now I know grub has been installed on the correct partition and the correct modules have been loaded and it still hangs after reboot.

My final desperate move to get this to work is to recompile the kernel to include the cpqarray and not have it as a module. should I even bother or should I give up and reinstall windows on this piece of junk.

---

### Post by hdixon on 2008-01-16
Isnt the driver for the SmartArray 5i the cciss one and not the cpqarray? I am confused on this point.

---

