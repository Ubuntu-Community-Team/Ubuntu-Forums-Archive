---
title: "Ubuntu desktop install Live cd"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by Qwarsdog on 2006-08-19
I am trying to install to a Dell Latitude and I can get as far as Uncompressing Linux... Ok, booting the kernel.

Nothing happens and it just hangs there. I've tried safe mode and using boot: napic but it still happens. No drives are spinning and the memtest passed as well. Any answers on this?

maybe a bios flash?

---

### Post by scxtt on 2006-08-19
could be a bad burn ...

---

### Post by Qwarsdog on 2006-08-19
nope I used this cd at work on a IBM thinkpad and it ran fine. Just cjhecked the bios and its at latest rev. I changed to system video and now using compatible mode for the processor and I get further and then this begins to dump across the scree.

Buffer I/O error on device hdc, Logical block 243518, 19, 20....

---

### Post by brim4brim on 2006-08-19
What model latitude.  I had to install a bios update from Dell for my ATI graphics card before I didn't get a black screen.  Mine was a D810 Latitude.

---

### Post by Qwarsdog on 2006-08-19
Its a Latitude Cpx p3 650 256 ram.

---

### Post by Qwarsdog on 2006-08-19
I think its the cdrom. Is there away to install from a HDisk location if I copy it to the drive?

---

### Post by Qwarsdog on 2006-08-19
FIGURED IT OUT WOOT!

under other boot options there is a listing in the bootstrap about using this parameter for certain Dell laptops Boot: live aic7xxx=no_Probe

Woot that was it so if you got a Dell Lattitude Cpx hit f6 and add Boot: live aic7xxx=no_Probe
and then install.

Thanks for assistance 

Now Im almost to the desktop and its hanging at the splash screen DOH!

---

### Post by Qwarsdog on 2006-08-19
Ok everything is good got installed and updated. Now I am gonna try and find a supported Wireless pcmcia card. I bought a Linksys 11g but its not supported. Anyone know of a good 11g supported card by ubunto?:confused:

---

### Post by K.Mandla on 2006-08-19
Who's your favorite vendor?

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Have fun!

---

### Post by Qwarsdog on 2006-08-20
Hey thanks! I think my card will work I seen someone using it with the NT driver. Gonna give it a shot.

---

