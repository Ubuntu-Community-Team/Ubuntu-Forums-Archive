---
title: "UBUNTU 10.4 install problem"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by croarmy2010 on 2010-05-14
Hello to everyone,

I have downloaded new version 10.4 of Ubuntu and burn it on CD with  power iso,
gave it a try to install but after it started from cd and waited to load  ...an error pop up
and says it can not install from cd ...then i tried to start live cd and  it started Ok with no problem.
In live cd mode i tried install again and started well ,1to4 step ok,  then at 4 step
when it comes to HDD and partitions the window to choose from is blank.
No HDD no partitions...

but interesting is that in this Os it has partitioning tool in system  tools GParted, and whit it i can see my HDD and partitions, even tried  format with it a partition for Ubuntu then tried install but problem is  the same = blank step 4,.. so on my pc i can not install 10.4

Pc ( Amd 2800+, Mbo ASRock K7Upgrade-600, vga ati 9600pro, rest  integrated, hdd maxtor 160gb (Maxtor 6L160M0)

I have older version of ubuntu = 8.10  and everything is ok and istall  is ok , hdd is visible,... installed and works ok

------------------------
I tried install 10.4 on my friends Pc which has Intel mbo, intel cpu,  ati 1550, sound+lan integrated on mbo, 2 hdd on sata 1 on Ata,..
on his pc i had no problems with install, runs good, sound ok, DSL ok  over lan, update ok,...all of hdd is visible.
------------------------

---

### Post by darkod on 2010-05-14
Usually this means you have remains of raid metadata on the hdd.

You are not using raid right now, right? The disk might have been used in raid earlier and the metadata remained there. Ubuntu started detecting this since version 9.10 and that why earlier versions will install correctly but 10.04 no.

If you are NOT running raid:
Boot the 10.04 live mode again, and in terminal execute:

sudo dmraid -r -E /dev/sda (if your disk is /dev/sda, if not change)

That should ask you if you want to remove settings. Then you know that is the problem. Confirm to remove the settings and it's solved.

---

