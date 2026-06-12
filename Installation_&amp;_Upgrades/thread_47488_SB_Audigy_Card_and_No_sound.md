---
title: "SB Audigy Card and No sound"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by woedend on 2005-07-08
Hey guys.. My name is Alex and I am very new to Linux.  Lets just say I know nothing about it but am learning by searching the web.  I have found a problem that I cannot solve however, getting my sound card to work!  When I installed, on the first boot it worked perfectly.  I made no changes whatsoever, just went to restart the computer immediately(to test GRUB) and sound is gone!  I've reinstalled and get the same exact thing, fine the first time, no more after first reboot.  It's a sound blaster audigy..it does show as a device in volume properties, but not matter what will not work.  I've tried a couple steps that I can't exactly recall at the moment but I found on here, still no luck.  Anyone know where a newb like me can get help on this.  Thanks guys.

---

### Post by maruchan on 2005-07-08
Hey, I have an Audigy too. It has always worked great here. There are quite a few threads about audio here, so searching for "audio" or "audigy" might help.

At least you know it works some of the time. You've made sure the volume is turned up and not muted? Are both boxes checked under System > Preferences > Sound?

---

### Post by BaffledMollusc on 2005-07-09
[QUOTE=woedend]Hey guys.. My name is Alex and I am very new to Linux.  Lets just say I know nothing about it but am learning by searching the web.  I have found a problem that I cannot solve however, getting my sound card to work!  When I installed, on the first boot it worked perfectly.  I made no changes whatsoever, just went to restart the computer immediately(to test GRUB) and sound is gone!  I've reinstalled and get the same exact thing, fine the first time, no more after first reboot.  It's a sound blaster audigy..it does show as a device in volume properties, but not matter what will not work.  I've tried a couple steps that I can't exactly recall at the moment but I found on here, still no luck.  Anyone know where a newb like me can get help on this.  Thanks guys.[/QUOTE]
I had a similar problem and what I had to do was unmute the appropriate channel. To do this call up a terminal (Applications | System Tools | Terminal) and type "alsamixer" (without the quotes). Now use the right cursor key to scroll across until you reach the  "Audigy Analog/Digital Output Jack". Now press "m" to unmute it. 

See if that works.

---

### Post by outcircuittheend on 2005-10-02
Changing the analog/digital line mute setting worked for me.  Thanks for the help.

---

### Post by doubletime on 2005-10-04
I would also like to thank you. I had no sound at all. It worked for me as well.:D

---

### Post by IvanIllyche on 2006-08-23
> **BaffledMollusc said:**
> I had a similar problem and what I had to do was unmute the appropriate channel. To do this call up a terminal (Applications | System Tools | Terminal) and type "alsamixer" (without the quotes). Now use the right cursor key to scroll across until you reach the  "Audigy Analog/Digital Output Jack". Now press "m" to unmute it. 

See if that works.

I have this same problem but doing that did not work for me I don't know what else to do but sure could use some help if you have any ideas

---

### Post by IvanIllyche on 2006-08-23
ok nevermind that I got things to work except for the sound in kaffiene any ideas

---

