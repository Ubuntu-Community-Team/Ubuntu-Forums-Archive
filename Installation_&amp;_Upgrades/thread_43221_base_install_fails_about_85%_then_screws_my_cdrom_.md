---
title: "base install fails about 85% then screws my cdrom till hard boot"
date: 2005-06-21
forum: Installation &amp; Upgrades
---

### Post by motstudios on 2005-06-21
greetings,

i tried to install ubuntu using the shipit cd's. i tried 4 of them and they all failed at the same point of install, about 85% through the base install.

i decided to try an install with "nodma" option as my cd-rw sometimes has problems with DMA. still failed at about 85% of the base install. the error said no installable kernel found.

ok if that wasnt enough, i went to reboot into my other linux and found that my cd-rw drive now wont read any CD's at all! after a hard boot it worked again. to me this is a big problem becayse no other linux distro install cd has given me probs except mandrake (it gave some odd error and wouldnt even boot).

ive noticed a lot of people seem to be having simular problems with this, so why hasnt there been any solutions, ideas, troubleshooting, workaround, alternate ways of install, etc?

i didnt notice anyway to install via mounted directory or mounted partition. im connected to the net with a 'windows only' wireless pci card that requires ndiswrapper (ha take that M$) so i cant install via network... so im stuck.

i guess back to slackware for me till this is resolved.

---

### Post by derrick1985 on 2005-06-21
Did you try to download the .iso image, burn it yourself and try that?

I know I have had problems too with the ShipIT cd's.

---

### Post by motstudios on 2005-06-22
ive thought about downloading the ISO and burning it but i have no blank CD's to burn it to and wont be able to get any for some time. plus my cd-burner usually doesnt wanna burn CD's without a few retries (hence why im always running short on CD's) and i cant afford a new one right now (also why i chose to try the shipit)

---

### Post by eskaypey on 2005-06-22
[QUOTE=motstudios]ive thought about downloading the ISO and burning it but i have no blank CD's to burn it to and wont be able to get any for some time. plus my cd-burner usually doesnt wanna burn CD's without a few retries (hence why im always running short on CD's) and i cant afford a new one right now (also why i chose to try the shipit)[/QUOTE]
 You've got a choice between net and floppy install. Information on those could be found in ubuntu wiki pages.

---

### Post by motstudios on 2005-06-24
well i guess its back to my modded slackware till this little prob is fixed.

---

### Post by fuit_ilium on 2005-08-12
This was a bug under Warty Warthog too, it seems. Somebody suggested that the CD-ROM drive stopped spinning after awhile during the unpacking/config process, and suggested changing your hardware setup to HD-master CD-slave on the same channel. I tried this and it didn't work. However, I tried a weird workaround: open up your box and take out the CDROM. At a point during the install pretty soon before you've been hanging, unplug the power from the CDROM and then plug it back in. Maybe even eject the CD and reinsert it. It's like voodoo, but it worked for me, and got me past the "no installable kernel" redscreen.

---

### Post by fuit_ilium on 2005-08-12
PS I was using an old box:

HP Pavilion 6535 w/ HP CD-Writer Plus
Celeron 466
Samsung 8.5 GB HD
64 mb RAM

HD-master, CD-slave on same channel.

---

