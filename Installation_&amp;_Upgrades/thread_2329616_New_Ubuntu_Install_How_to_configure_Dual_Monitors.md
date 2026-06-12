---
title: "New Ubuntu Install: How to configure Dual Monitors"
date: 2016-07-03
forum: Installation &amp; Upgrades
---

### Post by UserJB on 2016-07-03
I just installed Ubuntu 15.10.  I have a machine with two LCD monitors. Ubuntu displays the same thing in both monitors.  I tried SystemSetting->Displays, but this complained about an internal Ubuntu error, and then disappeared.  I never saw the error message again.

How can I force Ubuntu to use my two monitors correctly (not mirror of each other)?  In RedHat, the command was something like system-config-display.  I searched the entire filesystem and could not find an obvious command to do this.  What is the command to configure the monitors in Ubuntu 15.10?

---

### Post by TheFu on 2016-07-04
Support for 15.10 ends soon. Best to wipe that install and go with 16.04 which has 5 yrs of support for the core stuff and 3 yrs of support for most upstream things.
[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life) has a graph that will clarify this support cycle.  For most people, staying with an LTS release (even years, in April) is the best choice of release.

For dual monitor support, I've always used the proprietary graphics tools.  nvidia-settings (or something like that).  Has been a few years since the last time I set this up ... still running 14.04 here, which is the LTS release prior to 16.04.

For Intel IGP systems, I've been using lxrandr to handle dual and triple displays.

Don't have any ATI/AMD stuff running here. Sorry.  Do have an old machine, but it is with the Radeon line of GPUs, which isn't supported by AMD anymore. That means the F/LOSS GPU tools must be used - noveou or something like that. Suspect that lxrandr would work, but I don't know.

---

### Post by UserJB on 2016-07-04
Okay, I scrapped Ubuntu 15.10 and installed 16.04.  That was even more of a hassle then 15.10 (Flashing icons and blank screens when I log in).  But I fixed those.

---

