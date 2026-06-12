---
title: "unexpected onboard SPDIF volume control on a ASUS P5E-VM"
date: 2008-09-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Benjamin_Lebsanft on 2008-09-23
After upgrading from hardy and using the onboard sound card of my ASUS P5E-VM I noticed strange things going on with the audio controls. 

I followed the guides here to get pulseaudio working with flash etc. and have sound in all apps. But the volume control applet doesn't even change the volume when using the "HDA Intel (ALSA mixer)" which is I guess intended behaviour. 

But when using "Playback: HDA Intel - ALC883 Analog (Pulseaudio Mixer)" I get unintended behaviour. Changing it from 100% to around 20% doesn't change the volume at all, the last 20% change the volume until its muted. 
Is there anything I can do to change this?

---

### Post by Nullack on 2008-09-23
You can, by contirbuting to the bug reporting process :) Please refer to the contributing to Intrepid link in my sig.

---

### Post by Benjamin_Lebsanft on 2008-09-24
I already reported the bug, just wanted to ask here too in case somebody knows a solution.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263201](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263201)

---

### Post by Nullack on 2008-09-24
Good, it helps to include the bug number so people can look.

Looking at the bug report I note theres been a number of commits to Intrepid since in this area. Do you still have the problem following a synch to the repos (on main or an up to date mirror)?

---

### Post by Benjamin_Lebsanft on 2008-09-24
I always use latest upgrades and the problem is still there

---

### Post by Nullack on 2008-09-24
When you say your following the forum on how to setup pulseaudio, are you using themuso's ppa from psyeks guide or are you on the intrepid build?

---

