---
title: "How do I select where the bootloader is installed."
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by netytan on 2006-09-26
I'm having some problems doing a [sort of] custom installation. I've set up the partitions manually, splitting the drive into three so that I can keep my home directory separate.

When I do this however the boot loader is installed on hd0 I get a message requesting a boot disk when I start the computer. What in hell?

I’ve installed previous versions of Ubuntu without any problems :(.

I've been through this process a few times now and I can't find any way to install it on the MBR. Could someone give me a heads up on what I'm doing wrong here :).

Thanks a lot,

Mark.

---

### Post by neptune39 on 2006-09-26
This is a total guess but dont you need to set up a small 50mb boot partition, as well as the partions you want to use and the swap partition?

---

### Post by turbojugend_gr on 2006-09-26
Did you made the hd0 partition bootable? It is common that users trying custom installations forget to enable the bootable flag on their "/" partition. SO re-install making sure you did that...i hope that will do the trick!

---

### Post by jharr on 2006-09-26
Are you on crack? The bootable flag in the MBR isn't used by anything anymore (well, maybe dos/freedos, but I don't think netytan has either of those). Grub uses a config file at runtime. Besides, you can always go back later and set the bootable flags on partitions without a reinstall.

netytan, I'm assuming what you have is:
hda1 - /boot (~50mb)
hda2 - / (?)
hda3 - /home (?)
hda4:
  hda5 - swap ( 2 x [amount of ram you have] )

You can do two things:
1. Reinstall from scratch. Make sure when you partition to mount things appropriately.
2. Boot from live cd and fix it by opening up a terminal, and running:
$ sudo -i
# mkdir /target
# mount /dev/hda2 /target
# chroot /target
(chroot)# mount /proc
(chroot)# mount /boot
(chroot)# vim /boot/grub/menu.lst
make sure everything is ok in there, specifically groot=(hd0,0) somewhere in the comments. It's probably set to groot=(hd0,1)
(chroot)# update-grub
(chroot)# umount /boot
(chroot)# umount /proc
(chroot)# exit
# umount /target

Then reboot and see if that works.

If that doesn't help you or your setup isn't like that, you need to tell us more about your partitioning scheme. More than likely it's just a simple mistake that's easy to make and easy to correct.

---

### Post by randell6564 on 2006-09-26
Use the [Alternate CD]("http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/ubuntu-6.06.1-alternate-i386.iso") in order to get the option of where to install GRUB.

---

### Post by turbojugend_gr on 2006-09-27
> Are you on crack? The bootable flag in the MBR isn't used by anything anymore (well, maybe dos/freedos, but I don't think netytan has either of those). Grub uses a config file at runtime. Besides, you can always go back later and set the bootable flags on partitions without a reinstall.

I was talking about the root partition m8, you can check it out again in my post!
In case you don't remeber /boot/grub is the catalogue in which grub gets itself installed instead of the MBR! It only makes a link in the MBR leaving most of it untouched.
SO you need to have a bootable flag on for "/" partition. BTW I don't know of a way to enable the bootable flag in an easier way than re-installing, thus I suggested that, since he never used the OS nothing to be lost.

PS1: @jharr: Plz manner yourself m8, and if you can't do that at least read my freaking post first, then declare I am stoned...

PS2: @netytan: I suppose you only use ubuntu OS, and hd0 is where you put your root "/" filesystem. If that's not the case you should make it clear.

---

