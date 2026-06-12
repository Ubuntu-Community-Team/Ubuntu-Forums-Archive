---
title: "Trouble with Kubuntu 7.10 &amp; RAID 0"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by Keilious on 2007-12-01
Howdy. Having finally gotten sick of Windows XP I've been trying to set up a dual-boot with Kubuntu 7.10 64-bit. 

I've been running into a few problems though...
Neither the live install nor the alternate CD's text install give me any options for partitioning with RAID, instead I'm just given a choice between sda and sdb (even though my drives are SATA, which might be part of the problem?)

I've done a bit of research and looked into this fakeraid fix, however all the terminal command work went completely over my head, and I'm hearing its out of date.
Nevertheless, I followed a link within that article to a _[guide on installing 7.10]("http://wiki.eyermonkey.com/My_Ubuntu_(7.10)_Installation")_, but after getting the dmraid program loaded through the terminal, the partitioning application simply crashed and exited whenever I clicked on a drive.


p.s. I don't know all that much about hardware, and I've never touched a linux system before, so please let me know if I need to provide additional information about anything.

---

### Post by Pumalite on 2007-12-01
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Keilious on 2007-12-01
> **Pumalite said:**
> [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
Thanks for the reply, but as I said in my original post, following the fakeraid guide for 7.10 resulted in the partitioning application simply crashing. :(

---

### Post by Pumalite on 2007-12-01
What part of this crashed?:
[https://help.ubuntu.com/community/FakeRaidHowto#head-7918ab0def192cdf40484077136a40241732c669](https://help.ubuntu.com/community/FakeRaidHowto#head-7918ab0def192cdf40484077136a40241732c669)

---

### Post by Keilious on 2007-12-01
> **Pumalite said:**
> What part of this crashed?:
[https://help.ubuntu.com/community/FakeRaidHowto#head-7918ab0def192cdf40484077136a40241732c669](https://help.ubuntu.com/community/FakeRaidHowto#head-7918ab0def192cdf40484077136a40241732c669)
Mkay...
dmraid is installed okay,
I input "sudo dmraid -ay", it says two RAID sets are already active... "isw_bhegfbgegc_SIAA2" and "isw_bhegfbgegc_SIAA21"
> Optional: Resize your Windows partition
If you want to dual-boot windows, you may need to [WWW] resize your Windows partition to make space for Ubuntu. Most linux-based GUI tools won't properly work with fakeRAID devices, but the unix command-line combination of ntfsresize and fdisk is extremely reliable. Windows Vista users should use the [WWW] Vista Partition Manager.
I do want to dual boot, so I guess I have to do this. 
The link they provide says to first use fdisk. I try "fdisk -l /dev/sda", and the terminal returns "Cannot open /dev/sda".
...Oh, I get it. You chuck "sudo" in front. Fair enough.
Problem now is, this is still only listing one drive here... In the link they give, under device boot of this fdisk result they have "sda1", "sda2" and "sda3". Am I correct in assuming I should have a "sda1" and "sda2?"?

---

### Post by Pumalite on 2007-12-01
This means that you first have to boot into Vista and FROM THERE allocate space for Ubuntu with Vista partitioner.

---

### Post by Keilious on 2007-12-01
> **Pumalite said:**
> This means that you first have to boot into Vista and FROM THERE allocate space for Ubuntu with Vista partitioner.
Alrighty. I'm running on Windows XP however, and the disk management tool does not allow me to shrink the current, single partition in order to make room for a new one (unless I'm missing an option to do so somewhere?). Is there some other partitioning program I could download that you'd recommend?

In any case, its getting quite late, I'll continue hammering away at this tomorrow morning. Thank you for your help and patience, Pumalite. :D

---

### Post by Pumalite on 2007-12-01
You are welcome. I'll be here.

---

