---
title: "Grub Problems :\"
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by jaykup on 2005-11-23
THe hard drive that held the grub install died, so i moved it over to the drive Linux was on.  It worked when i booted it up, but when i selected my linux install, it gave me an error (cannot be mounted) or something to that effect.

This is what my grub looks like..

title		Ubuntu, kernel 2.6.12-9-k7-smp 
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.12-9-k7-smp root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-k7-smp
savedefault
boot

The hard drive that linux is on is the Secondary Slave, which im guessing would make that hd2 (Secondary Master is a hard drive, Primary  Master is a CDROM, Primary slave is a Hard drive)

It also doesnt recognize the file system, if that matters.

It also has at the bottem "NT/2000/XP" or w/e and that boots fine into WIndows 2003

Looks like:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Windows NT/2000/XP
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

Windows is on the Secondary Master

Any Ideas?

---

### Post by jaykup on 2005-11-23
I tried running

kernel /boot/vmlinuz-2.6.12-9-k7-smp
boot

and it does start to load the kernel, returns with this
kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)

so my question is it just booted the kernel, so its reading from the disk jsut fine, but it keeps giving errors that it cant mount the disk?  whats going on?

---

### Post by mlomker on 2005-11-23
I'm not sure how you installed grub...did you boot to a linux CD of some sort and do the install?  Here's a [how-to]("http://geodsoft.com/howto/dualboot/grub.htm#install") that I like.  The find command is the best way to be sure that you have the right drive/partition numbers.

---

### Post by jaykup on 2005-11-23
seems that it was hd0 after all.. i ran

root (hd0,0)
setup (hd0,0)

then had to change the grub lines to read of hd0

thanks :)

---

