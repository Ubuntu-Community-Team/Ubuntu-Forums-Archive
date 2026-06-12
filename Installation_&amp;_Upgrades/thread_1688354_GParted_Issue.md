---
title: "GParted Issue"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by doctorzeus on 2011-02-15
Hello,

I had a quick look around and didn't see any threads that related exacly to this so here goes..

I am trying to add an NTFS pation to my HD inside my 
Ubuntu 10.04 LTS OS so I can install Windows 7..

However whenever I try to install gparted I get this error:

```
~$ sudo apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  gparted: Depends: libparted0 (>= 2.2-1) but it is not going to be installed
E: Broken packages
```

Any suggestions on how to fix this please?

---

### Post by wormyblackburny on 2011-02-15
Doesn't matter if you find it or not, you can't run G-parted on a mounted filesystem. You will need to run g-parted from the Ubuntu install disk. Boot your system with the disk and use g-parted to adjust the partitions. There are several good tutorials out there on how to dual boot win/Ubuntu. It is 10 times easier to install win first THEN Ubuntu, so be prepared, the process is going to be a little messy.... Check out this article for starters

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by thefasterblueone on 2011-02-15
First try fixing broken packages in Synaptic Package Manager. Then try reinstalling Gparted.

If that doesn't work try installing libparted0.      

```
sudo apt-get install libparted0
```

---

### Post by sikander3786 on 2011-02-15
Try using aptitude.

```
sudo aptitude install gparted
```

Keep a close eye on what is going to be installed and what is going to be _removed_. If you are not sure, don't accept the solution, just post the output here.

---

### Post by doctorzeus on 2011-02-15
> **wormyblackburny said:**
> Doesn't matter if you find it or not, you can't run G-parted on a mounted filesystem. You will need to run g-parted from the Ubuntu install disk. Boot your system with the disk and use g-parted to adjust the partitions. There are several good tutorials out there on how to dual boot win/Ubuntu. It is 10 times easier to install win first THEN Ubuntu, so be prepared, the process is going to be a little messy.... Check out this article for starters

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

Ok thanks for the heads up :)

Will try that...is it possible to install gparted when running from a live CD?

---

### Post by plucky on 2011-02-15
> Will try that...is it possible to install gparted when running from a live CD? 

It is already installed on the Live CD.Look under **System > Administration > Gparted**

Good Luck

---

