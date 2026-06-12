---
title: "How to setup new ntfs partition"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by Olnex on 2008-03-13
I dual boot WinXP and Ubuntu 7.10, at first I formatted my hard disk and allocated two drives for XP, one for system, one for applications. The remaining part of my hard disk is not partitioned, I installed XP on C: and did not format D:, then I installed Ubuntu, it recognised C: with label WinXP, then I went to XP and formated D: however, D: does not appear like C: on my Ubuntu desktop, but I can see it in "Places" -> "Computer" and I have to enter my password in order to mount it, my question is, how to make D: available like C: ?
Thanks!

---

### Post by tomid on 2008-03-13
I hope I'm not hijacking this thread, but the title looks similar to my problem. Maybe the question is simialr enough that one answer will help both of us.

I have two hard disks. One for Windows and one for Ubuntu. Foolishly, I put Windows on the smaller disk and now I need more space since I don't expect Ubuntu to require nearly as much space as it currently has. Can I partition my Ubuntu disk so that I can use it for Windows (NTFS)? I think I have Edgy Eft Ubuntu, having installed it about a year ago.

---

### Post by sandysandy on 2008-03-13
> **tomid said:**
> I hope I'm not hijacking this thread, but the title looks similar to my problem. Maybe the question is simialr enough that one answer will help both of us.

I have two hard disks. One for Windows and one for Ubuntu. Foolishly, I put Windows on the smaller disk and now I need more space since I don't expect Ubuntu to require nearly as much space as it currently has. Can I partition my Ubuntu disk so that I can use it for Windows (NTFS)? I think I have Edgy Eft Ubuntu, having installed it about a year ago.

no issue at all.

try gparted live CD.

boot into gparted live CD and u can resize ur ubuntu partition. in the free space generated u can make one more partition with gparted and format to NTFS.

Backup data as a safety precaution.

regards

---

### Post by sandysandy on 2008-03-13
> **Olnex said:**
> I dual boot WinXP and Ubuntu 7.10, at first I formatted my hard disk and allocated two drives for XP, one for system, one for applications. The remaining part of my hard disk is not partitioned, I installed XP on C: and did not format D:, then I installed Ubuntu, it recognised C: with label WinXP, then I went to XP and formated D: however, D: does not appear like C: on my Ubuntu desktop, but I can see it in "Places" -> "Computer" and I have to enter my password in order to mount it, my question is, how to make D: available like C: ?
Thanks!


if u want to rename D;/ drive u can do so from windows itself. (from ubuntu also its possible).

it is not clear by what u mean by 

>  however, D: does not appear like C: on my Ubuntu desktop,

if u want it  mounted at startup its possible

regards

---

### Post by Oldsoldier2003 on 2008-03-13
[http://ubuntuforums.org/showthread.php?p=4507668](http://ubuntuforums.org/showthread.php?p=4507668)
[http://doc.gwos.org/doku.php/doc:hardware:fstab](http://doc.gwos.org/doku.php/doc:hardware:fstab)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Are all good resources to help you accomplish this. if you run into any problems  feel free to post again and folks will be glad to help clear things up for you.

---

### Post by sisco311 on 2008-03-13
> **Olnex said:**
> I dual boot WinXP and Ubuntu 7.10, at first I formatted my hard disk and allocated two drives for XP, one for system, one for applications. The remaining part of my hard disk is not partitioned, I installed XP on C: and did not format D:, then I installed Ubuntu, it recognised C: with label WinXP, then I went to XP and formated D: however, D: does not appear like C: on my Ubuntu desktop, but I can see it in "Places" -> "Computer" and I have to enter my password in order to mount it, my question is, how to make D: available like C: ?
Thanks!

open a terminal:

Applications -> Accessories -> Terminal

and post the output of this commands:

```
mount
``````
sudo fdisk -l
``````
cat /etc/fstab
```

---

### Post by konungursvia on 2008-03-13
+1 for Gparted. Love it, it works really well.

---

