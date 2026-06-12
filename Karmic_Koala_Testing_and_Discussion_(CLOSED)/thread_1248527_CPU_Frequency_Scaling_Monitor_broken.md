---
title: "CPU Frequency Scaling Monitor broken?"
date: 2009-08-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2009-08-24
The CPU Frequency Scaling Monitor panel applet will no longer change my CPU speed since, coincidentally, this was checked in:

```
cpufreqd (2.3.3-4ubuntu1) karmic; urgency=low

  * sensors-plugin: Change to support "ignore" lines in
    sensors.conf (LP: #403868).

```

I can still change my clock speeds with cpufrequtils:

```
sudo cpufreq-selector -c 0 -g performance &
```

Anyone else with this issue?

---

### Post by tekstr1der on 2009-08-24
Is the CPU frequency panel applet working for everyone?

---

### Post by Michaelg14 on 2009-08-24
Works for me.  :)

---

### Post by tekstr1der on 2009-08-25
Thanks for verifying. Looks like it was the recent policykit changes after all.

---

### Post by fela on 2009-08-25
I disable cool'n'quiet from my BIOS settings ;)

But when I had it enabled the cpufreq applet worked fine for me, I don't know what issue you're having.

---

### Post by Amaranth on 2009-08-25
What reason do you have for changing this? The ondemand governor should always be the best one to use.

---

### Post by tekstr1der on 2009-08-25
Well two separate reasons actually:

1) We are testing pre-release software. We should try to fiddle with every app and every option. The more we do this, the better things end up.

2) I have a cheesy atom-based netbook, so when it's plugged in, I set it to performance mode to ensure every clock tick is @1.6Ghz.


EDIT: @Travis Off-Topic, thanks for the compiz panel shadow Paper Cut fix. Removed the (any) & !(type=Dock) workaround and it's looking great!

---

### Post by Elliot44 on 2009-08-25
I have two intel dual core/core 2 duo desktops. I overclock. I've found the freq-scaling does work, but the applet display does not show the correct speed - the system runs fine though.

I came across this program that stresses the CPU and has compiled binaries all set to go for Linux/ubuntu/Mint and Windows. It is a clone of SuperPi. It is called "System Stability Tester" and can be found here: [http://systester.sourceforge.net/about.html]("http://systester.sourceforge.net/about.html")

The pre-compiled linux version of the program is slower than the XP version, but both show my CPU running at the overclocked speed of 3.0GHz and not what the freq-scaling shows 2.2GHz. Running the XP version under Wine is exactly as fast as under native XP and also shows the CPU running at 3.0GHz. 

I'm using version 0.9, which is about a year old but has re-compiled binaries and I'm getting lazy. 

If your running a newish intel machine and can get unto the bios - turning on/off "EIST" will turn on or shut down freq-scaling in ubuntu (if it's enabled in the kernel.) 

Conclusion: freq-scaling works and display changes, but dosen't show correct (top) speeds on my overclocked machines. This is fine with me. Just as long as I can have both speed when I need it and cool running for surfing etc.

---

