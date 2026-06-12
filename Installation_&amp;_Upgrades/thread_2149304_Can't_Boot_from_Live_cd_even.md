---
title: "Can't Boot from Live cd even"
date: 2013-05-28
forum: Installation &amp; Upgrades
---

### Post by arawngwydion on 2013-05-28
I have used Ubuntu in the past and wanted to get back to it. But I have been unable to even boot a live cd past 10.04 32 bit. My system is as follows: Amd Athlon 2 x640 64 bit quad core, 16 gb ddr3 1600, 160 gb sata, 2 tb sata, 320 gb pata, asus m4a78lt-m motherboard, NVidia ion (gt240) Video card and a chaintech av-710 sound card. I am running Dual displays both HP one via hdni and 1 via dvi. With a 550 watt power supply. What am I doing Wrong

---

### Post by grahammechanical on 2013-05-28
Please explain what you mean by "unable to even boot a live CD." What happens. What you see or do not see on the screen may be a clue to what is wrong or what you need to do. Without that information we could suggest any number of things most of which will be a waste of time for you and us because they are not appropriate.

Regards.

---

### Post by arawngwydion on 2013-05-28
all versions beyond 10.04  end up giving me a failed to idle channel 2, failed to idle channel 3 message, and lock up. They also lock up during the copying files portion of install, just stops and I have to reset. If I use wubi I at least get the grub boot screen. but It won't complete the install. just locks up.

---

### Post by arawngwydion on 2013-05-29
Hopefully this info will help so I can get this going.  Same hardware as in the original post, Ubuntu 12.10 via wubi. The windows side of the install works fine, however on reboot I get a splash screen, and then it goes to terminal and won't let me input any commands. It shows me a list of actions related to startup/shutdown. Mounting volume hda-blah, and so on. Then near the bottom of this list which is half a screen long, I get the following: [64.5386069] [drm] nouveau 0000:01:00.0: failed to idle channel 2  Next line: [68.532550] [drm] nouveau 0000:01:00.0: pgraph tlb flush idle timeout fail:0x011fde03 0x0000002d 0x0034db40 Next line: [70.529068] [drm] nouveau 0000:01:00.0: pgraph tlb flush idle timeout fail 0x011fde03 0x0000002d 0x0034db40 Next line: [70.520879] [drm] nouveau 0000:01:00.0: failed to idle channel 3 Next line: [118.065315] [drm] nouveau 0000:01:00.0: failed to idle channel 2. and it just keeps going black screen and then repeating this performance

---

