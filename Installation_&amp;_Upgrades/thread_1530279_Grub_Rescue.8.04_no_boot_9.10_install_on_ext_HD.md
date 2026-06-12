---
title: "Grub Rescue.8.04 no boot 9.10 install on ext HD"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by colintivy on 2010-07-13
Hi folks.

I have recently failed to instal 10.04 from Live Cd (LXF disk) to an empty 80GB external drive, it does its thing past Language and keyboard then burst into disk activity finally displaying the Log In panel Clearly this is quite immature. This activity is the subject of another post  but advice on this will be wekcome.

In deperation I tried to instel 9.10 from another LXF disk and it looked promising in live mode so I then installed it. All seemed to go well after a few hours. Not having set up a dual boot arrangement of oourse I could not boot it.

On trying boot back to 8.04 I found that I could not do so and got the "grub rescue" error. This was new to me and as it offered a sort of CL I tried several possible commands all of which were not recognised. I realised that I had failed to spot the need to load the grub loader to the external HD and it now had overwritten the old grub boot on the internal HD where 8.04 lives. I have backed up /home etc but not the whole system so I was abit stuck.

I went back and reinstalled 9.10, this time putting the grub loader on the external drive and it all went in, still unbootable.

I have looked a some past posts but they seem all to be for a failure to boot back to Windows and not applicable to my problem presumably.  I still have my Live CD for 8.04 but am uncertain how prcisely where to go from there. I have a fair amount of stuff on dual booting whichI will tackle when I get a usable 8.04again, I am presently on someone else's computer to send this.

---

### Post by colintivy on 2010-07-14
Sorry Chaps!

Bumping this one. At least I have managed to use 9.10 Live DVD to get on line but am a bit desperate to get 8.04 back in working order. Just the procedure to restore GRUB to sda will be a help please!

:(  :(

---

