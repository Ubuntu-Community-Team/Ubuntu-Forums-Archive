---
title: "SW Center Won't Update without Internet"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by johnfrediani on 2011-09-26
I am loading laptops for a service project in rural Nigeria with Ubuntu 10.04 using a USB drive (some of the laptops don't have CD ROM). I also want to be able to add some packages from the Restricted repository so I downloaded it to the USB drive as well, and then transferred it to the laptop's file system. I can't get Software Center to update and recognize the local repository unless I am connected to the internet even though I have internet disabled as a software source. Once I connect to the internet Softare Center updates I can disconnect and load packages from the local repository just fine. My problem is I want to be able to do this whole process in Africa without internet connectivity. How can I force Software Center to update.

---

### Post by zvacet on 2011-09-27
Put all packages ( and their dependencies) in one folder ( let name it folpack).Transfer that folder in Ubuntu home directory and then run

```
cd folpack
sudo dpkg -i *deb
```

---

### Post by johnfrediani on 2011-09-28
I tried that and got the following error mesage:
 
dpkg: error processing *deb (--install);
can't access achive: no such file or directory
 
I think I need to explain the structure I have. I am trying to create local copies of the restricted and main archives so I follwed these instructions:
 

Now, you have to store the files in your local Ubuntu repository in the same order. For example: 
[LIST]
[*]In /home/repository/dists/karmic you would have the files: Contents-i386.gz , Release and Release.gpg 
[*]And in /home/repository/dists/karmic/main/binary-i386 the files: Packages.bz2 , Packages.gz and Release
[/LIST]Then I used Software Source in the SW Center to add the correct path (/home/john/pack/repository lucid) to my repositories and seemed to get the correct line added to /etc/apt/sources.list. Then I did a apt-get update and it said   reading package list ...done
But SW Center still doesn't see the packages in the local repositories

---

### Post by plucky on 2011-09-30
> I tried that and got the following error mesage:

dpkg: error processing *deb (--install);
can't access achive: no such file or directory


I think the command should be ```
sudo dpkg -i *.deb
``` to install all the packages.

Good Luck

---

