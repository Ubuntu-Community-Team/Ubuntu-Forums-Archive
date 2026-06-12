---
title: "migrating installation to a new computer with remastersys"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by Knacker on 2010-09-23
Hi, 
I'm replacing my laptop with a new one (thinkpad t61p > T410s) and I've decided to try to use remastersys to re-install my current (old, t61) setup on my new computer -- at least as an experiment and hopefully as a way of saving a lot of time and bother with configuration and etc. I'll be moving to a new and slightly smaller HDD (SSD), but I'm not worried about that. There are, however, a few things that I really am unsure about...

1) If my goal is to avoid doing all the adding/removing of packages, custom keyboard mapping, the customization and the tweaking of appearance and etc. that I've already done to get my setup where it is now, does it make as much sense as I think it does to use remastersys to migrate my system to a new machine? I've never actually installed from a custom live-CD, so...am I missing something?

2) Is there any extra complexity to installing with a remastersys custom disk, if i want to dual boot (with the win7 that is pre-installed on my new machine)? Or is it the same as it would be with any normal ubuntu install disk?

3) When I install on my new computer with the custom disk I've made out of my old system's settings, what will happen with the partitioning that I've set up on my old system? Will I simply go through the usual disk configuration utility, which will set up a new configuration of partitions, a new fstab file and etc. Or will my old partition table/fstab file somehow be transfered to the new install (as seemed to be happening when I ran the remastersys disk as a live-cd)? 

4) When migrating my ssh settings to my new computer, is it as simple as moving my ssh keys from my old machine to my new one? Or do I need to generate new keys for the new install? (I depend a lot on network storage mounted with sshfs, so it's important this work without a lot of hassle.) Ssh settings + keys apparently aren't backed up by remastersys. 

This switch to a new machine is occasioned by an emergency (old machine broke) and I really don't have time to fiddle around with configuring/fiddling with settings again. Really hoping this will save me some time, but also want to be sure I'm not getting myself into more of a mess than a fresh install type migration of my data.

If anyone can answer any or all of these questions to any degree at all, I'd be really grateful.

Many thanks in advance!
:guitar:

---

### Post by perspectoff on 2010-09-23
I like moving things with Remastersys. 

Everything is moved almost identically. It works best if the target partition is the same size as the source partition. 

The eternal question is the bootloader. 

Unless you are like me and have a boot partition, the Grub configuration in your old partition will not likely match your new computer and you must find a way to edit it (perhaps using the Ubuntu LiveCD) or reconfigure it so it will boot properly.

If you can boot into the new partition and update-grub, it will likely identify the OSs on the hard drive automatically.

The trick is setting the MBR to point to it. You can usually do this using the LiveCD restore function and choosing Restore Grub.

---

### Post by Knacker on 2010-09-23
> **perspectoff said:**
> 
If you can boot into the new partition and update-grub, it will likely identify the OSs on the hard drive automatically.

The trick is setting the MBR to point to it. You can usually do this using the LiveCD restore function and choosing Restore Grub.

Hm...good to know. I was anticipating something grub related, with the dual-booting win7 and all. 

> 
I like moving things with Remastersys. 

Everything is moved almost identically. It works best if the target partition is the same size as the source partition. 


Well, this is one of the things I'm unclear about. My current set up involves a number of partitions, but the only ones that remastersys has backed up are the root (i.e. / ) partition and my /home partition (I manually unmounted the others when I did the remastersys backup). I assume I'll get a chance to partition the drive when I install and I was planning on keeping the two main two partitions (/ and /home) the same size on the new machine, but I'm not sure whether or not the custom installation will expect the other partitions that existed (unmounted, but still present in the fstab, for instance) to be present and/or the same size on the new machine (new drive is smaller so my other partitions will have to be smaller). Not sure if that's clear or not... I'm basically just curious about how the custom cd will handle the "custom" partitioning that it may (or may not?) have inherited from the system I backed up when it installs on a new system...?

In any case, thanks a lot for replying! :)

---

### Post by Knacker on 2010-09-23
Okay, I think I answered the partition question. fstab has nothing to do with remastersys. it's excluded from backup and so should have nothing to do with installation...I'm pretty sure. 
Also: [http://forums.linuxmint.com/viewtopic.php?f=90&p=105575&st=0&sk=t&sd=a](http://forums.linuxmint.com/viewtopic.php?f=90&p=105575&st=0&sk=t&sd=a)

So, the only question I have left are...

Anyone have a second to to quickly clarify my question about migrating ssh keys to a new installation? 

Anyone else have a good/bad experience using remastersys to move installation to a new machine? 


Thanks again, perspectoff!

---

