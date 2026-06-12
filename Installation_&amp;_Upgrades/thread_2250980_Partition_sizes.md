---
title: "Partition sizes"
date: 2014-11-01
forum: Installation &amp; Upgrades
---

### Post by jonnyrobbie on 2014-11-01
I've tried to do some research, but after reading countless threads, I'm still confused, because most of them suggest simple swap and / (and optionally /home). I'm switching from windows, so my mindset might be a little bit biased.

I have a 500GB drive and I want to partition it. On windows, I have three partitions: 40GB for os, 110GB for software and games and the rest (cca 315GB) for music, photos, downloads and other misc.

All the Ubuntu (Linux) partitioning guides suggested to make 20GB for /, but it seems awfully small from my perspective. What if I want to install a lot of applications either natively (or those that make sense through wine). What if I want to virtualize windows for some other essential stuff? What about Steam games? My software partition right now is somewhere around 90GB (not counting the windows itself). Where do all those files go?

And what about the size of /home? I don't want to put all my music, photos or downloads there, because I want all users have access to it. What size should /home be? Where should I put my media?

---

### Post by Bucky Ball on 2014-11-01
Please go to Disk Management, take a screenshot of the drive you're intending to install Ubuntu to, and post it back here.

Just a tip about /home. I hope you follow me. As far as your existing music, vids, etc. folders; create / at 30Gb (you can expand it later) and don't create a /home partition. That way, Ubuntu will, by default, create a /home directory inside /. In that you will have the directories /Video, /Music, /Documents, etc. Delete them and create symlinks to your existing folders. It works like this:

```
ln -s 'location to link to' 'name of symlink'
```

In other words the command would be:

```
ln -s /path/to/your/folder /name/of/symlink
```

For instance:

```
ln -s /data/MyExistingVideos /home/yourusername/Videos
```

That will create the directory 'Videos' in your /home directory. ;)

You are right to research this. It pays to make a solid partitioning plan BEFORE commencing the install as you're going to have to live with it.

And essentially, yes, all you need is / and a /swap to get things up and running. The sizes are really dependent on your needs and uses. I rarely use a / anything larger than 15Gb, but I run a minimal install with xfce4 desktop and have nothing but the OS on the partition. The install I'm running on now takes up just over 7Gb. All my personal stuff is on a 200Gb data partition. 

I generally advise a pen and paper and beverage of choice when planning partitioning.

PS: You can stick your virtual machine where you want. You can stick your virtual machine directory on another drive if you like.

---

### Post by jonnyrobbie on 2014-11-01
I've attached the screenshot. The UI is not in English, but I hope the stuff you need is there The drive is the first one, the one containing C:, D: and E:.

I'm aware of symlinks. I knew I wouldn't be able to go without them.

I thought having / and /home on different partitions might be better in case of reinstalling, upgrade and/or restoring.

Wouldn't it be better to have more than 20GB on / when I may need games and other applications, windows virtualization or wine installs there?

---

### Post by Bucky Ball on 2014-11-01
> **jonnyrobbie said:**
> I thought having / and /home on different partitions might be better in case of reinstalling, upgrade and/or restoring.


No issue with doing it that way. If you go the other way, as long as you have your personal settings backed up, you'd only need to recreate the symlinks and put back the settings on a reinstall. Either or, personal preference. 

> **jonnyrobbie said:**
> Wouldn't it be better to have more than 20GB on / when I may need games and other applications, windows virtualization or wine installs there?

And make / 50Gb then. As I said, you can install your virtual machines elsewhere, and you'd want to. Another partition, another drive.

Also as mentioned, essentially you need / and /swap (which should be 2Gb incidentally, the same size as your installed RAM or bigger if you are intending to hibernate with a heap of programs open). The rest is very much up to you, which is why it takes some planning to get what you want. Get a piece of paper and scribble a mud map of the way the disk is partitioned and what's where now. Then figure how you're going fit Ubuntu (you are going to need some unallocated space, obviously) and how you want it to interact with the existing partitions/data.

You decided you want /, /home and /swap. There's a start. But remember, the /home will be EXT filesystem, and that is not useable by Win. BUT, NTFS IS useable by Ubuntu. /home contains your system settings, BUT also /Videos, /Music, etc. You've already said you don't want to move them, and why would you? Windows won't be able to access them in /home. ;)

That's where the symlinks might come in. You don't really need a big /home from where I'm sitting. What are you going to do with it? Could you expand an existing data partition instead of having a /home and just symlink to that? Your call. Thinking cap on.

---

### Post by oldfred on 2014-11-01
I stopped using XP, but did keep my shared NTFS for a while until I could totally reconfigure with new system.

