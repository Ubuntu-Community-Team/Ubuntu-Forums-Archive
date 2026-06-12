---
title: "Upgrade to 2.6.26 kernel in hardy?"
date: 2008-06-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bpl07 on 2008-06-28
I'd like to move to the new kernel of Intrepid Ibex, but I also don't want to screw up my stable hardy system.  Is there a safe way I can go about getting the new kernel on my system?  I'm currently using all the hardy proposed updates but was too scared to do the upgrade/update from the alpha 1 cd just yet.

---

### Post by ronacc on 2008-06-28
if you need a stable system do not upgrade to intrepid until it is released . running an alpha or beta system is for testing only and will bring breakage and instability . if you want to help test use a seperate partition or a VM .

---

### Post by Raptor45 on 2008-06-28
> **bpl07 said:**
> I'd like to move to the new kernel of Intrepid Ibex, but I also don't want to screw up my stable hardy system.  Is there a safe way I can go about getting the new kernel on my system?  I'm currently using all the hardy proposed updates but was too scared to do the upgrade/update from the alpha 1 cd just yet.

Short answer: no.

Why do you want the new kernel?

---

### Post by bpl07 on 2008-06-28
> **Raptor45 said:**
> Short answer: no.

Why do you want the new kernel?

I have all of my documents on a common ntfs drive that I share between xp and ubuntu.  When I use microsoft office through wine with these documents, they are opened as read only or not at all because the 2.6.24 kernel does not support shared mmap.  The 2.6.26 kernel does.

Stupid reason I know, but it bugs me.  I tried compiling my own kernel but gnome wouldn't load in it.  From what I've read 2.6.24 is here to stay on hardy, so I'll eventually need to upgrade to intrepid anyways.  I have no problem with fixing things that break, I just wanted to know if there was a simple way to get the new kernel without doing a full-fledged update to intrepid alpha 1.

---

### Post by exploder on 2008-06-28
You could add the Intrepid repo and only install the kernel packages, then disable the Intrepid repo. If the new kernel does not work out you can just boot using the old kernel and delete the new one in Synaptic.

This of course is a "try at your own risk" solution.

---

### Post by ronacc on 2008-06-28
no simple way . Iv'e been upgraded to intrepid since the repos opened with no MAJOR problems but that is no garunte you system wont trash completly . lots of people seem to be having problems with the just out alpha 1 cd so if you do decide to go ahead I would suggest apt or aptitude as the safest way right now.

---

### Post by soccerboy on 2008-06-28
I may have found a nasty bug in 2.6.26-2 kernel.  My kernel panicked when I tried to boot from it.  Same thing happened on the installation disk. I am typing from IIa1 but installed  by installing hardy first.  anyone experience similar things.

---

### Post by Raptor45 on 2008-06-28
> **soccerboy said:**
> I may have found a nasty bug in 2.6.26-2 kernel.  My kernel panicked when I tried to boot from it.  Same thing happened on the installation disk. I am typing from IIa1 but installed  by installing hardy first.  anyone experience similar things.

Please don't hijack the thread.

Back on the original topic; building the kernel is probably your best bet. I would definitely not recommend moving to Intrepid, its simply not meant for use yet.

What problems did you have getting gnome to start when you tried compiling the kernel? You are aware that nvidia driver needs to be patched before it can be installed?

---

### Post by soccerboy on 2008-06-28
> **Raptor45 said:**
> Please don't hijack the thread.

Back on the original topic; building the kernel is probably your best bet. I would definitely not recommend moving to Intrepid, its simply not meant for use yet.

What problems did you have getting gnome to start when you tried compiling the kernel? You are aware that nvidia driver needs to be patched before it can be installed?

Sorry if it seemed like I was hijacking the thread.  I was giving an example of stuff that could go wrong.  Reasons why not to rush to the latest on a stable/non-testing system.

---

