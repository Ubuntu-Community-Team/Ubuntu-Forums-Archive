---
title: "Intrepid can't load partition?"
date: 2008-07-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phidia on 2008-07-16
I have two sata drives on this desktop-Gigabyte GA_M55SLI-S4 motherboard.
3 distros on 1st drive all boot fine 1 distro on 2nd drive boots fine too. I created a 30GB partition in freespace on the 2nd drive and installed intrepid x86_64 (the recently released alt install image) The md5sum and check cd for errors were both ok. The install completed ok-no errors, but when I try to boot I'm dropped to initramfs and get this error > ata1: SRST failed (errno=-16)
I can mount the partition /dev/sdb3 (hd1,2) in the other distros and have done so and checked menu.lst and fstab but nothing really seems wrong. The grub #'s are ok the UUID's for that partiton match in fstab and in menu.lst. The drive seems fine-I just mounted it. Anyone know why I'm getting this?

---

### Post by ronacc on 2008-07-16
if you have another ubuntu install you can mount the partition and when its icon appears on the desktop check the uuid with rt click >properties>volume and see if they are the same there also . Did you set the boot flag on that partition if you have grub installed there  or are you booting from another grub ? I multiboot but only have one grub and I just add bootstanzas as needed .

---

### Post by BwackNinja on 2008-07-16
I don't remember seeing the uuid when I go to properties, a "sudo blkid" will show it for all partitions on all drives though.

---

### Post by ronacc on 2008-07-16
see screenshot

---

### Post by phidia on 2008-07-17
Thanks ronacc your ideas got me thinking. I never seem to have to mark a partition for boot with linux and I don't have a windows install-I do chainload thru one grub btw. I did mark it for boot anyway but got the same error. I did a Ctrl+D though and this time it did continue to boot. X wouldn't start so I just did an apt-get update && upgrade, and after it finished x started up!!
> ibexx:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu intrepid (development branch)
Release:	8.10
Codename:	intrepid

YAY a new toy to play with!

---

### Post by ronacc on 2008-07-17
you shouldn't have to mark it for boot if the installer did its job right , but its always a good thing to check , I don't have a Windows install either but I multiboot several linux distros/versions . I just let the first install I do on the box install grub and add boot stanzas to boot the others . I do it that way because I have never had any luck getting ubuntus grub installer to find and add all the other installs.

---

### Post by phidia on 2008-07-17
Yeah, as I said I use the grub chainloader command to boot into the grubs, installed to the root partition, of my other installs-that way all kernel updates get picked up/used without my needing to do any further editing.

That error I opened this thread with came back, but I just have to wait a while do ctrl-d and it's boots. Now the error references ata5. I don't know if one of my optical drives is biting the dust. :( Doesn't happen in the other installs though.

---

