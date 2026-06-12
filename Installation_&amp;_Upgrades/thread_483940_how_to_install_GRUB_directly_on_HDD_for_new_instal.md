---
title: "how to install GRUB directly on HDD for new install"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by jake_the_quake on 2007-06-25
Hi, 

I'm hoping that someone can help me sort out a really annoying issue I have with installing ubuntu on my old Sony VAIO PCG-505FX (96Mb Ram, PII 233, 12Gb HDD)

In a nutshell, the vaio doesn't have an onboard CD-Rom, though I do have a PCMCIA CD-Rom, which works, but for some reason I can't install ubuntu from CD; I always get a corrupt data message on initial install.  It does have 1 usb port, but the bios doesn't support booting directly from USB (and never will - there are NO bios updates for this laptop).  I don't have a floppy drive either btw.

I have attempted to use the hd-media install and got most of the way there, but the laptop locked up on language-pack-en-base (and I *mean* locked up - like over 12 hours worth of locked up before I finally switched it off).

My install method was as follows:

partition HDD to give me a 1gb partition that i dump the ubuntu iso, init.gz and vmlinuz that I've downloaded from the hd-media mirror.

start to install win2000 on the other partition; stop it after the first reboot when it's written to the MBR and installed NTLDR.

boot from a BartPE disk and drop my GRLDR & menu.lst in the root of c:, then manually hack the boot.ini to add a c:\grldr="Install Ubuntu", my menu.lst is as follows:

color black/cyan yellow/cyan
timeout 30
default /default

title Install Ubuntu
root (hd0,1)
kernel /boot/vmlinuz
initrd /boot/initrd.gz

so it boots from the new partition, recognises the iso and carries on the install.  Problem is, I keep reading diff things about which flavour of ubuntu to use for low-memory systems, and therefore the iso I use keeps changing.  What I would like to do is as follows:

install GRUB directly on HDD without having to use a 2000 install to make the drive bootable first.

use menu.lst to point to my 1gb USB drive (sd0,0 ?) to look for init.gz & vmlinz and iso so that I can chop & change the iso I use without having to keep reformatting the HDD

install ubuntu without the CD by pulling the data from the USB drive, which keeps my one pcmcia slot open for a NIC instead.

so, how do I:

a. manually make the drive bootable and install GRUB on the drive with my amended menu.lst ?
b. point to my usb drive with menu.lst - is it just (sd0,0) ?

Believe me, I have spent literally days googling this and searching the forums, but no one seems to asked this exact question before.

thanks for any info whatsoever

jake

---

### Post by Shazaam on 2007-06-25
Can you network it with your main pc?

---

### Post by jake_the_quake on 2007-06-25
probably, but to what end ?  I can plug it directly into my router to get internet access if need be.

sorry to be picky, but that's not really addressing the problem as stated.

jake

---

### Post by Pumalite on 2007-06-25
But is simpler.

---

### Post by Shazaam on 2007-06-25
Sorry senior moment here. :D
What I have done is put an old Compaq laptop hard drive (500mb) in a usb enclosure; plugged the enclosure into the desktop pc's usb port and installed from there. BUT, Ubuntu Desktop was too much for the laptop so I went with damnsmalllinux instead.

---

### Post by Pumalite on 2007-06-25
If 250MB memory or less, you could also go for the 'Alternate Xubuntu CD'.

---

### Post by jake_the_quake on 2007-06-25
+++FRANTICALLY SCRABBLING TO GET BACK ON TRACK+++

Thanks for all the suggestions so far, I don't wish to sound ungrateful, but I know ALL about the alternate xubuntu iso, and even doing a base install of ubuntu server and then just installing fluxbox or icewm to keep requirements down.

the problem I have is this:

TO ALL INTENTS AND PURPOSES, THE CD DOES NOT WORK (at least as far as ubuntu, xubuntu, kubuntu etc is concerned)

I have 1 (one) pcmcia slot only, so I can have a CD (that doesn't work) OR a NIC, NOT BOTH. Because of this I can't boot into a minimal shell from CD and then do a network install.  If I'm missing a trick here, please let me know, rather than just say *'can you network it to your other PC*', or *'But it's easier*' - if I knew why it was easier I'd be doing it.

I think the only solution, and I may well be wrong in this, is to make the HDD bootable and have a GRUB option that allows me to install straight off USB.  This is NOT the same as booting off USB as the laptop will never support that.  If what I'm asking for is impossible, then fine, good,  at least I know.  If someone can tell me exactly how I can boot from a freshly formatted HDD and then do a network install of ubuntu server, then please tell me, in detail - preferably with pictures :)

jake

---

