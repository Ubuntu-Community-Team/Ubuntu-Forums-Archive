---
title: "Installing Xubuntu Over Ubuntu"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by Hexx on 2006-07-14
I have my hard drive partitioned so that I can dual-boot WinXP and Ubuntu 6.06. However, I'd like to make a fresh install of Xubuntu over my Ubuntu partition.

However, when I got to Xubuntu's partition managing screen during the installation, I realized I had no idea what to do. I want to keep the partition sizes as they are. I just want to install Xubuntu over the Ubuntu install. Can someone help me with this?

And before anyone tells me that I can apt-get install xfce, I realize that. What I want to do is a *clean install* of Xubuntu over my Ubuntu partition.

---

### Post by aysiu on 2006-07-14
This will give you a relatively clean Xubuntu. It's worth a try, since you're planning to reinstall anyway.

Step 1: [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)
Step 2: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by Hexx on 2006-07-15
> **aysiu said:**
> This will give you a relatively clean Xubuntu. It's worth a try, since you're planning to reinstall anyway.

Step 1: [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)
Step 2: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Thanks for the reply, but it doesn't sound like I'd be able to follow that tutorial, since the computer I'm installing on only has a dial-up connection to the internet. Is xubuntu-desktop a big download?

---

### Post by jvdowney on 2006-07-15
Are you using a Xubuntu live cd? It's been a while since my install, but I believe if you go to the next screen, without changing your partitions, you will see checkboxes that will allow you to select which partitions to reformat. Select the ones you have your Ubuntu install on and continue from there.

---

### Post by aysiu on 2006-07-15
> **Hexx said:**
> Thanks for the reply, but it doesn't sound like I'd be able to follow that tutorial, since the computer I'm installing on only has a dial-up connection to the internet. Is xubuntu-desktop a big download?
Xubuntu would be a sizable download over dial-up. If you have the Alternate CD (instead of the Desktop CD), you could use that as a repository: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

---

### Post by Hexx on 2006-07-15
> **jvdowney said:**
> Are you using a Xubuntu live cd? It's been a while since my install, but I believe if you go to the next screen, without changing your partitions, you will see checkboxes that will allow you to select which partitions to reformat. Select the ones you have your Ubuntu install on and continue from there.

Yes, I've got the live CD. I'll have to boot up the disc and see if you're right.

> **aysiu said:**
> Xubuntu would be a sizable download over dial-up. If you have the Alternate CD (instead of the Desktop CD), you could use that as a repository: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

Unfortunately I only have the live CD. But I'm going to see what I can do.

BRB!

---

### Post by Hexx on 2006-07-15
Okay, just installed Xubuntu over my Ubuntu partition and it appears everything went well. Thanks for your replies!

---

### Post by PmDematagoda on 2008-04-16
Due to some people replying to this thread, I have closed this thread for good measure.

---

