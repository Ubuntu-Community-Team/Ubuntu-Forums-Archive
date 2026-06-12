---
title: "Dell XPS 13 9350 Developer Edition settings  on Windows preisntalled machine"
date: 2016-03-27
forum: Installation &amp; Upgrades
---

### Post by andrea103 on 2016-03-27
Hello,

I bought an XPS 13 9350 hoping to run Ubuntu smoothly as the previous version was actually sold with Ubuntu preinstalled. Turned out to be a not so good idea: got all sort of problems with SSD, touchscreen, wifi, battery life, BIOS... Now that the Developer Edition has been released ([http://www.dell.com/us/business/p/xps-13-9350-laptop-ubuntu/pd](http://www.dell.com/us/business/p/xps-13-9350-laptop-ubuntu/pd)), I would like to reproduce the settings it is shipped with. Anyone having a clue on how to approach such a thing? 
The main reasons for doing so are that with the current settings I still have the following problems:
[LIST=1]
[*]Touchscreen freezes after suspend 
[*]Wifi seems to suck a lot of power 
[*]Battery life in general could be better (around 5 hours browsing now) 
[*]Boot takes longer than it should 
[*]Black screen at boot using BIOS with version 1.7 or later 
[*]... 
[/LIST]
I currently have Ubuntu 15.10, but I would not mind re-installing in order to have 14.04 as for the Dev, Edition. Thanks!

---

### Post by andrea103 on 2016-03-30
Maybe a more specific question can be answered. If I install Ubuntu 14.04 LTS, which is the version the XPS 13 9350 comes with, do I automatically get Dell's factory settings? Have they been integrated in the disctro? I could just try, but I need my laptop working at the moment, cannot afford another black screen :p Thanks!

---

### Post by howefield on 2016-03-30
> **andrea103 said:**
> If I install Ubuntu 14.04 LTS, which is the version the XPS 13 9350 comes with, do I automatically get Dell's factory settings?  Have they been integrated in the disctro?

Almost certainly not. The Dell driver specifics and modifications would usually be held on the recovery media that comes with a pre-installed Ubuntu Dell machine or possibly downloadable from the Dell website.

>  I could just try, but I need my laptop working at the moment, cannot afford another black screen :p Thanks!

Might be worth trying a 16.04 live media, the newer kernel might behave better towards your machine.

---

### Post by oldfred on 2016-03-30
Dell typically develops Sputnik or updates to make new hardware work with Linux. Which often then is included in later releases. but it can take a while for kernel, drivers and support software to be standard in a distribution.

Probably similar threads.
 Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)
Uses Intel Wi-Fi adaptors
[http://arstechnica.com/information-technology/2016/03/dells-skylake-xps-13-precision-workstations-now-come-with-ubuntu-preinstalled/](http://arstechnica.com/information-technology/2016/03/dells-skylake-xps-13-precision-workstations-now-come-with-ubuntu-preinstalled/)
Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)

---

