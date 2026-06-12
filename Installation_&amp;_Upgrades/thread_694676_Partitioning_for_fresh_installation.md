---
title: "Partitioning for fresh installation"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by Kivech on 2008-02-12
Ok, I am all ready and set up to make the big step from Vista to Ubuntu.

In my case Ubuntu seems to be working better than Kubuntu, so I decided to go for that one. All software I need I managed to get running properly on a dual boot system, and I'm convinced it is safe to make the full switch.

So this leaves me with the final step to use for wiping my disks and making a clean install of Ubuntu 7.10.

So how do I partition my disks? I have worked out a set up, but I'm not sure I have got it right. Mainly due to conflicting posts in these very forums. So I want to check with you guys if my setup is right.
Keep in mind that I want everything to be set up in such a fashion that if I ever have to upgrade in the future, all my data is safe and sound and I just have to change the new software. Also I'll be trying to set up a software RAID, so if any of you has experience with that with Ubuntu, please share me the details.

This is what I have now:

I have two disks of 190 Gb that I intend to run in a RAID 1 configuration.

/(root)             10 Gb
/boot             512 Mb
/usr                 10 Gb
/swap              16 Gb (anticipating 8 Gb of mem)
/var                   6 Gb
/home              all remaining Gb (about 140 Gb)

Please let me know if this setup makes sense. For me changing / from 512 to 128 is rather pointless for example since the large disks I have. I just need to know if this configuration will last me for years to come and if in comparison they are sized approximately right.

Thanks in advance for your help.

Kivech

---

### Post by mxg01 on 2008-02-12
I think you may have the sizes for /boot and / the wrong way around. Little goes into /boot but everything that's not mounted separately will end up mounted from /. 

Other than that I can't see much wrong with your plan.

---

### Post by chavanak on 2008-02-12
i second mxg01 

Everything is perfect other than the above mentioned

---

### Post by Kivech on 2008-02-12
Thanks for the replies guys, and you are right!

I just checked my notes I took from which I put the numbers in my post and I did mix those two up, so I originally had them the way you guys are suggesting.

I take it I'm good to go now. :)

Kivech

---

