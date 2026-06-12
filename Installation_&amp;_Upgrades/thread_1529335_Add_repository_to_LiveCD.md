---
title: "Add repository to LiveCD"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by jas007 on 2010-07-12
Hey
I have made several attempts at getting this to work, but no luck as of yet. I have followed the instructions [here]("https://help.ubuntu.com/community/LiveCDCustomization") without any success. 
All I want to do is install revolution-r on the 64 bit lucid distro. I have managed to add
```
deb [http://cran.melb.uni.edu.au/bin/linux/ubuntu](http://cran.melb.uni.edu.au/bin/linux/ubuntu) lucid/
```
to the sources.list file
i update the repo
```
apt-get update
```
but I am unable to use 
```
apt-get install revolution-r
```
or 
```
aptitude install revolution-r
```
within the chroot environment.

I have searched high and low for a solution, without any luck. Does anyone else have any ideas for a solution?
Thanks
Jason

---

