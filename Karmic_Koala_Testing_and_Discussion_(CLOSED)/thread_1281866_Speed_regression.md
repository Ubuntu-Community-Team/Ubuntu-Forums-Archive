---
title: "Speed regression"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by MarkusThielmann on 2009-10-03
I'm running Karmic on a quite outdated system (2 GHz, 1 GB RAM, Rage 128). Until last nights updates (from 02. to 03. Oct) the system was really fast. Now it's back to Jaunty speed and I think it might be related to the graphics card.

Does anyone know, what was changed in these updates?

---

### Post by jward3010 on 2009-10-03
Personally I'm finding it more sluggish than Jaunty, especially with Firefox. Now we're still in BETA but I hope it improves.

---

### Post by manysounds on 2009-10-04
I installed the UNR beta today (10/3/09) on an EeePC 900 and it was nice and snappy until.  Then I did updates.  Now it's all choppy and awful.
Smells like a regression.
I'd rather have an occasional hang or crash or whatever than this.

---

### Post by MarkusThielmann on 2009-10-04
Already found the source of this problem with the help of #ubuntu+1. Disabling NEW_FAIR_SLEEPERS in the kernel causes my system to run slower. It was disabled with a recent update, because other user experience a slower system when this is enabled. 

If you'd like to test it:

sudo su
echo NEW_FAIR_SLEEPERS > /sys/kernel/debug/sched_features # to enable it
echo NO_NEW_FAIR_SLEEPERS > /sys/kernel/debug/sched_features # to disable it

---

### Post by forcecore on 2009-10-04
Strange that i currently testing Ubuntu on Virtualbox and it is faster starting than it was 9.04? but i do not make upgrades ever i only like clean installs and now i test lastest daily build.

---

### Post by wireless on 2009-10-04
For me, disabling NEW_FAIR_SLEEPERS feture made the system go a bit faster, but still not as good as on Jaunty.

---

### Post by wireless on 2009-10-04
I'm not sure if it's related but i cannot find any other explanation, after disabling NEW_FAIR_SLEEPERS the system is not only faster, but I can now suddenly enable desktop effects and dual screen together as was on jaunty. I did nothing with the system (updates etc..) that can explain this sudden fix. GREAT!! Thanks Ppl!

---

### Post by Saneless on 2009-10-04
Thanks, that sleepers command helped a ton.  Not sure why all of a sudden some little change F'd so many things up.

---

### Post by jward3010 on 2009-10-05
I don't find much of a difference unfortunately, but with me it could be psychological negativity towards the fact that network manager doesn't "enable" my wireless card, thats driving me nuts.

---

### Post by buzzmandt on 2009-10-05
> **jward3010 said:**
> I don't find much of a difference unfortunately, but with me it could be psychological negativity towards the fact that network manager doesn't "enable" my wireless card, thats driving me nuts.

if you haven't already, you should start a new thread for the wireless problem, I had that too around alpha 2 and it's fixed now.  I pushed hard for that one with lots of help from wayne_cat and many others.

---

### Post by jward3010 on 2009-10-05
Cheers for the advice, I've been in others somewhat related and got to the point of filing a bug which seems to have support thankfully, from other frustrated people who just can't get this to make any sense, they're having MY specific problem.

---

### Post by manysounds on 2009-10-05
I ran:

sudo dpkg-reconfigure -phigh xserver-xorg

this solved my problem.

---

### Post by jward3010 on 2009-10-05
Interesting, I did think it was X based. I'm great for hunches!

---

