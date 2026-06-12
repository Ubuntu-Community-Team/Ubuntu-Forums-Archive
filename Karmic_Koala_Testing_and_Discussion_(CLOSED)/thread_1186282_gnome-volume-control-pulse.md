---
title: "gnome-volume-control-pulse"
date: 2009-06-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by taavikko on 2009-06-13
This was dropped in jaunty dev-cycle, will this cycle re-introduce this
to manage volume instead of traditional gnome-volume-control ?

---

### Post by Bou on 2009-06-13
I would welcome that. What was it removed for in Jaunty, anyway?

---

### Post by Slug71 on 2009-06-13
Im guessing it will be reintroduced.

It was dropped because it was pretty buggy. Jaunty was a bug fix release and to focus on boot performance and the new volume control was a little to bleeding edge for that release goal.

---

### Post by 23meg on 2009-06-13
> **taavikko said:**
> This was dropped in jaunty dev-cycle, will this cycle re-introduce this
to manage volume instead of traditional gnome-volume-control ?

That is the plan, as per the [desktop-karmic-audio-experience]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-audio-experience") blueprint. Do note the current values of the "Definition" and "Implementation" fields, though. 

> **Slug71 said:**
> Jaunty was a bug fix release

It wasn't, and there's no such concept.

[quote=Slug71]and to focus on boot performance and the new volume control was a little to bleeding edge for that release goal.[/QUOTE]

Separate people work(ed) on boot performance and desktop audio, so it's not about that mythical concept of "release focus". It was tested and found to have limitations that made it unsuitable for release at the time, that's it.

---

### Post by Bou on 2009-06-13
> **23meg said:**
> It was tested and found to have limitations that made it unsuitable for release at the time, that's it.

Do you know what these limitations were, and / or whether they have been solved now?

---

### Post by 23meg on 2009-06-15
> **Bou said:**
> Do you know what these limitations were, and / or whether they have been solved now?

Here are some:

[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/358131](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/358131)
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/322909](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/322909)
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/323498](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/323498)
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/377188](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/377188)
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/319443](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/319443)

---

### Post by ranch hand on 2009-06-15
I use gnome-alsamixer so I don't have any problems.

---

### Post by taavikko on 2009-06-15
> **ranch hand said:**
> I use gnome-alsamixer so I don't have any problems.

Thanks for this valuable information, the power of choice is gift we must cherish in gnu/linux community.

However, since this "gnome-volume-control-pulse" is going (someday) to be the default, might as well use it for testing it.

---

### Post by Regenweald on 2009-06-15
i noticed for the blueprint the win and mac do audio mixing in the kernel, is that why audio is 'better' in those OS'es ? Is linux audio implemented above the kernel ? please explain, I'm trying to understand the setup.

---

### Post by ranch hand on 2009-06-15
Regenweald
I can't help with your basic question and have no experience with Mac at all.

However, this box was designed to run Vista, came with home premium installed.  Even after the installation of the audigy sound card and Altec Lansing 5.1 speakers the sound was not good.  True it is an old card that I put in in anticapation of switching to Ubuntu.

The audio in Ubuntu is at least twice as good as it was under Vista.

I should note that Ubuntu seems to love this box so it may well be that I am just really lucky.  Audio, sometimes after a fight, on other linux flavors is the same though.

---

### Post by amano on 2009-06-15
No. The audio shouldn't care if being mixed in kernel oder userland. Many ALSA drivers are still broken these days. Much of those defects were shown by PulseAudio which stress-tests those driver a lot (by doing some advanced fancy things).

---

### Post by psyke83 on 2009-06-15
> **Regenweald said:**
> i noticed for the blueprint the win and mac do audio mixing in the kernel, is that why audio is 'better' in those OS'es ? Is linux audio implemented above the kernel ? please explain, I'm trying to understand the setup.

Vista and recent Mac OS X versions now do audio mixing in userland, as far as I'm aware.

---

### Post by psyke83 on 2009-06-15
> **amano said:**
> No. The audio shouldn't care if being mixed in kernel oder userland. Many ALSA drivers are still broken these days. Much of those defects were shown by PulseAudio which stress-tests those driver a lot (by doing some advanced fancy things).

Well, there is a performance hit when mixing in userland. Adding SSE optimizations to the resamplers will eliminate the performance deficit, though I'm not sure if it'll happen any time soon.

---

### Post by RAOF on 2009-06-15
> **psyke83 said:**
> Well, there is a performance hit when mixing in userland.

Um, why?  Code in the kernel isn't magically faster because it's in the kernel.

In fact, I could make a plausible argument for why userspace mixing is more efficient: Because all your userspace sound-producers are being routed through a single userspace daemon, you need to copy less data userspace->kernel.

I don't know whether this is true or not.  Do you have a source for "userspace mixing is less efficient"?

---

### Post by Regenweald on 2009-06-15
Thanks all, I get it a little better. Will do some research. Look forward to using/testing the new audio stack. On it's way soon RAOF ?

@Ranch Hand, same here, dell inspiron 531 and runs anything i put on it immaculately 8.04-9.10 testing, vista, XP, OpenSolaris. I've got great install mojo.

---

### Post by jeffus_il on 2009-06-23
> **RAOF said:**
> Um, why?  Code in the kernel isn't magically faster because it's in the kernel.

In fact, I could make a plausible argument for why userspace mixing is more efficient: Because all your userspace sound-producers are being routed through a single userspace daemon, you need to copy less data userspace->kernel.

I don't know whether this is true or not.  Do you have a source for "userspace mixing is less efficient"?

I'm not a kernel expert but I do know that the original Minix kernel was a set of programs, not one giant kernel like we have today. All those programs, like memory manager, file manager, drivers, and the whole long list of kernel functions were combined together in the Linux kernel only for performance issues, that is [COLOR=Red]the overhead of inter process communication[/COLOR]. It's much easier to maintain separate programs and of course they can't clobber each others memory by mistake. Programs in userspace have a much higher communications overhead with the kernel. Could be that things are changing and inter-process comms are improving, but the bottom line is that there is more work to be done, which can of course hit performance. I'll leave it to the "profilers" to do exact measurements! I remember a Professor Tanenbaum from a Dutch University who wrote about this...
Another thought, If you are right, we don't really need loadable modules in the kernel...

---

### Post by Starks on 2009-07-13
Any updates on g-v-c-p?

---

### Post by Hairy_Palms on 2009-07-13
The bug that made the new volume control useless for me was
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/322909](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/322909)

---

