---
title: "Correct partitioning steps for alternate installation"
date: 2017-01-25
forum: Installation &amp; Upgrades
---

### Post by gipsyshadow on 2017-01-25
Hi all,
I want to install lubuntu 16.04 on a notebook with an hd partitioned this way:

/dev/sda1 linux Swap; ID 82
/dev/sda2 Win (ntfs); ID 7; mounting point: /media/win; flag boot
/dev/sda3 Linux (ext4); ID 83; mounting point: /
/dev/sda4 W95 (LBA); ID F; flag LBA
[about 100MB of non partitioned space]
/dev/sda5 Archive (ntfs); ID 7; mounting point: /media/archivio

new lubuntu will replace the old one on sda3 and the rest of the hd will remain partitioned in the above way, that's my goal.

I'll use the alternate release of lubuntu 16.04 due to the little ram available. My main problem is I really don't know how to proceed in an alternate installation to obtain my result, so I ask you to tell me exactly what to select and type step by step in advance so I'll be able to carry a correct installation.

Now I'd want to refere to [this guide]("https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall"). In particular I don't know what to do at step 11 (partitioning). When and where and how will I tell the installer to set the hd's partitions in the above way? I guess I'll have to choose "2. Manual..." and then?
I saw a youtube video on a similar installation and I know the next step (video screen) is to set partitions as swap, /, ect. For ex: "you are editing partition #3 of ...." and I'll have to choose "use as ext4" and "mount point /". In other words won't I have to change anythyng? Will the installer understand it has to install lubuntu on / partition?

Sorry if those questions sound dumb to you but it's my very first time with alternate and I don't want to damage my data.

---

### Post by yancek on 2017-01-25
I've never used the "alternate Installer" but I'm sure you would need to use the Manual option.  That would be similar to the Something Else option in the graphical installer.  If you already have this partitioning set up, all you have to do is select to install the / (root) filesystem to the sda3 partition.  Did you watch the youtube video linked from the link page you posted?  Seems pretty detailed to me and I doubt you will find anything better.

---

### Post by gipsyshadow on 2017-01-25
Hi yancek, well [this is the video]("https://www.youtube.com/watch?v=Xi-VPj4jzrg") I was referring to. I just had dubts because he/she seems to do lots of mistakes, I mean he goes back and forth again and again. Anyway if it will be so easy it's better!

---

