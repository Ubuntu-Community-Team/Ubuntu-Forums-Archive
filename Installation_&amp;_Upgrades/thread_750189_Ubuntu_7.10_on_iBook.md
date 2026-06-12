---
title: "Ubuntu 7.10 on iBook"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by greensolutions on 2008-04-09
hello all,

ok so my mate left this country to go live in Greece, lucky get etc.and in his wake left me his old ibook G4 to fix.

the ibook itself looked as if it had been buried in sand and after dissasembly discovered that the hard drive was naffed, along with the optical drive. ( so no choice to boot from cd :( )

so my idea was to put the new hdd i bought into a different lappy (not a mac) clean install ubuntu on it and put it back in the mac.

unfortunatly i keep getting the finder/question mark folder icon on startup,

ive tried resetting the PMU, PRAM etc. but to no avail.

the only other thing i can think of now is to format the hdd, install mac osx on it on the other laptop and trying the hdd back in the mac.

please dont suggest i buy a new optical drive as i am ordering one on friday, but now i want to fix without it as this seems like a nice little challenge lol

any ideas would be greatly appreciated

thanks
x

---

### Post by Erin on 2008-04-09
Have I missed something? A G4 is a PPC based system. Another (non-Mac) will likely be an i386 system. You will need a PPC based system to install Ubuntu (PPC) onto or a full blown Mac. Using a x86 based Ubuntu will just end you up with the '?'.

Erin

---

### Post by greensolutions on 2008-04-09
> **Erin said:**
> Have I missed something? A G4 is a PPC based system. Another (non-Mac) will likely be an i386 system. You will need a PPC based system to install Ubuntu (PPC) onto or a full blown Mac. Using a x86 based Ubuntu will just end you up with the '?'.

Erin

unfortunatly yes it is a x86 based system, is there any way to install on this, and then use the hdd in the mac.  theyre aren't many macs round these ways lol. 

I know it's a bit of a big ask but theres no harm in hope :)

Thanks for the quick reply btw

---

### Post by dstew on 2008-04-09
See [This Document]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html"). Apparently, you can prepare a USB stick with a PowerPC install system on it, and boot it using the Open Firmware key combination cmd-opt-O-F at boot time. You can also install over a local network using tftp file transfer. The same document has information on that too.

---

### Post by greensolutions on 2008-04-09
excellent thanks a lot mate,

i will try when i get home from work, 15mins left yay.

---

