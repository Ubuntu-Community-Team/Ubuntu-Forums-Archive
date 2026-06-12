---
title: "Can dual boot share the same data drive?"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by Ozsmoka on 2006-06-11
Hey all,

Im preparing my system for installing Ubutu 6.06 and I have a few simple questions. I hope its ok to wrap them together in one post :confused: 

I have an 80 gig hd with xp installed. I have a 300 gig hd with no OS on it which is used to store/retreive data, ie movies, music files, art work, back ups etc.  I have just picked up and installed and formatted an old 20 gig drive which contains two partions (which I cant seem to merge grr). 

Question 1: I want to dual boot my system and allow both Ubutu and Xp to share my 300 gig data drive is this possible?

Question 2: I would like to set up Ubutu on my 12 gig partion- is this enough space for the OS, which would hopefully become my primary OS?

Question 3: If this works out the way I expect, I would like to add Ubutu to a new 80 gig drive, so that both OS have the same amount of hd space and they would share the data drive. Can I set up Ubutu on my 12 gig partition, then port that to a new drive. Would I need to install twice, the second time could I just copy my exising settings over the new install if I change  hard disks?

Sorry if this has too many issues in the same post, but I seriously want to get Ubutu up and running asap and I need to get the foundation for my platform right for the best results.

Thanks in advance,

Oz

---

### Post by bruce89 on 2006-06-11
[QUOTE=Ozsmoka]
Question 1: I want to dual boot my system and allow both Ubutu and Xp to share my 300 gig data drive is this possible?[/QUOTE]
If it partitioned as FAT, yes.
[QUOTE=Ozsmoka]Question 2: I would like to set up Ubutu on my 12 gig partion- is this enough space for the OS, which would hopefully become my primary OS?[/QUOTE]
It should be enough, depends on how much stuff you install.  I have Ubuntu on a 8GiB partition here.
[QUOTE=Ozsmoka]Question 3: If this works out the way I expect, I would like to add Ubutu to a new 80 gig drive, so that both OS have the same amount of hd space and they would share the data drive. Can I set up Ubutu on my 12 gig partition, then port that to a new drive. Would I need to install twice, the second time could I just copy my exising settings over the new install if I change  hard disks?[/QUOTE]
You can copy the partition with Gparted, which is on the LiveCD.

---

### Post by bohboh on 2006-06-11
[QUOTE=bruce89]If it partitioned as FAT, yes.[/QUOTE]

I cant stress how important it is to partition the drive as FAT. I recently went through it all and not knowing it, i formatted it as ntfs which ubuntu cant write to (still in its experimental stage).

---

### Post by Ozsmoka on 2006-06-11
Hey thanks all, thats invaluable information. I really appreciate the benefit of your experience. Thanks bohboh, I would have gone through the procedure the same way as you did (ntfs) so you saved me some serious grief :)

Cheers

---

