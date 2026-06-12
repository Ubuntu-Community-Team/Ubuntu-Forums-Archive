---
title: "New kernel killed sound"
date: 2008-06-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2008-06-18
The new kernal was installed on my system yesterday but after install a few extra lines were displayed during boot up, something about ELF I think. The system would boot and let me log in correctly then hang.

I've been running on the previous kernel until today's updates which corrected the bootup issue but I've now got no sound. I'm unsure if it's the kernel update or another update that came with it.

The soundcard is a VIA high definition audio controller.

Anyone else getting interesting side effects?

---

### Post by dyno7351 on 2008-06-18
When Update Manager installed the latest kernel (version ending in 19), my display only allowed 640x480. The only error I could find in the log files was something to the effect that EDID failed. I presume this means X couldn't probe my Samsung 712N monitor (LCD). The Nvidia driver does load and at the lower resolution the desktop effects work. If I boot into version 18 everything works normally again - 1280x1024.

---

### Post by Eclipse. on 2008-06-18
All of this is expected, the actual kernel itself is still in development.Stick to your working hardy kernel if you can.

---

### Post by pferraro on 2008-06-18
My experience is the new kernel killed pulseaudio specifically - since my sound works if I change my settings to use alsa.

---

### Post by philinux on 2008-06-18
Killed my machine completely. Previous kernel works fine. Tried recovery mode no dice.

However I booted it today and it booted fine so something must have fixed itself, very odd.

---

### Post by ShirishAg75 on 2008-06-18
It killed pulseaudio yesterday, today the sound works, I am using exaile bzr development snapshots and there is a lag between two songs. Also the CPU usage was high yesterday which got also fixed today in some of the updates. Let's see where it goes from here.

---

### Post by chrismine on 2008-06-18
I can confirm both issues. When using ALSA I have sound and using the nv driver I have a 1280X1024 resolution on my one screen. At least it is still usable.  My problem is that the updates removed the nvidia kernel headers so my previous kernel does not work with the nvidia drivers. What bugs me is that updates never did this before. I was always able to go back to the previous kernel. Anybody knows id\f this is by design or a bug. Maybe I did something wrong.  Off topic: When doing updates I always install the updates first and then only do the Partial update if any.  I am eagerly awaiting the fixed kernel and nvidia drivers. Miss my compiz!  Forgot to mention: lm-sensors also not working, kernel interface error.

---

### Post by psyke83 on 2008-06-18
> **chrismine said:**
> I can confirm both issues. When using ALSA I have sound and using the nv driver I have a 1280X1024 resolution on my one screen. At least it is still usable.  My problem is that the updates removed the nvidia kernel headers so my previous kernel does not work with the nvidia drivers. What bugs me is that updates never did this before. I was always able to go back to the previous kernel. Anybody knows id\f this is by design or a bug. Maybe I did something wrong.  Off topic: When doing updates I always install the updates first and then only do the Partial update if any.  I am eagerly awaiting the fixed kernel and nvidia drivers. Miss my compiz!  Forgot to mention: lm-sensors also not working, kernel interface error.

And that's why you shouldn't do a Partial Upgrade without care to check that it only removes obsolete packages.

---

### Post by chrismine on 2008-06-18
> **psyke83 said:**
> And that's why you shouldn't do a Partial Upgrade without care to check that it only removes obsolete packages.

I have been told, LOL!  I may have missed it his time because I usually checked that. With todays partial upgrade I kept all the packages, because there was a lot I do not know about.

---

### Post by macroshaft on 2008-06-18
A few points, firstly the new kernel was working this morning and this afternoon is locking up again, no changes to the system though.

And secondly everyone says check for obsolete packages before doing a partial upgrade but I've never heard anyone mention how you determine if a package is obsolete.

Is there no way the update tools, either graphical or command line, could be modified to 'tag' the obsolete ones so you can tell?

---

### Post by Raptor45 on 2008-06-18
Its not so much that a package is "obsolete" as someone has yet to upload all the correct dependencies. Just go into synaptic and mark the affected upgrades, synaptic will warn you whats going to happen. If packages are going to be removed, just wait it out.

---

### Post by psyke83 on 2008-06-18
> **Raptor45 said:**
> Its not so much that a package is "obsolete" as someone has yet to upload all the correct dependencies. Just go into synaptic and mark the affected upgrades, synaptic will warn you whats going to happen. If packages are going to be removed, just wait it out.

Yes, but older packages need to be removed sometimes. For example: libntfs-3g24 became obsolete by libntfs-3g28. There may be some situations in which a dist-upgrade is necessary to "force" new packages to get installed. What you said is best, though: If packages are going to be removed, just wait it out.

---

### Post by macroshaft on 2008-06-18
Now that's the missing link! I'll bare it in mind, thanks.

---

### Post by eeclark on 2008-06-18
Audio pumps out correctly at GDM. (Heard the drums on the Line Out on my laptop).
Once Gnome/Desktop starts to load, the start up sound sounds like an old 78 record playing (all gritty and poppy, nice for nostalgia, bad for my speakers?). -- oh and it comes out the laptop speakers instead of the "line out" like the drums did.

---

