---
title: "transfer ubuntu 10.04 to new harddrive with Win 7 already on it"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by cglee on 2010-05-17
[SIZE=2][COLOR=Indigo]Hello all,
I have a interesting situation.
I have Ubuntu 10.04 64 bit loaded on a 160 gig hard drive, the hard drive has errors on it and is going bad.
I have a newer hard drive 280 GB that I want to transfer the existing Ubuntu image over to, I want to load Windows 7 on it first so that I can have a dual boot.I also want to make the Ubuntu partition larger
What are the best steps for me to take to make this happen and is this even possible.

Is it better for me to install a new copy of Ubuntu, if so how can I transfer all my bookmarks, history,drive links and user accounts over to a new install of Ubuntu? [/COLOR][/SIZE]

---

### Post by ronparent on 2010-05-17
The easy way to transfer your current ubuntu install is to simply copy and paste it to the new drive using gparted in the live cd! You might want to verify the partitions integrity prior to transfering if the old drive is failing. You will need to unplug the old drive and use the live cd to also setup and update the grub.

Since the original ubuntu install and the copy both have the same uuid, it would be best to remove it from the computer before trying to load the copy!

---

