---
title: "Update process interrupted by my kid, now can't start"
date: 2021-04-16
forum: Installation &amp; Upgrades
---

### Post by BigBaka on 2021-04-16
Dear forums,
I'm running an old 16.04 LTS on an ancient Lenovo notebook S205 that is mostly used by my 8 year old. Today I was running an update process after not having done so for a year or more, and then towards the end my son came in a halted the update mid-stream. From there on I tried to update again to no avail, then tried to run synaptic and the whole thing crashed and I had to restart. Normal restart wouldn't work, so tried recovery restart and got the following error
Kernel offset: disabled
---[end Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

I've attached a pic of the error.

Also I don't have any other devices running ubuntu or any linux distro. 

Any tips about what I should do?
Regards,
Glenn

---

### Post by mikewhatever on 2021-04-16
If the recovery mode doesn't work, there is probably no way to fix things without a bootable USB stick with Ubuntu. You should make one.

Then, I'd try to check the root partition with <fsck> for consistency.

---

### Post by CatKiller on 2021-04-16
So, essentially it looks like your package manager is in an undefined state, and your kernel/grub is confused about how to boot. Not a nice position to be in.

However, a live USB boots into a perfectly functional Linux environment, and the rest of your computer - the part that's having trouble - is just files on a disk from that perspective.

There's a command called **chroot** that lets you **ch**ange the effective **root** location for commands. So you can boot one system (such as your live USB) and run commands as if you'd booted a different system (such as your currently non-functional computer). There's a bunch of information about it, but the gist is that you'd boot your live USB, mount your computer's drive somewhere (and *sometimes* some of the other special pseudo-filesystem places, depending on what you need to achieve), then say that the place you've mounted it to is really / with the chroot command. Then you can complete your upgrades, and whatever other maintenance you need to do. 

Bear in mind that 16.04 has about a fortnight's support left, and a reinstall takes less than 20 minutes, so you'll want to balance how much time you want to spend troubleshooting versus how much time a backup-install-restore cycle would take.

---

### Post by BigBaka on 2021-04-16
Just formatting the USB bootable ubunut drive.

Wondering how to use this chroot command to complete the upgrade?

---

### Post by Impavidus on 2021-04-16
Have you tried an older kernel? Maybe the upgrade was interrupted in the middle of the installation of a new kernel. The old kernel might still work. If that doesn't allow you to boot your system, you need a live disk.

Support for 16.04 is about to end, so, if you can use a different computer to create a live disk, you could also jump ahead to 20.04 by fresh install. It's probably easier. As it appears you're not in the habit of regularly installing upgrades, I suggest you make sure the security upgrades get installed automatically

---

### Post by BigBaka on 2021-04-16
Old Kernel was a good idea, but there was a problem with that Kernel and an app called timekpr, which I accidently set to Zero, which means I automatically get logged out as soon as I log in.

Have booted up on the flash drive and just copying the files off, and going to run a fresh install of lubuntu 18.04 as it's the last i386 release and is specifically designed for older machines.

Thanks for the tips, but i'll sign off on this one.

---

### Post by CelticWarrior on 2021-04-16
> [COLOR=#000000]going to run a fresh install of lubuntu 18.04 as it's the last i386 release and is specifically designed for older machines[/COLOR]
No.
If you really have a 32-bit CPU, as opposed to having a 64-bit and decided to install a 32-bit OS for... reasons, you now need to find alternative distros outside the Ubuntu family. Debian is one of the possibilities but they're becoming less and less as the time goes by.
**Lubuntu 18.03 has only 3 years of support therefore it'll will end in a matter of days.**

---

### Post by Impavidus on 2021-04-16
[Lenovo support]("https://support.lenovo.com/de/en/solutions/PD022804") tells me that the S205 has an AMD Brazos C30, C50, E240 or E350 CPU, which is 64 bit. It isn't exactly a powerful processor, not even by 2011 standards (when it was released), but it should run the lighter flavours of 20.04 (Lubuntu, Xubuntu, Ubuntu Mate, ...) You didn't say how much memory is in it, but it supports 8GB. I guess graphics will be a bit poor too.

My current laptop is of the same vintage, although more powerful, and runs Xubuntu 20.10 very smoothly. I think it would run regular Ubuntu 20.10 too, but I just like Xubuntu more.

---

