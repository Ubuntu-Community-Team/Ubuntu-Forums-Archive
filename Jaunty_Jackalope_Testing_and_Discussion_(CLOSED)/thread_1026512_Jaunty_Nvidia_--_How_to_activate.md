---
title: "Jaunty Nvidia -- How to activate?"
date: 2008-12-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dawynn on 2008-12-31
My Intrepid system seems to be working fine, so I took the plunge and migrated my Hardy system up to Jaunty.

What's the new process to try to get nVidia working in Jaunty?  I have a GeForce FX 5700 LE in an Athlon Classic.  I cannot use the 173 drivers -- the card can handle them, but the lack of SSE instructions in the CPU prevents use.  That's fine, I'm satisfied with the 96 series in Intrepid (and previous versions).

But when I go to System -> Admin -> Hardware Drivers, nothing is listed for available drivers.

So, how do we activate the nVidia drivers for the Jackalope?

---

### Post by gnomeuser on 2008-12-31
one of two ways:

1) Wait for a Free Software driver to become available

2) Wait for nVidia to adapt their proprietary driver to the X server 1.6 API

2 is likely going to be quicker, 1 will solve the problem once and for all. Sorry but nvidia are not supporting you as best they could, the sad fact of life.

---

### Post by alexv75 on 2008-12-31
What about manually installing the driver with the "IgnoreABI" workaround?

> **jfernyhough said:**
> Have you read this thread?

Anyhow, in /etc/X11/xorg.conf you need the following:
```

Section "ServerFlags"
    Option    "IgnoreABI"    "True"
EndSection

```

---

### Post by autocrosser on 2008-12-31
There are several posts about this--dinxter has posted the "no ABI" part of the fix & I posted the PPA for the nVidia drivers---see the "xorg breakage" thread or the more current nVidia driver posting---I'm at work, so can't post the PPA right now, but you can use the newest drivers with that repository.....

---

### Post by jmdsdf on 2009-01-09
This is a big hack, but this worked for me. Since the latest development version of Ubuntu's Jaunty Jackalope broke the nvidia-glx-173 package some time ago, what I decided to do was drastic and not pretty, but did work. Basically I updated xorg as you did, and found it removed nvidia-glx-173 (and fell back to the open source nv or vesa driver). I installed nvidia-glx-173, then uninstalled nvidia-glx-173, then changed my repos back to Intrepid, installed nvidia-glx-173, updated my /etc/apt/sources.list back to Jaunty, locked the xorg updates in Synaptic and applied the rest of the updates. I wish there was a better solution to it, but at least I'm back up and running with Compiz with the nvidia driver. I'm also staying with the 2.6.27 kernel for the time being.

Can you post the link to the other post so I can do this a better way? I don't see a solution for the 173 driver. :(

---

### Post by LordVeovis on 2009-01-10
[http://ubuntuforums.org/showthread.php?t=1011847](http://ubuntuforums.org/showthread.php?t=1011847)

That is the post.  You need to get the info for the PPA and then make the other minor tweaks to xorg.conf  All changes are mentioned in there.

---

### Post by tsukasa80 on 2009-01-10
I added -ignoreABI in gdmsetup under configure xserver worked for me.

---

### Post by Starks on 2009-01-10
> **LordVeovis said:**
> [http://ubuntuforums.org/showthread.php?t=1011847](http://ubuntuforums.org/showthread.php?t=1011847)

That is the post.  You need to get the info for the PPA and then make the other minor tweaks to xorg.conf  All changes are mentioned in there.

You didn't link the post.

:3

---

### Post by LordVeovis on 2009-01-11
> **autocrosser said:**
> I just got updates & the path was clear--updated Xorg (all of it) & the driver 180.16 was unblocked...using PPA:
@Starks

#Restricted PPAs for .28 Kernel
deb [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main

180.16 driver installed without problems--just added the:

Section "ServerFlags"
Option "IgnoreABI"      "True"
EndSection

as per dinxter's fix.

:popcorn: :guitar: :):):)

There you go!! :P  I was lazy

---

### Post by autocrosser on 2009-01-11
Ditto here--I could have posted it & "duh" forgot ;)

---

### Post by jmdsdf on 2009-01-11
I'm sorry. I don't see how this applies to the nVidia 173 or 96 drivers as the original poster and I require? Oh well, no worries. The Intrepid xorg is still working fine with the 2.6.27 kernel with my card.

---

### Post by LordVeovis on 2009-01-11
> **jmdsdf said:**
> I'm sorry. I don't see how this applies to the nVidia 173 or 96 drivers as the original poster and I require? Oh well, no worries. The Intrepid xorg is still working fine with the 2.6.27 kernel with my card.

It applies in the way that you can't use the old drivers.  You have to use the new ones if you want to use jaunty w/ 3D GFX

---

### Post by dawynn on 2009-01-15
> It applies in the way that you can't use the old drivers. You have to use the new ones if you want to use jaunty w/ 3D GFX 

Then it does not help the problem at all.  Let's remember the focus of Ubuntu.  Everything should "just work".  Not: everything should just work as long as you're using all the latest hardware.

Am I using a computer that's 7 years old, and wasn't the top of the line when I bought it?  Yes.  But isn't that what Linux is often touted for -- being able to keep old hardware running smoothly?

I have both Intrepid and Jaunty installed on the PC, and I'm fine with using Intrepid for now.  But when the problem is that I've got hardware that won't allow me to use the latest drivers, the solution to get the hardware working is not -- "Hey, update to the latest drivers!".

