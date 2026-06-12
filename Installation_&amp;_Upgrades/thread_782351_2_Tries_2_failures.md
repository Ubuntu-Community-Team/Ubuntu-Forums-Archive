---
title: "2 Tries 2 failures"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by grndragon57 on 2008-05-04
First, I tried a fresh install from the live Cd on a Dell Dimension 4550 the live CD ran fine, the install went fine. When I booted into Ubuntu it loaded with some really low graphics settings. I D/L the nVidia drivers through Synaptic with no improvement. Then I tried the legacy driver with the same maximum resolution 400something. I ended up reinstalling 7.10 and all is well. I assume the problem is with the old nVidia 4 MX series card, but I don't understand why it ran at 1024 x 768 on the Live CD.

The other computer is my main system I tried the upgrade from the update manager from 7.10 to 8.04. The upgrade seemed to go well until it restarted. I then recieved  Busybox  with Initramfs. I have searched the forums and tried the fixes I saw posted. Edited the Grub Menu and switched the SATA settings in BIOS. None of these worked. Then I tried to do a fresh     install from The Live CD and the Live CD did the same thing. 

When I tried to boot the older kernal I could get it to run, but the graphics were messed up and I got crashes when I tried to run anything. My hardware is: AMD Athlon 64 X2 4800, Biostar TF520 A2, 2X1gb DDR2 800, Seagate 80gb SATA. 

I ended up reinstalling 7.10 and all is well. While I have no problem keeping 7.10 on my computer(runs great) I really would like to have the latest Distro. Does any one have any ideas What the problem may be and how I can fix it? 

Any advice would be appreciated, however I am a complete noob when it comes to Linux. Thanx.  ](*,)

---

### Post by grndragon57 on 2008-05-05
Bump

---

### Post by pro003 on 2008-05-05
I would recommend you to check out restricted driver manager or:

System > Administration > Hardware drivers


...and check the box for Nvidia accelerated graphic driver (or so..)

previously enable repositories and create the internet connection, do the update

```
sudo apt-get update
``` 

and then the first two lines above...

---

