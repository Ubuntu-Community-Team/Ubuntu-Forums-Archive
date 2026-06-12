---
title: "Wubi to ubuntu only"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by sorryiambad on 2011-03-19
Hi everybody.

I used Wubi to install ubuntu and now I would like to use it as my main OS. First off, I'm obviously very new to ubuntu so my knowledge is extremely limited but I'd like to learn. I found this thread [http://ubuntuforums.org/showthread.php?t=1519354]("http://ubuntuforums.org/showthread.php?t=1519354") and got wubi-move-2.0.sh and extracted it but I have no idea what to do next. If anyone could get me headed in the right (and most likely obvious) direction I would appreciate it! 

Thanks

---

### Post by bcbc on 2011-03-19
That script allows you to migrate the wubi install to a partition install. You need to create the partitions first. A migration is good if you have spent some time customising Ubuntu and don't want to do it all over. Plus it maintains your installed programs and data.

If you don't know how to partition, you could always do a normal dual boot install - as it will automatically set up the partitions for you. Use this if you haven't done too much on your Wubi Ubuntu and you are OK starting fresh.

To start off, boot into Ubuntu and paste the output of:
```
sudo fdisk -l
``` That's a lower case -L

---

### Post by sorryiambad on 2011-03-19
> **bcbc said:**
> That script allows you to migrate the wubi install to a partition install. You need to create the partitions first. A migration is good if you have spent some time customising Ubuntu and don't want to do it all over. Plus it maintains your installed programs and data.

If you don't know how to partition, you could always do a normal dual boot install - as it will automatically set up the partitions for you. Use this if you haven't done too much on your Wubi Ubuntu and you are OK starting fresh.

To start off, boot into Ubuntu and paste the output of:
```
sudo fdisk -l
``` That's a lower case -L

I actually don't even want to dual boot. All I would like is to have ubuntu with all of the customizations and tweaks that I have right now (running wubi). 

What would be the easiest way of doing that for ubuntu noob? btw I have a 40gb ssd that I want to install ubuntu on (currently has win7 on it) and a 500gb hdd for storage.

---

### Post by Frogs Hair on 2011-03-19
Do a clean installation of Ubuntu and remove Windows.Make sure that you don't or won't need Windows and proceed. [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

