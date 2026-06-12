---
title: "Grub error 17"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by pascalhos on 2006-03-09
I just tried to install dapper flight 4 onto my work laptop. This is an HP nw8000. The internal hard drive contains windows2000 and I'm not supposed to touch that drive. So installing grub to the MBR of hda is out of the question.

The laptop has a removal drive onto which I have installed dapper. The layout of the disk is:

[LIST]
[*]hdc1: ntfs data partition
[*]hdc2: swap partition
[*]hdc3: reiderfs root partition
[/LIST]

Now, I chose to install grub to the root of this drive, so grub-install /dev/hdc and when choosing to boot from this disk in the bios I get the annoying grub error 17. The root partition is bootable and checking everything with the live cd shows that everything looks fine. I have reinstalled grub multiple times and it never works.

I though that perhaps booting from the second drive might make this drive /dev/hda instead of /dev/hdc, so I changed the appropriate entries in menu.lst and in /etc/fstab but that apparently was not he solution since I got the same error.

Has anyone seen this problem before and if so, what is the solution?

---

### Post by meborc on 2006-03-09
i know that [this page]("http://users.bigpond.net.au/hermanzone/p15.htm") contains a lot of info on grub and how to configure it... hope you are up to some reading :mrgreen: 

good luck

---

### Post by pascalhos on 2006-03-09
Thanks for the link. I had already read through that page. This does not solve my problem.

I found that error 17 means: 

> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

This I do not understand. When I boot up from the livecd or any rescue cd I can mount the partition no problem. Does this mean that grub does not have reiser support builtin?

---

### Post by pascalhos on 2006-03-09
I just flashed my bios to the latest version and all of the sudden it just works.

---

