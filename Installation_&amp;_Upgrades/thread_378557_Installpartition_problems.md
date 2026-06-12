---
title: "Install/partition problems"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by kjelle392 on 2007-03-07
Hello everyone :-)

Eager to try Ubuntu for the first time, I booted up the live-cd and went on with the installation.

In the installation process, I came at the "choose hd/partition"-section. I was not sure which hd/partition that I had prepared for Ubuntu, so I canceled the installation process to go back into Windows and find out.

When I started Partition Magic, the WHOLE disk was marked BAD and NO partitions are left. That is; I can access it from Windows, but PM tells me nothing is on that disk.

How do I fix this?

---

### Post by milton1 on 2007-03-07
Is PM telling you even your functional windows disk is bad? That suggests something aint right with PM.

---

### Post by kjelle392 on 2007-03-07
> **milton1 said:**
> Is PM telling you even your functional windows disk is bad? That suggests something aint right with PM.

Sorry for my lack of information. I have 2 disks. On the first one, I have a working installation of Windows on its own partition together with 3 other partitions. The 2nd disk had 3 partitions and I wished to use one of the partitions of that disk for Ubuntu. Now PM shows me just at yellow bar over the whole disk - and all the partitions on the disk is gone (PM tells).

---

### Post by milton1 on 2007-03-07
> **kjelle392 said:**
> Now PM shows me just at yellow bar over the whole disk - and all the partitions on the disk is gone (PM tells).

But win can access these supposedly nonexistent partitions? Weird.

you could simply blank a chunk of space on the drive and select the install option of "use largest free space"

---

### Post by dannyboy79 on 2007-03-07
so did the 2nd disk just have storage space for winbloz? does it have an os on it? what is it's filesystem type? you can always try to run fsck on the disk using the live cd. first you will want to find out which disk is the "2nd disk", which is the 1 that has a yellow mark over it when you're in PM. you can find this out by booting to the live cd, and then opening a terminal and typing in sudo fdisk -l. this will list your 2 hard drives and each of the hard drives partitions. once you make a determination of which disk you'd like to run fsck on (it will either be hda, hdb, or hdc, or hdd, depending on whether you have any optical drives), after you know what the drive is labeled in linux. you type in the terminal, sudo fsck -r /dev/hdx  (where x is the letter of your drive you want to check) this will interactively repair any issues with the filesystem.

---

### Post by kjelle392 on 2007-03-07
> **milton1 said:**
> But win can access these supposedly nonexistent partitions? Weird.

you could simply blank a chunk of space on the drive and select the install option of "use largest free space"

Yes I can access them from Windows the usual way. I am actually backing them up right now and plan to reformat the whole disk afterwards.

---

### Post by kjelle392 on 2007-03-07
> **dannyboy79 said:**
> so did the 2nd disk just have storage space for winbloz? does it have an os on it? what is it's filesystem type? you can always try to run fsck on the disk using the live cd. first you will want to find out which disk is the "2nd disk", which is the 1 that has a yellow mark over it when you're in PM. you can find this out by booting to the live cd, and then opening a terminal and typing in sudo fdisk -l. this will list your 2 hard drives and each of the hard drives partitions. once you make a determination of which disk you'd like to run fsck on (it will either be hda, hdb, or hdc, or hdd, depending on whether you have any optical drives), after you know what the drive is labeled in linux. you type in the terminal, sudo fsck -r /dev/hdx  (where x is the letter of your drive you want to check) this will interactively repair any issues with the filesystem.

I hate to admit this, but I am a new user to Ubuntu/Linux and have to get things told VERY easy :lolflag:

---

### Post by dstew on 2007-03-07
Your plan is good. Back up, and create new partitions when you re-try the Ubuntu installation. I don't know anything about Partition Magic, but if you can back up from the disk, clearly there are partitions there. Why PM cannot see them I don't know.

When you install Ubuntu, you will make it a dual-boot system, right?

---

### Post by kjelle392 on 2007-03-07
> **dstew said:**
> 
When you install Ubuntu, you will make it a dual-boot system, right?

Yes - hopefully the installation prosess automate dual-boot

---

### Post by dannyboy79 on 2007-03-07
if I were you I would try to learn something about fsck as it can save your butt in the future! after you are done backing them up, try to preform the functions that I stated earlier using fsck, this way if this happens to you in the future and you can't resort to backing up your info, you'll know that it works. obviously it's up to you, good luck either way.

---

