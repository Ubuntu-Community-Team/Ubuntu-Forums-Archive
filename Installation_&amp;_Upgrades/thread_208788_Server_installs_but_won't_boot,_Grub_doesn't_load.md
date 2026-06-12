---
title: "Server installs but won't boot, Grub doesn't load"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by nudaz on 2006-07-04
Hi, sorry if this has been answered but I couldn't find quite the same problem...

Situation:
Spare server at work... (perfect for the linux n00b like me!)
Installed ubuntu 6.06 desktop - ok, booted ok, worked fine.
Started over, installed 6.06 server - installed ok but wouldn't boot properly,
message like "dropping to a shell"
So found out you can hit Esc when grub is loading,
the scsi disk was listed as ```
/dev/i2o/hda1
``` and I hit 'e' and changed it to ```
/dev/sda1
``` and then hit 'b' to boot that line and it worked.

Ok, then I tried to get it to boot without having to edit the line each time,
(edited menu.list I think) but I messed it up because it wouldn't work after that. Was a shame I couldn't get back into ubuntu because I had VMware server installed and ready to install Win2003.

Unfortunately I had to have Windows 2003 installed to do some tape backup stuff, so I had to wipe it out and start fresh.

Ok, so now finished with that and installed ubuntu server 6.06 again.
Completely wiped the disk, repartitioned it all for ubuntu.
The install went fine, but when it rebooted it gets to:
```

GRUB loading, Stage 1.5

Error 17
```

