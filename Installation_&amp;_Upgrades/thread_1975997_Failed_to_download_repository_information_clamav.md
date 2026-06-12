---
title: "Failed to download repository information: clamav"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by tristevoix on 2012-05-08
Hi,

I upgraded last week from oneiric to precise and now I get this error message each time I try to update:
W:Failed to fetch [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

On top of that, even though I last updated yesterday, I'm being told my latest update is 9 days ago. I suspect this has something to do with it. I searched left and right but couldn't find exactly what it is I should be doing to solve this issue.

Can anyone here help me, please?

[SOLUTION]

K, finally found out how to solve this issue. For those interested, I used ubuntu tweak's source editor (under admins) and found out everything I needed to know. Thanks, google!

Thanks! =)

---

### Post by dino99 on 2012-05-08
you are using an unmaintained ppa: nothing new since oneiric :lolflag:

[https://launchpad.net/~ubuntu-clamav/+archive/ppa](https://launchpad.net/~ubuntu-clamav/+archive/ppa)

you dont need ppa there

---

### Post by tristevoix on 2012-05-08
Um, k, weird it just started showing up after the upgrade. I mean, I updated just before the upgrade and didn't get that error. Must be a coincidence or something. ;)

Anyway, I tried to remove them from source.list but when I look into the file I can't find them. So this ppa information is somewhere I don't know and I can't remove it and still get the error.

How should I fix that?

Thanks!

---

### Post by tristevoix on 2012-05-09
Hi,

Just checking again to see if I can get any more help with this issue.

Thanks!

---

