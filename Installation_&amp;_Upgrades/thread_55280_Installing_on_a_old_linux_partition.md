---
title: "Installing on a old linux partition"
date: 2005-08-08
forum: Installation &amp; Upgrades
---

### Post by Pablo El Vagabundo on 2005-08-08
I am in the middle of an upgrade of some hardware and a linux partition. I have an old Mandrake version installed that does not currently boot. I would like to install Ubuntu on the  partitions I currently have setup (40 gig root and 500meg swap)

There is about 20-30 gigs of data in the home dirs that I do not want to try and transfer to another disk or backup. I dont need to keep the old directories though.

What is the best method of installing ubuntu on this settup?
Do ubuntu like some funky partition setup? Can I install without it formating the root partition? Just applications/kernal/boot loader?

thanks

Pablo

---

### Post by Pablo El Vagabundo on 2005-08-08
After buzzing around this forum it looks like the root will have to be formated.

For others out there with this problem here is what I will try:

- Using a liveCD I will have to burn the information onto DVDs <sigh>
- Install ubuntu, reformatting the partition
- copy the data back onto the new installation

I am sure that there is some funky ubuntu from scratch thing i could do to install a base system manually and then  do an apt-upgrade or something, but it looks like the straightforward and tedious way is probably more reliable.

I think maybe a suggestion for future installers would be for an advanced option to use the partition as is and only keeping the home dir, that is all anyone usuauly wants to keep anyway.

Some people have suggested that it would be best to have a separtate /home partition, but to be honest I like having the flexibility and I never know how much to give apps...

Pablo

---

