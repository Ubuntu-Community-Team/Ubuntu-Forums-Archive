---
title: "Cannot Partition Hard Drive"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by deanjm1963 on 2010-04-23
I came across this problem earlier, and I thought it was just me or a dodgy build ... but I'm unable to partition with the desktop installer. I have no problems with an alternate installer or with karmic-desktop. It makes no difference whether it's 32 or 64 bit, I come across the same problems with the lucid betas/rc builds.

I have a fairly large HD, 750gb ... I partition it into the following

24GB - /
24GB - /home
110GB - /documents
430GB - /multimedia
110GB - /backup
108GB - /scratch
rest - swap

I can boot into the desktop installer, I go through the motions of setting up my partitions, add my user name, password, etc, but the moment I go to install I get a message saying that there is no partition setup.

Any help would be greatly appreciated.

---

### Post by dino99 on 2010-04-23
> **deanjm1963 said:**
> I came across this problem earlier, and I thought it was just me or a dodgy build ... but I'm unable to partition with the desktop installer. I have no problems with an alternate installer or with karmic-desktop. It makes no difference whether it's 32 or 64 bit, I come across the same problems with the lucid betas/rc builds.

I have a fairly large HD, 750gb ... I partition it into the following

24GB - /
24GB - /home
110GB - /documents
430GB - /multimedia
110GB - /backup
108GB - /scratch
rest - swap

I can boot into the desktop installer, I go through the motions of setting up my partitions, add my user name, password, etc, but the moment I go to install I get a message saying that there is no partition setup.

Any help would be greatly appreciated.

you might have miss a validation when you have created / or swap (dont make it larger than twice your ram)

---

### Post by amsterdamharu on 2010-04-23
Boot the live cd and then use gparted to partition the disk. During setup choose manual and select the mount points you want.

One advice for / this is your system and ubuntu system with some software should not easily go over 8G anything else goes in the home so I'd think that 16G should be enough. You can make a tar backup of the system and untar this with a live cd if you did something to mess up the system.

---

### Post by ratcheer on 2010-04-23
I found out by posting a question on Launchpad that they have changed the valid partition boundaries between Karmic and Lucid. Therefore, I had to use the Karmic partitioner to work with my existing partitions. Then, I could use the Lucid partitioner to create new ones that Lucid would use.

[https://answers.launchpad.net/ubuntu/+question/105020](https://answers.launchpad.net/ubuntu/+question/105020)

Tim

---

