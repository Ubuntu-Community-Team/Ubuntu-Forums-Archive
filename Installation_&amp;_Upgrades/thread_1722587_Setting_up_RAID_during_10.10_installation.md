---
title: "Setting up RAID during 10.10 installation"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by griztown on 2011-04-05
Is this possible?  I was able to do this with Debian 6 no problem.  The installation interface is really nice but seems to be lacking any way to do more advanced configurations.  Is there some boot option I can pass in?

---

### Post by griztown on 2011-04-06
It appears from the documentation that this is not possible with the standard Desktop install CD.  It also appears that if you want to do RAID 5, this will have to be done post install.  Does anyone have any experience with this?

---

### Post by griztown on 2011-04-07
I was able to set up RAID 5 using the alternate CD.  I set up a partition for the /boot and I used RAID 1 for that with a spare.  Then used RAID 5 across the other partitions and everything seems to be working great.

---

