---
title: "How do I upgrade one of two Ubuntu versions dual booted on my hard drive?"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by Starfleet on 2011-10-06
Hi everyone, I have two versions of 10.04LTS on my hard drive. The primary partition sda1 has a 32bit version, and my sda6 has a 64bit version. Of course there are swap partitions relating to each one also. I've been running both versions for sometime and have found it very useful.

I now want to replace my 32bit version of 10.04 with Ubuntu 11.04. This will therefore go on the primary partition directly in it's place. When I load my 11.04 disc it wants to triple boot alongside the two 10.04's (I think!). Can anyone tell me...how do I remove 10.04 32bit so that 11.04 installs in it's place? I don't want to ruin my 64bit Ubuntu 10.04. It's in constant use. I've tried searching for the answer to this one but not found anything.

Thanks in advance for any replies.

---

### Post by oldfred on 2011-10-06
Since partitions already exist, you need to use manual install or Something Else in Natty. You then just choose which partition to use as / (root) and what format (ext4 or ext3). If you have a separate /home you have to tell it which partition to mount but DO NOT format it. You do not need two swaps, it normally finds swap if it exists, but with two I am not sure what it will mount (maybe both?).

Have you backed up all your data from that install. Made a list of installed apps with dpkg?

---

### Post by Starfleet on 2011-10-06
Oldfred, thanks so much for your input. Using the method you outlined I was able to install 11.04 perfectly over the top of the old 10.04LTS 32bit version. It was indeed the 'Something Else' button that I needed, selecting the options you mentioned. However, I did tell 'Natty' what swap to use also. It all worked like a dream with 'Natty' saving all my documents and applications (which I had already backed up by the way!). 'Natty' upgraded Grub and I still have the perfect dual boot system. 

I have to say I'm very impressed with Natty and the way it handled the entire operation. It's seems very intelligent and coped with everything.

I will mark this thread as solved as soon as I find out how to do that. Yep...just noticed your sig which tells me how. Thanks again oldfred, your a star!

---

