---
title: "Unable to Continue to Installation"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by ArkaniKarin on 2008-02-06
I'm very new to Ubuntu. I installed it a while back, but never did much with it. I just got serious about using it last night, but couldn't get it to even begin installing. I've searched the forums, but nothing seems to handle my exact problem.

I ran off several copies of both 7.10 x86 and 64.

And I have an older 64 version, 7.04.

They all give me the same result: I boot from the disk, brings me to a menu at which I can select a boot method. I've tried both Safe graphics mode and start/install. After making my selection, it brings me to the Ubuntu loading screen, where it will sit for a while, and eventually start to work it's way up, like it's actually going somewhere. The screen blinks, and for a moment I get a distorted Ubuntu image at the top of the screen and then I'm taken to a black screen with white text reading...

[   229.120000] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   229.120000] ata5.00: (irq_stat 0x08000000)
[   229.120000] ata5.00: cmd c8/00:04:04:00:00/00:00:00:00/e0 tag 0 cdb

 * Starting deferred exectution scheduler atd
 * Starting periodic command scheduler crond
 * Checking battery state...
 * Running local boot scripts (/etc/rc.local)

And it just sits there. I've seen people suggesting opening up the console from this type of thing, but the first time I tried it, it mentioned something about not being authorized to do it. Now ctrl+alt+F2 does nothing.

I've tried using several different disk drives. No difference.


If anyone can think of anything, I'd be greatly appreciative.

---

### Post by ArkaniKarin on 2008-02-06
I managed to get it to the console. I ran the two things I had seen suggested to others with a similar problem:

sudo dpkg-reconfigure xserver-xorg

sudo /etc/init.d/gdm start

I went through the set up for the first, and all that did for me was cause my monitor to stop supporting the signal.

The second one failed as well.

So I'm completely out of ideas.

---

### Post by jken146 on 2008-02-06
Install using the Alternate CD.

---

### Post by Gimpojones on 2008-02-06
alternate CD?

---

### Post by pmshirey on 2008-02-06
If you used the Live CD you may want to try the alternate cd. Or, you may want to check your system, there are different kinds of ubuntu for different kinds of computers, for example, if you have a 64 bit AMD computer, you need that system. There is also one for mac, amd, and SUNSPARC. Go to the download page and see if you chose the right system.:popcorn:

---

### Post by ArkaniKarin on 2008-02-07
The alternate CD did the exact same thing.

I finally got it to run one of the Live disks. It'll only load the 7.04 64bit version.

But the problem is, it will only load if I unplug my harddrives. I have 3 drives, and I've tried all sorts of combinations, but it will only load if I have them -all- unplugged.

What would cause this, and how do I solve it?

---

