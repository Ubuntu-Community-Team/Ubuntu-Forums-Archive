---
title: "I effed up...oops"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by CrooKxD on 2011-03-11
Like a bonehead I only checked a few places when setting up my PC for a dual boot (MS Win 7, and Ubuntu 10.10) and created my root partition as a 5GB partition. I am now seeing that its filling up relatively fast (89% full in 2 days). My question is, should I go ahead and reinstall Ubuntu now, before my root is full? I have pretty much installed what I am going to install, of course I say this now but I have no idea what the future holds.

Also the HDD is 640GB with 100GB that I have designated for Ubuntu(When I did the install I did 4 partitions: Boot 500MB,Root 5GB,Swap 2GB and Home 90GB).

Any advise is appreciated

---

### Post by Sef on 2011-03-11
1) You should make your Ubuntu root 8 - 10 gigabytes at a minimum.

2) You do not need a boot partition.

3) You ram should be the same size as your swap, if you use suspend or hibernate.

---

### Post by CrooKxD on 2011-03-11
> **Sef said:**
> 1) You should make your Ubuntu root 8 - 10 gigabytes at a minimum.

2) You do not need a boot partition.

3) You ram should be the same size as your swap, if you use suspend or hibernate.

So go ahead and do a reinstall? Also I was reading in another thread that a large swap is necessary in low RAM instances. Im currently working with 6GB with an 8GB kit in the mail now. What would u recommend?

---

### Post by b0b138 on 2011-03-11
Depending on your partition structure, you might be able to just resize.

Low ram = 256 MEG, 6GB is plenty

---

### Post by Dutch70 on 2011-03-11
> **CrooKxD said:**
> So go ahead and do a reinstall? Also I was reading in another thread that a large swap is necessary in low RAM instances. Im currently working with 6GB with an 8GB kit in the mail now. What would u recommend?

Yes, you need to make your "/" partition larger. Any time you use more than 75% of it, you're slowing down your machine & no one wants that. Otherwise, we'd juse use that other OS. 8-10 GB is a safe minimum, but I would recommend 10-20. Especially since I have a feeling you'll be installing Wine. 

Swap = physical RAM is a good rule of thumb. You can add a little for good measure if you want, but if you have 6GB, and don't want to hibernate, you really don't even need a Swap partition.

> b0b138 - Depending on your partition structure, you might be able to just resize.
Low ram = 256 MEG, 6GB is plenty

+1

---

### Post by CrooKxD on 2011-03-11
> **Dutch70 said:**
> Yes, you need to make your "/" partition larger. Any time you use more than 75% of it, you're slowing down your machine & no one wants that. Otherwise, we'd juse use that other OS. 8-10 GB is a safe minimum, but I would recommend 10-20. Especially since I have a feeling you'll be installing Wine. 

Swap = physical RAM is a good rule of thumb. You can add a little for good measure if you want, but if you have 6GB, and don't want to hibernate, you really don't even need a Swap partition.



+1

Its a laptop so I will most likely use the hibernation at some point in time. So if I am understanding everything correctly you recommend reinstalling Ubuntu with roughly 20GB for (/) and 8GB for Swap (since I am going to be installing 2 more GB in less than a week) the boot partition u said isnt necessary? Its being dual booted if that matters and the remainder will go to my home partition.  I wanna make sure I got it B/C Im grabbin discs out now to git r done.

Also I was up all night last night getting my conky to work and I have no idea how I managed to get it to work but I somehow did and I have a synaptics touchpad which was fickle to say the least where would I find those config files to back them up so that I dont have to go through that headache all over again?

One more thing...does the root serve the same function as the program files folder in Windows? You referenced me using Wine alot so I wasn't quite sure if the root was more or less the equivalent. Thanks

---

### Post by Sef on 2011-03-11
> ts a laptop so I will most likely use the hibernation at some point in time. So if I am understanding everything correctly you recommend reinstalling Ubuntu with roughly 20GB for (/) and 8GB for Swap (since I am going to be installing 2 more GB in less than a week) the boot partition u said isnt necessary? Its being dual booted if that matters and the remainder will go to my home partition. I wanna make sure I got it B/C Im grabbin discs out now to git r done.

Since you want to use hibernate, I would make the swap 8 gb. 20 gb is more than enough for root. I usually make mine around 10, but having 20 will not hurt anything.

---

### Post by Dutch70 on 2011-03-11
> **CrooKxD said:**
> Its a laptop so I will most likely use the hibernation at some point in time. So if I am understanding everything correctly you recommend reinstalling Ubuntu with roughly 20GB for (/) and 8GB for Swap (since I am going to be installing 2 more GB in less than a week) the boot partition u said isnt necessary? Its being dual booted if that matters and the remainder will go to my home partition.  I wanna make sure I got it B/C Im grabbin discs out now to git r done.

That is correct. 20GB for / is quite large, but it depends on how much software you think you'll install. 
Mine is 15GB, I'm only using about 7-8.

> Also I was up all night last night getting my conky to work and I have no idea how I managed to get it to work but I somehow did and I have a synaptics touchpad which was fickle to say the least where would I find those config files to back them up so that I dont have to go through that headache all over again?

They would be in your .config folder with all of your current settings. You'll have to click "show hidden folders" to see them.

> One more thing...does the root serve the same function as the program files folder in Windows? You referenced me using Wine alot so I wasn't quite sure if the root was more or less the equivalent.
Thanks

I'm not real keen on windows, but I believe that would be correct as well.

---

### Post by CrooKxD on 2011-03-11
Awesome! Well I am off to reinstall and hopefully this is the last time I have to do all this! At least for a while xD I appreciate the help

---

### Post by CrooKxD on 2011-03-11
Reinstall went off without a hitch...kinda. I got sloppy an accidentally had grub placed on my windows MBR partition, so I fixed that and Im back up to good with a 20GB (/) and 8GB Swap xD Thx for the advise

---

### Post by Dutch70 on 2011-03-11
You're welcome, let us know how hibernation works for you before you mark this thread solved.

---

