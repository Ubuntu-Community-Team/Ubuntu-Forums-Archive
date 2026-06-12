---
title: "Attention Core 2 Duo users: using your PATA controller"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by simbaB on 2006-09-02
I'm sure anyone with a Core 2 Duo box is aware that a lot of PATA optical drives don't work with the Ubuntu and Debian installation discs. The conventional wisdom is to boot with 'all-generic-ide'. I have pinpointed why this doesn't work. Take a look at this code from drivers/ide/pci/generic.c:

```

#ifndef MODULE
static int __init ide_generic_all_on(char *unused)
{
        ide_generic_all = 1;
        printk(KERN_INFO "IDE generic will claim all unknown PCI IDE storage controllers.\n");
        return 1;
}
__setup("all-generic-ide", ide_generic_all_on);
#endif

```

Since debian-installer, and indeed Debian official kernel images (probably Ubuntu too), has the generic PCI IDE driver as a module, this option does nothing.

While this won't help you install, you can install by [other methods]("http://d-i.alioth.debian.org/manual/en.i386/apds03.html"). Knoppix-derived LiveCDs have worked consistently for me. Once you are up and running, you can:

[LIST]
[*]compile a custom kernel image that includes the PCI IDE generic driver in the bzImage.
[/LIST]

Also, I'm working on a [page]("http://www.oakcourt.dyndns.org/~andrew/wiki/index.php/DebianOnIntel965") chroncling my attempt at getting Debian unstable fully functioning on a Intel DG965RY Desktop Board. This is a Core 2 Duo processor board, so hopefully those of you with similar hardware (and a similar distribution) can find a useful tip or two there. I haven't updated the page yet, but I will shortly after I compile a custom kernel.

Let me know if this works for you.

**Update: ** adding the PATA PCI ID to generic.c didn't work for me.

---

### Post by bstock on 2006-09-27
So, have you gotten anywhere with this? I also have a DG965RY board with 2 SATA hard disks and an IDE DVD burner. I do have Ubuntu Edgy up and running, though it was a pain to do so. Here are the steps I took:

1) Downloaded the daily Edgy build (mine was as of 9-27-06).
2) Using another linux/unix box (my mac), I used dd to copy the iso file to my thumb drive.
3) Went into BIOS and changed IDE mode to AHCI. Unfortunately this breaks my already-installed Windows installation, so I'll either have to re-install or change this option each time I want to switch OS's. This was necessary to get Ubuntu to recognize my hard drives.
4) Booted from the CD to start the installation. I tried booting from the USB device but it didn't want to for some reason. Once the install came up and said it didn't find the cdrom, i specified /dev/sdc as a cdrom and the install went fine from there.

With Ubuntu up and running, pretty much everything is working with exception to my IDE device. Audio and Network came up no problems.

I was hoping the 2.6.17-10 kernel would add support for the PATA drives, but it appears it did not. 

So, have you gotten everything working on Ubuntu? I'm thinking I may just need to get a 2.6.18 kernel to get everything running...

Thanks for the help!

---

### Post by simbaB on 2006-09-27
A fix went into the generic IDE driver to allow modular builds to use the all-generic-ide option (I think before 2.6.18, but I'm not sure). Bug the Ubuntu kernel maintainers to backport it or upgrade their kernel sources. Without it, Ubuntu (or Debian) kernels will not work at all. They build the IDE generic driver as a module and the all-generic-ide option does not work then without the patch.

With regards to USB boot, there was a fix in recent BIOS release related to this. Try upgrading your BIOS.

---

### Post by computersolutions on 2006-10-15
Some notes on installing with Dapper or Edgy on Core 2 Duo board with PATA.

[http://www.ubuntuforums.org/showthread.php?t=277137](http://www.ubuntuforums.org/showthread.php?t=277137)

---

### Post by ColDebug on 2006-10-15
If you're going to the trouble to recompile the kernel you would be far better off using the generic 2.6.18.1 from kernel.org that has the PROPER JMB drivers built in. No monkey games with not being able to use the intel sata controller, no "generic" overhead.

I just wish they would get the i810 module fixed so I could use this intel on-board video i paid for and get that noisy nvidia card out of the box.

---

### Post by simbaB on 2006-10-16
The board I am referring to does not have a JMicron controller, but a Marvell one. There was an initial driver posted to LKML by Alan Cox not too long ago. 

As far as the "i810 module", I have no idea what you are talking about. There is no kernel module called "i810" anymore--the OSS sound driver is gone--I guess you mean the X11 driver. That has been working since release 1.6.5, at least the 2D parts. For 3D you need to fetch Mesa CVS and an updated libdrm, which still has a few unresolved issues, especially with some OpenGL compositing managers. Most everything else works for me however.

The closest thing to a kernel-land driver for Intel video is the DRM driver (called 'i915'), which *should* work in 2.6.18 for the new Core 2 Duo stuff. If not there is an out-of-tree tarball at intellinuxgraphics.org which has what you need.

---

### Post by takifugu on 2006-10-21
µ

---

