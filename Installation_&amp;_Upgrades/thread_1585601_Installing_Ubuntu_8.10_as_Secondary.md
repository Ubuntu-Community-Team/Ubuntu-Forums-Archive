---
title: "Installing Ubuntu 8.10 as Secondary"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by yalfers on 2010-09-30
I currently have Windows Vista as my main OS, and I'd like to keep it that way for now. My HD is ~60 Gigs, 42 or so occupied by Vista (most space allowed to it apparently), and I have a swap of 4.5 Gigs. I'm not sure if I need a swap that big, or if I even need one...

Anyways, I want to install Ubuntu and give it a few Gigs to test out. I was fine setting it up and leaving about 4GB to Ubuntu out of the Vista share, but I'm getting an error with too many primary partitions. Is there a problem with my swap (it is a primary I believe), or am I missing something silly here..?

Edit:
I have a swap of 6.35 Gigs, 3.65 Gigs unallocated, OS at 43.84, and a 2 GB partition set as a primary and unnamed(this one's throwing me off).

---

### Post by mörgæs on 2010-10-01
8.10 is unsupported and hence a security risk. Go for 10.04 or 9.10 in stead.

---

### Post by snowpine on 2010-10-02
No reason to install 8.10 as it is completely unsupported. 10.04 is the current release and 15gb is the [recommended minimum]("https://help.ubuntu.com/community/Installation/SystemRequirements") hard drive space. 6.35gb is way too big for swap; if you have enough RAM you don't need any swap at all!

A hard drive can only have 4 primary partitions max. What you need to do is delete one of your primary partitions (your gigantic swap would be a good candidate) and create an ["extended partition"]("http://en.wikipedia.org/wiki/Disk_partitioning") which can then be divided into several logical partitions.

If you are not sure about partitioning it is easiest to just use the "Guided install: resize" feature of the Ubuntu installer. Always back up all data to an external drive before repartitioning your drive. The Ubuntu documentation is very detailed on how to partition a drive (but ask if you have questions). Good luck!

---

### Post by yalfers on 2010-10-03
Eh, somewhat stupid question. Sorry and thanks for the replies. I had 8.10 from a friend (didn't want to wait for a shipment and the flashdrive wasn't working - u3 Launcher bs). I'm completely updated now, so no worries with the 8.10.

I've had Ubuntu up and running for a little over a day now and it's working great. Only about 10 gigs available, but I'm thinking I'll have to get some more memory this way.

---

