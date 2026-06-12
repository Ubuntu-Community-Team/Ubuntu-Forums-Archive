---
title: "Laptop Kernel Panic Continually after 8.10 Upgrade"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by ergjoop3 on 2008-11-16
Hi

I recently upgraded my Lenovo Thinkpad T61P to 8.10 from 8.04.

I am experiencing a serious number of kernel panics (where the display locks up and the capslock light blinks) after the upgrade. There have already been 5 since I started using the new distribution this morning. 

I cannot continue to work in this way, obviously. This did happen infrequently (once a month) in 8.04, but it was not so serious. How do I check what went wrong in this updgrade?

It this a hardware problem? Are there any known resolutions?

Thanks very much.

---

### Post by djm-uk on 2008-11-16
I had this on one install - I /Think/ it was down to a dodgy RAM stick. IIRC I had no end of problems with the install CD failing to read & Kernel Panics & in the end I ran memtest & found a failing RAM area... It might even have been temperature related just to add to the fun!

David

---

### Post by eldragon on 2008-11-16
> **ergjoop3 said:**
> Hi

I recently upgraded my Lenovo Thinkpad T61P to 8.10 from 8.04.

I am experiencing a serious number of kernel panics (where the display locks up and the capslock light blinks) after the upgrade. There have already been 5 since I started using the new distribution this morning. 

I cannot continue to work in this way, obviously. This did happen infrequently (once a month) in 8.04, but it was not so serious. How do I check what went wrong in this updgrade?

It this a hardware problem? Are there any known resolutions?

Thanks very much.

if you have been experiencing these locks under hardy, dont expect this to be a software problem

run memtest for 24hs.

stress the cpu and check for temps with the cpuburn pacakge.


these kernel panics shouldnt happen at all on a working computer.

---

### Post by ergjoop3 on 2008-11-16
> run memtest for 24hs.

I will do this.

> stress the cpu and check for temps with the cpuburn pacakge.

Looks like this is a risky process. Any other way to get the same result?

Also, I have Lenovo warranty. Whenever I call, they ask me to prove the hardware problem. Will these suffice as evidence? Or do I need to run their software package. Does anyone know?

Thanks very much for your help.

---

### Post by djm-uk on 2008-11-16
If memtest reports faulty ram then that is a hardware problem...

In my experience most faulty ram shows up quite quickly - certainly in the first run of tests, as you are experiencing problems from startup rather than from when the machine has been on for a while so it doesn't sound temperature related...

David

---

### Post by ergjoop3 on 2008-11-16
Sorry for being unclear. The problems were after the machine was running for about 1-2 hours.

---

### Post by djm-uk on 2008-11-16
OK So run memtest for at least that long.... I think tt exercises the CPU as well ...

David

---

### Post by Duf_Sh on 2008-11-16
I've been having this kind of problem too, might be temperature related since acpi -t gets me something around 80-85 celsius when I'm stressing my laptop a bit; most probably software related since I don't have that kind of problem on vista (which is a huge cpu drain) or on 8.04 (using 8.10 here)
Also, it almost never does this on startup, just after 30-60 minutes or so, and putting cpu policy on powersave gets the temperature down to 60-65...

---

### Post by trampas on 2008-11-17
I had same problem, installing the backport of the wifi drivers fixed part of the problem. However I get a kernel panic now about every 3 days. No it is not hardware as 8.04 had no problems. 

Trampas

---

### Post by djm-uk on 2008-11-17
> **trampas said:**
> ... No it is not hardware as 8.04 had no problems. 

Trampas

Not true, if you have dodgy RAM it can show up with a change in the memory usage patterns so the faulty bits are now in a critical area...
(EG a machine that ran fine, but would NOT install an AV package turned out to have faulty RAM not a malware infection!)

David

---

### Post by Duf_Sh on 2008-11-18
Still, the dodgy ram doesn't explain the intense heat that didn't show up either in Windows or in 8.04...

---

### Post by ergjoop3 on 2008-11-18
I got this error on startup at least two times, suspecting bad ram. Duf_Sh, how did you measure cpu temp and what is the expected value?

---

### Post by ergjoop3 on 2008-11-18
Oh, using apci -t I get
     Battery 0: Charging, 94%, 00:00:41 until charged
     Thermal 0: ok, 47.0 degrees C
     Thermal 1: ok, 49.0 degrees C

just under normal use. Is this okay?

---

### Post by ergjoop3 on 2008-11-18
When loaded (~100% on both cores)

     Battery 0: Full, 100%
     Thermal 0: ok, 72.0 degrees C
     Thermal 1: ok, 67.0 degrees C

Please let me know if I should be concerned about these values.

---

### Post by Duf_Sh on 2008-11-19
Maybe there are two totally unrelated problem, since my acpi -t returned almost 85 at times, soon before a hard lockup. I also tested my ram with the program included with ubuntu (last option in grub) and it said it was ok...

---

### Post by underyourskin on 2008-11-19
I had many panics while attempting to install ubuntu/xubuntu on other pc's. i got round it by using an iso image for a 'lesser machine' than the one that's recommended, then going through the normal course of updates when installed.

---

### Post by ergjoop3 on 2008-11-20
Sorry, I don't understand the last solution.

---

### Post by ergjoop3 on 2008-11-20
This issue is getting even more weird. When I use the laptop in one office, this crash almost never happens. I connect to the internet via wireless.

But in my other office, I have already seen the panic twice in the past hour. I connect via wired ethernet.

The method of internet is the only discernible difference between the two locations. My laptop has not peripherals attached to it. Ambient temperature is within +/- 10 degrees (~70 degrees) F at all locations.

What is going on?

Thanks.

---

### Post by Duf_Sh on 2008-12-08
Maybe something wireless-driver-related? I've already heard something like this, think it was in 8.04 though...

---

### Post by ergjoop3 on 2009-01-17
Tried installing wireless in the other office. It is still crashing there and not anywhere else that I can tell.

---

### Post by ergjoop3 on 2009-01-20
Any idea how to find root cause of Kernel panic? I.e., some log

---

### Post by trampas on 2009-01-21
After upgrading to 8.10 I was having kernel panics, about once a day usually with wireless. Did a backport of the wireless drivers and problem went from once a day to once every couple of weeks. 

I just did a clean install of 8.10 and did not do backport and so far I have had a kernel panic once in 3 days. 

I ran memtest86 for 9 hours with out a problem thus I doubt it is a memory issue. 

Does anyone know a good way to debug kernel panics? I tried the ALT-sysrq but when I get panic everything seems dead. 

Trampas

---

