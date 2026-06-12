---
title: "install 10.04LTS mount problem"
date: 2011-08-22
forum: Installation &amp; Upgrades
---

### Post by ddavidddd on 2011-08-22
I am trying to install 10.04LTS as a complete replacement for an older Ubuntu on a Fujitsu computer.
The last time I installed it, it required the option "noapic" to boot.
The install went through but would not start from the new installation, the grub menu appeared but then only a blinking dash.
My attempts to add noapic manually failed.
I then successfully started from the CD with the manual addition of the option noapic.
I edited /etc/default/grub by replacing "quiet splash" with "noapic" in the line:
GRUB-CMDLINE-LINUX-DEFAULT-"noapic"
and did: sudo update-grub
which brought the error:
/usr/sbin/grub-probe: error: canot find a device for / (is /dev mounted?)
The command mount gave info including the line:
none on /dev type devpts (rw,noexec,nosuid,gid=5,mode=0620)
The computer on which I am writing this, a successful installation of 10.04, has the line:
/dev/sda9 on / type ext4 (rw,errors=remount-ro)
As the new computer also has the installation on sda9, I did:
mount /dev/sda9 on / type ext4 (rw,errors=remount-ro)
which brought the error:
bash: syntax error near unexpected token '('

Can anyone help, please?:(

---

### Post by ddavidddd on 2011-08-22
I installed it again, I made absolutely certain that the intended system partition sda9 was to be formatted and mounted as /, but the result was the same.
I started from the CD with option noapic and succeeded in mounting the partition with the result as shown by simple command mount:
/dev/sda9 on /  type ext4 (rw)
I don't know how to get the options into it.

I then edited /etc/default/grub to introduce noapic and then did:
sudo update-grub
but it still brings the same error:
usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)

The successful installation has no mount entry for /dev, only /dev/sda9 and /dev/sda7

These steps (noapic, grub update) are the same which led to success with the old installation on the same computer (after a very long time trying)

HHEELLPP

---

### Post by ddavidddd on 2011-08-22
mount also shows the line:
aufs on / type aufs (rw)
should I try to delete it?

is that correct? This entry is not present on my working installation.
The working installation does, however, have the entry 
none on /dev type devtempfs (rw,mode=0755)

---

### Post by ddavidddd on 2011-08-22
I wanted to give up and install 11.04 instead (I would actually prefer the LTS version because you don't have this completely wasted day for another 3 yers) , but that does not work either.

Whether I try to start the CD or install, the blinking dash goes small and that. I have learnt, is the sign that nothing further is gong to happen.

Can anyone help, please?:(

---

### Post by ddavidddd on 2011-08-22
It did eventually bring an error message:

Busybox ...

(initramfs) Unable to find a medium containing a live file system

---

### Post by ddavidddd on 2011-08-22
I have wasted all day here.
My wife needs to be able to work.
She had a working computer yesterday but it is gone now.
Is there really nnone out there who can help?
I think I will have to buy her a Windows computer

---

### Post by ddavidddd on 2011-08-22
On going for a restart after installing yet again, it fils the screen with 

....end_request. I/O error, dev sr0, sector ......

---

### Post by ddavidddd on 2011-08-22
Is anyone out there?
Any suggestions?

---

### Post by jjpcexpert on 2011-08-22
ddavidddd, you are in a desperate situation.
Try re-burning the ISO to a CD or DVD that is blank or rewritable.
Try FreeBSD.
Other than that and try Debian, I cannot suggest anything else.

I am very sorry I couldn't help you more.

All the best and a :KS to you, From, Jack J.

---

### Post by YesWeCan on 2011-08-22
> **ddavidddd said:**
> Is anyone out there?
Any suggestions?
Hi there. Would you boot live CD, download and run [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post the RESULTS.TXT here inside code tags (highlight anf clikc #)?

---

### Post by ddavidddd on 2011-08-23
Thanks very much for the suggestions!

I am currently trying to install 9.10 with the intention of then doing an online upgrade.
I did this with my computer and it sort-of worked although there were some funny problems (Unity desktop, window manager disappeared, network manager disables network after standby) and some manual repair necessary.

If I succeed in installing again and have boot problems, I will do the boot info script.

---

### Post by ddavidddd on 2011-08-23
I think I found the problem!!!
I will give the steps as the forum seems to be full of desperate cries for help

The computer is a Fujitsu Esprimo P2550 with 2 Pentium E5300 2.60 Ghz
and nVidia graphics.
As I already knew, it needs the option "noapic" in order to install, start the live CD or boot.
My mistake was simply to introduce the option "noapic" at the wrong place in the grub menu.

Steps:
Install. At the first screen, press F6 for options and tick the option "noapic"
Installation runs. Reboot. Grub menu appears. Press e for edit, add noapic at the end of the entry (two lines) thus:
linux /boot/vmlinuz....bla bla...quiet splash noapic
Press ctrl X to boot
Boots successfully! Hardware drivers - activate nvidia drivers.

To introduce the option "noapic" permanently:
Command: sudo nautilus
Navigate to and edit /etc/default/grub by changing "quiet splash" to "noapic", save
Command: sudo update-grub

This has successfully installed 9.10 and it is now doing the online update, but the method would probably also work to install the latest Ubuntu directly.

---

