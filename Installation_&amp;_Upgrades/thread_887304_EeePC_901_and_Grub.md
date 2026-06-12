---
title: "EeePC 901 and Grub"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-08-12
I got Ubuntu 8.04.1 installed on the SD card. It runs!

However, there is a small thing what I don't understand / need to change.

The installed Ubuntu is on a removable SD card. If I remove it and boot, then I get an error, while if I have the card inserted I can boot either Xandros toy or Ubuntu.

Grub shows hereby:
> Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, memtest86+
Other operating systems:
Normal Boot (on /dev/sda1)
Perform Disk Scan (on /dev/sda1)
Restore Factory Settings (on /dev/sda1)

What means Restore Factory Settings (on /dev/sda1)?

I thought / hoped, that GRUB will be installed on the /dev/sdc, but above shows that GRUB is installed on /dev/sda. Booting from /dev/sdc should show me GRUB, but it does also without the SD card.

This gives me the "advantage" that even Xandros is now protected by removing the SD card, but that is not really I was looking for (yet).

However, I also would like to (have to) install on another SD card Windows XP. I can live with GRUB on /dev/sda, but I think it would be better if there would be a way to say:
"If there is a /dev/sdc inserted and it is Ubuntu, show this option for booting, otherwise move on in the list of OSes". I think we could then also get another statement in, saying:
"If there is a /dev/sdc inserted and it is Windows XP, show this option for bootint, otherwise move on in the list of OSes".

Is that possible?
Any suggestions, hints, concerns?

bye

R.

---

### Post by ELMIT on 2008-08-30
Has anybody an idea?

bye

R.

---