### Post by bpl07 on 2008-06-28
> **Raptor45 said:**
> Please don't hijack the thread.

Back on the original topic; building the kernel is probably your best bet. I would definitely not recommend moving to Intrepid, its simply not meant for use yet.

What problems did you have getting gnome to start when you tried compiling the kernel? You are aware that nvidia driver needs to be patched before it can be installed?

When I logged in it would temporarily load then crash back to a terminal log in.

I have ati integrated graphics.  I used kernelcheck to build my kernel and went through almost everything in the configuration menu to make sure all of my hardware was supported.  After a few unsuccessful attempts (each taking roughly 4 hours of compiling) I gave up and decided to wait for an update to the repo.

When I load the alpha cd to package manager the kernel is available but in order to install the header files, which EnvyNG uses to configure the graphics card for the kernel, it asks me to uninstall a lot of software that I don't want to remove (g++, gcc, etc.)

---

### Post by Raptor45 on 2008-06-28
Building a kernel is not something I am overly familiar with; perhaps someone else can give more specific help in that regard?

> When I logged in it would temporarily load then crash back to a terminal log in.

That almost sounds like a video driver error. Did you ever try switching to vesa in your xorg.conf? Just to test? Or could you tell the problem was something else?

soccerboy: Not a problem, just trying to keep the original issue from getting lost in the shuffle; your phrasing made it seem to me you were asking for help. Perhaps I was too hasty in that reply.

---

### Post by ronacc on 2008-06-28
trying to install the intrepid kernel in hardy is a recipe for disaster use a seperate install on a different partition or run a VM .
on your self compiled kernel check your logs to try to determine why gdm isn't starting , like raptor45 siad it may be a video driver problem .

---

### Post by bpl07 on 2008-07-07
I got 2.6.25 working, now I'm trying 2.6.26 again.  The most recent proprietary ati driver (8.6) was the first to be compatible with 2.6.25.  I'll report back on the results with 2.6.26 soon.

---

### Post by bpl07 on 2008-07-07
> **bpl07 said:**
> I got 2.6.25 working, now I'm trying 2.6.26 again.  The most recent proprietary ati driver (8.6) was the first to be compatible with 2.6.25.  I'll report back on the results with 2.6.26 soon.

> To the dismay of some users, Catalyst 8.6 for Linux doesn't support the Linux 2.6.26 kernel or X.Org 7.4 (X Server 1.5).

Boo, gotta wait for the next ati driver for 2.6.26 support.

However, using the mesa drivers, I can confirm that the issue I mentioned in the fourth post is fixed in kernel 2.6.26.

---

### Post by deepclutch on 2008-08-07
@OP : why not compile one yourself.there are lotta guides out there :) .I will be compiling one with zen sources...and I expect the Atheros lan card driver is more matured and better in 2.6.26 kernel.

---

### Post by mattr01 on 2008-08-26
I need the new kernel because according to [this]("http://www.hauppauge.com/site/support/linux.html") page, it provides support for my EyeTV Hybrid, which is a rebadged Hauppauge WinTV HVR-900 TV Tuner.  And as you can guess, I want to watch TV on my ubuntu box.  But nonetheless, I can install intrepid alpha 1 into a new VM.  It doesn't bother me.

---

### Post by dozersmasher on 2008-09-24
Question for what I am working on.

What is your architecture?

Also, you may want to have broadband for my idea.

And will 2.6.27 work?

---

### Post by dozersmasher on 2008-09-24
NO!!! DO NOT RUN EITHER OF THE SCRIPTS I HAD POSTED!!! believe me, you don't want to have to deal with that.
I just rebooted to try out the new kernel,
the first time, it booted in the server kernel, the second time, after I reenabled it, it booted in generic, got half-way through and froze, which I am guessing is the GUIs way of saying kernel panic.

So, uh, bad idea. never mind.

---

### Post by singtoy on 2008-09-25
Question for what I am working on.
:popcorn:

---

