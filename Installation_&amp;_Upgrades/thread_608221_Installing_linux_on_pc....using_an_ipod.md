---
title: "Installing linux on pc....using an ipod"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by henry806 on 2007-11-09
is there anyway to install linux on a pc using an ipod?

not using it to boot linux like a start up disk but to actually install it just by plugging the ipod into the pc as it starts up and installing it from there onto the actual pc hard drive?

---

### Post by BoneKracker on 2007-11-10
I think so.  Here are some thoughts that might help.  First of all, I think you have to make it boot from the iPod to do what you're talking about (so your "not" is actually a requirement of the second part after "but").

If #1) Provided that the pc in question has a bios which is capable of booting from an external disk (i.e. USB or Firewire) then yes.

If #2) Also, and I don't know if this is the case, you would have to be able to make the iPod a bootable disk.  The last time I screwed around with my iPod, I seem to recall that there are partitions there that contain the iPod's software.  Providing the disk is not somehow protected and you can fdisk it like any other, you should be able to make it a bootable disk.

Then, the task is to create a Linux system thats sole purpose is to install a Linux system.  Here is where I might steer you wrong:

There may be a way to turn the iPod into a sort of LiveCD.  If that's possible then that would be easiest and most efficient.  I've never built a Live CD myself, much less turned a disk into one, so I can't help you there.

Not knowing how to do that, my approach would be to do it in two steps:

1.  Install a minimal Linux system onto the iPod disk.
2.  Store a cd image of an installer cd on the disk.

Then, you want to create a script or something that will load the installer CD image (via a loop device) and launch the installer.

---

### Post by henry806 on 2007-11-10
thank you very much i'll give it a try.

---

### Post by BoneKracker on 2007-11-16
Something else just occurred to me.

People put a live cd image on a usb key, so it ought to be possible to just put an installer cd (or live cd) image on the iPod.

---

