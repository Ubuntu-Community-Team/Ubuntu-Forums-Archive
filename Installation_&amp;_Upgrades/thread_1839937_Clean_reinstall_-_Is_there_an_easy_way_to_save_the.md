---
title: "Clean reinstall - Is there an easy way to save the data?"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by dom1n1cus on 2011-09-06
Hello,
I came to a point where some consistent bugs are making me mad enough to take action.
Namely I'm speaking about an issue while shutting down - my laptop just doesn't feel like doing that kind of stuff. When I try the gnome button in upper right corner, no reaction comes at all. And when I do it manually via terminal with "sudo shutdown 0" it always freezes down while shutting down. I suspect preload to have someting to do with this, because it's always one of the last things that show on the text messages while shutting down.
My second big issue with my system is its inability to run Basket Notes properly. It always starts popping up error messages "Insufficient permissions in target directory".
I'd like to do a clean installation to see whether these bugs were created by my interventions or not. The thing is I don't feel like doing a clean installation if all my system settings saved in my /home on a separate partition stay. Is there a way to save the data but delete all the other things?
Thank you for any piece of advice. If you know how to solve my original problems, that would be even better. ;)

---

### Post by Beacon11 on 2011-09-06
If I were you I'd just backup everything I wanted to keep on an external drive. Do you have one?

---

### Post by haqking on 2011-09-06
> **dom1n1cus said:**
> Hello,
I came to a point where some consistent bugs are making me mad enough to take action.
Namely I'm speaking about an issue while shutting down - my laptop just doesn't feel like doing that kind of stuff. When I try the gnome button in upper right corner, no reaction comes at all. And when I do it manually via terminal with "sudo shutdown 0" it always freezes down while shutting down. I suspect preload to have someting to do with this, because it's always one of the last things that show on the text messages while shutting down.
My second big issue with my system is its inability to run Basket Notes properly. It always starts popping up error messages "Insufficient permissions in target directory".
I'd like to do a clean installation to see whether these bugs were created by my interventions or not. The thing is I don't feel like doing a clean installation if all my system settings saved in my /home on a separate partition stay. Is there a way to save the data but delete all the other things?
Thank you for any piece of advice. If you know how to solve my original problems, that would be even better. ;)


Do a custom install and mount your existing /home as /home in the new install.

Though there might be some DE conflicts.

Best to back up your data and do everything fresh.  Once you have take a clone so with any new isues you can just clone it back again  [www.clonezilla.org](www.clonezilla.org)

---

### Post by dom1n1cus on 2011-09-07
That's the point. I'd like to backup, format and reinstall, but I don't have an external drive. I don't have time nor will enough to burn everything on DVDs so I was looking for a way around. Is there no trick to do this? An extra partition maybe? Shall I really have to invest the money into an external drive I don't really need otherwise?

---

### Post by Hakunka-Matata on 2011-09-07
Yes, there is a way to save your data and do a 'clean install' on the / root partition.  You already have the requisite /home partition, which does indeed have your data on it, YES?  
Please post output from code
```
sudo sfdisk -luM
```

---

### Post by dom1n1cus on 2011-09-07
Yes I do have a separate /home partition. But I'd like to get rid of all the system settings saved in my /home partition as well.

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sda1   *     1  111111  111111  113777664   83  Linux
/dev/sda2     473105+ 476938   3834-   3924993    5  Extended
/dev/sda3     111112  473104  361993  370680832   83  Linux
/dev/sda4         0      -      0          0    0  Empty
/dev/sda5     473106  476938   3833    3924992   82  Linux swap / Solaris

---

### Post by Hakunka-Matata on 2011-09-07
> **dom1n1cus said:**
> Yes I do have a separate /home partition. But I'd like to get rid of all the system settings saved in my /home partition as well.

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sda1   *     1  111111  111111  113777664   83  Linux
/dev/sda2     473105+ 476938   3834-   3924993    5  Extended
/dev/sda3     111112  473104  361993  370680832   83  Linux
/dev/sda4         0      -      0          0    0  Empty
/dev/sda5     473106  476938   3833    3924992   82  Linux swap / Solaris

Yes, I do also.  and I also would like to remove all system settings in  the /home folder.  Time to start a thread on that, I'm sure oldfred has  explained it  in one of his threads.  oldfred also uses a third  partition I believe for settings.

---

### Post by oldfred on 2011-09-07
No, I converted /home to back inside my root since it is 1GB and 3/4s of that is .wine for Picasa.

I moved all the folders to a data partition that has no hidden folders and then link those folders back into /home so it looks like a standard install and all the default folders are still there like Downloads, Documents, Video etc. I have anther data folder 'shared' NTFS for when I used XP a lot and have the normally hidden Firefox & Thunderbird profiles in that. I move any hidden folder with much data into my data partitions.

I have many / (root) partitions with different versions of Ubuntu all linked into my same /mnt/data & /mnt/shared partitions. I did it so many times I stopped retyping and copied history into a bash file and just rerun that on a new install.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by srs5694 on 2011-09-07
> **dom1n1cus said:**
> Hello,
I came to a point where some consistent bugs are making me mad enough to take action.
Namely I'm speaking about an issue while shutting down - my laptop just doesn't feel like doing that kind of stuff. When I try the gnome button in upper right corner, no reaction comes at all. And when I do it manually via terminal with "sudo shutdown 0" it always freezes down while shutting down. I suspect preload to have someting to do with this, because it's always one of the last things that show on the text messages while shutting down.

