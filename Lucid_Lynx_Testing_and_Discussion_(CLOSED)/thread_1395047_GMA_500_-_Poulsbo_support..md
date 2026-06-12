---
title: "GMA 500 - Poulsbo support."
date: 2010-01-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by exploder on 2010-01-31
I was wondering if the GMA 500 - Poulsbo will be supported in Lucid? Last I read Intel was not providing Linux drivers and I was wondering if anything has changed. I would appreciate any information on this that is available.

Thanks!

---

### Post by jbernardo on 2010-02-14
Unfortunately, AFAIK there is no poulsbo xorg driver for xorg >= 1.7. And since Lucid will ship with 1.7.x, unless Intel keeps its promise to deliver a Gallium 3D based driver soon, all psb owners are stuck with karmik

---

### Post by exploder on 2010-02-14
Thanks for the response jbernardo! I had almost forgotten about this post.

---

### Post by jbernardo on 2010-02-14
I was just doing my weekly search for any news on the psb support... :)

---

### Post by crjackson on 2010-02-14
Although I have no need for this, if I did, at this point I would have to go with Mandriva's commercial software.  It's pretty damn nice.  It's not free but if you're going to have to pay someone at least it's Linux, and a nice distro that's well supported (including Poulsbo).

---

### Post by jbernardo on 2010-02-15
I've got Mandriva 2010 in my netbook too. It is nice, but it still uses the same poulsbo driver. Which means that 2010.1 won't run, if they also switch to xorg 1.7. So there is no advantage there.

---

### Post by Zorael on 2010-02-15
The Poulsbo graphics core was developed by PowerVR/Imagination Technologies, no? So the linux Intel guys' hands are basically tied, and PowerVR will have to get their hands out of their pockets.

---

### Post by lucazade on 2010-02-15
Anyone tried out the new Iegd 10.3beta drivers?

(Available on [Moblin rpm packages]("http://repo.moblin.org/moblin/development/8ce7221dd874d71978baaeffecd06c8e/archive/20100208/ivi/ia32/os/i586/") or from [Iegd main page]("http://edc.intel.com/Software/Downloads/IEGD/"))

I'd like to update the [Fitpc2 PPA]("http://www.fit-pc2.com/download/ubuntu/dists/karmic/source/") with these new files and try them on Xorg 1.7 and Kernel 2.6.32.

---

### Post by jbernardo on 2010-02-15
That sounds like a good idea. Now that suspend/hibernate fails more often than not with the regular drivers, I won't mind so much trying the iegd ones.

---

### Post by jurekiteresa on 2010-02-15
Hi

Jbernardo, Lucazade
Did you try Moblin 2.1 IVI final Project with IEGD Release
February 8, 2010:

