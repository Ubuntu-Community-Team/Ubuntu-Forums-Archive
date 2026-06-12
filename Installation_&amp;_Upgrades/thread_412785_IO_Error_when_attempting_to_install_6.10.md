---
title: "I/O Error when attempting to install 6.10"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by NuttBoxer on 2007-04-18
I'm trying to install 6.10 on a Dell Optiplex GX1(extremely old computer).  I get an error that looks something like this "[126.616857] Buffer I/O error cannot reach hdc, logical block 1".  This error repeats for numerous lines over several minutes, with the numbers changing for each line.  When it stops attempting the install it tells me that the "tty" cannot be reached.  The hard drive control is a National PC87309.  I have tried all the hardware configurations I can think of with no success.  Is there a way around this error?

---

### Post by aidanr on 2007-04-18
boot up the live cd and select "check cd for defects" (or something similar to that), if it finds any errors, download the iso again and burn it again

i got the same problem yesterday installing feisty, it was just a bad burn

---

### Post by NuttBoxer on 2007-04-18
I selected the check disk for error option, and it did the same thing as if it was going to install(Ubuntu logo screen with loading bar), and I got the same error.  Would that still be considered a bad burn?

---

### Post by aidanr on 2007-04-18
possibly, in any case i think redownloading the iso, checking the md5sums and make sure your burning app checks the disc after burning it (brasero's option is check disc integrity, nero's is verify data on disc, etc) and burning at a lower speed and maybe even making a couple of discs using different computers/burning software, would be the first thing to do before troubleshooting hardware

---

### Post by NuttBoxer on 2007-04-19
Did a fresh burn, checked the the burn to make sure it was good.  Still getting the same I/O error with my hdc device(hard drive control).

---

### Post by NuttBoxer on 2007-05-24
This error was related to having an old CDRom that couldn't read the ISO fast enough.  Hope this will be helpful to someone else.  Thanks for the help.

---

