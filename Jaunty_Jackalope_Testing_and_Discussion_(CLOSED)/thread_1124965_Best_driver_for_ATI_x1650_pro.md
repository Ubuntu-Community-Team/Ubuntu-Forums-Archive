---
title: "Best driver for ATI x1650 pro?"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sansa dude on 2009-04-13
ok im about to install 9.04 on my computer again after a video card failure. how can i install the right drivers for x1650 pro 512mb video RAM before when i upgraded from 8.10 i install ATI catalyst control center and it searched and dint find any ATI video cards. So which is the best stable driver for thus video card for 9.04?

---

### Post by ghstzr0 on 2009-04-14
Could you get X to start after installing 9.04 with X1650? I am unable to get X to start normally with either open source radeon drivers, or with the proprietary FGLRX drivers. It works with the VESA drivers, but I don't want to use them :(

If I have either of the first two drivers installed, X displays garbled colors when it should display GDM (login screen). The keyboard is unresponsive. I can tell, however, that my CPU is being used quite heavily while sitting at the login screen (via SSH-ing into that box and checking). Any ideas?

---

### Post by sansa dude on 2009-04-14
i had problems when i installed either the ATI Binary X.org Driver ( also which driver is this ATI or open source) or the ATI Catalyst Control Center. after installing one of those my display after reboot would show the last screen and i would get black and white lines all over it.  i want to get compiz working but i dont want to mess up my system again.

---

### Post by sansa dude on 2009-04-14
bump

---

### Post by krazyd on 2009-04-14
When you first install 9.04, your card should work completely without you having do do anything (the open source driver is included with Ubuntu). Don't install fglrx (the binary ATI driver) because it no longer supports your card. 

If your card doesn't work "out-of-the-box", please file a bug on launchpad.

---

### Post by Woody1987 on 2009-04-14
the radeonhd drivers should work fine. They have both 2d and 3d acceleration on your generation of card. Run:

sudo apt-get install xserver-xorg-video-radeonhd

then restart X by logging out and back in. You should then be in business.

---

