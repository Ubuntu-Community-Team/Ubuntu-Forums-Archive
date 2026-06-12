---
title: "rt-kernel for lucid?"
date: 2009-12-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bluesscream on 2009-12-21
is there already rt-kernel developement available?

---

### Post by gnomeuser on 2009-12-21
There isn't a port of the rt patchset to the .32 kernel yet so you shouldn't expect this.

On the plus side merging functionality from rt into the mainline kernel is progressing and is in high demand especially by embedded vendors. Hopefully soon you'll have a means to boot a realtime capable kernel without a separate kernel package (likely either by a runtime throttle or a boot time parameter)

---

### Post by ranch hand on 2009-12-21
> **gnomeuser said:**
> There isn't a port of the rt patchset to the .32 kernel yet so you shouldn't expect this.

On the plus side merging functionality from rt into the mainline kernel is progressing and is in high demand especially by embedded vendors. Hopefully soon you'll have a means to boot a realtime capable kernel without a separate kernel package (likely either by a runtime throttle or a boot time parameter)
When is this likely to come about?

My son has an AMD mobo and some kind of tri-cpu 64bit system.  He would love to use Studio but the rt kernel will not install on his box.

The generic works fine.

Also, isn't there a way, already, to control your cpus usage?  Where do I even look for info on that, assuming it exists?

---

### Post by gnomeuser on 2009-12-21
> **ranch hand said:**
> When is this likely to come about?


It's notoriously hard to predict when the full rt tree will be merged, I would feel uncomfortable saying it would happen soon. 

However the embedded vendors are very interested in seeing this happen also both Novell and Red Hat have real time products on the market. Having the code in the kernel would mean a lot of saved effort for a great number of people.

Solving the remaining technical issues will likely be a priority for them.

I feel optimistic about at least major parts being merged during the next year.

---

### Post by bluesscream on 2009-12-22
In kernel.org sites last rt-patch is for 2.6.31-6. I'd really hail these rt-features being integrated into mainstream kernels so we'll have to take care for only one trunk.
Some time soon I'll give  lucid's  2.6.32/33 kernels a try and test their low latency performance for jack firewire audio apps.

---

### Post by trulan on 2009-12-22
I've been keeping my eye on the rt kernel package as well.  I do have an install of Lucid on my desktop, but as I'm sure you know the rt kernel is still the one from Karmic.  I'll have to hook up my firepod and see what the .32 generic kernel can do.
> **ranch hand said:**
> isn't there a way, already, to control your cpus usage?  Where do I even look for info on that, assuming it exists?
I'm not quite sure what you mean.  You can set the cpu governor, and set some process priorities, but real time preemption is a different animal.

There seems to be a slightly newer rt kernel in gmaq's AVLinux.  It exhibits similar nvidia issues to the current Lucid generic kernel, so I guess that's a good sign.  :confused:  If you get impatient waiting for something new along this line in Lucid (like me), I guess you could try that one.

---

### Post by ranch hand on 2009-12-22
I had the impression, very likely falsely, that you could give presidence to particular functions to individual cpu's in a multi cpu set up.

I am going to look at the scaling monitor because in sounds neat.  I believe I already have my cpu's going at full blast.  My bios has a setting for that.

---

### Post by falconindy on 2009-12-22
Find instructions to compile a kernel. There's a hundred of tutorials, and its a fairly simple process. During the `make menuconfig` stage, set the following options:

```

Processor type and features
  |--> Preemption Model
  |       |--> Preemptable Kernel (Low-Latency Desktop)
  |
  |--> Timer Frequency
          |--> 1000 HZ

General Setup
  |--> RCU Subsystem
          |--> Preemptable tree-based hierarchical RCU

```
You also might look into getting Con Kolivas's [BFS Scheduler]("http://ck.kolivas.org/patches/bfs/2.6.32-sched-bfs-311.patch"), or even the [entire -ck patchset]("http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.32/2.6.32-ck1/"). 10000Hz timer frequency is insanity (and insanely smooth) if you can run stable with it.

Note that these patches aren't guaranteed for the .33 kernel (yet).

---

### Post by ranch hand on 2009-12-23
I will pass that on to my son.  He is the one interested in recording using studio.  The RT kernels that he has tried will not install on his hardware although the generic has no problem with it.

What he wants is the capability to give recording high priority for cpu power.

---

### Post by diebels on 2009-12-23
You can change priority by right-clicking a process in gnome-system-monitor.  Also see nice and renice commands.  But I'm not sure how useful this will be compared to a rt-kernel.

---

### Post by gnomeuser on 2009-12-23
> **ranch hand said:**
> I had the impression, very likely falsely, that you could give presidence to particular functions to individual cpu's in a multi cpu set up.

I am going to look at the scaling monitor because in sounds neat.  I believe I already have my cpu's going at full blast.  My bios has a setting for that.

You can also look at the Control Groups feature. I believe that should let you control which processes have access to how much of which resources. However I haven't played with this at all so I could be wrong, also it looks terribly complex.

---

### Post by ranch hand on 2009-12-23
> **diebels said:**
> You can change priority by right-clicking a process in gnome-system-monitor.  Also see nice and renice commands.  But I'm not sure how useful this will be compared to a rt-kernel.
WOW, thanks for that.  I thought I had fooled with G-S-M about all you can.  Live and learn.

Thanks again, that will be handy for me.  I run boinc on here and have is set pretty aggressive (right now all 4 cpu's are at 100%) with the condition that it gives me the cpu power I need.  Changing the preferences there is a pain in the but if you have to do it every time you need to do something intense on Gimp or even just put some tunes an a CD.

I will definately tell my son about that.  I tried it and it is easy and slick.  I do not know if it will do for hem or not.

It sure will for me.

That is really neat.

---

### Post by bluesscream on 2009-12-26
> **falconindy said:**
> 
You also might look into getting Con Kolivas's [BFS Scheduler]("http://ck.kolivas.org/patches/bfs/2.6.32-sched-bfs-311.patch"), or even the [entire -ck patchset]("http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.32/2.6.32-ck1/"). 10000Hz timer frequency is insanity (and insanely smooth) if you can run stable with it.

In the meantime I read a lot of scheduler discussion personalized to Molnar and Kolivas (new for me, I started with linux after Con Kolivas' withdrawal) without really understanding the background. Compiled a customized 2.6.32-ck1 and tested with identical settings against 2.6.31-9-rt and 2.6.31.17-generic on my elderly amdx2 nvidiachipset desktop and notebook  with intel dualcore and chipset, but still in karmic. My first impression:  On the desktop I found no relevant difference for native linux audio but wine/wineasio/vst stuff even better running with karmic's original 2.6.31-17-generic then with -9-rt or -ck. On the notebook I found -ck better performing.
BFS looks promising. Thank you very much for this christmas present ;)

---

### Post by geoff123 on 2010-02-21
I've tried the -rt kernels before and never got that much better performance and they always have some weird issues also (unless I build myself from kernel.org source).  

What I would like to see for Lucid is a generic kernel with the timer set to 1000HZ (instead of 250HZ) and low-latency desktop preemptible set.  Apparently this is better for midi timing and rosegarden recommends it.  

I've built generic kernels along with nvidia driver before to do this, but it would be great to have an ubuntu package that has this also.

---

