---
title: "Alternate or Desktop Install?"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by bvsingh on 2006-07-04
I have a problematic 845gv based motherboard from ASRock. It has a feature called "Easy Dual Monitor" which allows both the graphics chipset(onboard and AGP) to be connected to a display each. The problem is that even though my display is connected to AGP card mx440Geforce it is not detected, instead, the onboard chipset is detected by dapper drake.

(*)Can using alternate install help me?

(*)Should I intall using onboard graphics, and later after installing is there a way to get dapper to use the agp card?

(*)I know that my agp card is on IRQ16, can I use this information to help it get detected by dapper?

Urgent help needed...

---

### Post by confused57 on 2006-07-05
[QUOTE=bvsingh]I have a problematic 845gv based motherboard from ASRock. It has a feature called "Easy Dual Monitor" which allows both the graphics chipset(onboard and AGP) to be connected to a display each. The problem is that even though my display is connected to AGP card mx440Geforce it is not detected, instead, the onboard chipset is detected by dapper drake.

(*)Can using alternate install help me?

(*)Should I intall using onboard graphics, and later after installing is there a way to get dapper to use the agp card?

(*)I know that my agp card is on IRQ16, can I use this information to help it get detected by dapper?

Urgent help needed...[/QUOTE]

I don't believe the alternate cd would help, but until someone experienced with this comes along, you might look into something like this:
[http://www.ubuntuforums.org/showthread.php?t=33142&highlight=onboard+graphics+nvidia](http://www.ubuntuforums.org/showthread.php?t=33142&highlight=onboard+graphics+nvidia)

A better title for your post would have been something like "onboard graphics and AGP mx4400 GeForce"...The reason I say this is that, this would catch the eye of someone experienced with this issue.   Good luck.

---

### Post by bvsingh on 2006-07-05
[QUOTE=confused57]A better title for your post would have been something like "onboard graphics and AGP mx4400 GeForce"...The reason I say this is that, this would catch the eye of someone experienced with this issue.   Good luck.[/QUOTE]

Done that, hope it helps...

---

### Post by nsabatino on 2006-07-05
[QUOTE=bvsingh]Done that, hope it helps...[/QUOTE]

You could also disable the onboard graphics controller in the bios, forcing ubuntu to recognize the agp based one.

---

