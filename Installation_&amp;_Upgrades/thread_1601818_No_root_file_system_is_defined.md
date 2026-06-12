---
title: "No root file system is defined"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by corncob on 2010-10-20
When I tried to install 10.10 'side by side' with 10.04 and OpenArtist for triple booting I get the message
> No root file system is defined.  Please correct this from the partitioning menu.
I don't have the screen in front of me now but what5 does it want me to do and how do I do it?

---

### Post by VMC on 2010-10-20
> **corncob said:**
> When I tried to install 10.10 'side by side' with 10.04 and OpenArtist for triple booting I get the message

I don't have the screen in front of me now but what5 does it want me to do and how do I do it?

You need to tell it where your root "/" is located. I haven't used side by side, so I'm not sure how to use that. I only use the manual partitioning method.

---

### Post by Dale61 on 2010-10-21
I got the same / similar message trying to perform a wubi install on my Acer laptop.  *Specs: Core i5 processor, NV GeForce 330M, 8GB RAM, 640GB HDD.*

I tried it with 10.10, *but wubi indicated it was a 10.04.1 install,* then I tried with my 10.04 cd, and I got the same message both times.

I ditched Ubuntu because of that BS wubi/grub conflict, and it looks like I may have to wait until 11.04 before I can come back.

---

### Post by corncob on 2010-10-22
Hasn't anybody installed 10.10, as a fresh install, along side of windows as a duel boot system?  Its obvious that its asking where root "/" is but how do I go about telling it?  It just gives me a choice of use entire disk or choose partition (advanced).  I chose the latter as I wanted to keep windows but, although it did install, it wiped out windows and left a large amount of unallocated space.  I've been installing Ubuntu since Feisty Fawn and its always been easy until now.  I'm thinking of a possible workaround -- installing 10.04 and then upgrading -- but I'm teaching a class and this won't impress them.

---

### Post by CadetD on 2010-10-22
> **corncob said:**
>  [...]  I'm thinking of a possible workaround -- installing 10.04 and then upgrading -- but I'm teaching a class and this won't impress them.

That won't help either. I had my son upgrade from 10.4 on his laptop and after the upgrade he reported that Ubuntu would not boot and left him at a black screen. 

Thinking he was just been dumb, I upgraded mine last night and guess what? ...well I am trolling forums now, so I'll leave you to deduce what happened to me. :(

---

### Post by Dale61 on 2010-10-22
I tried installing 10.04, but the same message came up as that when I tried to install 10.10.

Maybe it's a Windows7 thing, but I know that 10.04 will load on the Vista laptop (but with that grub conflict), but neither 10.04 or 10.10 will install as it should (as a wubi install) on the W7 laptop.

---

### Post by psusi on 2010-10-22
> **corncob said:**
> Hasn't anybody installed 10.10, as a fresh install, along side of windows as a duel boot system?  Its obvious that its asking where root "/" is but how do I go about telling it?  It just gives me a choice of use entire disk or choose partition (advanced).  I chose the latter as I wanted to keep windows but, although it did install, it wiped out windows and left a large amount of unallocated space.  I've been installing Ubuntu since Feisty Fawn and its always been easy until now.  I'm thinking of a possible workaround -- installing 10.04 and then upgrading -- but I'm teaching a class and this won't impress them.

When you choose manual partitioning, you get a screen listing all of your partitions and what you want Ubuntu to do with them.  It starts off as doing nothing with any of them.  You need to pick one to use for the root and tell it to use that one mounted as "/".

---

### Post by corncob on 2010-10-22
> **psusi said:**
> When you choose manual partitioning, you get a screen listing all of your partitions and what you want Ubuntu to do with them.  It starts off as doing nothing with any of them.  You need to pick one to use for the root and tell it to use that one mounted as "/".

I can highlight a partition but that in itself doesn't seem to tell it to use that partition.  I don't see anything else to do and I'm stuck.

---

### Post by psusi on 2010-10-22
> **corncob said:**
> I can highlight a partition but that in itself doesn't seem to tell it to use that partition.  I don't see anything else to do and I'm stuck.

Click the edit button.

---

### Post by perspectoff on 2010-10-22
There were a lot of graphics incompatibilities going from Karmic to Lucid. Many people's screens went black because the graphics drivers weren't working. If you are using an older burn of the LiveCD, you may have these problems.

That happened to me, but a recent LiveCD burn has newer drivers and loaded fine on the computers that previously gave me a black screen.

(Of course, if you can run the LiveCD, it ought not be a graphics problem).

The other problem is the location of the Grub2 bootloader. It is normally stored in the partition of an Ubuntu installation. If that installation has gone awry for any reason, you won't be able to boot your computer until you do a completely new installation.

One possible solution (which I recently did) is to create an entirely new small partition (about 4-5 Gb) using GParted on the LiveCD and reinstall a completely new installation of Ubuntu there. That will allow you to reinstall Grub 2, which will then scan the computer for other OSs and subsequently allow you to multi-boot. You could then try to boot into the malfunctioning installation, do whatever it takes to fix it, and once it is working run update-grub from within it (after removing the 4-5 Gb installation).

Bit of a roundabout method, but it works.

In the future, if you are interested in an alternative failsafe way to multi-boot many operating systems, take a look at

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation) 

or

[http://kubuntuguide.org/Multiple_OS_Installation](http://kubuntuguide.org/Multiple_OS_Installation)

---

### Post by corncob on 2010-10-22
> **psusi said:**
> Click the edit button.

I'll remember this although I hadn't noticed an edit button at the time.  Actually, the problem seems to have disappeared.  I went to install it in my Vista laptop (which also had 10.04) and I got the "Install alongside other operating systems" option which was missing in my previous attempts.  Go figure.  Letting things cool off over night, picking up a different disk, prayer......
Thinking of what Dale61 said about it possibly being a Win7 problem, I next tried my win7 box (which is also running 10.04) and it worked there too.  I didn't go on with the installations as I'm saving that for my presentation next week (hopefully everything will be working then).  Honest, I was only getting 2 options last week (erase entire disk or specify partition), "Install alongside other operating systems" just wasn't there.

---

### Post by corncob on 2011-04-06
I just got private mail about this thread.  I had concluded that it was a bad burn on that one disk I was using.  Other disks worked fine, giving me all the choices.  I'll mark the thread as solved.

---

