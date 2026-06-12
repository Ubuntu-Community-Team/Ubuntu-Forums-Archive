---
title: "Install Help: Partitioning Freezes"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by carcharius on 2010-05-06
Hi everyone, new guy to the forums and Ubuntu here. 

I'm trying to install 9.10 on my desktop, but when it gets to the part where it starts partitioning the drive it just sits at 5%. I let the installer run for over and hour and it never got further. I've tried installing on two separate drives and both times the same thing happens.

Thanks in advance for your help.

---

### Post by oldfred on 2010-05-06
Were these drives ever in a Raid configuration - Do not run this if they are raid drives:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

### Post by carcharius on 2010-05-12
No, they haven't been used in a raid config.

---

### Post by dino99 on 2010-05-12
a small howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

