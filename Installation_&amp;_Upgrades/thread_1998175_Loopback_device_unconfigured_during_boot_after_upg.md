---
title: "Loopback device unconfigured during boot after upgrade to Ubuntu 12.04 from 11.10 on"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by giannoug on 2012-06-06
Everything seemed fine during the upgrade I did on my main production server, except some MySQL and libc issues that are common and which were easy to fix. Another problem that arose is related to the network loopback device. The device isn't configured during boot which causes many problems with applications that rely on it (pretty much everything as you can imagine, in my case MySQL).

I think I made a mistake by keeping the local version of the configuration files or at least some of them. This brought the system in a weird state which some configuration files are old and some new. The networking part seems to be changed a lot in the Ubuntu 12.04 release with initialization being split between files. I don't know where to start. First of all which package is responsible for those scripts (is it ifupdown?)? How can I reinstall it? aptitude reinstall didn't ask to replace files with the package maintainer versions.

By the way the machine is a VPS on OpenVZ, but other people didn't have problems.

---

### Post by giannoug on 2012-06-10
I was able to recreate the problem on a new VPS with the same specifications (same OpenVZ version and kernel). I replaced all the configuration files with the package maintainer ones.

There is something I don't like with OpenVZ and upstart. Networking seems to be moved to upstart in Ubuntu 12.04. A wild guess is that the upstart job responsible for the lo interface is not running for some reason.

Anyone else with an Ubuntu 12.04 VPS? Can you check [FONT="Courier New"]ifconfig[/FONT] and see if [FONT="Courier New"]lo[/FONT] is listed?

I want to be sure this is actually a bug before I submit it.

---

