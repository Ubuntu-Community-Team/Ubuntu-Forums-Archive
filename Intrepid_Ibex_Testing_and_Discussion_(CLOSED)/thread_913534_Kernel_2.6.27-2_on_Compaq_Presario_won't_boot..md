---
title: "Kernel 2.6.27-2 on Compaq Presario won't boot."
date: 2008-09-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2008-09-07
Alpha 5 CD Live hangs a few seconds after boot.  
See [https://bugs.launchpad.net/ubuntu/+bug/265049](https://bugs.launchpad.net/ubuntu/+bug/265049)
for description.  Last line on screen is:
pci 0000:00:00.0: MSI quirk detected; MSI disabled.
I don't have a clue what MSI or MSI quirk is.

So I installed Alpha 4 with kernel 2.6.26-5, updated all the packages to Alpha 5 level, including kernel 2.6.27-2 package.  

Booting with 2.6.27-2 the following line prints:
Starting up ...

then nothing.  No keyboard, no mouse, no display.  The install will boot with kernel 2.6.26-5 however I have to use the recovery start and XFIX 
every time.

From dual boot on another partition browsing the Alpha 5 partition, I can't find any files or logs or reports or messages that Kernel 2.6.27-2 posted.

By the way, that same CD with kernel 2.6.27-2 runs and installs O.K. on my IBM Thinkpad R31 .... while Alpha 4 won't ...

Any clue on the Compaq Presario kernel 2.6.27-2 situation?

Thanks, Jerry

---

### Post by Ayuthia on 2008-09-07
> **jerrylamos said:**
> Alpha 5 CD Live hangs a few seconds after boot.  
See [https://bugs.launchpad.net/ubuntu/+bug/265049](https://bugs.launchpad.net/ubuntu/+bug/265049)
for description.  Last line on screen is:
pci 0000:00:00.0: MSI quirk detected; MSI disabled.
I don't have a clue what MSI or MSI quirk is.

So I installed Alpha 4 with kernel 2.6.26-5, updated all the packages to Alpha 5 level, including kernel 2.6.27-2 package.  

Booting with 2.6.27-2 the following line prints:
Starting up ...

then nothing.  No keyboard, no mouse, no display.  The install will boot with kernel 2.6.26-5 however I have to use the recovery start and XFIX 
every time.

From dual boot on another partition browsing the Alpha 5 partition, I can't find any files or logs or reports or messages that Kernel 2.6.27-2 posted.

By the way, that same CD with kernel 2.6.27-2 runs and installs O.K. on my IBM Thinkpad R31 .... while Alpha 4 won't ...

Any clue on the Compaq Presario kernel 2.6.27-2 situation?

Thanks, Jerry

Are you using the 64-bit version with an AMD chip?  If so, you might try using noapictimer in the boot parameters.

---

### Post by cantas on 2008-09-07
It actually doesn't hang. if you press any button during boot, you help the kernel booting. it's a bios issue i heard. keep pressing buttons until you boot.

---

### Post by jerrylamos on 2008-09-07
> **Ayuthia said:**
> Are you using the 64-bit version with an AMD chip?  If so, you might try using noapictimer in the boot parameters.

This Compaq Presario is a 3.3 gHz Intel Celeron 32 bit.

I tried kernel 2.6.27-2 recovery mode.  It gets the same MSI quirk detected, MSI disabled line that CD Live gets.  I could find no logs or messages posted for the time of the failed boot.

Jerry

---

