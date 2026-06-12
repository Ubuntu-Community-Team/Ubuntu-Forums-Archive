---
title: "Ubuntu 8.04 Installation help"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by tocad on 2008-07-04
First let me tell you a bit about my computer and history

**currently**:

-(/dev/sda1)Windows Vista partition(main os -label: HP  - 262.75GB)
  -(/dev/sda3) Windows partition(i think boot - label:FACTORY_IMAGE - 8.85GB

-Unallocated - 101GB

**before**:

-(/dev/sda1)Windows Vista partition(main os -label: HP  - 262.75GB)
  -(/dev/sda3) Windows partition(i think boot - label:FACTORY_IMAGE - 8.85GB

-OpenSuse 10.3 w/other partitions for it

----------------------------------

**Story**:

I put OpenSuse on it, but didn't really like it. I went on Ubuntu and erased it using the partition editor. When I tried to boot into windows it said "loading GRUB then error 22"

I rebooted into Ubuntu and began installing it(Ubuntu). I'm making partitions now, using the installation thing. I chose the resize choice and made it to previous set up (windows 262, Ubuntu 101).

**My Question**:

Would installing Ubuntu fix the error 22 booting problem?

[I]- I'm probably just over thinking things, but I thought I'd ask to be sure.
[/I]

_Question 2_:

After hitting forward it said *"...previous changes must be written... cannot be undone..."* Is this referring to the information entered before this stage, or is it referring to the partition sizes?

_Question 3_:

I resized the partitions to what they were, but it didn't show the other windows partition (/dev/sda3 - FACTORY_IMAGE). If I hit ok to the aforementioned message, would it format this partition, erasing the data on it or would it be left alone?

Thats all my questions (for now, at least :p ) your help is much appreciated.

-Meghan

---

### Post by VMC on 2008-07-04
I'm not quite sure what this means?
> I resized the partitions to what they were, but it didn't show the other windows partition

It doesn't really matter now. Let's just find out "Who's on first" :)

From a Terminal type this:

```
sudo fdisk -l
```

---

### Post by tocad on 2008-07-04
I meant when installing it, on the "prepare disk space" page I chose the guided - resize option and it only had two bars. the windows one says "Windows Vista/Longhorn (loader)" and the other says "Ubuntu 8.04" ...but I think I just answered my question lol

anyway, it says:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
240 heads, 63 sectors/track, 51681 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36445   275518472+   7  HPFS/NTFS
/dev/sda3           50454       51681     9283680    7  HPFS/NTFS


-Meghan

NOTE: Also, I haven't installed it yet because the second question.

---

### Post by tocad on 2008-07-04
I'm kinda confused now, I took another look while I was about to go ahead with the partitioning and on with the installation, but I noticed it's only the size of the windows main partition which is 262GB... here's a screen cap

[http://s238.photobucket.com/albums/ff60/tocassi/other/?action=view&current=Screenshot.png](http://s238.photobucket.com/albums/ff60/tocassi/other/?action=view&current=Screenshot.png)

Do I have to do in manually than, since I don't want to mess with the windows partition(shared computer :mad: )

---

### Post by tocad on 2008-07-04
> **tocad said:**
> I'm kinda confused now, I took another look while I was about to go ahead with the partitioning and on with the installation, but I noticed it's only the size of the windows main partition which is 262GB... here's a screen cap

[http://s238.photobucket.com/albums/ff60/tocassi/other/?action=view&current=Screenshot.png](http://s238.photobucket.com/albums/ff60/tocassi/other/?action=view&current=Screenshot.png)

Do I have to do in manually than, since I don't want to mess with the windows partition(shared computer :mad: )

I'm now doing it manually because that's how I did it before and it seemed to work out... so pretty much this whole thread is kinda useless other than it proving being lazy doesn't pay off.

---

### Post by tocad on 2008-07-04
Sorry for all the questions, I'm doing like 30 things at the moment while trying to install this and don't think fast enough.

Anyway, hopefully the last question I'll have.

 I was wondering where to mount the swap partition.



Thanks,
-Meghan

EDIT: I think i fixed the problem

---

### Post by pavel989 on 2008-07-04
doesnt really matter, but its typically like u have a seperate partition for ur linux, and inside that partition, u have the linux part and swap part

[IMG]http://i28.tinypic.com/mt1e2g.png[/IMG]

---