You wouldn't happen to be using a system that boots in UEFI mode, would you? If you're not sure, you can type:

```

dmesg | grep EFI

```

If you get output that includes many lines of memory mapping and other information, you're also certainly booting in UEFI mode. If you get no output, or just one or two lines in which "EFI" appears as part of a longer word, then you're booting in BIOS mode.

I mention this because there's a [known bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/721576) that causes this symptom on some UEFI systems. If you're suffering from this bug, the "reboot=a,w" kernel option (specified in your GRUB configuration) might fix it.

> Yes I do have a separate /home partition. But I'd like to get rid of all  the system settings saved in my /home partition as well.

If you specify a different username when you do a fresh re-installation, you'll get a new home directory within the /home partition. Alternatively, prior to re-installing, you can rename your current home directory to something else (say, /home/fred to /home/derf). If you find the re-installation works, you can then move the files you want to keep over to the new location and delete the old user home directory.

---

### Post by dom1n1cus on 2011-09-08
> **srs5694 said:**
> You wouldn't happen to be using a system that boots in UEFI mode, would you?


umm ... This is the result. Would I? I can't tell as none of the possibilities you explained seem to be the case.

```
dom1no@dom1no-Satellite-L650D:~$ dmesg | grep EFI
dom1no@dom1no-Satellite-L650D:~$ 
```

Thank you for the renaming idea. It is simple and seems to be able to do the trick. And in the long run I will consider creating separate data partition. Not because I'd need to share data between different platforms but to avoid any data loss and because having separate things separately seems more logical to me.

---

### Post by srs5694 on 2011-09-08
> **dom1n1cus said:**
> umm ... This is the result. Would I? I can't tell as none of the possibilities you explained seem to be the case.```
dom1no@dom1no-Satellite-L650D:~$ dmesg | grep EFI
dom1no@dom1no-Satellite-L650D:~$ 
```

[quote=srs5694]If you get no output... then you're booting in BIOS mode.[/quote]

You got no output, so you're booting in BIOS mode.

[quote=dom1n1cus]And in the long run I will consider creating separate data partition. Not because I'd need to share data between different platforms but to avoid any data loss and because having separate things separately seems more logical to me.[/QUOTE]

IMO, there's no point to a separate /data partition. It serves exactly the same purpose as a separate /home partition, just with some wrinkles on what goes where -- and those wrinkles actually complicate life if you start dealing with multiple accounts for multiple real users (or if you want multiple separate accounts for yourself). In other words, a separate /data partition just reinvents the wheel.

---

### Post by oldfred on 2011-09-08
I know srs5694 and I disagree and that is ok. But a data partition then does not have the hidden user configuration settings that are in /home. I only copy some setting from one install to another from my /home. While you can share the /home partition it is not so easy to share all the data in one user with other users without lots of permission settings. The advantage of a separate /home is ease of upgrades as the user settings & user data are all included without backing up and reinstalling (but you still should have backups).

The /data is not an end all for everyone. If different distributions ownership & permissions can be a big issue. But some use the NTFS partition for that since it does not support any permissions or ownership. For me with many Ubuntu flavors the / data works well.

---

### Post by Camilia on 2011-09-08
> **Hakunka-Matata said:**
> Yes, there is a way to save your data and do a 'clean install' on the / root partition. 
YES? ```
sudo sfdisk -luM
```
I am in the same position. Pasted the command.
Got Warning:
The partition table looks like it was made
for C/H/S=*/6/63 (instead of 1001/1/32).
For this listing I'll assume that geometry.
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sdg1   *     0+    15-    16-     15996+   1  FAT12
		end: (c,h,s) expected (84,4,52) found (83,5,63)
/dev/sdg2         0      -      0          0    0  Empty
/dev/sdg3         0      -      0          0    0  Empty
/dev/sdg4         0      -      0          0    0  Empty

What is the next step.

---

### Post by Hakunka-Matata on 2011-09-08
> **Camilia said:**
> I am in the same position. Pasted the command.
Got Warning:
The partition table looks like it was made
for C/H/S=*/6/63 (instead of 1001/1/32).
For this listing I'll assume that geometry.
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sdg1   *     0+    15-    16-     15996+   1  FAT12
        end: (c,h,s) expected (84,4,52) found (83,5,63)
/dev/sdg2         0      -      0          0    0  Empty
/dev/sdg3         0      -      0          0    0  Empty
/dev/sdg4         0      -      0          0    0  Empty

What is the next step.
next step?, that is a really good question you know
what do your drives look like in gparted?
sudo fdisk -lu
Disk Utility, what does it show?  7 drives?

---

### Post by srs5694 on 2011-09-08
> **Camilia said:**
> I am in the same position. Pasted the command.


It's unclear precisely what you want to do, Camilia, but given the output you posted, you clearly do *not* have precisely the same issue as dom1n1cus, who began this thread. Trying to resolve two peoples' problems in one thread becomes very confusing and frustrating very quickly, so it's best to begin another thread. When you do so, please state clearly and precisely what your current situation is and what you hope to achieve.

---

### Post by Camilia on 2011-09-08
Oh, I thought we had the same problem. That is wanting to save data and do a clean reinstall.

Perhaps will better understand link you gave me. I have to eat now though.

---

