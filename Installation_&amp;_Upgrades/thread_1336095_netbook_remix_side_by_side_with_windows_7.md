---
title: "netbook remix side by side with windows 7"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by Felix-angeli on 2009-11-24
I recently got a a Samsung N130 which comes with windows 7. I use and love ubuntu on my regular laptop I and currently have a side by side installation so my wife can use windows. Is there a way to install Ubuntu Netbook Remix side by side with windows 7? When I started the install from USB drive ( the partition editor (for the netbook remix) did not offer the side by side option. Any tips would be helpful.

---

### Post by raymondh on 2009-11-24
> **Felix-angeli said:**
> I recently got a a Samsung N130 which comes with windows 7. I use and love ubuntu on my regular laptop I and currently have a side by side installation so my wife can use windows. Is there a way to install Ubuntu Netbook Remix side by side with windows 7? When I started the install from USB drive ( the partition editor (for the netbook remix) did not offer the side by side option. Any tips would be helpful.

Installing UNR based on 9.10?  I've seen threads in the forum where win7 is not recognized.

Here's another workaround if you want to consider.

-  Boot into windows7 and access its' disk management tool
-  Defrag windows7 (at least a couple of times if you have the patience)
-  Shrink windows7 ... allocating say 30GB (as an example).  Leave it unallocated/unformatted.
-  Close and exit windows7
-  Boot into your ubuntu install medium (CD, USB or DVD)
-  When you get to step 4, install ubuntu in the largest, continuous free space (which ought to be the recently freed-up space)

If indeed installing UNR 9.10 (which uses GRUB2), peruse and browse the forums first for experiences with regard to a win7 + 9.10 combination .... that way you can anticipate any challenges that may arise.

If using another version (say 9.04) .... here's a good read from Herman's site.

[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

As you may know by now .... UNR is "regular-ubuntu-optimized-for-a-netbook's-smaller-screen-size-using-maximus".  I.E.  You can install desktop Ubuntu and just add the UNR style (which is in the repos now).

Good luck and happy ubuntu-ing.

---

### Post by Dooms_day on 2009-11-24
i can successfully multi-boot backtrack4, win7, and UNR with a customized grub menu...once you figure out grub, its easy

---

### Post by raymondh on 2009-11-24
> **Dooms_day said:**
> i can successfully multi-boot backtrack4, win7, and UNR with a customized grub menu...once you figure out grub, its easy

Any hints/tips on how to get gparted to recognize his win7 install so he (OP) may install ubuntu ..... as per his original message/post?

If no hints, any workarounds you may recommend?

Congratulations on your 3-boot.

---

