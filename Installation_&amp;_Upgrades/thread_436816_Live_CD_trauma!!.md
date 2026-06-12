---
title: "Live CD trauma!!"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by Zeedok on 2007-05-08
Decided to ditch Mepis on my laptop (love Ubuntu on my desktop) and install worked fine (so I thought). I deleted the Mepis partitions (leaving my Win XP partition, never use it but it's like a security blanket!) and Ubuntu booted beautifully - so I thought. One thing I noticed though, was that Mepis still showed up in my GRUB menu . . . 

I added some software and codecs etc then things got funky . . . my update manager and synaptic stopped working.

I rebooted and then I couldn't login to Gnome . . .

Having filled my root partition (and being unable to login to gnome before) I realised what had happened:

1. The Live CD had not deleted my Mepis partition, just installed Ubuntu next to it (in a bloody small parition!)
2. Installing the tiny amounts I installed filled up said partition, hence synaptic etc stopped working, and I couldn't login to gnome

I tried using the Live CD to reinstall and found that I had to choose the manual partitioning option. I deleted all the non-winXP partitions and created a new ext3 and swap partition (ext3 with mount point "/") and all seemed well - unfortunately the install hangs after ~ 280mb of installation and after an error message (something about the swap drive I think) I am directed back to step 5 (the partition table).

What I'd really like to do is use the option 'select the largest available free space' but for some reason that's not available for me to select (Not sure why - it was before).

Is there something stupid I'm missing here??

One of the reasons I like Ubuntu so much (over Mepis etc) is the ease of the Live CD install . . . I'd rather stick to this if I can (other methods seem daunting!)

Any help gratefully accepted.

---

### Post by chewearn on 2007-05-08
The option "select largest available free space" requires that you free up a large area in your harddisk (a few gigs).  This space has to be unallocated, i.e. it cannot contain any partition.

---

### Post by Zeedok on 2007-05-09
Problem solved.

I just tried rebooting and retracing my steps.

Now it works brilliantly - Mepis is gone and within 20mins I am fully customised again.

---

