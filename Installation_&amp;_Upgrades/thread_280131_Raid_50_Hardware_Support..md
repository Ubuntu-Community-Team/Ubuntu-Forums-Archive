---
title: "Raid 50 Hardware Support."
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by Lasander on 2006-10-19
I am planning on purchasing a RAID controller such as [http://www.newegg.com/Product/Product.asp?Item=N82E16816102076]("http://www.newegg.com/Product/Product.asp?Item=N82E16816102076")
While it says it supports linux I was wondering if anyone had any experiences with hardware RAID.  I have read other threads and people seem to have trouble with software RAID.  

My ideal setup is a RAID 50 with 8 drives or so.  But I can't bare to stick only with linux if it doesn't support my data storage needs.

---

### Post by Dreadknott on 2006-11-03
I just tried to do the same thing...
I used a Highpoint Rocket Raid 464 4 channel that supports eight drives.
I got it working but its not worth the trouble...

1st. the Linux drivers and source on the HP/RR site are not maintained.  they claim the image for Suse 10, Fedora 5, work, but they do not.

2nd. the source won't compile on Ubuntu, Suse 10, FC5, Gentoo.

3rd. I got to someone via email, and they dont care if the latest builds for the Suse 10, FC5 work or not.

4th. I finally got it to install on FC4, but if you upgrade the kernel it stops working.

5th. the crappy card has decided it doesnt want to maintain one of the raid 5 drives after its been up a week so it defaults to raid 0

I saw on a thread somewhere on Ubuntu forums, there are Hardware Raid, not 464 Highpoint $150 fakeraid garbage, that actually work out of the box.
I plan on trying one of those and using my Ubuntu instead of crap FC4...

---

