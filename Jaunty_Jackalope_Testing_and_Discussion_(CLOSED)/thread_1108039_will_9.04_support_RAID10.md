---
title: "will 9.04 support RAID10?"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by vsiege on 2009-03-27
I'm in the process of building a new machine and am unsure how to proceed. I would like to create a RAID10 setup on it and have read that using software for to create an array like this would be my best bet or go with an expensive high-end RAID controller. I have also read that MOBO RAID's are fake too. So going of this info I'm thinking of installing 8.10 or possibly 9.04 when it comes out... any opinions of whether or not I should wait for the new OS?

Will that support RAID10?

---

### Post by Rocket2DMn on 2009-03-27
Moved to Jaunty Jackalope Testing and Discussion

---

### Post by xens on 2009-03-27
Linux md software raid support raid10 natively you can try it on 8.10 if you wish, here's a howto  [http://www.howtoforge.com/install-ubuntu-with-software-raid-10](http://www.howtoforge.com/install-ubuntu-with-software-raid-10).

I recommend to try it on a test machine.

---

### Post by vsiege on 2009-03-27
thanks... i've actually checked out that tutorial and wondered... is this just a bad idea?

I read [here]("http://linux-raid.osdl.org/index.php/Linux_Raid") about the mdadm and the linux RAID kernal, then got to the end whre they pose the question... what happens if the mdadm daemon stops? I dunno, do you?

Thats why I was wondering if 9.10 would solve this issue or just make setup of RAID10 less work (not that its tons)?

---

