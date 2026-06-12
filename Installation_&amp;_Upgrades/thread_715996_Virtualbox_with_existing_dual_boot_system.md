---
title: "Virtualbox with existing dual boot system"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by huviduc on 2008-03-05
I currently have an existing XP and Ubuntu 7.04 install. Both are working great but i am wondering if it is possible to use my existing XP installation through Virtual box. I have figured out how to install a new virtual installation, but i cant figure out how to boot my existing installation with it. Any help would be great? Im not very familiar with it, so i would prefer in depth explanations if possible. I have also searched for threads on my situation but i cant find anything.

---

### Post by kellemes on 2008-03-05
Not possible as far as I know..

---

### Post by pete on 2008-03-05
[This thread]("http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn") got me up and running with my XP partition in Virtualbox.

I've been running this setup for a few months now with no problems.

---

### Post by huviduc on 2008-03-05
I cant figure out what i am doing wrong, i am trying to follow that thread but i am getting the error below. Thanks for the help. Also, when it says "efore you boot to your windows partition I highly recommend you create a second hardware profile. ", how do i make this profile? thanks


i tried this:
```
huviduc@huviduc-laptop:/home$ VBoxManage internalcommands createrawvmdk -filename /home/huviduc/.VirtualBox/Machines -rawdisk /dev/sda -register
```


and got this:
```

VirtualBox Command Line Management Interface Version 1.5.0
(C) 2005-2007 innotek GmbH
All rights reserved.

Error opening the raw disk: VERR_FILE_NOT_FOUND
```

---

### Post by pete on 2008-03-09
I might be wrong, but I think the reason you're getting the error is that you haven't specified a filename for the vmdk you're creating.

You've got "/home/huviduc/.VirtualBox/Machines", but that's just directory-- it should be "/home/huviduc/.VirtualBox/Machines/<FILENAME>", where <FILENAME> is the name of the .vmdk file you're creating, e.g., "winxp.vmdk".

As for creating a profile, you'd need to boot into Windows, right-click on My Computer, go to Properties, and in one of the tabs of the properties window, you should have the option to create a new hardware profile (don't remember exactly where it is off the top of my head, but it's fairly easy to find by clicking around).  You can just create a copy of your current hardware profile, and from then on, whenever you boot into Windows, it will ask you which hw profile you want to use.

---

### Post by huviduc on 2008-03-10
> **pete said:**
> I might be wrong, but I think the reason you're getting the error is that you haven't specified a filename for the vmdk you're creating.

You've got "/home/huviduc/.VirtualBox/Machines", but that's just directory-- it should be "/home/huviduc/.VirtualBox/Machines/<FILENAME>", where <FILENAME> is the name of the .vmdk file you're creating, e.g., "winxp.vmdk".

As for creating a profile, you'd need to boot into Windows, right-click on My Computer, go to Properties, and in one of the tabs of the properties window, you should have the option to create a new hardware profile (don't remember exactly where it is off the top of my head, but it's fairly easy to find by clicking around).  You can just create a copy of your current hardware profile, and from then on, whenever you boot into Windows, it will ask you which hw profile you want to use. 
Thanks, i thought that may be what it meant

i tried this and it tells me "No such file or directory. 
```
 huviduc@huviduc-laptop:/home$ VBoxManage internalcommands createrawvmdk -filename /home/huviduc/Winxp.vmdk -rawdisk /dev/sda -register
```

I also tried this cause me windows partition is mounted on /media/hda1
```
huviduc@huviduc-laptop:/home$ VBoxManage internalcommands createrawvmdk -filename /home/huviduc/Winxp.vmdk -rawdisk /media/hda1 -register
```

same thing. not sur eif that made sense but it didnt work anyway. Any help?

---

