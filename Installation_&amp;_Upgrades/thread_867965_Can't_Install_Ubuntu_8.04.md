---
title: "Can't Install Ubuntu 8.04"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by fedra88 on 2008-07-23
When i added an nVidia graphic card to my pc, Ubuntu did't recognized it. so i tried to reinstall the system (keeping the /home partition, obviously), but the install process always freezes at 22% (6% using alternate cds). i experienced this issue with Ubuntu, UbuntuStudio, and even LinuxMint -latest versions- and nothing changes. same crash at the same points.

mind that:
- it's the whole pc that freezes, cursor does not move, and even Ctrl+ALT+CANC does not work
- restoring grub and booting from windows xp partition... well, everything works fine, and windows recognizes the new graphic card. (hard to admit :( )
- i formatted and checked root partition several times, so i think it's pretty safe


well... what should i do?
if any developers know exactly what the installation process do in that moment, it could help...

thanks

---

### Post by dislocated on 2008-07-24
It might help to know exactly which graphic card you installed.

You might also want to take a read here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) and see if the video options don't help.

---

### Post by fedra88 on 2008-07-25
It's an nVidia GeForce FX 5200 (128 MB RAM).
by the way, i unplugged that card and nothing changed.
Usually there are no matters with the booting process (only a couple of times resolution was VGA only): the matter is that the installation process TOTALLY FREEZES my pc during the file copying, always at the same point, and my hard disk (apparently) has not fault - same issue installing ubuntu in different partitions.

maybe i should throw that 6-year-old iron box out of my window...

---

### Post by jimv on 2008-07-25
For some reason my laptop froze up during install whenever I used a CD.  Installing from a USB thumbdrive, on the other hand, worked fine.

[http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html](http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html)

---

### Post by fedra88 on 2008-08-04
Altough my BIOS seems to allow it, there is no way to boot from an USB drive.

meanwhile:

- ubuntu 8.04 live cds don't work properly anymore (max resolution is always vga)
- i can't even install good old win xp, the cd doesn't boot anymore.

any hopes?

---

### Post by bichon101 on 2008-08-04
I have exactly the same problem with the same card, even with safe graphics it freezes or the video is scrambled, may have to go back to vista!!!!!

---

### Post by fedra88 on 2008-08-05
please,
everything but vista.

---

### Post by Greenmutt24 on 2008-08-06
I'm having the same problem anyone have any ideas?

---

### Post by BiscuitTin on 2008-08-06
Don't know if its the same issue but, I had a similar problem trying to install onto my Sony VGX-TP1E Media Centre. I would get past the keyboard, network, partitioning options and Ubuntu logo and then screen would just go blank and the installation stopped. Nothing responded except power off. I tried using the 'safe' VGA mode but got the same result.

The alternative install CD at least allowed me to complete the file copy, however on re-boot, again I got the Ubuntu logo and then ... nothing!

I found however, that I could boot and go into recovery mode. From there, I could configure Xorg manually, using the information I found here:

[http://www.freebsd.org/doc/en/books/handbook/x-config.html](http://www.freebsd.org/doc/en/books/handbook/x-config.html)

I created a xorg.conf.new file as described. Running this failed initially, but subsequently adding my monitor resolution modes did the trick.

It would seem then that the installer does not correctly detect my dispay modes and as a result does not configure the X server properly.

---

### Post by fedra88 on 2008-08-08
i'm not sure it's only an x configuration issue, it seems to be more an hardware failure :(
anyway, i can't copy files at all. i described in the first post the exact points where file copying stops - they're always the same.

---

