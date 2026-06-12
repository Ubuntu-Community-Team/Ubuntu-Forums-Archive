---
title: "how to save patitions after opensuse formated them to dm raid?"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by Ascenti0n on 2009-11-25
Hi all, I have been using Ununtu/Kubuntu for many years, with only minor problems, but I was tempted over to opensuse 11.2 after some glowing reviews and the desire for something different. Anywho, I have three HDDs and opensuse correctly guessed the drive and partition ubuntu was on, the same drive also included my /home and /datafiles partitions.

opensuse formatted them to ext4 but they have a 'dm raid' type attached to them, and I was not aware this would happen. As a result, I want to re-install Ubuntu, but I want to try and save the two partitioned I mentions above, which live on sdb alongside whatever OS is installed, currently opensuse 11.2.

I've loaded an Ubuntu liveCD and whilst Ubuntu regognises the above partitions, it does so as a volume per partition and it doesn't any longer recognise /datafiles and it's contents.

Can anyone offer some guidance to help prevent me having to reformat the entire drive.

---

### Post by oldfred on 2009-11-25
If you do not want to keep the drives as raid, you have to remove some settings that Karmic finds:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)

---

### Post by Ascenti0n on 2009-11-26
The following code stripped the 'dm raid' status away, leaving me free to work with 'normal' partitions using gParted


```
sudo dmraid -E -r /dev/name_of_your_disk
```

---

