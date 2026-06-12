---
title: "Raid started checking automaticatlly in fresh install"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by SpadaSpud on 2012-05-05
Hi All,

Hope someone can help here. After having a perfectly working Ubuntu desktop 11.04 running a raid6 with 12x2TB drives I upgraded to 11.10 then to 12.04 and this screwed everything. I tried so many things to recover my raid I screwed it even more I decided to scrap the lot and start a fresh. I wish I just left it alone to start with.  

SO Since I had the prob with 12.04 I did a fresh install of 11.10. Wiped all the raid off the drives installed mdadm then created the raid and waited for the build to be completed.  I did have the boot issues explained in [here]("http://ubuntuforums.org/showthread.php?t=1861516&") but was fixed by there solution.

So I was all back to normal with fresh install but with no data. So I started copying over the data from a backup and left it over night. I come in the next morning and I notice that the raid is now in a action of checking(not degraded) in the disk utility. I also checked cat /proc/mdstat and it showed the checking and had something like 25000+ (however has also dropped to under 1000 sometimes then back up again) minutes to complete. Along time I guess but it is still copying data across.

My question is:
1: How did the raid automatically start a check process? Is there a default schedule setting to check raids on new installs that I can turn off?
2: Can I stop it checking mid way through and how? (as it still copying from the back up and has slowed down)

Thanks

PS. If this is in the wrong spot can a mod move to the correct location thanks.

---

### Post by SpadaSpud on 2012-05-06
Seems there is a auto check of raid setup for first sunday of the month. Which was yesterday.  [http://ubuntuforums.org/showthread.php?t=408461&page=4](http://ubuntuforums.org/showthread.php?t=408461&page=4)

I have commented out the line in the script. Dont know if that will work. But now to safely stop the check?

Any Ideas anyone?

---

### Post by SpadaSpud on 2012-05-07
nope no one has an idea. it finished now so dont need to know now. :D

---

