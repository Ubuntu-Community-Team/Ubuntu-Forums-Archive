---
title: "Is the Sound Blaster X-Fi driver included with Jaunty?"
date: 2009-04-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by vade on 2009-04-15
Some months ago Creative released a GPLv2'd driver "XFiDrv" for the X-Fi line of sound cards. As far as I know it's the only X-Fi driver for Linux that works, at least for basic functionality. Does it come with Jaunty? If not, why not integrate this driver with Jaunty?

---

### Post by Reiger on 2009-04-15
Far as I know: no it doesn't ship with Jaunty. Altough there is/has been some experimental support for X-Fi cards in OSS, I think.

At any rate the XFi driver doesn't really seem to work out of the box: you have to check that your hardware revision number matches that in some .h file (and change the file accordingly if not)...

... Basically the driver was written for X-Fi cards of a couple of generations ago... ?

---

### Post by olskar on 2009-04-15
Check [http://ubuntuforums.org/showthread.php?t=1115910](http://ubuntuforums.org/showthread.php?t=1115910)

---

### Post by PGHammer on 2009-04-15
> **Reiger said:**
> Far as I know: no it doesn't ship with Jaunty. Altough there is/has been some experimental support for X-Fi cards in OSS, I think.

At any rate the XFi driver doesn't really seem to work out of the box: you have to check that your hardware revision number matches that in some .h file (and change the file accordingly if not)...

... Basically the driver was written for X-Fi cards of a couple of generations ago... ?

I think he may be referring to the newer 32/64-bit driver (which works a treat with Jaunty, actually; I'm using it); I had to download it from Creative myself, though.

The newer driver is for all PCI/PCIe versions of the XFi (except XtremeAudio).  I have the newer low-profile XtremeGamer in PCI.

---

### Post by vade on 2009-04-16
> **PGHammer said:**
> I think he may be referring to the newer 32/64-bit driver (which works a treat with Jaunty, actually; I'm using it); I had to download it from Creative myself, though.
Yeah this is what I meant. The driver's installation is complicated unless you're familiar with the command line and the configure/make/make install routine, so it would be nice for a lot of X-Fi users to have the driver included by default.

---

