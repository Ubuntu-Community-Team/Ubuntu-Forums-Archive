---
title: "Ubuntu live CD of 700MB?"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by Tylerp99 on 2010-10-23
So i was wanting to make a live CD for ubuntu, but upon getting the .ISO i found that the .ISO was 709MB, and my disc is 700MB.

How could i precede in making this live CD?

If i use some sort of over burning software, will the live CD work, and please recommend a software to do so if it does indeed work.

Any feedback would be much appreciated.

---

### Post by sikander3786 on 2010-10-23
Which version of Ubuntu is it? I never had any version exceeding the size of 699 MB till now. Where did you download it from?

---

### Post by Tylerp99 on 2010-10-23
10.10 (Latest build) I got it directly from ubuntu.com 
NOTE: I have not attempted to burn it yet, i was just wondering if i would have any problems since windows explorer says its 709MB and my disc is specs are:
CD-RW
Speed - 1x to 4x
700MB/80 Minutes

---

### Post by sikander3786 on 2010-10-23
This would confirm the problem, if any.

Check the MD5SUMs as per instructions here. Do they match?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Tylerp99 on 2010-10-23
I've decided to take my chances and burn it using nero, if i have any success i will change this post to 'solved'

---

### Post by mörgæs on 2010-10-23
It might be due to a miscalculation. 1 kB = 1024 B, 1 MB = 1024*1024 B and so on. 

If you read 709.000.000 bytes, the ISO will still fit on a CD.

---

### Post by Tylerp99 on 2010-10-23
Nero read the image as less than 700MB, so probably a miscalculation like you said, anyway, thanks for the help!

---

### Post by kansasnoob on 2010-10-23
MB vs MiB :)

I threw a wrench in that works when I filed this bug report:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/538165](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/538165)

And I wonder why I'm not loved :lolflag:

---

### Post by gbrowne on 2011-03-14
Just wondered how you got on with the Nero-burned image ?  I tried to burn an oversize image with Brasero and it just plain refused saying the media is too small.

(Trying to burn latest beta build of Natty by the way)

Cheers,
G

---

