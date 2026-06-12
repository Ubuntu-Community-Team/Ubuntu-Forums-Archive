---
title: "hardy 8.04 boot fails"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by brendan.lefoll on 2008-05-07
Ok I'm pretty annoyed with the newest release of ubuntu, the bugs in networking (synergy shows them best), but anyways here's my latest problem that I can't solve and I'm just going to have to go back to opensuse if I can't sort it out.

I have a :
Tyan S5396 i5400XT
2x 2.5ghz harpertown xeons
8x 2G FB-DIMMs
1x SAS 15k 73GB seagate Cheetah
1x SATA 7.2k 750GB samsung spinpoint
Nvidia 8600GT

Ok so I install ubuntu with the alternate CD. All goes fine I set up the following partitioning:

SAS disk :
LVM with / and home sharing the disk all on reiserFS
SATA disk :
/boot 100MB on reiserFS
4 GB of swap

It all goes well, I install everything all happy. get the nvidia drivers to work and set dual monitors up with nvidia-settings. I reboot to make my system happy (it keeps complaining that after updates you have to...)

And grub doesnt load.... just get the flashing underscore from the mobo's bios.

I tried again this time with /boot and swap all in an LVM from the SAS drive. LILO is the boot loader. Again All seems good, I do an apt-get update and upgrade, and reboot, bam LILO goes "L 99 99 99".... and so on.

Is there a problem with dual drives and LVM's or something? What kind of partitioning should I use? I want to have an LVM with / in it at least, I don't mind moving /home to the slower SATA drive. But in that case swap has to go on the faster drive at least.

Any help would be welcome.

Thanks,
Brendan

---

### Post by brendan.lefoll on 2008-05-07
Turns out opensuse provided me with the answer, the disk lable was set to whatever Mac OS X uses and not ms-dos. Therefore grub and lilo seemed to have trouble with it. I'm impressed opensuse told me straight away and had a tool to fix it. I'm less impressed with the fact it crashed twice while trying to create the LVM. However I have now reinstalled ubuntu 8.04 and it seems to be all fine now (fingers crossed just updated all and installed nvidia drivers, now installing kde3 and kde4.)

---

