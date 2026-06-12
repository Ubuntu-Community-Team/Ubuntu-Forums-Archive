---
title: "Need Help for Alternative Way to Install Kubuntu"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by guyver on 2007-04-20
I originally posted this in the "Beginner Talk" category before I realized there was a category just for installation issues.  Sorry for the double post.

Okay here's my situation. I would like to install Kubuntu / Ubuntu on my GF's laptop except there's a catch. Her hot swappable CD-ROM drive does not work and her system does not support booting from a USB storage device.

What I'd like to do is somehow boot from a floppy which would either allow me to do one of two things:

1. Recognize a USB CD-ROM drive and allow me to do a regular install of Kubuntu (preferably) straight from the CD.

2. Autodetect her onboard ethernet from the boot floppy and from there I might get instructions to type some script commands to get installation underway via the ethernet.

For the life of me I do not know why she's even running Windows XP on this machine because it only has 128MB of RAM. I also realize I should be looking at Xubuntu for this laptop but she prefers the KDE environment.

If there are other options, I am receptive to this, but I am essentially a Linux newbie, so some of the more exotic ways of doing this may fly over my head.

Any help would be greatly appreciated.

---

### Post by Patrick K on 2007-04-21
Here is something I found (Google search on "grub floppy boot") that might help.
[http://www.openbg.net/sto/os/xml/grub.html#fs_floppy](http://www.openbg.net/sto/os/xml/grub.html#fs_floppy)

---

### Post by guyver on 2007-04-21
So basically, boot from this disc and I should be able to run the install from a USB CD drive?

---

### Post by Patrick K on 2007-04-21
I don't know, but maybe.

---

### Post by guyver on 2007-04-21
I just tried getting it now, but I cannot get the binaries.  I'll see if I can find a similar site.  One thing I want to do though is totally purge the contents of this laptop.  It will be a dedicated Linux computer, but I wil need to repartition the hard drive from NTFS to the ext3.  For some reason I get the impression from reading the text that this is a boot loader for someone with a pre-existing Linux install.

---

### Post by Patrick K on 2007-04-21
I think the section above that one is about doing this with no OS installed.

---

### Post by Sef on 2007-04-21
Do a [Minimal Install]("https://help.ubuntu.com/community/Installation/MinimalCD").  That's about 10 mb on a cd.

Read this for[ netboot install]("https://help.ubuntu.com/community/Installation/Netboot?highlight=%28net%29%7C%28install%29").

---

### Post by guyver on 2007-04-21
I tried it, but I didn't know how to kick it off... I did some more looking around and thought I found my answer, but everytime I install InstLux, it wants to reboot Windows.  When windows reboots, InstLux wants to uninstall itself.

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by guyver on 2007-04-21
Sef,

The laptop in question has a hotswappable CD-Drive that went bad.  My other option is using a USB CD-ROM drive, but the computer doesn't support booting from a USB storage device.

If I can maybe find a way to boot up via a floppy boot with network support or USB storage support, I think I'd be on a roll.

Am I missing something from your suggestion?

---

### Post by guyver on 2007-04-21
> **guyver said:**
> I tried it, but I didn't know how to kick it off... I did some more looking around and thought I found my answer, but everytime I install InstLux, it wants to reboot Windows.  When windows reboots, InstLux wants to uninstall itself.

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

After the automatic procedure failed miserably, I tried the manual process for netbooting, but it's always wanting to search for the image from the CD.

No luck.

---

