---
title: "Dual booting with Ubuntu 8.04"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by basilwatson on 2009-11-18
Hi all 

I would like to dual boot 9.10 with 8.04 

The reason , I use some Engineering software which I am having difficulty installing 

So there is a Live CD  CAELINUX which is already good to go 

But it uses 8.04 and I had a lot of problems getting that to work with my hardware ( bluetooth mouse ) 

So 

I have partitioned my HD but when I try to install 8.04 I cant install grub correctly so either I get 9.10 OR 8.04

And then theres EXT4 ...

How can I do this ( dual boot with 8.04

Stephen

---

### Post by iniesta on 2009-11-18
I have a similar question. I want to triple boot 3 OSes: Ubuntu 8.04, Ubuntu 9.10 and Windows XP. I have already installed Ubuntu 8.04 and Windows XP. If now I install another OS (Ubuntu 9.10) is there any problem?

Thanks!

---

### Post by ShadowMage on 2009-11-18
Hi,

I'm sure there are other ways to do it, but on one of my comps I have 3 OS (Ubuntu 9.10 + Ubuntu 9.04 + Windows XP) and here is what I did:

First, I had a dual boot of Ubuntu 9.04 / Windows XP. Then to install Ubuntu 9.10, I first played around with my partitions using a GParted Live CD (which can be created from an iso downloaded from [[COLOR=Blue]GParted Homepage[/COLOR]]("http://gparted.sourceforge.net/") - currently the latest stable "Live" version is [[COLOR=Blue]0.4.8-6[/COLOR]]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.4.8-6/")) so that I could put 9.10 in the same *extended partition* as 9.04, in order to share the swap partition.

[COLOR=Red]NOTE: Just to be clear, what I did was I put it *beside* the old Ubuntu's partition in the same *extended partition*. Overwriting the old Ubuntu's actual ext3 (or whatever the case may be) partition would obviously destroy it![/COLOR]

During installation, I selected the "Specify partitions manually (advanced)" option. I formatted the unallocated space I had created inside this extended partition (personally I used ext3) for mounting "/" for 9.10, and by default I believe it recognized the swap and was already selected to be used. Of course, **do not format your old Ubuntu partition** (or the swap), since you want to keep it!

This worked for me. Not entirely the same situation, but I hope it helps anyway.

Cheers.

---

### Post by iniesta on 2009-11-18
Hi ShadowMage,

Thank you very much for your answer. Your method is a good solution. However, since my hard disk has been partitioned as follow:

+ /dev/sda1: Ubuntu 8.04
+ /dev/sda2: Linux Swap
+ /dev/sda3: Windows XP
+ unallocated: ~50GB

(The above 3 partitions are all primary)

And now I want to install Ubuntu 9.10 on the unallocated space. In this case, I intend to choose the option "Use the largest continuous free space". But the thing I wonder is: what will the 9.10's installation do to my hard disk? To be more specific, will it create another Linux Swap partition? Will the 'only 4 primary partitions at the most' law be violated? And to be short, will it be ok to do so?

Thanks and regards,

Iniesta.

---

### Post by ShadowMage on 2009-11-18
Hmm, I see. Well I think it should still be possible to tell it to use the same swap if you choose "Specify partitions manually (advanced)", but I always had my swap inside the same extended partition as my Ubuntu(s), so I can't confirm.

Unfortunately, I also do not know for sure about your other questions, so I won't try to answer them, but I hope someone more experienced in this regard can help you out.

---

