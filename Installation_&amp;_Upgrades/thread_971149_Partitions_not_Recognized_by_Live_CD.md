---
title: "Partitions not Recognized by Live CD"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by CanasClone on 2008-11-04
I had 8.04 happily installed on my computer on a partition along with a /home partition, swap and vista. I tried to install 8.10 off a live CD (wiping my / partition but not /home) but halfway through the installation it said that it failed, possibly due to a defect in the burning. I reburned it at the slowest speed, but then when that booted up that partitions don't even appear, it just has a general disk for instead. I redownloaded the ISO and burned multiple times but nothing is showing up.

I read something about this possibly being caused by a partition that wasn't unmounted properly. I can see my partitions in Vista and the /home is fine but I couldn't access my / partition and there were only a couple hundred megabytes there anyway (because the installation only got halfway through). I formatted the / partition, but still nothing.

Since this means no GRUB from the failed installation, I now have to boot into Vista through my Ultimate Boot CD that I have on my flash drive. I can't continue to depend on a flash drive for my whole computer. Please, does anyone know how to make my Live CD recognize the partitions?

---

### Post by CanasClone on 2008-11-04
No one?

---

### Post by caljohnsmith on 2008-11-04
If somehow your HDD's partition table becomes corrupt, that is one cause of the Ubuntu installer not recognizing your partitions. I would recommend checking it to see if that is the case; from your Live CD, please open a terminal (Applications > Accessories > Terminal), and post the output of:
```
sudo fdisk -l
```
And if you have internet access from your Live CD, first make sure the Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

If you don't have an internet connection on your Live CD, you can run testdisk from your Ultimate Boot CD under Disk Tools > Partition > Testdisk. Let me know how it goes. :)

---

### Post by eltama on 2008-11-06
Thanks caljohnsmith. I had a similar problem with the partitions not being recognised. 
Although fdisk -l showed them, testdisk revealed some conflict. Deleting the conflicting partition and restarting solved the problem.
Note that it is important to make a deep search in the test.

---

