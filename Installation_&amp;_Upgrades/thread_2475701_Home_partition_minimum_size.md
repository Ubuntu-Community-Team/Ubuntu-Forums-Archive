---
title: "Home partition minimum size"
date: 2022-06-05
forum: Installation &amp; Upgrades
---

### Post by habana on 2022-06-05
I am about to install 22.04 as a dual boot system on a single user Win 11 Acer Swift 3 (i5, 8GB, 500GB). I intend to use shared data in an NTFS data partition which will be most of the drive. I like to use a separate /home partition on my machines and in this case it will have a symlink pointing to the shared partition.

My question is: What size should I allow for the /home partition which will only contain config files etc? I would imagine that 1GB would be more than enough but I could be wrong. There are a couple of posts on this topic but they are quite old.

Any advice appreciated.

---

### Post by oldfred on 2022-06-05
I am using Kubuntu and have moved all data to a /mnt/data partition that is ext4. Years ago when using XP I had both NTFS & Linux formatted data partitions. I kept Firefox & Thunderbird in NTFS so I could use in both XP & Ubuntu. But lately Firefox has regularly complained about versions when trying to link into my test installs. Linking may not work with Windows now for Firefox?

My /home is inside / and I suggest you do that since it will be small. That way you share the unused space between / & /home.
My /home is currently 584M per du.
But I also move some hidden folders in /home like Thunderbird & Firefox into my data partition. Those folders are 3.2GB so if in /home and vary a lot in size.

[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

Even / now needs to be larger as snaps take a lot of space. But I do not install snaps and use Kubuntu which currently is about 11GB used in 30GB partition.  Test installs with little update are between 6 & 10GB.

---

### Post by habana on 2022-06-05
Thanks Oldfred. I like to have a separate /home as it makes upgrades from iso so much easier. I don't need to link Firefox as I will hardly use the Windows o/s at all. I only need it for itunes and to manage my GPS and universal TV remote. I don't use snaps either.

My main PC (ubuntu only) currently has about 500MB in .mozilla and a whopping 5.9GB in .thunderbird but I won't be using the latter on the new laptop which is really for travelling and other mobile activities. Webmail will be sufficient. However, I have now noticed that .config on this PC is 170MB so my 1GB proposal is probably a bit light.

---

### Post by TheFu on 2022-06-06
Most of my systems have tiny /home partitions, but they don't have **any** data local to them.  I keep data on network storage using NFS.
Here's a desktop that I don't really try very hard to keep clean - /
```
$ du -shc ~/
5.5G    /home/tf/

```

3G of that is in the ~/Downloads/ directory.  Another 1G is used by stuff you wouldn't likely have - Android stuff and a number of perl virtual environments.  
Snap packages, if you use those, will eat up some storage in your HOME.  500M is used by ~/.cache/   So, I'd start with 2G but I'd use LVM-LVs so that expanding /home wouldn't be hard. If you don't use LVM, it might be a huge hassle to expand if you don't leave some empty room after the partition just for future expansion.

I don't run Thunderbird on that system. I run it over a remote X11 tunnel on a different system. Same for Firefox and Chromium.

It is very difficult to plan storage, which is why LVM was invented.  Start by allocating a minimal amount for the next few months, then use lvextend to add a little when and where you need it.  We can think of LVs as partitions, but they are flexible partitions that can be extended while being used. Just make the VG the total size you'll ever allow Linux to use, then you can parse out LVs and LV-extends where needed, as needed.

---

### Post by habana on 2022-06-06
Thanks TheFu. I'll have to read up on LVM!

---

### Post by habana on 2022-06-07
I will mark this as solved as I have a more serious problem - there is no option in BIOS to change the boot sequence. I'll start a new thread for this.

---