[http://moblin.org/projects/2.1-ivi-project-releases](http://moblin.org/projects/2.1-ivi-project-releases)

[http://repo.moblin.org/moblin/development/8ce7221dd874d71978baaeffecd06c8e/images/moblin-2.1-PR-Final-ivi-201002090924.img](http://repo.moblin.org/moblin/development/8ce7221dd874d71978baaeffecd06c8e/images/moblin-2.1-PR-Final-ivi-201002090924.img)

Regards?

Jurek

---

### Post by lucazade on 2010-02-15
> **jurekiteresa said:**
> Hi

Jbernardo, Lucazade
Did you try Moblin 2.1 IVI final Project with IEGD Release
February 8, 2010:

[http://moblin.org/projects/2.1-ivi-project-releases](http://moblin.org/projects/2.1-ivi-project-releases)

[http://repo.moblin.org/moblin/development/8ce7221dd874d71978baaeffecd06c8e/images/moblin-2.1-PR-Final-ivi-201002090924.img](http://repo.moblin.org/moblin/development/8ce7221dd874d71978baaeffecd06c8e/images/moblin-2.1-PR-Final-ivi-201002090924.img)

Regards?

Jurek

I haven't tried this release yet.. downloading :)

---

### Post by lucazade on 2010-02-15
Update: tried and it works well.
(started in init3 and modified xorg monitor settings)
Performances are better than 10.2.2 release (widget drawing/firefox scrolling) and similar to the Psb driver stack.

Any links to Iegd release notes or info about xorg 1.7 / kernel 2.6.32+ support?

---

### Post by jurekiteresa on 2010-02-16
Hi

Unfortunately suspend (white screen) on my Aspire One 751 during boot.
Could you tell me how fix it?
(started in init3 and modified xorg monitor settings)

Regards

Jurek

---

### Post by lucazade on 2010-02-16
> **jurekiteresa said:**
> Hi

Unfortunately suspend (white screen) on my Aspire One 751 during boot.
Could you tell me how fix it?
(started in init3 and modified xorg monitor settings)

Regards

Jurek

Append "3" to grub options, this way live cd will boot in init3 (X will not be started).
Login as "moblin" and blank password.
Edit xorg.conf, remove 2nd display settings and configure the resolution (vi /etc/X11/xorg.conf).
Type "init 5" to start X server.
It's a bit tricky but it works!

---

### Post by jbernardo on 2010-02-17
I've given up on the IEGD for now. Downloaded the release for moblin (seems to be the one for a more recent kernel), found it has a windows exe inside the zip. Ran it with wine, and found there is another windows exe to generate the packages for a specific configuration you need to select. That second exe doesn't run properly under wine, shows blank pages where you should be able to select options.
Gave up...
Anyway, the user manuals included mention xorg only up to 1.6, so I'm guessing it is still broken under lucid.

---

### Post by Mizukusai on 2010-02-17
I'm trying to make it work on a eeePC T91.

So far, the display issue remains. (Wrong sync, wrong color, wrong resolution).
I'll try to empty the xorg.conf little by little.

---

### Post by Mizukusai on 2010-02-17
Any more precise clue to make it work will be welcome :D

And by the way, I have another linux installed on an ext4 partition. This Moblin distro can't recognize ext4, so grub can't propose to boot on it.  How can I change that ? I don't know which package to install with yum.

---

### Post by jurekiteresa on 2010-02-18
Hi

Lucazade

Yes it works. Thank you.
But why I cannot see any Clutter GUI effects?
I can see only oridnary XFCE :((

Please advice.

Regards

Jurek

---

### Post by Mizukusai on 2010-02-19
Same here.

---

### Post by LifeTheHound on 2010-02-25
I have never been able to get Poulsbo working on karmic (Vaio P). It always makes me shake my head to see people yap about getting it to work, because there are no clear instructions anywhere that work with the latest karmic kernel (which I *need* or else wifi and sound are epic b0rk'd).

Anyone else think this worthless PowerVR company should hurry up and die?

Okay, so maybe I'm being a drama queen but honestly, the GMA500 is the worst joke ever, not able to live up to the gma950 in a single way (even given the hit-and-miss video acceleration and "support" for PS3).

---

### Post by Mizukusai on 2010-02-26
I'm using an up-to-date karmic on my T91 (with this wonderfull GMA500).
Look for a topic about T91, you'll find the how-to you need.
No quite difficult actually, you'll see.

---

### Post by Phobiac on 2010-03-02
So is a GMA 500 driver for Lucid at the moment nonexistent? So far it's the only thing major that I can't get working on my U820.

---

### Post by jap1968 on 2010-03-05
And what about 64 bits?

I have a Intel D510MO motherboard. I have installed Ubuntu 9.10 x86_64 but I can not find information or experiences about installing GMA500 on a 64 bit machine. It is even possible to do that?

---

### Post by oneguynick on 2010-03-22
> **jap1968 said:**
> And what about 64 bits?

I have a Intel D510MO motherboard. I have installed Ubuntu 9.10 x86_64 but I can not find information or experiences about installing GMA500 on a 64 bit machine. It is even possible to do that?

No, 32bit support only

---

### Post by descendent87 on 2010-04-08
Everyone who is effected by this please add to the bug report, hopefully it will get some attention or at least a definate answer on whether there will be any support
[https://bugs.launchpad.net/ubuntu/+bug/553898](https://bugs.launchpad.net/ubuntu/+bug/553898)

---

