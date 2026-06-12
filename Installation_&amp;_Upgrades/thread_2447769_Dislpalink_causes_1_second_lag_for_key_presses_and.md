---
title: "Dislpalink causes 1 second lag for key presses and mouse clicks"
date: 2020-07-25
forum: Installation &amp; Upgrades
---

### Post by triplemaya on 2020-07-25
New install of ubuntu mate 20.04
installed displaylink with
displaylink-driver-5.3.1.34.run
install goes fine
Monitor is connected to docking station with displayport cable. 

PROBLEM
key presses and mouse clicks take about one second to register. So the system is unusable.
Mouse movement is fine

This is only the case when the large monitor is set to primary and the laptop screen is off. When the system is running with two monitors there is no problem.
This configuration works perfectly when laptop is directly connected to large display with displayport cable. 

Symptom present on three different docking stations, so not a hardware issue there.
All versions of hardware working perfectly in this configuration with ubuntu mate 18.04

---

### Post by lastdanz on 2021-04-26
Hia! I'm getting the same failure.
Here, displaylink-driver-5.4.0-55.153.run.

When the two screens are connected to the Displaylink, I get that 1sec lag. If I connect one of the screens directly to the laptop and the other one to the Displaylink, everything works smoothly. What a shame.

Any help will be welcome :KS

---

### Post by triplemaya on 2021-05-24
Hi
I think I have solved it. Details on this thread:
[https://ubuntuforums.org/showthread.php?t=2462571]("https://ubuntuforums.org/showthread.php?t=2462571")
Best of luck!

As root:
apt-mark hold xserver-xorg-core

---

