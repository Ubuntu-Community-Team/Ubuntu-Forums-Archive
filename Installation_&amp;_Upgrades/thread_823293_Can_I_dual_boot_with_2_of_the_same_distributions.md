---
title: "Can I dual boot with 2 of the same distributions"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by sofasurfer on 2008-06-09
I want to have a spare installation to practice on. But I only have 1 hard drive. Can I dual boot with 2 copies of Hardy? Or do dual booted distros have to be differant from each other?

---

### Post by kellemes on 2008-06-09
> **sofasurfer said:**
> I want to have a spare installation to practice on. But I only have 1 hard drive. Can I dual boot with 2 copies of Hardy? Or do dual booted distros have to be differant from each other?

Works fine..

[All the info on dual booting you need]("http://www.users.bigpond.net.au/hermanzone/").

---

### Post by sofasurfer on 2008-06-09
But I have never seen reference to 2 identical os's on same hd.

---

### Post by ibutho on 2008-06-09
It possible to have to versions of the same distro. The procedure is just the same as that of dual booting between multiple distros. One thing you may want to do is to avoid installing grub on one of the versions so that you do not get into a vicious circle of each versions grub overwriting the others when you do a kernel upgrade.

---

### Post by sofasurfer on 2008-06-09
Then if I install the second Hardy OS I would chose not to install grub during setup? But then I would need to learn how to reconfigure grub manually, correct?

---

### Post by Herman on 2008-06-09
I do it all the time and I highly recommend it, I think more people should install two or more Ubuntus.

My wife likes having two Ubuntus in her desktop PC because if anything goes wrong with one installation while I'm not home, she just boots the other and resumes whatever it was she wanted to do. 
Nothing goes wrong very often, but it's nice to know she can do that if she wants to.

For other people who want to learn the Linux command line, or experiment with programming of installing software that might make the system unstable or insecure, a secondary Ubuntu installation can be used as a sandbox, to try out new ideas without affecting the main installation.

When Intrepid Ibex is developed enough, it will help developers if a few of us install it as a second Ubuntu after our Hardy Heron or earlier Ubuntu systems. We can preview Intrepid and help developers at the same time by sending back (sensible) bug reports about how it performs on various hardware.
It's no good waiting until the final release day and then posting here to the forums and complaining about how the developers didn't do things well enough. Remember, Ubuntu is our operating system too, and it's up to us users to help the devs out a little. Even if we can't code, if we can try to learn to be useful testers then we will be helping the next release of Ubuntu to be better than any before! :)
Intrepid's nowhere near ready at this stage for us to be useful yet though. It will be a while yet.

You can install GRUB to MBR again or to the boot sector, it's up to you, a matter of personal preference I think. 
If you install to MBR, the second GRUB will automatically be configured to boot the first OS without the user having to know anything.
That's all you really need to do.
However, if you want to do things properly, you should change the boot stanza to a chainloader boot or a configfile boot, so that you will be booting the other Ubuntu by its own GRUB menu. That way it will be booting the most up to date kernel. For more info,  [Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems"). It's quite simple really.

---

### Post by ibutho on 2008-06-09
Yes, you would need to reconfigure grub manually but its not as complicated as it seems. The way I approach this is that on the distro that has grub installed, I create an entry for the distro without grub e.g.
```
title SomeDistro
    root (hd0,2)
    kernel /boot/vmlinuz root=/dev/sda3 splash=silent
    initrd /boot/initrd.img

```
I then mount the root partition of the distro without grub, change to its /boot directory and then create symlinks for the kernel and initrd image e.g.
```
ln -s vmlinuz-<$SOMEVERSION> vmlinuz
ln -s initrd.<$SOMEVERSION>.img initrd.img

```
This means that when you upgrade your kernel on the distro without grub, you don't have to touch the grub config file on the distro with grub. What you simply need to do is delete the symlinks pointing to the vmlinuz and initrd image files and recreate them for the new kernel.

If you don't want to go through all that, you can simply install one grub to the MBR and the other to the root partition.

---