But I keep /home inside my / (root) and it is about 2GB. My total / partition is 11GB including the 2GB. Most of the 2GB is Picasa in .wine as that is a bit more difficult to move to a data partition. All my data was in the NTFS partition and then in a Linux formatted data partition as I weaned my way off XP. But I do not install games. Games can be in other partitions also.

I do use the symlinks to my Music, Documents, Videos etc folders in my data partitions. I usually do not totally restore /home when doing a new install, but scripted some of the major changes, and prefer to manually change the rest. I only have backup of /home to restore in case system totally crashes & I do a new re-install of the same version. I keep my working install as the newest LTS, but like to install in another 20 or 25GB partition each version as it comes out to know what changes are on the way. Then the 2 year leap to next LTS is not so large.

---

### Post by Bucky Ball on 2014-11-01
> **oldfred said:**
> I do use the symlinks to my Music, Documents, Videos etc folders in my data partitions ... I only have backup of /home to restore in case system totally crashes & I do a new re-install of the same version. I keep my working install as the newest LTS, but like to install in another 20 or 25GB partition each version as it comes out to know what changes are on the way. Then the 2 year leap to next LTS is not so large.

This is pretty much identical to my modus operandi. As I say, it is really about what suits you. You'll be working with it.

---

### Post by jonnyrobbie on 2014-11-01
> **Bucky Ball said:**
> But remember, the /home will be EXT filesystem, and that is not useable by Win. BUT, NTFS IS useable by Ubuntu.

I don't really plan on dual-booting. So unless I would decide to switch back to Win for some reason, I don't need ntfs anymore. I wouldn't need the virtualized one to have access there.

> **Bucky Ball said:**
> You decided you want /, /home and /swap. There's a start.

That's what I knew from beginning. What I didn't know and what I came here to ask is the rest. I kinda had the idea that I'd want to put my music etc. to a separate partition I'd mount to /data and then symlink it from /home like you suggested. But that still leaves the question how much space I need for applications and games. And that goes back to my initial concern that those 20GB most guides recommend feels really small. And if I'm able to create a separate partition for them (like my current 110GB D:) and symlink to it. That's where I run into another problem that Linux doesn't seem to keep application on one folder. I'd want to symlink all my apps andd games to a separate partitions, but linux has all it's components throughout all the filesystem.

In other words, I can have my windows partition 40GB, because I can install all my software to another 110GB partition. On linux, this is slightly harder and I ask how do deal with this.

---

### Post by Impavidus on 2014-11-01
Good advice above, but some points haven't been answered.

> **jonnyrobbie said:**
> 
I have a 500GB drive and I want to partition it. On windows, I have three partitions: 40GB for os, 110GB for software and games and the rest (cca 315GB) for music, photos, downloads and other misc.Count on 5GB for the operating system including some more or less vital applications (like the desktop) and about 8GB for your other software, excluding the big data directories coming with some applications (games, mostly). Add some reserve and you get to 20GB. The big data directories can often be moved to a different partition. Linux handles disk space efficiently, thanks to its wide usage of shared libraries and the like. Difficult to say how much space you need for your games. Some come with several GB of data, most are smaller. But I'm not a very active gamer. Have you kept in mind that many of your games may not have a Linux version and may not run in wine? I think wine installs your Win applications in your home directory.> And what about the size of /home? I don't want to put all my music, photos or downloads there, because I want all users have access to it. What size should /home be? Where should I put my media?It is not so that the home directory means inaccessible to other users and a separate partition is the only solution. But a separate partition can be good as you can safely wipe your system, reinstall and keep your data. You have to set up permissions so that it is readable (and possibly writable) by all. Better to avoid NTFS partition when you have no Windows installed, as NTFS sometimes needs a check from Windows.

---

### Post by jonnyrobbie on 2014-11-01
> **Impavidus said:**
> Have you kept in mind that many of your games may not have a Linux version and may not run in wine?

I have. CSGO got its linux client (one of the reasons I'm pushing to linux right now) and the rest of the games I play should run reasonably well on wine (according to the wine database).

Does this partitioning sound reasonable?

swap 5GB (I have 4gb ram + I want to hibernate)
/ 20GB
/home 10GB
/apps 100GB - to be symlinked from big software/games directories
/data 329GB - media to by symlinked from /home

all ext4 except swap

That is the point. I'm still not sure what's better. Having it like I described above, or just merge /home and /data into a big 340GB /home partition and / and /apps into a big 110GB root partition.

---

### Post by Bucky Ball on 2014-11-01
Sounds great, but I'd put /swap at the end. Just convention. In the 'old' days that would mean it was on the slowest part of the drive and the OS was on the fastest. Still does, unless you're using an SSD, but with a 7200rpm hard drive you'd not notice much diff.)

If you like, I like. In other words, if it's going to suit your purpose, great, and it is sound.

---

