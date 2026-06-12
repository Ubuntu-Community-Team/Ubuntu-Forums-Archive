---
title: "feisty crashes on boot, &quot;/&quot; system disk does not exist"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by kalimotxo on 2007-04-20
First of all i will describe my sistem:
Pentium IV 1.5 Mhz on a SiS 645DX/961B (NS70-EL from DFI) chipset board, with two ATA Hard Disk. I am trying to install feisty final release, and with the feisty livecd, hard disks are partitioned like this:

First Hard Disk 40 gb (Master of IDE1)
hda1-> Windows XP (30 gb). I want to keep it aswell.
hda2-> / (8.5 gb approx)
hda3-> swap (1.5 gb approx)

Second Hard Disk 120 gb (Slave of IDE1)
hdb-> /home (120 gb)

After installing, i reboot and the remove the livecd, and when when grub loads, I select the latest Kernel (2.6.20-15), and then the progressbar does not make any progress. (Same bug in the Kernel (2.6.20-12 to 2.6.20-15 last one). After one or two minutes i can see this:

"Udevd-event [1950]: run-program: '/sbin/modprobe' abnormal exit

BusyBox v.1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-install (ash)

/bin/sh: can access tty; jub control turned off (initramfs)"

and this:

"ALERT! /dev/disk/by-uuid/xxxxxxxxxxx Does not exist, dropping to a shell"

i thinks that "xxxxxxxxxxxx" is the by-uuid identificator for the system disk "/"
The number of Udevd-event [xxxx] can vary from 1950 to 1960 (in other install tryings)
The system works perfectly with Edgy with the same partitioning configuration.

Any solution?

---

### Post by brutal_deluxe on 2007-04-20
> "ALERT! /dev/disk/by-uuid/xxxxxxxxxxx Does not exist, dropping to a shell"

i thinks that "xxxxxxxxxxxx" is the by-uuid identificator for the system disk "/"
The system works perfectly with Edgy with the same partitioning configuration.

I have exactly the same problem after upgrading from edgy :(   
I've tried replacing the uuid id of the root filesystem in menu.lst (with /dev/hde2) but without success.

Reading some support threads for the feisty beta releases last night (which of course I haven't bookmarked on this LiveCD) it seemed some people were experiencing similar problems with SATA drivers not loading at the right time / at all.

Could it be a similar problem here? No SATA controller though:
Chaintech CT-9BJD motherboard;
HighPoint Rocket 133 ATA controller 
with a couple of Seagate HDDs plugged into it.

---

### Post by hoagie on 2007-04-20
I have the same problem. 
Anyone with a working solution?

---

### Post by John Williams on 2007-04-20
try mounting your root filesystem. for the above /dev/hde1 I would try mount -t ext3 /dev/sde1 /root, assuming the FS is an ext3 type. Then hit CTRL-D. That worked for me...

---

### Post by kalimotxo on 2007-04-20
> **John Williams said:**
> try mounting your root filesystem. for the above /dev/hde1 I would try mount -t ext3 /dev/sde1 /root, assuming the FS is an ext3 type. Then hit CTRL-D. That worked for me...

Yes, FS hda2 (where "/" is) is an ext3.
How should i do that? or better where should i do that? in the initframs prompt?

---

### Post by kalimotxo on 2007-04-20
> **John Williams said:**
> try mounting your root filesystem. for the above /dev/hde1 I would try mount -t ext3 /dev/sde1 /root, assuming the FS is an ext3 type. Then hit CTRL-D. That worked for me...

Another tag, my harddisk is ata (IDE) no sata, therefore the disk's name has to be hda not sda. How could i mount it then? Were your disk a sata one or an ata one?

---

### Post by brutal_deluxe on 2007-04-20
> **John Williams said:**
> try mounting your root filesystem. for the above /dev/hde1 I would try mount -t ext3 /dev/sde1 /root, assuming the FS is an ext3 type. Then hit CTRL-D. That worked for me...

None of my harddrive partitions seem to be present under /dev at the BusyBox prompt.   
"Mounting /dev/hde2 on /root failed: No such file or directory"
They're all as they were when booting with Edgy Live CD.

---

### Post by line72 on 2007-04-20
Here's what I had to do (I'm sure there's a proper way to do this)

```

modprobe ide-disk
modprobe ide-generic
mount -t ext3 /dev/hda1 /root
mkdir -p /dev/disk/by-uuid
ln -s /dev/hda1 /dev/disk/by-uuid/xxxxx-xxxxx-xxxx-xxxx (replace with your uuid in /root/etc/fstab)
Control-D

```

Everything should start booting.  Unforunately, this doesn't seem to stick around, so everytime I reboot, this must be done.  Hopefully a real solution will come along soon.

---

### Post by brutal_deluxe on 2007-04-20
line72

Thanks for the advice, this looks like it could work for me but at the moment modprobe only finds my cdrom attached directly to the motherboard.  The harddrives are connected to an ATA controller card.  Do you happen to know how to modprobe the devices attached to this card?

Thanks

---

### Post by kalimotxo on 2007-04-20
> **brutal_deluxe said:**
> line72

Thanks for the advice, this looks like it could work for me but at the moment modprobe only finds my cdrom attached directly to the motherboard.  The harddrives are connected to an ATA controller card.  Do you happen to know how to modprobe the devices attached to this card?

Thanks


Thanks both,

i have been checking on my system directories (/dev) and none of my partitions seem to appear aswell. /dev/disk doesn't exist in the dev directory, another directories in dev that would have to be there, aren´t aswell. During the installation something is happened, that directories and files haven't be copyed to /dev, and i dont now why.

---

### Post by kalimotxo on 2007-04-20
> **line72 said:**
> Here's what I had to do (I'm sure there's a proper way to do this)

```

modprobe ide-disk
modprobe ide-generic
mount -t ext3 /dev/hda1 /root
mkdir -p /dev/disk/by-uuid
ln -s /dev/hda1 /dev/disk/by-uuid/xxxxx-xxxxx-xxxx-xxxx (replace with your uuid in /root/etc/fstab)
Control-D

```

Everything should start booting.  Unforunately, this doesn't seem to stick around, so everytime I reboot, this must be done.  Hopefully a real solution will come along soon.

Finally i've tryed line72 has told, and it does work, now i'm posting this from the feisty. I havent still reboot, so i dont know if it goes on working when rebooting. But i have another problem,unfortunately the sound doesnt work now.

---

### Post by line72 on 2007-04-24
I solved this by generating a new initrd with yaird.  If you can't boot into ubuntu using the above method by manually loading the ide drivers and mounting, then download the alternative cd, and go to repair.  Once in ubunut do:

```

apt-get install yaird
sudo cp /boot/initrd.img-2.6.20-15-386 /boot/initrd.img-2.6.20-15-386.bk
sudo yaird -o /boot/initrd.img-2.6.20-15-386

```

Then reboot!

---

### Post by kalimotxo on 2007-04-24
thanks line 72, i appreciate your answer.

I can boot by that mannually method, now i will try it installing the yaird from the alternate cd, (any special reason?, cannt  it be done from desktop cd?)

---

### Post by tsuen on 2007-05-10
I have a similar error when doing a fresh install of the Desktop version.  In my case, it died in pata_sis during modprobe.  I followed this method and was not able to get the system to fully boot.  However, I did find a workaround.  Since the original CD boots and can see all my disks, I figure the original ramdisk contains at least  a working driver for the system.  So, when the boot fail and drops into initramfs, I
1. modprobe ide-disk
2. modprobe ide-generic
3. remounted the boot partition somewhere (could be on root partition depedning on how you partition your drive)  In my case, 
#  mkdir /target
#  mount -t ext3 /dev/hda1 /target
4. and renamed the switched the ramdisk image with the backup (that's also on the /boot directory).
#  cd /target
#  mv initrd.img-2.6.20-15-generic initrd.img-2.6.20-15-generic.new
#  mv initrd.img-2.6.20-15-generic.bk initrd.img-2.6.20-15-generic
5. finally reboot

With the changes, the system boots successfully (and reboots after that).  It is probably not optimal for my hardware since it's using a lot of generic stuff but it works and the system is usable.

In a way, it is similar to getting the alternate cd and building a new ramdisk but you don't have to do the down load with this.  If you prefer, after the system comes up, you can install the package and rebuild the ramdisk.


Hope this helps.

---