Thats basically it (I'm at home now, so maybe not exact)
I can't hit Esc to get into Grub either, it just hangs there.

I tried the rescue option from the CD, 
and tried to reinstall grub, but I can't get past the Partition disks part.
The problem was it complained of not having a root filesystem or something,
so I toyed around with the mount of the 1st partition, but nothing worked.
(It was set to /media/i20_something/hda or something, I tried '/' but that didn't work either.)

And just trying the "Finished partitioning disks.." just brings me back to the same partiton disks screen. I have to go back.

So I'm stuck - I could just install the desktop, but I really want to fix this!

Anyway, here are the specs:

HP Netserver E 800
2 x 1Gh PIII
1152Mb RAM
2 x 36Gb SCSI HDD in Raid 1 on Adaptec 2100S controller
2 x 72GB SCSI HDD on mainboard controller
IDE CD-Rom

Installing OS on the Raid 1 scsi (Partition utility shows it as 1 disk).
#1 is 34GB ext3
#5 is 1.4GB swap

If any one out there has any clue/help/suggestions/advice I'd really appreciate it!

Thanks,
Darren

---

### Post by mlind on 2006-07-04
Boot using Ubuntu live cd. If you're using alternate installcd, it will do the chrooting
automatically, but doesn't have gui.


Open a terminal

find your root partition using fdisk
```

sudo fdisk -l

```

Let's assume it's /dev/sda1

Mount your root partition and chroot it. You'll have to mount /boot paritition inside
chrooted environment if it's on different partition.
```

sudo mkdir /mnt/root
sudo mount /dev/sda1 /mnt/root
sudo chroot /mnt/root /bin/bash

```

Edit */boot/grub/menu.lst* on chrooted environment. check that **groot** points to your root partition.
**sd**x devices go before **hd**x devices, so /dev/sda is probably hd(0,0). 


Install grub on /dev/sda (device, not a partition)
```

grub-install /dev/sda

```

and try to reboot. If grub was installed to correct device, and next time you alter
grub options, run **update-grub** instead of grub-install.

---

### Post by nudaz on 2006-07-04
Thanks mlind - that worked up until
grub-install /dev/sdc
(fdisk showed root partition as sdc1)
Iwas pleased to see groot pointed to hda(2,0)
so I was hopefull!
```
grub-install /dev/sdc
sdc doesn't have a BIOS drive
``` (or similar)

but I can load grub and hit Esc at boot.
This is what I see (which was same as before when I can edit it with 'e'
and boot with 'b'):
```
root (hd2,0)
kernel /boot/vmlinuz-2.6.15-23-server root=/dev/i2o/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-server
savedefault
boot
```

but editing the kernel line to 
... root=/dev/sdc1 ...
 and trying to boot does work!

Not sure if I should try update-grub, cos I don't want to mung it again,
but it seems its calling the drive /i2o/hda when it should be sdc?

Thanks again - at least now I can boot!

cheers

---

### Post by mlind on 2006-07-05
[QUOTE=nudaz]Thanks mlind - that worked up until
grub-install /dev/sdc
(fdisk showed root partition as sdc1)
Iwas pleased to see groot pointed to hda(2,0)
so I was hopefull!
```
grub-install /dev/sdc
sdc doesn't have a BIOS drive
``` (or similar)

but I can load grub and hit Esc at boot.
This is what I see (which was same as before when I can edit it with 'e'
and boot with 'b'):
```
root (hd2,0)
kernel /boot/vmlinuz-2.6.15-23-server root=/dev/i2o/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-server
savedefault
boot
```

but editing the kernel line to 
... root=/dev/sdc1 ...
 and trying to boot does work!

Not sure if I should try update-grub, cos I don't want to mung it again,
but it seems its calling the drive /i2o/hda when it should be sdc?

Thanks again - at least now I can boot!

cheers[/QUOTE]

find **kopt** line from */boot/grub/menu.lst* and change it to
```

# kopt=root=**/dev/sdc1** ro

```

and then run 
```

sudo update-grub

```

---

### Post by nudaz on 2006-07-16
That worked well (bootup no probs), thanks mlind.
I followed a grub tutorial and created a fresh menu.lst
and that was working well too (booting up no probs), until the other scsi drives failed.
Then the root was no longer sdc/hd2 so I went through the
steps again. As it didn't work I added in scsi drives so my root was again sdc/hd2 and went through the steps again.
This time however, it doesn't work :(

I get:
```
GRUB loading stage1.5.

GRUB loading, please wait...
Error 15
```

I've followed the instructions again(except in the chroot environment I can't use sudo)
but when I run update-grub I get the
```
/dev/sdc does not have any corresponding BIOS drive
```
message.
I also tried
```
grub-install --recheck /dev/sdc1
```

and get the message
```
/dev/i2o/hda1 does not have any corresponding BIOS drive
```

Any ideas anyone?

---

### Post by nudaz on 2006-07-17
Update: changed BIOS boot order, and redid the intsructions,
now Grub loads but I get error 17: cannot mount selected partition.

---

### Post by nudaz on 2006-07-17
Update:
OMG just tried grub command line, find /vmlinuz
and result was (hd0,0)!
Edited menu option to root(hd0,0) and booted up ok!
Live cd sees it as sdc/hd2, and it had been booting as root (hd2,0).
Will it change again? Why?

---

### Post by mlind on 2006-07-17
> **nudaz said:**
> Update:
OMG just tried grub command line, find /vmlinuz
and result was (hd0,0)!
Edited menu option to root(hd0,0) and booted up ok!
Live cd sees it as sdc/hd2, and it had been booting as root (hd2,0).
Will it change again? Why?

There's a related note about this on grub's [manual]("http://www.gnu.org/software/grub/manual/grub.html#Naming-convention")
```

[I]Note that GRUB does not distinguish IDE from SCSI - it simply counts the
drive numbers from zero, regardless of their type. Normally, any IDE drive
number is less than any SCSI drive number, although that is not true if you
change the boot sequence by swapping IDE and SCSI drives in your BIOS.[/I]

```

---

### Post by nudaz on 2006-07-17
Well that kind of makes sense - although they're all scsi drives, on 2 controllers, that were swapped in bios.
fstab shows
/dev/i2o/hda1
while fdisk shows
/dev/sdc1
for the same drive/partition. I think the cause of the original problem is something to do with that.
Ubuntu desktop doesn't have a problem with it - installs fine AND reboots ok.
Server installs but doesn't reboot.

Thanks for all your help, cheers.

---

