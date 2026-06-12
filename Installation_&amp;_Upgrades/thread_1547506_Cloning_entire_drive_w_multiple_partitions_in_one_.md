---
title: "Cloning entire drive w/ multiple partitions in one step"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by Rubicon421 on 2010-08-06
I have used GParted several times but I only know how to clone a single partition. I am looking for a way to clone and entire drive that has several partitions, along withthe MRB, unpartitioned space and everything else in one step.

I have a 500 GB drive that is going out and I want to clone it to a 1 TB drive so I don't have to reinstall 3 different OSs and fix the GRUB. One of the other OSs is on anther drive so I'm not sure that it would work even if I can clone everything exactly. I'm not sure if the drive that is failing is the one with the MBR on it or not. 

Anyone know how to do this in GParted or know another good program I can run from a live CD to do this?

---

### Post by oldfred on 2010-08-07
I have not copied or cloned a drive as I believe reinstall is better, safer & actually quicker. I have seen some users use dd but then there new drive became the same size as the old drive and major effort was required to get the driver resized to its correct larger size. I also believe gparted will copy partitions, but am not sure about MBR. But reinstalling grub is easy.

I think when you have a new large drive it may be time to think about how you have things partitioned and what you plan to use computer for until you then buy another drive. Do you have lots of data then new separate /home and/or /data partitions may be worth having. Are you thinking about testing other systems? Then extra 20-25GB system partitions may be worth allocating. If not sure you do not have to fully partition system now.

If reinstalling you can copy /home and preserve all your user files and settings. If you still have your old drive you can check for any system wide settings in /etc (grub setting, networking, video etc). You can export a list of installed applications and easily reinstall. 
 dpkg --get-selections > ubuntu-files
More info:
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---

### Post by Rubicon421 on 2010-08-07
Well, I ended up just doing a reinstall and decided to go with a linux only set up this time. Thanks for the suggestion but I think it's time to ditch windows completely.

---

