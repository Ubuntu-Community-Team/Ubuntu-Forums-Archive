---
title: "UDEV and ubuntu support"
date: 2006-05-09
forum: Installation &amp; Upgrades
---

### Post by JimBodkins on 2006-05-09
Hi,

I have had a problem with UDEV. Initially, the problem involved upgrading kernels - which failed due to lack of UDEV support. I contacted the hotplug group (who gave me this headache) and was told they could care less. I tried to explain this wasnt a personal system, it was an attempt to use debian (including ubuntu) in a commercial setting. They didnt care - they were geniuses for thinking UDEV up in the first place, all the rest was left as an excersize for the unwashed to perform.  (And the Debian group are ... well .... 'hypothetical'. That is, I have been told they exist, but have never heard or seen them)


Sense a little hostility on my part? .... good. I just hate UDEV. (But understand that I and the entire world are now stuck with it)

Here is my current problem. I need to install ubuntu on one of two servers - supermicro duel xeons. One with a gdt sata raid controller (ICP-Vortex) and one with a gdt scsi raid controller. Good, high performance, german controllers. Neither work. Both fail to find /dev/sda, UDEV I am sure. (Both install, but drop to busybox on boot. Clean installs).

I am not going to configure UDEV. The reason is I have too much else to do. (Including adding a gui to about 3/4 million lines of curses code - hotel management software). What I do need is a port that I can install on high performance servers. Redhat does it - I hate redhat. Suse is wobbly. Debian is great, but is a disaster in UDEV land.

I would love .... really love .... if the debian community would work with the hotplug thugs to address this once and for all. (I dont want to be a pioneer - I am a programmer who has no interest in this at the moment due to time constraints - sorry).

I think debian and derivatives are limited unless and until that happens - sadly. (We currently use CentOS with great ease and success. But I prefer Debian/Ubuntu, if only it were as easy).

Thanks
Jim

---

### Post by JimBodkins on 2006-05-10
Bump

---

### Post by JimBodkins on 2006-05-11
Bump.

This is a deal killer as about 90 percent of all systems in the field currently have high performance gdt (ICP-Vortex) cached raid controllers. And UDEV under debian/ubuntu doesnt  appear to like them at all. Which is a shame as the gdt is a serious controller for high performance servers. We are testing FC bordeaux as a replacement. (We would rather not use it, but may be forced to abandon debian/ubuntu).

---

