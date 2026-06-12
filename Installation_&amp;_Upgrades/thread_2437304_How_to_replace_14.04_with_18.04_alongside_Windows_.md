---
title: "How to replace 14.04 with 18.04 alongside Windows with 'Something Else'"
date: 2020-02-21
forum: Installation &amp; Upgrades
---

### Post by davy jones on 2020-02-21
I had a dual boot system with Ubuntu 14.04 and Windows 8. I wanted to replace 14.04 with 18.04 without disturbing Windows. I've always used the 'Something Else' option while installing, but it was very confusing this time. I didn't know which partition to select for boot installation (I have a UEFI boot system and the Windows Boot Manager is in /dev/sda1). On top of that, I didn't know how exactly to direct the installer to select my current / partition for installing 18.04. So I decided to just select the option which erases 14.04 and installs 18.04. The problem now is that my previous / partition has been overwritten to contain the entire 18.04 installation **including the home folder**. My previous home folder is still there as an external partition. 

This is not what I want at all. **I want there to be a /home partition and a / partition in the new installation as well.**

If there's a way to integrate my previous /home partition with this without reinstalling, that would be great. If not, I want to know how exactly to reinstall 18.04 in a way that I get what I want. Even if this means formatting the current /home partition, I'm okay with it. Please help.

---

### Post by CelticWarrior on 2020-02-21
The correct way, with "something else" would have been to select each of the required partitions with the same type as before:

ESP (EFI Partition) as EFI partition;
/ as / (root) (and, of course, tick "format");
/home as /home (and, of course, DO NOT tick "format").

Now, what you can do is edit the fstab to point to the old /home. There are several guide in the internet for this:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[https://www.maketecheasier.com/move-home-folder-ubuntu/](https://www.maketecheasier.com/move-home-folder-ubuntu/)

You will notice that the guides are geared towards users that don't have a separated /home and want one. That means that those users will need to follow the guides from the beginning to the end but in your case a) you don't have files to copy to the /home partition and b) you already have and it shouldn't be touched... So, you should follow the guides from the point where they mention editing the fstab.

---

