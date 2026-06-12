---
title: "Problem Solution : (Intrepid blank screen problem)"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by amaiko on 2008-11-03
Problem 5 (Intrepid blank screen problem)

I wanted to install the Intrepid Ibex [8.10] upgrade. Today I started the Update Manager and let it upgrade to 8.10. Downloading the Binaries took 5-odd hours[I'm on a 384Kbps connection and the download size is just a mite less than 1GB].It took an hour to install and asked to reboot. This is where the troubles started. After rebooting, it went to the beige screen that precedes the splash screen and then to a black blank screen. I could move around the mouse and that was it.

Solution

Apparently the compiz [which is responsible for the visual effects] module has problems with older Intel graphics cards [on-board graphics module aboard my Intel 845 GVSR]. A suggested work around was to boot into recovery mode and remove the compiz module. Apparently the bus has been around for a couple of months now[Launchpad Bug #259385].

select root shell prompt and run the following commands

sudo apt-get remove compiz

sudo apt-get remove compiz-core

exit

from [UbuntuGeek]("http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html")

---

