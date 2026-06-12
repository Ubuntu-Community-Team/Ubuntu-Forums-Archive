---
title: "Need Help with Fresh Install"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by homerj742 on 2008-05-16
I'm looking to redesign my entire PC setup. Any feedback would be greatly appreciated. Here's the breakdown

Dualboot 2 harddrives:

500GB (280 used) - Ubuntu (Studio) 7.10 32bit
250GB - Windows XP Pro

My goal, 

Get rid of windows partition, and use ubuntu exclusively and run windows out of virtualbox. I no longer want to use Ubuntu Studio, I just want a few apps that I will install via synaptic (ie- Ardour, jack, hydrogen).

I also would like my ubuntu partition and home directory partition separated. 

I do NOT have an external hard drive. so here is my plan:

1) Unplug 500GB hard drive (w/the ubuntu 7.10 install)

2) Perform setup on 250GB Hard drive w/ this partition:
		20GB - Ubuntu 8.04 OS
		4-8GB - SWAP Partition
		The rest - Home Directory

3) Once install is completed, plug in 500GB hard drive, copy data in Home directory to the new Home Directory (thus preserving my data).

4) Format/Erase 500GB hard drive w/ ext3

5) Mount 500GB to current Home Directory (if this is possible). 

Does all of this make sense? The only problem i can foresee is maybe not enough space left on the 250GB HD to copy the data I want to perserve from the 500GB drive before it's wiped? 

Last, but not least, would I benefit from using the 64bit version (especially when using ardour/jack? 

damn an external HD would make this a heck of a lot easier. 

Thanks to everyone, I really appreciate any and all feedback from the community.

---

### Post by dstew on 2008-05-16
How much RAM does your system have? If 4 Gb or more, you probably should consider the 64-bit system. You probably don't need that much swap, even if your system has a lot of RAM. 1 GB is probably enough.

The rest of the scheme seems OK. I am not sure what you mean by mounting the 500 GB disk to your home directory though. Do you mean giving it a mount point inside your home directory, or replacing your home directory with a new directory on the 500 GB disk?

---

### Post by bobblehat on 2008-05-16
Seemed OK to me. (As long as you don't give me grief if something unforseen goes wrong :)  )·

It might be too much hassle but if you're really short of space you could always create a new, smaller (say 100GB) partition on the 500GB drive, copy part of your data into there and part onto the other drive, then resize the new partition to the full drive size and copy the rest over (I hope that made sense).

Edit with another thought: or since presumably it's ext3 anyway, just delete everthing you don't need, copy your data into the root of the drive and mount it as your home directory?

---

### Post by homerj742 on 2008-05-16
Thank you for the quick response. I currently have 2GB of RAM, I MIGHT upgrade it to 4, but not anytime soon.

So I will reserve 1GB for the SWAP. 

Yes, I would probably mount the 500GB hard drive to a point in the home directory, thus expanding the home directory. Unless you have a better suggestion of how to utilize that drive? I do a lot with music and movies.

---

### Post by homerj742 on 2008-05-16
> **bobblehat said:**
> 

Edit with another thought: or since presumably it's ext3 anyway, just delete everthing you don't need, copy your data into the root of the drive and mount it as your home directory?

That seems even easier. Would you consider that a "clean" way of doing it?

Another question, if I decide to go 64bit, will there be any issues in regards to the data?

---

### Post by bobblehat on 2008-05-19
> **homerj742 said:**
> That seems even easier. Would you consider that a "clean" way of doing it?

A reformat is the cleanest but I don't think ext3 filesystems suffer too much from fragmentation so if you're short of space I'd personally save the hassle  of all that copying around and just reorganise the data.

> **homerj742 said:**
> Another question, if I decide to go 64bit, will there be any issues in regards to the data?

There shouldn't be. I've copied my entire home filesystem from 32 to 64 bit in the past and it's been fine.

---

### Post by homerj742 on 2008-05-19
Thanks all for your kind replies!

---

