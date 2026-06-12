---
title: "Booting Kubuntu from an external USB drive using a floppy with no USB BIOS support"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by Crusader370 on 2008-05-31
Hi all,

I have an installation of Kubuntu on my 500Gb USB drive. I made it using a Kubuntu 7.10 liveCD. However, my CDROM does not read any burnt CDs and my BIOS does not support USB booting. I would also like to not use my internal hard disk at all, as it's a laptop and I want to make sure it works if my hard disk fails.

So, I am thinking that I should create a bootable floppy, load USB drivers, and somehow boot Kubuntu from the USB hard drive.

Can anyone provide some instructions how to do this? I found a lot of info scattered around the forums but none of it that I found does the exact thing that I need.

Thank you,

Crusader

---

### Post by logos34 on 2008-05-31
[QUOTE]> **Crusader370 said:**
> So, I am thinking that I should create a bootable floppy, load USB drivers, and somehow boot Kubuntu from the USB hard drive.

I think your only solution is to put a /boot partition on the internal drive.   Doesn't have to be large--maybe ~50 MB.  Then copy contents of external /boot to it, and install grub to the mbr of the internal drive, pointing to the separate /boot instead of ubuntu / on the external.

---

### Post by MQMike on 2008-05-31
Maybe a long shot -- he builds a bootable CD that boots the USB, but you may find some principles that transfer to floppy (in fact, he may address that, I can't recall):

If your BIOS does not support booting from USB:
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by logos34 on 2008-05-31
> **MQMike said:**
> Maybe a long shot -- he builds a bootable CD that boots the USB, but you may find some principles that transfer to floppy (in fact, he may address that, I can't recall):

If your BIOS does not support booting from USB:
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

Yes, that's the very link I had in mind...I've often recommended it.  

I was thinking more of the boot kernel from hard disk approach outlined therein, but the CD would work just as well too.  Except with the CD is harder to update--you basically have to redo it. 

It's just that I think your fear, crusader, of messing up windows boot on the hard drive is misplaced--a grub partition will not (at least should not) disturb windows installation or prevent you from booting into it (unless you have vista which it doesn't sound like you do).  There's always Super Grub Disk or restoring the windows bootloader using the XP install CD in the unlikely event grub doesn't want to boot windows. 

You could even chainload linux [from XP bootloader]("http://users.bigpond.net.au/hermanzone/p9.html") (point it to separate /boot).

I'm not trying to sell you on hard disk route, simply pointing out it isn't as problematic as you imagine.

---

