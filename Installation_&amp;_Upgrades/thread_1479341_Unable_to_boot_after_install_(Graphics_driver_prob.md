---
title: "Unable to boot after install (Graphics driver problem)"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by Rahu on 2010-05-10
Apparently my old laptop card has some issues with the nouveau driver that shipped with Ubuntu 10.04.

Whenever I started the live cd the screen just went green or purple and the whole computer froze. I was able to get to the installer by using the nomodeset option and successfully install it.

Now after the install I get that same graphics problem when I try to boot off the hard drive (even in recovery mode). I was going to use the live cd to change my xorg.conf to use vesa so I could at least boot, but xorg.conf doesn't seem to exist.

Anyone have some idea on what I could do to make this work? If I could get the HDD installation to boot exactly the same as the cd with nomodeset on that would be great, but I'm not certain how I would do that.

---

### Post by davidmohammed on 2010-05-10
whilst rebooting press shift to display the grub menu, then select one of the recovery options

when you boot into recovery try

sudo nano /etc/default/grub

edit the line to look something like

GRUB_CMDLINE_LINUX="nomodeset"

write out the file

run

sudo update-grub

reboot.

---

