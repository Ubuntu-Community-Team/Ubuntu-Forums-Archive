---
title: "Ubuntu 10.04 LTS installation issue, no partition list"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by wewo on 2010-06-10
Hi there,

I have problem with installing Ubuntu.

I used to use Ubuntu 9.04, then I installed Windows 7 in summer 2009 and I used it. I deleted Ubuntu, but now I want it back (dualboot with Win7). I mentioned that I used Ubuntu to say that I have experience with installing it. I had no problem with 9.04.

However, with installing 10.04 from Live CD, there is a problem. After choosing my time zone and my keyboard layout, when I should be able to set partitions, there is only blank window, no list with hdds and nothing happens. The installation is doing nothing, no progress, nothing is loading so waiting is not solution I think :) No error message, no bug log...

At this moment, I am writing from Ubuntu - booted with Live CD.

I made screenshot:
[IMG]http://img691.imageshack.us/img691/5556/screenshotrup.png[/IMG]

Also, I found video, this problem happens me right at 4:05.
[http://www.youtube.com/watch?v=Dn3L9wuU4js](http://www.youtube.com/watch?v=Dn3L9wuU4js)


I tried to end installation and start it again, I tried booting from CD again, but it is always same.

Any idea how to help me? Thanks a lot.


P.S.: Sorry if there are mistakes, I am not from english speaking country ;)

---

### Post by staleks on 2010-06-11
I have same problem.

System Description:

HDD: SATA Maxtor 6V160E0 Diamond 160 GB
MB: MSI MS-7143 ver: 2B

Except I had WinXP prviously on HDD and I want to delete that WinXP and switch to Ubuntu 10.04 (clean, all space, I don't want any tray of WinXP)

Anyone found a solution ?

---

### Post by darkod on 2010-06-11
Usually this happens if there is raid metadata on the disk. If the disk was used in raid earlier, or similar. Formatting doesn't remove the metadata.

If you are NOT running raid, boot into live mode and do:

sudo dmraid -r -E /dev/sda (or /dev/sdb, etc, depending on the disk name)

If that asks you to remove raid settings, that was the problem. Remove them and it should be fine.

---

### Post by garvinrick4 on 2010-06-11
Open a terminal apply this code and then install. Did not see darko more or less
a duplication of #3 but works.


sudo apt-get remove dmraid

---

### Post by srs5694 on 2010-06-11
There are at least two other possibilities:


[list]
[*]The chipset for the hard disk controller (usually on your motherboard) may be unsupported by Linux. This is uncommon, but possible. Sometimes you can fix the problem by moving the hard disk from one SATA or PATA connector on the motherboard to another one. Other times you can find an upgraded driver (but integrating that into an Ubuntu installation can be difficult). Occasionally the only solution is to buy a new PCI adapter for your hard disk.
[*]The partition table may be corrupt. Partitioning tools based on libparted, including the Ubuntu installer, tend to flake out and claim that no partitions are defined when they encounter even very minor problems in the partition table. I've got a [Web page that describes this issue,](http://www.rodsbooks.com/missing-parts/index.html) along with one possible solution.
[/list]

---

### Post by wewo on 2010-06-13
Thanks guys,

I found out how to "solve" it, but it was so unpractical.

I found my old CD with Ubuntu 9.04 and I installed it (no problems during installation) and then I upgraded it to 9.1 and then to 10.04.

I had to download a lot of data, but my 10.04 works good now :)

---

### Post by darkod on 2010-06-13
It was more practical to install 9.04 and do two upgrades instead of removing the metadata with single command?

Also if the disk is not used in raid any more, it's probably good practice to remove the raid data.

Anyway, what ever works better for you.

---

### Post by jtheoof on 2010-06-24
Thank you darkod, that fixed the issue for me.

That's why I love Ubuntu, the community is just awesome!

---

### Post by JakeRam on 2010-07-06
Thanks Darkod, I had the same problem, and your suggestion fixed it instantly.

---

### Post by tehveihlator on 2010-07-11
i have the same issue but i cant find any of my hard drives i even tried using the fdisk -l command and nothing shows up.
and the dmraid command just says no blocks found.

---

### Post by slday on 2010-11-24
> **darkod said:**
> Usually this happens if there is raid metadata on the disk. If the disk was used in raid earlier, or similar. Formatting doesn't remove the metadata.

If you are NOT running raid, boot into live mode and do:

sudo dmraid -r -E /dev/sda (or /dev/sdb, etc, depending on the disk name)

If that asks you to remove raid settings, that was the problem. Remove them and it should be fine.

Worked like a charm with Ubuntu 10.10. Thank you.

---

### Post by albrt741 on 2011-01-14
> **darkod said:**
> Usually this happens if there is raid metadata on the disk. If the disk was used in raid earlier, or similar. Formatting doesn't remove the metadata.

If you are NOT running raid, boot into live mode and do:

sudo dmraid -r -E /dev/sda (or /dev/sdb, etc, depending on the disk name)

If that asks you to remove raid settings, that was the problem. Remove them and it should be fine.


Thanks! that's what I needed to know. 

Alberto

---

### Post by bobbryce on 2011-01-23
> **darkod said:**
> Usually this happens if there is raid metadata on the disk. If the disk was used in raid earlier, or similar. Formatting doesn't remove the metadata.

If you are NOT running raid, boot into live mode and do:

sudo dmraid -r -E /dev/sda (or /dev/sdb, etc, depending on the disk name)

If that asks you to remove raid settings, that was the problem. Remove them and it should be fine.

DARKOD - Many thanks for this. As a new user on a new installation of 10.04LTS, the automatic install kept failing in its attempts to set up partitions on a previous Serial ATA RAID (pdc_....). 

Use of dmraid as above killed off the RAID and then had to perseve with GPARTED and Disk utility together with a couple of power cycles before the automatic install would kick in and complete.

Thanks again - now on to the wonderful world of Linux...
Bob :D

---

