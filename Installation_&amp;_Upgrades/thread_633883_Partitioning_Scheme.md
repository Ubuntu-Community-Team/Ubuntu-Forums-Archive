---
title: "Partitioning Scheme"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by Danikar on 2007-12-07
Ok so I have an old laptop with 2 hard drives and I want to put Ubuntu on it.

Master 2GB
Slave 6GB

This is the scheme I am thinking of.  I have never had to do over multiple hard drives so any suggestions are appreciated.

```
/hda1
	/	1.5GB
	swap	5GB
/hda2
	/usr	3GB
	/home	3GB
```

---

### Post by kidders on 2007-12-08
Hi there,

Your figures don't add up ... perhaps you mean "_**.**_5GB swap".

The amount of space you have available will make for a pretty tight install ... at some point, I'm worried that you'll find yourself in need of a couple of hundred megabytes, only to find that the free space you want is on the wrong partition.

I would suggest at least *considering* two options (ie you don't absolutely _have_ to do either of them) ...

**I - Something involving RAID 0**
Ordinarily, I would think someone an idiot for using RAID 0 (hehe), but it does have its uses. You could install Ubuntu into one single partition, spread across two disks, so juggling the amount of space the different parts of your system are using would be as easy as possible. For example, by taking the Microsoft approach to virtual memory (ie swap *files*, not partitions), and not drawing a hard boundary between /usr and the rest of your system, it'll be far less likely that you'll find yourself having to repartition your disks as your Linux evolves. If you suddenly find yourself needing an extra 200MB to re-encode a CD or something, you could simply steal it from your swap, and give it back when you were done.

The down side is that you'd have to be prepared to back up your system religiously, given the high failure probability of a RAID 0 configuration ... perhaps by automatically burning /home onto a CDRW on a nightly basis. In addition, the use of a swap file over a swap partition entails a slight performance hit, but you may feel the advantages outweigh these issues.

**II - Not using Ubuntu**
Ubuntu is by no means optimised for size. Everything from the core of the Linux OS itself to the software you run can be tweaked and pared down to take up as little space as possible, by turning off useless features, and removing lesser known libraries/utilities/etc. Distros like Gentoo let you do this (provided you have the necessary knowledge), and things like DSL come pre-configured to work this way.

I hope that helps a little.

---

### Post by Pumalite on 2007-12-08
A good scheme:
10 GB for '/'
2x RAM up to 1 GB for /swap
The rest for /home

---

### Post by kidders on 2007-12-08
> **Pumalite said:**
> A good scheme:
10 GB for '/'
2x RAM up to 1 GB for /swap
The rest for /homeHi there,

Did you read the o/p? Even between both of his hard disks, the poster doesn't *have* 10GB!

---

### Post by Pumalite on 2007-12-08
He should shrink the ideal proportionally.

---

### Post by lha on 2007-12-08
> **Danikar said:**
> Ok so I have an old laptop with 2 hard drives and I want to put Ubuntu on it.

Master 2GB
Slave 6GB

This is the scheme I am thinking of.  I have never had to do over multiple hard drives so any suggestions are appreciated.

```
/hda1
	/	1.5GB
	swap	5GB
/hda2
	/usr	3GB
	/home	3GB
```

If that swap was meant to be 0.5GB, your plan sounds ok. Are you sure you have two hard disks and not one bigger? You wrote as if hda1 and hda2 were two different hd's. Did you mean hda and hdb or something similar?

 I would make only one partition the bigger drive and use it for usr and home. For example, you could symlink /usr to /home/usr, /home to /usr/home, or something like that. With only one partition on the slave drive, you wouldn't run out of space on home or usr so quick.

> **kidders said:**
> Hi there,

Your figures don't add up ... perhaps you mean "_**.**_5GB swap".

The amount of space you have available will make for a pretty tight install ... at some point, I'm worried that you'll find yourself in need of a couple of hundred megabytes, only to find that the free space you want is on the wrong partition.

I would suggest at least *considering* two options (ie you don't absolutely _have_ to do either of them) ...

**I - Something involving RAID 0**
Ordinarily, I would think someone an idiot for using RAID 0 (hehe), but it does have its uses. You could install Ubuntu into one single partition, spread across two disks, so juggling the amount of space the different parts of your system are using would be as easy as possible. For example, by taking the Microsoft approach to virtual memory (ie swap *files*, not partitions), and not drawing a hard boundary between /usr and the rest of your system, it'll be far less likely that you'll find yourself having to repartition your disks as your Linux evolves. If you suddenly find yourself needing an extra 200MB to re-encode a CD or something, you could simply steal it from your swap, and give it back when you were done.

The down side is that you'd have to be prepared to back up your system religiously, given the high failure probability of a RAID 0 configuration ... perhaps by automatically burning /home onto a CDRW on a nightly basis. In addition, the use of a swap file over a swap partition entails a slight performance hit, but you may feel the advantages outweigh these issues.

**II - Not using Ubuntu**
Ubuntu is by no means optimised for size. Everything from the core of the Linux OS itself to the software you run can be tweaked and pared down to take up as little space as possible, by turning off useless features, and removing lesser known libraries/utilities/etc. Distros like Gentoo let you do this (provided you have the necessary knowledge), and things like DSL come pre-configured to work this way.

I hope that helps a little.

**I** Since your drives aren't the same size, raid0 may not be ideal. A better approach is to use jbod (just a bunch of disks). You can use mdadm to create one bigger virtual drive consisting of the two hard drives. In mdadm jargon, jbod is called linear.

**II** It is true that some distributions require much less space than Ubuntu. [Damn Small Linux]("http://damnsmalllinux.org/"), for example, takes only 50 MB. However, instead of worrying about hard drive space, the other specs of your laptop may cause trouble. A computer with only 8 GB of hard drive space is definitely a low-end machine. Are you certain that Ubuntu will be usable on your computer? There exists lighter options.

---

### Post by louieb on 2007-12-08
On a P2-400 / 384mb ram. 
Just for grins I used this [Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")
And added Fluxbox  [Fluxbox - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Fluxbox")
No graphical login manager I use [B]startx
[/B]Uses a little less that 1  GB disk space. of that /usr is about 450MB.

Fun getting it to work.
But for out of the box DSL or Puppy or my new favorite lightweight distro  [PCFluxboxOS:]("http://pcfluxboxos.wikidot.com/")

---

### Post by louieb on 2007-12-08
> **Danikar said:**
> 
Master 2GB
Slave 6GB
```
/hda1
    /    1.5GB
    swap    5GB
/hda2
    /usr    3GB
    /home    3GB
```
Just noticed are you sure there are two hard drives in the laptop? That just seems wrong. 

I would guess it has an 8GB drive with 2 partitions  of 2GB and 6 GB.  

It would be normal

---

### Post by wpshooter on 2007-12-08
If there really are 2 hard drives, the first thing I would do would be to make the 6gm the master and the 2gb the slave.

I don't think you are going to be satisfied running Ubuntu on that machine very long.

But good luck.

---

