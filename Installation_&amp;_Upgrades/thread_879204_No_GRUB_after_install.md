---
title: "No GRUB after install"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by TheHudson on 2008-08-03
I just installed Kubuntu 8.04 and everything went successfully, however after the installation GRUB does not show up on my primary disc. The thing is GRUB claimed to be installed successfully after install.

I have had XP installed on my primary drive (WD500 SATA) for a while (downgraded from vista for reasons), my IDE drives are on a PCI controller (Rocket IDE).

This has never been an issue before, however for some reason it refuses to install GRUB on my primary disc/partition. I have done this many times before with IDE + IDE controller ([k]ubu always on the latter).

I tried the default grub installation as with older builds and the main drive still doesn't recognize it.

Anyone else having this issue? Can anyone help?

---

### Post by tamoneya on 2008-08-03
not really sure what happened but in my opinion the easiest way to repair grub is with super grub.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by TheHudson on 2008-08-03
I get an address not found/page load error from that link :(

[Edit]: found another mirror, getting super_grub_disk_0.9726.iso and will give it a try.

Will post back with results, thanks man :)

---

### Post by TheHudson on 2008-08-03
Tried SGD and got error 17 on my kubu installs, selected WinXP and wouldn't boot (just hung).

Downloading the latest version (8.04.1) and will try again.

Status update after installation.

---

### Post by TheHudson on 2008-08-03
Same issues, gets error 17 about partition not found.

Ran SGD, no effect. Tried to reinstall GRUB via live CD through terminal, no effect.

Any other suggestions?

---

### Post by xen-uno on 2008-08-03
This is the best GRUB page I've found to date ...

[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by TheHudson on 2008-08-03
Worth a shot, i'll let you guys know how it goes!

---

### Post by zxscooby on 2008-08-03
Is grub installed on the wrong drive or partition?
Try selecting another drive as the initial boot device.

---

### Post by TheHudson on 2008-08-04
No, GRUB is installed on the correct drive/partition. I get the menu (on my main HDD), however trying to select Kubuntu/Kubuntu Safe/memtest86 gives me the 17 error.

hd0 is the primary drive, it has XP installed on it (as well as GRUB). I think it may have to do with me using an IDE controller card (PCI).

Although I never had this issue before on my other machines/servers using the same IDE controller.. from what I have looked up error 17 has been plaguing a number of people, both with and without (more of the latter) the IDE controller card.

[Edit]: Is this an 8.x.x issue? Should I downgrade and update through the O/S?

---

