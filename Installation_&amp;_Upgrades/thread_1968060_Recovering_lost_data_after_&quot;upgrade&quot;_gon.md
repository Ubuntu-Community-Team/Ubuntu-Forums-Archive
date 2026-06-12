---
title: "Recovering lost data after &quot;upgrade&quot; gone awry"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by Hasuppa on 2012-04-28
Dear Installation & Upgrades Board

A couple of days ago when Precise came out I tried to perform an upgrade from Oneiric to Precise by booting from a Precise install disk and selecting "**upgrade**" in the installation GUI. A little later I was informed by a message prompt that the installer could not detect a swap partition and that therefore I could either proceed without a swap partition, or go back and select one via the partitioning tool. I did the latter and designated my existing swap partition as the swap partition to be used (partition layout: 40GB ext3 for /, 4GB swap and 955GB for /home). At no point was I prompted to confirm whether I wanted to format any partition.

Later during what I had until then believed was the upgrade process I was asked to set up a user account. I already got the sense something was seriously wrong here, but I set up an account using the same name, password etc. as my old account, figuring that since the installation was already under way there was nothing I could do to save my data at this point.

Anyway my worst fears came true and I am left with a **fresh install of Ubuntu Precise and 750GB of lost data in my home directory**, a small part of which I did not back up. My question, then, is **how to recover as much of this data as possible?** It's a 5,25 HDD and all other computers I can get my hands on are all laptops, although I do have a spare casing that I could use to turn the HDD into an external USB 2.0 hard drive. I would, however, prefer a method that doesn't require me to use a second computer in the process.

39

---

### Post by darkod on 2012-04-28
You can boot into live mode with the cd and try to recover the old partition table with testdisk.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Download and run the program in live mode, do the Deeper Search and look carefully at the partitions detected. If it finds your old partitions, change the D letter code into P or L depending if the partition was primary or logical, and only after you have all partitions listed with P or L write the new partition table.

The deep search might offer few variations of partitions to restore so look carefully what looks most like the setup you had. When a partition is selected you can also try to list the files with P. That will show if there are readable files on it and if it's worth saving.

If you intend to try saving the data DO NOT boot from the hdd any more, only into live mode with the cd.

---

### Post by Hasuppa on 2012-04-30
I booted from the live cd, made sure my computer was connected to the internet and tried to install testdisk. It seems to be unavailable though. Am now trying to boot using a specialty distro called "Recovery Is Possible" because that apparantly has testdisk on it.

---

### Post by darkod on 2012-04-30
Not sure if it's available in repositories. You can download it from its website, put it in a folder and execute. It works fine like that too.

---

