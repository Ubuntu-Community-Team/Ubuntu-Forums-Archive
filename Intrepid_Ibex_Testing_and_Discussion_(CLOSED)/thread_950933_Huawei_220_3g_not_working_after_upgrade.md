---
title: "Huawei 220 3g not working after upgrade"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dextur on 2008-10-17
Installed Intrepid Ibex beta in order to get my 3g modem working with networkmanager. It worked great with the autoconfig for a week. After an upgrade last weekend it stopped working. I don't even get prompted for pin code when trying to connect since then.

Any ideas?

---

### Post by jerrylamos on 2008-10-17
What I've had to do when updating caused problems was to save any data I had done since install, and go back and install again.  Then don't do any updates!

If you really want to see if a new level works better, then download the latest daily build and run it CD Live to see if it works or if it has problems.  If it has some advantage and not too many problems, there's a way with Synaptic repositories to update from the CD Live however I've never tried it.

Jerry

---

### Post by dextur on 2008-10-18
Any tips on how to reset the configuration for NM and try to see what is going wrong?

---

### Post by NiklasV on 2008-10-24
Try disabling the PIN. I just configured an E220 under Ibex, and NetworkManager only worked once I had disabled the PIN. You can use an unlocked phone, or one locked to the same company that provides your internet service, to disable the PIN.

---

