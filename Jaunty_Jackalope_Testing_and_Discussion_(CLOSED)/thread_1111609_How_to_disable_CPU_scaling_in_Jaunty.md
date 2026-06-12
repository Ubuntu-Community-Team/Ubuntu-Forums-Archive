---
title: "How to disable CPU scaling in Jaunty?"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Chris on 2009-03-30
[Edit: can someone please move this thread to the Jaunty forum?  I thought I was posting there.. thanks!]


It seems I go through this every release because everything gets moved around.  However, this time I have been unable to figure out how to do it myself.

In the old days I would use gconf-editor->gnome-power-management->cpufreq->policy_ac and set the permanent mode.  In Intrepid it was easier because I just went to System->Administration->Services and disabled the "CPU Scaling" service.  None of these options appear to exist in Jaunty.

I can set the mode in the CPU Frequency Monitor applet but it's not permanent.  I can certainly hack it and force the scaling mode by updating /proc at boot time but that's just a hack.

So anyone how to permanently disable the CPU scaling?

---

### Post by abyssius on 2009-03-30
> **Chris said:**
> [Edit: can someone please move this thread to the Jaunty forum?  I thought I was posting there.. thanks!]


It seems I go through this every release because everything gets moved around.  However, this time I have been unable to figure out how to do it myself.

In the old days I would use gconf-editor->gnome-power-management->cpufreq->policy_ac and set the permanent mode.  In Intrepid it was easier because I just went to System->Administration->Services and disabled the "CPU Scaling" service.  None of these options appear to exist in Jaunty.

I can set the mode in the CPU Frequency Monitor applet but it's not permanent.  I can certainly hack it and force the scaling mode by updating /proc at boot time but that's just a hack.

So anyone how to permanently disable the CPU scaling?

You could try uninstalling powernowd. I don't know about jaunty, but this works for intrepid.

```
sudo apt-get remove powernowd
```

---

### Post by Chris on 2009-03-30
> **abyssius said:**
> You could try uninstalling powernowd. I don't know about jaunty, but this works for intrepid.

Thanks but I don't have powernowd installed.

---

### Post by Slim Odds on 2009-03-30
How about cpudyn or powesaved?

---

### Post by Chris on 2009-03-31
> **Slim Odds said:**
> How about cpudyn or powesaved?

Nope.

I'm not sure how it's controlled in Jaunty except for the kernel-only stuff.  Maybe gnome-power-manager but I can't find any settings for it that control CPU frequency scaling.

---

### Post by indigas on 2009-04-19
Bump. Any other ideas? I have the same problem. It is not a good thing to limit CPU, while I'm using Intel Core2Quad Q6600 i wan't to get all performance and not to save energy. I tryed to turn all cores to Performance by using CPU Frequency Scaling Monitor, but each time I reboot, settings are reseted. Without limits Nautilus loads 2x faster.It's noticeble speeds for me.

---

### Post by keep-on-smiling on 2009-04-19
hi

try installing rcconf or bum and disabling there.

incidentally bum is a gui, while rcconf is run from terminal, using spacebar to select or deselect services. I usually use them both - remember to check before disabling something....

Cheers

---

### Post by ssam on 2009-04-19
i think the system should be using the ondemand governor, which should speed up the CPU when needed. there should not be a performance penalty.

maybe you should file a bug.

(ondemand also saves the most power, because it gets tasks done faster so the CPU can sleep sooner. if its working properly it should be the best for all systems)

---

### Post by indigas on 2009-04-19
> **keep-on-smiling said:**
> hi

try installing rcconf or bum and disabling there.

incidentally bum is a gui, while rcconf is run from terminal, using spacebar to select or deselect services. I usually use them both - remember to check before disabling something....

Cheers
Thank you problem is fixed. Disabled "On Demand" service while using rcconf and everything works just fine. :)

---

### Post by indigas on 2009-04-19
> **ssam said:**
> i think the system should be using the ondemand governor, which should speed up the CPU when needed. there should not be a performance penalty.

maybe you should file a bug.

(ondemand also saves the most power, because it gets tasks done faster so the CPU can sleep sooner. if its working properly it should be the best for all systems)
It's good idea for Notebooks/Netbooks and for people who want to save energy. I am not one of thoose. So I want to get full performance always. Like I said, as it is On Demand it doesn't mean, that it will speed up itself for opening nautilus or any other kind of software. It will speed up only when CPU usage will be closely to 100%, it seems to work like that. So this is not a good idea for me. I bought computer with Intel Core2Quad Q6600 processor not because I want to save energy, but because I want to get better performance. Which CPU Limiting on Demand would not let me to get.

---

### Post by Polygon on 2009-04-19
are you running an amd processor? i think the amd one is powernow-k8 or something like that

---

### Post by indigas on 2009-04-19
Just edited my previous message. Problem is fixed. Here is what I did:

1. Installed rcconf. (In terminal sudo apt-get install rcconf).
2. Opened it with terminal. (sudo rcconf)
3. Found "On Demand" service and disable it. 
4. Rebooted PC and all cores are changed to performance mode.

---

### Post by ssam on 2009-04-19
can you post the output of

```
cat /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate
```

according to [http://www.mjmwired.net/kernel/Documentation/cpu-freq/governors.txt](http://www.mjmwired.net/kernel/Documentation/cpu-freq/governors.txt) that is how often the kernel check to see if the CPU needs speeding up.

maybe you could also try lowering /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold

use
```
sudo bash -c "echo 80 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold"
```
to adjust values

---

### Post by indigas on 2009-04-19
> **ssam said:**
> can you post the output of

```
cat /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate
```

according to [http://www.mjmwired.net/kernel/Documentation/cpu-freq/governors.txt](http://www.mjmwired.net/kernel/Documentation/cpu-freq/governors.txt) that is how often the kernel check to see if the CPU needs speeding up.

maybe you could also try lowering /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold

use
```
sudo bash -c "echo 80 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold"
```
to adjust values

Here is output:
```
Anonim@Anonim-desktop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate
160000
Anonim@Anonim-desktop:~$
```

---

