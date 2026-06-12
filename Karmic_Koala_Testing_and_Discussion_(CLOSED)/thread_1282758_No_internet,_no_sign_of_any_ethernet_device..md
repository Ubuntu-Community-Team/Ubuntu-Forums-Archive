---
title: "No internet, no sign of any ethernet device."
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rsheridan6 on 2009-10-04
I have a new installation of Karmic Alpha 5 in which there is no internet connection.  The motherboard is a GIGABYTE GA-EG43M-S2H LGA 775 Intel G43 (copied from the product page at newegg where I got it) with onboard ethernet - Realtek 8111C according to newegg.  But I can't find any sign of it.  lspci shows no ethernet device.  ifconfig shows "lo" but that's all - no "eth0" or anything else.  dmesg | grep -i eth shows nothing.  The machine is hooked up to a live ethernet wire which is known to be good, but the motherboard itself has never been used, so it could be defective.

I wouldn't normally install an alpha, but I couldn't get the installation of Jaunty to work when I tried it several months ago, and I didn't touch it for a long time after that.  Karmic has a new USB drive installer that works (unfortunately, this means

Anyway, I was under the impression that lspci should show a device whether there's a driver problem or not.  Does the lack of anything under lspci mean that I have non-working hardware?

---

### Post by forumache on 2009-10-05
check if the light blinks on your ethernet card

---

### Post by rsheridan6 on 2009-10-05
It does blink when the ethernet cable is plugged in.

---

### Post by ElSlunko on 2009-10-05
Are you dual booting with W7 by any chance? I had the RC version and there was a feature that put my NIC card to sleep and it sometimes wouldn't wake up.

---

### Post by rsheridan6 on 2009-10-06
No, I'm windows-free here.

---

### Post by forumache on 2009-10-06
maybe you can try with ubuntu beta LiveCD? It is one month more advanced than Alpha 5. Maybe you are lucky.

---

