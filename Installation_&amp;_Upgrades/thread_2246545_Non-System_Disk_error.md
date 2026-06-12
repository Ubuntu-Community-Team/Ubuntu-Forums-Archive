---
title: "Non-System Disk error"
date: 2014-10-01
forum: Installation &amp; Upgrades
---

### Post by jack107 on 2014-10-01
I'm installing ubuntu 14.04 off of a USB, and everytime I've tried running my machine after "successfully" installing ubuntu, I get an error:

Non-System disk or disk error
replace and strike any key when ready

I'm at a lost. As far as i can see, i'm installing it correctly, and i've checked the bios, and the hard drive is being read from.
Does anyone have any ideas what could be causing the error?

---

### Post by slickymaster on 2014-10-01
*Moved to the ***Installation & Upgrades*** sub-forum*

---

### Post by grahammechanical on 2014-10-01
> [COLOR=#000000]Non-System disk or disk error[/COLOR]

That message usually appears when the boot system (BIOS/UEFI) cannot find a disk with an OS on it. What happens when you re-insert the USB memory stick and then  you"strike any key?" does the Ubuntu live session load? If it does, then the BIOS is most likely seeing the USB stick as an external USB hard drive and is set to boot from it and not from the hard drive.

Regards.

---

### Post by Bashing-om on 2014-10-01
jack107; Hi ! My Welcome to the forum .

I would hazzard to guess that grub did not get installed to the hard drive.

You can check and see what the situation is by mounting the partition from the liveUSB and reading the contents of the boot config file "/boot/grub/grub.cfg". 
OR just (re-)install grub.
If you want to (re-)install grub show us what we are working with, so we can craft up the proper syntax to make that happen.
From the liveUSB; terminal commands
```

sudo fdisk -lu
sudo parted -l

```

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by JKyleOKC on 2014-10-01
That message is coming from the Master Boot Record of your hard drive. Apparently, when you did the installation from USB, the installation programs put the bootstrap loader into the MBR of the USB drive rather than into the MBR of the hard drive.

You can try re-installing from the USB, but when you get to the window that asks whether you want to replace the existing system, install alongside it, or "something else," select "something else." This is the only option that lets you select where to place the bootstrap loader!

It's also, unfortunately, the most complicated of the choices, since it lets you do everything for yourself instead of performing behind-the-scenes magic. If you're uncomfortable with this, let us know and someone will probably show up to guid you through it step by step.

---

