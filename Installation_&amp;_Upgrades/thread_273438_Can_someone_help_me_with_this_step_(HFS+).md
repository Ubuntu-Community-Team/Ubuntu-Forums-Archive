---
title: "Can someone help me with this step (HFS+)"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by mztriz on 2006-10-08
I'm running off of the ubuntu live cd (but ubuntu is the only OS on this computer)

[http://www.teachucomputers.blogspot.com/](http://www.teachucomputers.blogspot.com/)

```
3. Partition your Harddrive, This is the most time consuming part, resize your current partition by using a tool like partition magic (I know in ubuntu you have Gparted, and in Knoppix you have QTparted), take off six gigabytes of it, because the image requires six gigabytes, if you take off more you will just be wasting harddrive space. [B]Create a new HFS+ partition that is 6 GB using a tool like Partition magic, QTparted, Gparted, etc. or in the disk prompt do this (copied from andrewescobar's the simple installation)
[/B] 
``` How do I do this?

Also here is a SS of my gparted:
[http://img216.imageshack.us/img216/8801/screenshotnm3.png](http://img216.imageshack.us/img216/8801/screenshotnm3.png)


And after much searching I found this: [http://forum.insanelymac.com/index.php?showtopic=512#3](http://forum.insanelymac.com/index.php?showtopic=512#3)
```
First we boot LIVE CD linux, doenst matter really what flavor i used gentoo, but get into prompt and:


sudo cfdisk /dev/hda


then hit new partition and create it, then goto the new partition with the cfdisk program and hit type, change the type of the partition to AF. its not on the list but if you just type "AF" it will make the partition AF, then write the partition table. reboot the computer, open up applications>utilitys>disk utility and format the hard newly created partition. ill do some pictures and what not later and make the tutorial better, but for now, you guys can comment and dick around.

REMEMBER: DONT MESS WITH YOUR FIRST 6gig DRIVE. thats where your OS is installed. so dont accidently format that.
``` Should I try that?

Thanks, 
Ava.

---

