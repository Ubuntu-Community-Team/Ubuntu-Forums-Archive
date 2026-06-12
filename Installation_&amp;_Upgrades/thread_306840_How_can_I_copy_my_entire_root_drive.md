---
title: "How can I copy my entire root drive?"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by kdawg on 2006-11-25
I have two drives in my edgy system, one is root mount point and swap partition and the other is my home directory.  I want to upgrade the aging hard drive that is the root and swap partitions.  Can I plug the new drive in as a slave and copy the entire hda drive bit for bit to it and not have to reinstall?  Or would it just be easier to install onto the new drive and mount the hdb /home drive afterwards? thanks!

---

### Post by taurus on 2006-11-25
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by kdawg on 2006-11-25
Thanks for the quick reply.... going to try this out tonite!

---

### Post by kdawg on 2006-11-26
Well I ended up just reinstalling onto the new drive.....  They were different size drives so I didnt want to take an image from my 40 gig and not have it fit on the 30 gig!

---

### Post by MJN on 2006-11-26
Partimage would have refused to do it anyway even if you'd only used 20GB of your 40GB partition (this isn't because it's crap, it's merely an inevitable consequence of how it works).

I've done this on a number of occasions and have always booted from a LiveCD, partition the new drive and mount both new and old. Then it's simply a case of copying everything across (I actually use rsync merely out of convenience). You may need to reinstall GRUB too.

Mathew

---