In this case, its not strictly a matter of the video card (although a move away from nVidia cards may help).  The CPU is the issue.  The latest nVidia drivers use SSE instructions, something that was not fully working until the Athlon+.  So, Athlon Classics, regardless of which nVidia card they use, cannot use any drivers later than the 96 series.

So, I'm fine with waiting for a fix, but it needs to be a fix that will actually work for my computer.  Until that comes along, I'm not really interested in how some other fix works for your rig.  As we saw with Intrepid, once they get the latest drivers working, nVidia will eventually spend some time on the older drivers.

---

### Post by LordVeovis on 2009-01-15
> **dawynn said:**
> Then it does not help the problem at all.  Let's remember the focus of Ubuntu.  Everything should "just work".  Not: everything should just work as long as you're using all the latest hardware.

Am I using a computer that's 7 years old, and wasn't the top of the line when I bought it?  Yes.  But isn't that what Linux is often touted for -- being able to keep old hardware running smoothly?

I have both Intrepid and Jaunty installed on the PC, and I'm fine with using Intrepid for now.  But when the problem is that I've got hardware that won't allow me to use the latest drivers, the solution to get the hardware working is not -- "Hey, update to the latest drivers!".

In this case, its not strictly a matter of the video card (although a move away from nVidia cards may help).  The CPU is the issue.  The latest nVidia drivers use SSE instructions, something that was not fully working until the Athlon+.  So, Athlon Classics, regardless of which nVidia card they use, cannot use any drivers later than the 96 series.

So, I'm fine with waiting for a fix, but it needs to be a fix that will actually work for my computer.  Until that comes along, I'm not really interested in how some other fix works for your rig.  As we saw with Intrepid, once they get the latest drivers working, nVidia will eventually spend some time on the older drivers.

Perhaps you forget that this is ALPHA.  Alpha won't support everything that the final will.  As far as legacy drivers (96 and before) that is allot different than current drivers.  And you are right that it does not auto install or find the 96 drivers.  I have not yet tried to force a manual install of those.  I just recently installed jaunty on my laptop and I am now experiencing this too.  I thought the PPAs would fix the issue, but it does not.  Once I get my legacy drivers up I will let you know what I did.

My above info is the proper solution for anyone that was using 173 drivers.  As far as 96, I will try to come up with that solution. now.

---

### Post by tpe11etier on 2009-01-15
> **dawynn said:**
> Then it does not help the problem at all.  Let's remember the focus of Ubuntu.  Everything should "just work".  Not: everything should just work as long as you're using all the latest hardware.

Am I using a computer that's 7 years old, and wasn't the top of the line when I bought it?  Yes.  But isn't that what Linux is often touted for -- being able to keep old hardware running smoothly?

I have both Intrepid and Jaunty installed on the PC, and I'm fine with using Intrepid for now.  But when the problem is that I've got hardware that won't allow me to use the latest drivers, the solution to get the hardware working is not -- "Hey, update to the latest drivers!".

In this case, its not strictly a matter of the video card (although a move away from nVidia cards may help).  The CPU is the issue.  The latest nVidia drivers use SSE instructions, something that was not fully working until the Athlon+.  So, Athlon Classics, regardless of which nVidia card they use, cannot use any drivers later than the 96 series.

So, I'm fine with waiting for a fix, but it needs to be a fix that will actually work for my computer.  Until that comes along, I'm not really interested in how some other fix works for your rig.  As we saw with Intrepid, once they get the latest drivers working, nVidia will eventually spend some time on the older drivers.

Whoa!  Settle down and step away from the keyboard...

Maybe you shouldn't have taken the "plunge" and upgraded to an Alpha OS????

---

### Post by dawynn on 2009-01-16
I don't understand how jmdsdf's and my own reminder to keep with the focus of the thread has anything to do with forgetting that this is alpha.  LordVeoris, even after a first reminder from jmdsdf, didn't seem to catch on to the original post indicating that 173 and 180 series drivers just will not work in my situation.

I am completely aware that this is still heavy in testing.  But my experience, historically, has been that if an issue isn't reported before a release goes stable, it does not get fixed in the current version.  If, say, I were to report something wrong in Intrepid at this time, I would expect (based on past answers) to hear that its too late to fix Intrepid, check Jaunty.  Which is why I always switch early.

Basically, this thread indicated that I'm an nVidia user, that nVidia wasn't working for me, and I wanted to know what anyone knew.  I made it clear that the 96 series is the latest series that I could use, so fixes for 173 and 180 series do not apply at all.  The initial answers that came back were the best -- Ubuntu knowingly brought in a new Xorg that nVidia hadn't had time to adjust to.  Just wait, and give nVidia a chance.

LordVeoris strayed from the topic providing what seemed to be attractive fixes that, in the end, had nothing to do with my situation.  Of course, such answers lead to huge frustration.  Fortunately, after a second reminder, LordVeoris did come back and offer to try to find a fix for the 96 series.  I applaud any such efforts, including his return to the topic at hand.

---

### Post by jmdsdf on 2009-02-02
The latest updates for Jaunty now fix this problem! A big kudos to the developers! Now... if someone could just tell me why my sound isn't working any more. :p OK! Development version... I know. :)

UPDATE: with the SB Live Audigy that I have, I just had to install gnome-alsamixer, and turn off the SPDIF output that is enabled by default so my 5.1 analog output would work.

---

### Post by Gina on 2009-02-03
My sound, which was perfect, is now all crackly :(

---

