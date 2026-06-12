---
title: "Boot a Ubuntu 10.04 desktop live from an iso image in /boot partition"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by divino_marchese on 2010-11-09
Hi!
My laptop can't boot from cdrom becouse it is broken and it can't boot from USB becouse it has never been able. Ubuntu 8.10 now run in my laptop with grub 1.

I've just try the following trick.

1) I put grub4dos in /boot
2) I put iso image in /boot
3) I add the follwing entrt in source.list

```
# =========== GRUB4GOS ===================================
title == Use grub4dos for the following entries: ==

title 1:	Reload this menu using grub4dos to enable booting the next entries
kernel 		/boot/grub.exe

title 2:	boot Ubuntu live
map --mem /boot/ubuntu-10.04-desktop-i386.iso (hd32)
map --hook
chainloader (hd32)
```

It seem fine but ... it falls. An eror message says thath the system is not able to load the file system from live cd.

If someone had the patient to try my solution and give me an usefull suggestion I will thank you!

---

### Post by cybergnome on 2010-11-09
According to Grub4DOS documentation, the creation of a virtual disk is implemented using INT13, and therefore can be accessed in systems that use INT13, such as DOS, Win9X/ME, but can't be accessed by systems that use protected mode drivers.  That includes NT class OSes and Linux.  Sorry.

---

### Post by divino_marchese on 2010-11-10
Thx very mach for your clear answer. Could you suggest me a work around?

---

### Post by divino_marchese on 2010-11-14
I made a first step in order to resolve my problems.
I'va got a partitions in /dev/sda7 i.e. /opt
1) I created a directory: live
2) I put initrd.lz,  ubuntu-10.04-desktop-i386.iso,  vmlinuz in /opt/live
3) I created a new entry in menu.lst

```


# =========== LIVE ===================================
title		Live
root		(hd0,6)
kernel		/live/vmlinuz boot=casper iso-scan/filename=/live/ubuntu-10.04-desktop-i386.iso
initrd		/live/initrd.lz


```

It works!

Now, I try the installation program in live. It says that I've to umount sda ... ok I umount it .... but, at this point, I chose to don't go forward in the installation. Could someone confirm my choice. I prefer to not enter in a black hole.

Thx.

---

