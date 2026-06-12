---
title: "Can't configure network, and Kernel not found?"
date: 2004-11-03
forum: Installation &amp; Upgrades
---

### Post by francis on 2004-11-03
During installation, the NIC cannot be found so no network configured. It is a 3COM
(3c905b)  internal on the motherboard.  I tried all the netcard choices with no luck.
Also as I continue the installation, it stops at 82% with the statement "No installable
kernel was found in the defined APT sources. Current default package is 'linux-386'. You may try to continue, though this strange error is probably fatal."  Then it  starts
over with the base install.  The CD-ROM integrity check is OK. The computer is a Dell
450 mhz PIII. It runs the network ok with Debian, Slackware, YOPER, Knoppix, MEPIS, Lindows, Libranet, Puppy, Feather,  and even FreeBSD.
Need some advice! Thanks.

---

### Post by Mighty Mik on 2004-11-04
The 'no installable kernel' is a known bug.

---

### Post by francis on 2004-11-04
Thanks  Mighty Mik.  Do you have a reference for the bug ?
Wish  I had known this before I ordered the CD from a dealer.

Guess I'll wait  six months and try again, because it seems to be a pretty
nice  distro.  I requested a CD from Ubuntu, but have not received it .
Hopefully that  'no installable kernel bug' will have been corrected when I
finally get it in the mail.  Still need a solution to the network card configuration,
however.

---

### Post by Mighty Mik on 2004-11-04
Try bug#3196, and see if that looks familiar. Oooo look, i'm posting from Ubuntu! Getting here was not easy, however, in fact...i was able to get here from a busted Sarge install. Sarge was installing well last week, but something changed. I was able to install a kernel, x-window-system, and gnome from the command line i wound up with, but if it's not detecting your card, that's not helpful. Network cards are cheap anymore...if you have a few bucks, maybe you can find a newer card to swap in and see if that helps. My mobo has 2 different NIC chipsets on it, and i didn't have problems with either.

[QUOTE=francis]Thanks  Mighty Mik.  Do you have a reference for the bug ?
Wish  I had known this before I ordered the CD from a dealer.

Guess I'll wait  six months and try again, because it seems to be a pretty
nice  distro.  I requested a CD from Ubuntu, but have not received it .
Hopefully that  'no installable kernel bug' will have been corrected when I
finally get it in the mail.  Still need a solution to the network card configuration,
however.[/QUOTE]

---

