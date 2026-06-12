---
title: "Keep getting the grub rescue prompt after a fresh install"
date: 2015-01-28
forum: Installation &amp; Upgrades
---

### Post by vecordae on 2015-01-28
So, here's what's going on:  After a fresh install of kubuntu (tried 14.04, 14.10, and 15.04 multiple times from disks, usb sticks, you name it), the system won't boot.  I get a grub rescue prompt instead.

Now, this isn't an uncommon problem and I've already tried boot-repair, reinstalling grub from a live-cd and even doing the whole complicated chroot thing to set it up.  

Here's the odd bit:  If I mount the SSD where I've installed kubuntu, I can see that the boot menu contains a grub folder, my linux kernal, and all the other stuff I need to get my system to boot.  If I try to boot from the SSD, however, the /boot menu comes up empty.  And this happens every single time.  I'm kind of flummoxed.  The grub2 superdisk can't see the kernal or grub configuration files, either.

Other important bits:  This is an old dell lattitude e5410 laptop that has been able to run Ubuntu 14.04 (64-bit) successfully in the past.  I haven't changed any hardware on it and I only intend to run a single OS on it.

---

### Post by vecordae on 2015-01-28
UPDATE:  So, I ended up trying the kubuntu installation again.  This time I wiped the ssd completely and manually set the partition sizes.  The bad news is that I'm still getting a grub rescue prompt.  The good news is that I'm also getting the "ELF magic" error, too.

Normally those would both be bad news, but I actually know how to handle a dearth of elfin magicks.

---

### Post by fantab on 2015-01-28
If you can boot Kubuntu Live with 'Try Ubuntu' option, then open Terminal [ctrl+alt+T], run the following and post its output here:
```
sudo parted -l
sudo fdisk -l
```

You said you've used Boot-Repair, can you post the _Bootinfo Summary_ created by Boot-Repair? (Just post the URL Link).
Tell us more about your machine: RAM, Graphics, etc.... model and make.

---

### Post by vecordae on 2015-01-29
Thanks for your response, fantab.

Looks like I got it sorted out.  I don't know what the problem was, but after the most recent install (using the exact same liveusb setup as I had twice before), I got the elf magic error.  That particular problem is resolvable by using the boot-repair cd.

Still, it seems odd that I'd have this much trouble.  I've linked the bootinfo summary below anyway.  The machine itself is Dell Lattitude e5410 with a 1st-gen i5 mobile cpu, integrated 1st-gen Intel HD Graphics display adapter, and four gigs of RAM.  It's using a cruddy 256g Crucial V4 SSD.  I've installed the 64-bit version of Ubuntu 14.04 on it before without any problems at all.

[http://paste.ubuntu.com/9938777/]("http://paste.ubuntu.com/9938777/")

---

