---
title: "edgy: mouse slow after update"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by eantoranz on 2007-02-08
I updated edgy a while ago. Besides noticing that there are three packages that break themselves (all being related to the linux kernel) I have noticed that the mouse refresh rate is toooooooooooooo slow. If I move the mouse, I can see the pointer move, but the movement in the screen is not smooth and seems to take much time between each refresh.... I can say it reminds me of stroboscopic lights.

Just as a workaround I changed my xorg driver from ati to vesa and tried different resolutions, but the same behavior showed up everytime.

Is there a work around? :confused:

---

### Post by mlissner on 2007-02-09
I'd guess that something worse than the mouse is the culprit. In my experience the mouse goes slow when something else is taking all the processor's attention. 

You try looking at the output of dmesg for weird things? 

If you switch kernels in grub to the old one, do you have the same problem?

What's your system monitor look like when this is happening?

---

### Post by eantoranz on 2007-02-09
As a matter of fact, the kernel wasn't updated... I think.

The monitor looks normal.. completely normal.... just the mouse doesn't move at my pace and position refreshes are separate from each other.. say.... 3 maybe 4 times per second... guess how that would look like. :-(

I'll see if there are funny things in dmesg when I get back home.... by the way, the mouse is USB... but it is working perfectly in windows... and it worked perfectly until I upgraded (not "dist-upgraded to".... just upgraded) edgy two days ago... of course, the problem showed up after I restarted the box.

---

### Post by pizpot on 2007-03-09
I've had this problem bad for a week on my 2nd computer. I guess that is why it took so long to solve. I had trouble telling when the mouse got slow, so I could not tell what I did wrong. Usually, it would slow down like 2 mins after restarting type of thing.

It happens after updates alright. It happens to xubuntu-fromcd, ubuntu, and alternate ubuntu. The system is a duron 1.2 with 256 and a nforce2 and gf4mx.

I fixed it by plugging a ps2 adapter into the usb mouse. USB is the problem. Man I am happy to fix this, it really was a strange behavior. Like the guy said, usually the mouse being slow indicates the cpu being busy, but this was not the case here. Eventually, I noticed that by watching some utube. See... computer is fast, just mouse is slow. 

Cheers.

---

### Post by fredericthewise on 2008-03-31
i have exactly the same problem in hardy, except with me its the touchpad of my thinkpad laptop.
always worked fine, even on earlier alphas of hardy, but now has wrecked up with update.

Any ideas?:confused:

---

