---
title: "partition help - dual BSD vmware Feisty Fawn"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by tiro on 2007-04-20
Hello,

In this post I am going to mention OpenBSD and VMware, but I am really only asking about how I am partitioning under Feisty Fawn. My problem is that I can't understand why the graphical installer is not letting me make a huge primary ext3 partition. Please ignore the OpenBSD/VMware stuff.

I just got a 500GB disk. I installed openBSD on the first 16 GB partition. It doesn't boot but that's okay, I believe the Ubuntu boot loader will sort it out.

I want to make a 400 GB ext3 partition as the second partition. Then I will have a smaller ext3 partition as a Ubuntu root partition as partition 3, and partition 4 as linux swap.

The graphical installer will not let me make a huge partition. I put in 448000 in the megabytes field and it gives me a 53482 MB ext3 /dev/hda2.

I should mention that I am using VMware and the feature that lets you use an entire disk. I don't think this is the problem but if it is I can burn an ISO.

I read the FAQ that Ubuntu links to at [http://www.tldp.org/HOWTO/Linux+FreeBSD-2.html](http://www.tldp.org/HOWTO/Linux+FreeBSD-2.html)
It says to put BSD after Linux, but I don't have that option because openBSD has to be under cylinder 1024.


William

---

