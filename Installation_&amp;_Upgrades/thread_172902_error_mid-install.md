---
title: "error mid-install"
date: 2006-05-09
forum: Installation &amp; Upgrades
---

### Post by climbdahill on 2006-05-09
Ok, so the live cd works and boots up fine, and i like it, so i decide to install.  I progress through the whole install process only for an error and a failure to copy file to come up.  It freezes after the partition process and after installing the base layer and then about half way through the copying other files process i get a failer and all the steps after it won't work.  

Now i tried buring the iso again on a different burner and i get a problem in the same step.  I ran the check integrity of cd-rom program at the end of the list of install processes and both times the cd failed saying that some file failed the md5 test.  

Is this cd integrity test reliable?  I downloaded the original iso twice and did md5 on both and they both checked out.  Could this be a hardware problem?  I used the partitioner to create a / 60GB ext3 chunk and a 1.5Gb swap and left 61 Gb free (for a windows load later).  What could be the problem?  Should i try a third burn?  

Thanks alot for any help!

---

### Post by Dr. Nick on 2006-05-09
[quote=climbdahill]Ok, so the live cd works and boots up fine, and i like it, so i decide to install.  I progress through the whole install process only for an error and a failure to copy file to come up.  It freezes after the partition process and after installing the base layer and then about half way through the copying other files process i get a failer and all the steps after it won't work.  

Now i tried buring the iso again on a different burner and i get a problem in the same step.  I ran the check integrity of cd-rom program at the end of the list of install processes and both times the cd failed saying that some file failed the md5 test.  

Is this cd integrity test reliable?  I downloaded the original iso twice and did md5 on both and they both checked out.  Could this be a hardware problem?  I used the partitioner to create a / 60GB ext3 chunk and a 1.5Gb swap and left 61 Gb free (for a windows load later).  What could be the problem?  Should i try a third burn?  

Thanks alot for any help![/quote]

You say you switched burners, how about cd media? If you were using -rws that may be the problem, I have had similar trouble with -rw discs. If you are using -r then I am not sure what would be the problem, maybe try a different brand or burning application? I would believe the test to be reliable

Also I would reccomend loading windows now if you know you will need it, its easier to install linux after windows since windows will overwrite grub when it installs making your ubuntu unbootable until you fix it.

---

### Post by damianubuntu on 2006-05-09
some people have reported errors from burning, ie the downloaded iso checks out but then the cd fails.  Reportedly solved by burning at 1x.  See also 

[https://wiki.ubuntu.com/HowToMD5SUM](https://wiki.ubuntu.com/HowToMD5SUM)

for a useful bit on checksumming the CD iso after burning it.

Plus a search in this forum for debootstrap should highlight a number of similar faults and possible ways forward.

Good Luck :-)

---

