---
title: "random lockups (caps lock blinks)"
date: 2008-09-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by reacocard on 2008-09-12
Since upgrading to intrepid, I've been experiencing random lockups. Everything will just freeze, completely unresponsive to anything and the caps lock light blinks, forcing a hard reset. Any ideas?

Thinkpad T61, intel c2d@2.5ghz, intel x3100 graphics, intel 4965 wifi, 2gb RAM, clean install of intrepid alpha 5 with all updates

---

### Post by olskar on 2008-09-12
That usually means a kernel freeze I think? I do not know why though.. :/

---

### Post by plun on 2008-09-12
Well... I think we have some sort of kernel regression...

Somehow "sluggish".

I am testing latest PulseAudio and it is heavily disturbed.

```
I: module-alsa-sink.c: Underrun!
N: module-alsa-sink.c: Increasing wakeup watermark to 247,01 ms
D: sink-input.c: Requesting rewind due to corking
D: module-alsa-sink.c: latency set to 250,00
D: module-alsa-sink.c: hwbuf_unused_frames=5359
D: module-alsa-sink.c: setting avail_min=5888
I: sink-input.c: Freeing input 98 "ALSA Playback"
D: module-alsa-sink.c: Requested to rewind 65536 bytes.
D: module-alsa-sink.c: Mhmm, actually there is nothing to rewind.
I: module-stream-restore.c: Restoring device for stream sink-input-by-applicatio
```

Exaile manage its best....:)

Never a complete freeze for me.

---

### Post by jzerbini on 2008-09-12
> **reacocard said:**
> Since upgrading to intrepid, I've been experiencing random lockups. Everything will just freeze, completely unresponsive to anything and the caps lock light blinks, forcing a hard reset. Any ideas?


AKA Kernel Panic :D

Bad thing is that we're not reading the messages log while that happened, so it's hard to know what really happened.

I had 2 kernel panics so far, after I was already logged in. 
I was wondering if it was the wireless adapter fault. I've compiled my own modules (Atheros AR242x).

---

### Post by plun on 2008-09-12
Anyone knows how to change printk  ?

[http://kernelnewbies.org/KernelHacking-HOWTO/Debugging_Kernel](http://kernelnewbies.org/KernelHacking-HOWTO/Debugging_Kernel)

All I got in my kern.log after boot

> Sep 12 20:44:01 plun kernel: [24061.157588] APIC error on CPU0: 40(40)
Sep 12 23:40:27 plun kernel: [34647.461129] APIC error on CPU0: 40(40)

:confused:

---

### Post by syko21 on 2008-09-13
I'm getting kernel panic on boot when X starts on 2.6.27-3. I booted into -2 fine.

Hardware:

Intel C2D T5600 1.83ghz
2GB RAM
Nvidia 7400 Go (using the nv driver until I figure out whats going)
Broadcom bluetooth module
Intel 4965agn

---

### Post by RaZoR1394 on 2008-09-13
I have this as well when I haven't used the laptop for a while. Uncharging the battery and then fully charging it normally fixes it which usually means a battery calibration problem.

---

### Post by MALEADt on 2008-09-13
You could try installing the kerneloops package, which tries to capture the kernel panics and send them to the kerneloops.org website. Not only you help the kernel developers by doing so, you will also know more yourself about the reason your system is crashing :)

(Shouldn't this app be enabled by default, or by prompt on installation? If only 50% of the Ubuntu userbase would do this, it'd be a huge help to kernel devs I guess)

---

### Post by Syke on 2008-09-18
This happens on my laptop when my 4965 is enabled - quite frequently. I haven't had a crash while using Ethernet. Alpha 5 with updates installed. Will try out Alpha 6 soon then I'll file a bug.

---

### Post by reacocard on 2008-09-18
> **Syke said:**
> This happens on my laptop when my 4965 is enabled - quite frequently. I haven't had a crash while using Ethernet. Alpha 5 with updates installed. Will try out Alpha 6 soon then I'll file a bug.

Now that you mention it, it did seem to happen more often if I'm actively using the wireless. I've reverted to the hardy kernel for now, which seems to work just fine. If you do file a bug please post the link here so I can follow it as well.

---

### Post by klange on 2008-09-18
iwl wireless drivers are quite horrid. (It's the modules, not the kernel, personally, I've had *much* better experience with the Intrepid kernel/modules, but the problem still persists, can't leave my wireless on and leave my laptop without it faulting)


Ah, how I long for the old days of IPW...

---

### Post by Syke on 2008-09-19
I swapped my wifi card to 3945, and it's rock solid - seems it's just the 4965.

Alpha-6 was just released, so I'll download that, switch back to 4965, and post the results.

---

### Post by Syke on 2008-09-19
Bug posted at [https://bugs.launchpad.net/ubuntu/+bug/272015](https://bugs.launchpad.net/ubuntu/+bug/272015)

---

### Post by plun on 2008-09-20
> **MALEADt said:**
> You could try installing the kerneloops package, which tries to capture the kernel panics and send them to the kerneloops.org website. Not only you help the kernel developers by doing so, you will also know more yourself about the reason your system is crashing :)

(Shouldn't this app be enabled by default, or by prompt on installation? If only 50% of the Ubuntu userbase would do this, it'd be a huge help to kernel devs I guess)

Yup... "mdz" fixed this package... coincidence..:)

[http://packages.ubuntu.com/intrepid/kerneloops](http://packages.ubuntu.com/intrepid/kerneloops)

[https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007130.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007130.html)

---

