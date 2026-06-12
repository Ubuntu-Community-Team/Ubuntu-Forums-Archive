---
title: "Settings and files gone after 11.04 upgrade and reboot"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by j8kster on 2011-04-29
So here's the problem. I upgraded to Ubuntu 11.04 final from 10.10 yesterday. The process went smoothly and everything seemed to be working fine. All my files and previous settings had survived the upgrade and were just as they were before. I shutdown my system and rebooted later that day. Upon starting my system I found that Ubuntu booted into what looked like a fresh install. All of my icons on the unity bar were gone, all the files in my home directory gone, and all of my personal settings and tweaks were gone. After frantically searching around I found that the space used on my hard drive had not changed and therefor I think my files and settings are still on the drive just not being picked up by ubuntu for some reason. My previous home dir was encrypted and I think the problem be that for some reason the new ubuntu install is not reading the encrypted files in my old home directory. Also there is a hidden folder in my home dir called .ecrypts which contains what appears to be my old home dir only encrypted. Please help me. If anything I would just like to be able to get access to my old files to back them up. Thanks.

---

### Post by alex.wifiguy on 2011-05-01
I'm currently running 10.10 with full disk LVM encryption.
Has anyone upgraded a setup like this to 11.04 without running into some serious problems/major data loss?

---

### Post by alex.wifiguy on 2011-05-05
Bump
Has anyone make the 11.04 upgrade on LUKS encrypted system successfully?
I personally would rather do a clean install but just don't have the time right now.

---

### Post by AchBlewy on 2011-06-20
You have found no explanation or obtained no cogent reply? At least see: [http://ubuntuforums.org/showthread.php?t=1785753](http://ubuntuforums.org/showthread.php?t=1785753)

---

### Post by elundmark on 2012-05-31
Open a terminal and type in
```
ls ~
```
If you see a lot of weird "double" files/folders, I have a solution:
[http://ubuntuforums.org/showthread.php?p=11985796#post11985796]("http://ubuntuforums.org/showthread.php?p=11985796#post11985796")

---

