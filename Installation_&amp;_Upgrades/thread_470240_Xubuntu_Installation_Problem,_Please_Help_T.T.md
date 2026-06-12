---
title: "Xubuntu Installation Problem, Please Help T.T"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by RayjinBlitz on 2007-06-10
Hello all.

I am currently having a problem with installation of Xubuntu on one of my dekstops, and since I am a Windows user, I don't know much of the Linux OS. In other words, I'm completely new to Linux itself.

My desktop is a eMachine eTower 500 model with Intel Celeron processor, 128MB RAM, ATI 3D Rage Pro video card, 40x CDROM, 4.3 GB HD, and 1.5 MHz. The OS used before attempted Xubuntu installation is Windows ME.

I downloaded the Xubuntu 7.04 ISO off the Xubuntu site and burned the ISO with Active ISO Burner.

Afterwards I booted the Xubuntu CD. The kernal would load, and an error would pop up saying "ACPI: Unable to locate RSDP". The Xubuntu loading screen appears, and after a minute or two these phrases would appear repeatedly with different number prefixes:

hdc: error code: 0x20 sense_key: 0x05 asc: 0x64 ascq: 0x00
Buffer I/O error on device hdc, logical block (0 or 1 or 2)

After many of these looped messages this appears:

BusyBox v1.1.3(Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help for a list of built-in commands

/bin/sh: can't access tty; job control turned off
initramfs) __

Currently this appears whenever I choose "Start or Install Xubuntu, "Start Xubuntu in Safe Graphics Mode", Install with Driver Update CD", Check CD for defects", and "Boot from First Hard Disk".

I've used the Memory Test utility and it's passed thrice over.

I ask for help with how to fix these errors, and thank you in advance.

---

### Post by confused57 on 2007-06-11
With 128 Mb ram, you definitely need to use the alternate install cd...to be sure the downloaded iso is complete, you need to do a md5sum...burn the iso at a low speed(8x or less).

This is link has the procedure for doing a md5sum check on an iso:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

You might also need to use boot options:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by RayjinBlitz on 2007-06-11
> **confused57 said:**
> With 128 Mb ram, you definitely need to use the alternate install cd...to be sure the downloaded iso is complete, you need to do a md5sum...burn the iso at a low speed(8x or less).

This is link has the procedure for doing a md5sum check on an iso:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

You might also need to use boot options:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Aha, I thank you for your advice =] I will test this out ASAP

---

