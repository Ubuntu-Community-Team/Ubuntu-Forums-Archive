---
title: "Ubuntu friendly raid controller"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by fechin on 2008-03-19
Hi,
I'm  building a new ubuntu 7.10 64 bit server.  I looking at having a raid 0 configuration using 3 SATA drives.  Can you recommend a  RAID card that is ubuntu friendly. The [HighPoint RocketRAID2314MS]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816115042") seems good but it supports Redhat and Suse.  No mention of ubuntu.

Other info about the server:  
3 * 10,000 rpm 150GB WD1500ADFD
Intel [DG33FB]("http://www.intel.com/products/motherboard/DG33FB/index.htm") Mother Board
Intel Code 2 Quad

Thanks,
Fechin

---

### Post by sidprak on 2008-03-19
I was using RAID0 on two WDC 160GB SATA drives in my Core 2 Quad machine for a few months with absolutely no problems.  It has an Intel ICH9R raid controller.  
There was one slight problem and that was getting it installed in the first place.  As for that, I used the guide at:
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)

This guide got the RAID set working perfectly.

---

### Post by Herman on 2008-03-19
I understand you are asking about a RAID controller card so you will be using hardware RAID. I don't know enough to be any help with that.
I was just wondering if you were aware you can use the Ubuntu 'Alternate' installation CD to install Ubuntu with software RAID.
The best information I know about is [Ubuntu Screencasts's]("http://screencasts.ubuntu.com/") video, '[Installing Ubuntu part 2]("http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2")', just in case you're interested in checking that out. I'm not sure how well that will suit your purpose, but if will do the job you want it might save you some time and expense.

Regards, Herman :)

---

### Post by fechin on 2008-03-20
Thanks.  I'll give the software raid a go.

---

