---
title: "Help! Ubuntu doesn't boot"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by Aeolosoma on 2007-11-08
Hi,  yesterday I bought a new 250gb HD where I've successfully installed  ubuntu gutsy and on the same machine I also have an 80gb HD with Win xp. Now the problems begin, the bios sees my ubuntu HD as master and the Xp one as slave, but it's not able to boot any of them by itself! It keep asking me to insert a bootable cd or floppy, GRUB doesn't even start.
The only thing I can do is to use the ubuntu  live cd and select the option "boot from HD" then grub starts and ask me which OS I want to boot.
I've already tried to recover grub mannually with this script I found on wki
> sudo /sbin/grub 
grub> root (hd0,2)
grub> setup (hd0)
grub> quit
Everything seems to work fine, but when I reboot nothing has cahnged, it still ask  me to insert a bootable device.
I tried to use the "super grub disk" that seems work fine too, until I reboot :(
I also tried to mess a bit with the bios; first  I set no boot device, then I set to boot from hd... Still nothing chage

I'm not an expert, I don't really know why this happens. Please someone give me some advice

---

### Post by Sef on 2007-11-08
Use a Live CD, if can't boot into Ubuntu.  Then Applications > Accessories > Terminal.

Type in this command: ```
sudo fdisk -l
```

That will show you your partitions.  Copy and paste that here.

---

### Post by Aeolosoma on 2007-11-08
Here it is
> Disco /dev/hda: 250.0 GB, 250059350016 byte
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ce095

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4863    39062016   83  Linux
/dev/hda2            4864       29908   201173962+  83  Linux
/dev/hda3           29909       30401     3960022+   5  Esteso
/dev/hda5           29909       30401     3959991   82  Linux swap / Solaris

Disco /dev/hdb: 80.0 GB, 80026361856 byte
255 heads, 63 sectors/track, 9729 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92a692a6

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9728    78140128+   7  HPFS/NTFS


---

### Post by Aeolosoma on 2007-11-08
help please:(

---

### Post by maybeway36 on 2007-11-08
Could you boot from your hard drive before? Sounds like a BIOS problem.

---

### Post by Aeolosoma on 2007-11-08
If I use only the Win Xp HD then windows does boot properly. If I set them in master/slave configuration (with the linux one as master) none of them boot

---

### Post by Therion on 2007-11-08
This is a TOTAL stab in the dark and I only mention it because I had a similar problem at one point.  In my BIOS settings I have the usual Boot-to sequence - First, Second, Third boot device (e.g. Device 1=CD ROM, Device #2=HDD) but I also have an option for configuring ALL my bootable devices individually.  I'm just trying to remember where that menu is, because it sticks in my mind it's NOT under the BOOT menu of the BIOS.

At any rate, my point here being, and what solved the problem for me was that I needed to configure this other, section as well the boot sequence section, so the BIOS knew which drive I wanted as the *primary* bootable hard drive, and which as the *secondary* (but still bootable, since it contained an OS) hard drive.  

I'm sorry I can't be more precise but I'm in my office at the moment so I can't reboot my Linux-box and pin things down for you any better than that.  Maybe that will point you in the right direction though.

---

