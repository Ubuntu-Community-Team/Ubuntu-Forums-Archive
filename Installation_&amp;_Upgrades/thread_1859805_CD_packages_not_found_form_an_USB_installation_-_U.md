---
title: "CD packages not found form an USB installation - Ubuntu 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by simongaiteiro on 2011-10-14
Hi @ll!!

I'm intensively trying to install the new Ubuntu 11.10 without success.

I have made a bootable USB stick of it. Everything seems to be ok but close to the end of the installation the program gives an error. Something like this:

*Apt configuration failed. Unable to locate CD packages...*

Again, the installation is being performed form an USB stick. So, no such CD...

I was googling it but I haven't found anybody wit this problem with 11.10 so far.

Nevertheless, I found a workaround to fix this matter in an Ubuntu 10.10 installation, if I recall correctly.

It was about copying filesystem.squashfs from the ISO to the USB stick. But it didn't work out.

The main problem now is that the installation program erased the Grub2. So, I'm not able to enter in other OS. :(

Any ideas of how to fix this?

---

### Post by brar on 2011-10-14
I am facing the same problem. I tried repairing grub2 using boot-repair. Although grub gets installed but while booting into Ubuntu I get the error something like "root not found on sda4".

---

### Post by jockyburns on 2011-10-14
I've just downloaded 11.10 and tried to create a usb startup disk (so I can boot from this to see if everything will run on my computer) when writing to the usb, I got an error message ,something like error reading from temp file ??? Now the usb stick doesn't do anything at all. inserting it into my computer, it doesn't show up on the desktop. Grrr (and to think I was going to upgrade from 11.04 glad I didn't) I'll stick with Natty for now until the bugs have been sorted out.

---

### Post by brar on 2011-10-14
I would recommend installing using cd. I finally decided to burn a cd and install from it and the installation was as painless as it can be :)

---

