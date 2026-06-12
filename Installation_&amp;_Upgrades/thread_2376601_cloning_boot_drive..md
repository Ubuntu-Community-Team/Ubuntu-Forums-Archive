---
title: "cloning boot drive."
date: 2017-11-04
forum: Installation &amp; Upgrades
---

### Post by because7892 on 2017-11-04
Hello i have been using Ubuntu on my PC for about 8 months and it has been great Linux and Ubuntu in my opinion is far better than windows or mac OS. However the PC on which it is installed has a single 7200 rpm 1TB HDD. as a result it is quite slow when booting and loading applications. i was wondering if there is a way to clone the entire boot drive to an ssd and then select the ssd to boot from. i want to do this as i spent ages downloading stuff and customising my OS. i have like 300GB of games on here that i dont want to haft to re download. so is there anyway to copy the entire OS in its current state to an ssd without reinstalling anything. all help will be much appreciated.
thanks.

---

### Post by sudodus on 2017-11-04
It would probably work to clone with [Clonezilla](http://clonezilla.org), if you get an SSD of exactly the same size (in bytes) or bigger, but such an SSD is very expensive. You should check that the drives use the same sector size, which can be checked with ```
sudo parted -ls
```

Otherwise you have to do a more complicated operation. What size of SSD are you intending to buy? Do you want 'everything' on the current 1 TB HDD to be copied to the SSD? How much data are there? as seen by ```
df -h
```

---

### Post by because7892 on 2017-11-04
i was looking at a 120GB SSD the only thing on the one TB HDD that i wanted to move was my steam library witch takes up about 300GB. i was going to install Ubuntu on the ssd and then use the 1TB HDD for large files like the steam library. i might just haft to bite the bullet and format the drive and do a fresh install on the SSD when i get it. 
thanks for your help anyway.

---

### Post by sudodus on 2017-11-04
You are right. In this case it is probably easiest to do a fresh install on the SSD.

---

