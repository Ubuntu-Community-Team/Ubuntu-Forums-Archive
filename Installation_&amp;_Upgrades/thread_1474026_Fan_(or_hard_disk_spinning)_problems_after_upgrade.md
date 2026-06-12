---
title: "Fan (or hard disk spinning?) problems after upgrade from Karmic 9.10 to Lucid 10.04"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by MsKK on 2010-05-05
Hello everyone,

I have an HP Mini 210 and I recently performed an Upgrade from 9.10 to 10.04 and noticed that the netbook is much more noisy now (and can get very warm). I am not sure wether is the fan or the hard drive spinning. I did a "top" but no process was high consuming. 

I also thought that maybe compiz could be responsable for it, so I disabled all the visual effects, but still no change. I am afraid this could have long term effects on the battery or graphic card or whatever (I'm half n00b half human). 

Any ideas or suggestions?

Thanks

---

### Post by ubuntologist on 2010-05-24
Hi MsKK,

I believe it is most likely the fan as HDD activity is not that noticeable.

The BIOS has the fan set to Always On, which I don't think is necessary. If you disable the Always On setting, the fan will come on only when needed. The Atom N450 CPU in the HP Mini 210 has a TJunction of 100degC so it can heat up quite a bit without causing any damage.

Another bonus is that you'll experience better performance from the battery!

To fix this fan issue, enter the BIOS on boot by pressing ESC, then press F10 for BIOS settings. Find the reference to Fan Always On (under System from memory) and switch it to Disabled. Then, Save and Exit.

You can always monitor the CPU temp by typing the command "sensors" in Terminal. Might be a good idea to keep an eye on it for a few days to confirm all's well.

---

### Post by bumanie on 2010-05-24
check top a few times - i had a similar problem and found that there was one process that turned itself on and off, but when on, was driving the cpu very hard - 80%+. It may be a different issue, but I had checked top a few times and saw nothing untoward, until yesterday and then the process was on 90% of the time, but not 100% of the time. If you do find a process driving the cpu hard, post its name as if it is the same as mine, there is a fix, but I won't post it in case it turns out to be a different problem.

---

### Post by rob-ward on 2010-05-24
It might also be worth checking that CPU scaling hasn't been disabled. If it has you CPU might always be running at 100% clock speed, not only will this increase it's power consumption but it will also make it hotter.

There are lot's of guides on web about setting up and configuring CPU scaling however as a quick check you can add the CPU scaling monitor to you top panel(right click on the panel and then select add to panel), it should show you what speed your CPU is set at and allow you to choose different levels.

---

### Post by Karim_ on 2010-05-24
I just installed ubuntu 10.04 brand new, it's on a dual boot with vista.
It feels hot over time it didn't get this hot so quickly with vista.
And there isn't any laud noises but I was running only a few programs like opera, exaile, Nautilus file manager and the fan got laud but I don't think that's a problem.

I just did a check on System Monitor and...
CPU1 is 25.0% to 50.0% and CPU2 is lower then 20.0% this is higher then Vista! and I'm only running 4 programs now, well on is one standby.

In Vista I can run several programs without overheating or crashing, except with flash I hate flash but flash is great for animations.

Probably think I'm being one sided by mentioning Vista so many times. Truth is I'm not. Vista might be slow but that gives it a little character.

---

### Post by dino99 on 2010-05-24
look at your bios settings about powersaving prefs

then some hardware (ibm, dell, ...) need some driver to be installed with synaptic (search about the company)

---

