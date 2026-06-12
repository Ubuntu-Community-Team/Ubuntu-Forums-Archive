---
title: "Jaunty CPU scaling steps misdetected"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by scorchedbysun on 2009-03-13
Hello,

I'm testing the Jaunty Alpha releases and I can see there have been big changes in powernow and/or cpufreq. Namely no cpufreq modules are loaded anymore, powernowd is not present, and yet the kernel still scales the CPU frequency.

My problem is that before (last version I tested was 8.04) my CPU speeds were detected correctly (but only after I passed "options powernow-k7 acpi_force=1" to the module, and even then after a few restarts only) and now they are no more.

On 8.04 the available speeds were: 663, 1.06, 1.33, 1.46, 1.59, 1.86.

Now, the speeds are: 929, 1.06, 1.19, 1.33, 1.46, 1.59, 1.72, 1.86.

(As you can see, the CPU is underclocked slightly).

I don't mind the extra steps, but I do mind the higher-than-before minimum speed.

What has changed? Should I file a bug report? If so, should I file it with Ubuntu devs or kernel devs?

Thanks for any info.

System is:
Acer Ferrari 3000 notebook
Athlon XP 2500+
chipset VIA KM400
graphics Mobility Radeon 9200
sound VIA 8235

---

### Post by pelle.k on 2009-04-22
Apparently, powernowd is not used anymore, and furthermore, the frequency modules and governors is compiled in the kernel, not as modules. I can see that being be a problem for people wanting to use another module for speedstepping, and/or passing options to that module.
In my case, the "performance" governor is loaded by default, while it used to be the "ondemand" governor (<jaunty). On a laptop, that's bad, even though i can fix that myself, i'm thinking of new ubuntu users.
I'm not sure if i'll post a bug on this. I'm not sure if it would matter being so close to the "release" date and all. It's not really a bug per se, but certainly an annoyance.

EDIT: Links
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355232](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355232)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/327193](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/327193)

EDIT2: Link about default governor in jaunty
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343354](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343354)

---

### Post by scorchedbysun on 2009-04-22
Thank you for your answer.

Funny thing is, I installed Jaunty anew on the same notebook maybe a week ago and on first boot the frequency steps were correct (like they used to be in Hardy).

Because this computer is unable to resume from standby under Jaunty, I put it in standby, hoping the newer Jaunty would resume correctly (bugs [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339336](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339336) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/362468](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/362468) both filed by me and unfortunately ignored) I suspended the computer (it didn't resume) and after restart the frequencies were as described in my post above.

This situation is actually worse and better than it was in Hardy.

It is worse because the min speed of the CPU is higher than I know it can be. It is better, because in Hardy the CPU speeds were incorrectly detected (2.17GHz instead of 1.86 GHz down to 773 MHz instead of 663 MHz) until I input

```
options powernow_k7 acpi_force=1
```

into /etc/modprobe.d/options

BTW, when Jaunty started for the first time, the available speeds were incorrect (773 through 2.17), like in Hardy.

It's almost as if on first boot Jaunty used powernowd and only after it failed to resume from standby it started using whatever is built into the kernel.

Jaunty is very frustrating :-( On the one hand it's much improved from Hardy, and on the other it introduces a series of new problems (at least for me).

---

