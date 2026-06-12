---
title: "Problem installing bootloader with XFS"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by huberc on 2006-03-14
Hi,

First time installing Kubuntu. Everything went great until I hit the bootloader installation section.

I'm installing the latest version of Kubuntu for AMD64.
Here's my system:
Shuttle SN95G5
amd64 3500+
300gb hd dual booting with windows (30GB for windows, the rest for Kubuntu)

I wanted to use XFS since I will be using this for a Myth TV HTPC. 

The installer defaulted to LILO...but it won't install or the MBR or the ubuntu install partition. It gives me a error 1 message. So I tried GRUB and I get another error..this time it's a "fatal error" it tells me.

So now I'm stuck without a bootloader other than the windows one that's already installed:-k 

I've read there's some issue with debian and XFS, how do I get around this issue?

---

### Post by Roman27 on 2006-04-28
I know this is resurrecting and old thread, but I just ran across it.  The issue is documented and bug reports have been made.  Here's a link to one:

[https://launchpad.net/distros/ubuntu/+source/grub-installer/+bug/31719](https://launchpad.net/distros/ubuntu/+source/grub-installer/+bug/31719)

In the bug report, it describes that you can still install GRUB by> ...using 'chroot /target grub' and the below commands...:

grub> root (hd0,6)
grub> setup (hd0)...from a LiveCD.

---

### Post by jaclayton on 2006-05-18
Ran into a near-identical problem.

I'd been reading the merits of XFS and decided to re-install my home PC with a nice, shiny new Dapper-Drake Kubuntu.

All goes well until the error "We haven't installed a bootloader - or you haven't chosen to install one" (or words to that effect).

Searching around the forums shows that the version of GRUB currently in (K)Ubuntu isn't compatible with XFS, so the choice of installing a bootloader isn't even offered.  Thanks for the warning.

Long story short, started the re-install again, picked Ext3 for both hard drives and everything whizzed through.  I really wish I hadn't had to spend another half-hour or so enabling all the "restricted file formats" such as the unpopular mp3, DVD-playback and all the other things you can't really expect a computer to do "out of the box".  I understand the reasoning behind not including such support, and the wiki instructions are excellent, but that's one big stumbling block for newbies wanting to give Linux a go...

And these forums are an absolute godsend.  Thanks to everyone who's contributed and made (K)Ubuntu easier to use.

---

### Post by garretwp on 2006-05-21
Another thought is you can format the boot partition as ext3 and the rest of your file system as i.e. home and root etc as xfs.

Garrett

---

