---
title: "Installing Ubuntu 11.04 A3 along with Ubuntu 10.04 sharing same /home &amp; /opt partitio"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by dpen41 on 2011-03-21
Dear Fellow members,

I have been using Ubuntu for quite sometime and looking forward for Natty (11.04) release. 

While Natty being in alpha release I would like to test it. Currently I have 10.04 installed with separate /home & /opt partitions. Now I want to install 11.04 along with 10.04 but both should share same /home & /op partitions. 

I will create separate user for 11.04. So let me know is it Okay to do above? Or what could be better way to do?

-
Regards,
dPEN

---

### Post by Dutch70 on 2011-03-21
I'm not sure it would be a good idea to share a /home partition because your .config files are in there. Which contain all of your settings. 

What may be a better idea is to share a data partition. If you even need that, because all of your files in /home on 10.10 will be accessible from 11.04. I would just install 11.04 without a separate /home, Make the partition large enough to keep a few files, but save/move all of your important files to your 10.10 /home.

---

### Post by dpen41 on 2011-03-21
Hi Dutch70,

Thanks for quick reply and I agree with you your approach as it is safe also.

One more Qs. if I have separate users (of course in same /home) for 11.04 and 10.04 wouldn't it preserve settings?

-dPEN

---

### Post by Dutch70 on 2011-03-21
> **dpen41 said:**
> Hi Dutch70,

Thanks for quick reply and I agree with you your approach as it is safe also.

One more Qs. if I have separate users (of course in same /home) for 11.04 and 10.04 wouldn't it preserve settings?

-dPEN

 I believe it would. One way to do that to help keep them separate is to have user names like mav-david & natty-david. I've never done anything like that though. 

Have a look at my hdd...lol. It's still a work in progress. I also have Maverick with a separate /home & Vista on my other hdd, but these all share the same data & swap partition.

---

