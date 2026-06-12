---
title: "New (big!) Harddisk, how to partition."
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by juamez. on 2007-11-06
Ok, so I'm on a laptop which only supports one internal harddisk. I currently have a 80GB disk installed. This one was - read: before I installed ubuntu - partitioned into 3 partitions, 20GiB for windows, 20GiB for games and rest which is about 55GiB for data. OS and games in front of the HDD due to performance reasons, obviously. All of them were primary partitions.

Now I had to install linux for my studies and I went into the disk manager of windows to fiddle a slight bit with the non-OS partitions. Finally I came up with this which I now still use, although with urgent need of more space:
[LIST]
[*]20GiB for windows - still **primary**.
[*]13GiB for games - I shrank it because I was having some headroom that could be used for linux. Also still **primary**.
[*]12GiB for linux' and shared partitions - **extended**, splitted into 4GiB for linux itself except for /var, 1GiB for swap and 1GiB for /var, with also 6GiB for a FAT32 partition which is obsolete since I discovered ntfs3g to be pretty reliable.
[*]rest which is about 29GiB for data - also still **primary**
[/LIST]

NOW, I have a whopping Western Digital 250GB harddisk which has to replace my old but veteran 80 Hitachi.
I was thinking of these points to take into account:
* I will be installing feisty again, since I have the most knowledge of that version atm. I have a Dell laptop. Are there any reasons I should consider installing Gutsy instead?
* I want /home to be on a seperate partition
* /var also on a seperate partition (or isn't this really necessary?)
* my /home has to be large enough to be able to hold many installed games I would like to play through wine, like steam, Diablo 2, etc
* windows should still be on there, since I still need that for my studies
* I'm thinking of not making any partition larger than 120GB since ntfs3g can have problems with that size of partition

So here is my deal:
[LIST]
[*]20GiB for windows (no questions asked)
[*]20GiB for linux incl swap (should be enough with /home and maybe /var on another partition, no?)
[*]40GiB for windows games (yes I still like games, so what? although 40GiB might be a little much, since I won't be installing those lastgen games like supreme commander and the likes since I wouldn't even think of trying those on my laptop with that crappy onboard intel GMA 900. Half-Life 2 and the lot is the farthest I'd go)
[*]50GiB for linux /home which has to store my games and maybe some other things, because documents will be stored on the last "data" partition.
[*]~110GiB for data (NTFS) which will be used to store files which aren't needed by applications.
[/LIST]

I know that I'm going to make the first partition primary, because of earlier (bad) experiences with windows installed in an extended partition and GRUB not willing to load that installation.
But what with the other partitions? I have linux now installed on an extended partition, and I'm not experiencing any problem whatsoever, so I guess it's safe to put linux again on an extended partition, right?
Also what should I do with the /var and the /swap? Should I use the 20GiB for those aswell as root? Since I manage to have linux WITH /home but without /swap and /var cramped onto a 4GiB partition with no problem, really.
Should /swap be the amount of RAM I have installed in my laptop because of hibernation possibilities, or isn't that related in the way I think it is? I have 1GB RAM atm, but when I'm going to install this harddisk, I will be having 2GB. Now I have 1GiB for /swap, should that be adequate still for use in a 2GB RAM system?

---

### Post by kshane on 2007-11-06
> **juamez. said:**
> Ok, so I'm on a laptop which only supports one internal harddisk. I currently have a 80GB disk installed. This one was - read: before I installed ubuntu - partitioned into 3 partitions, 20GiB for windows, 20GiB for games and rest which is about 55GiB for data. OS and games in front of the HDD due to performance reasons, obviously. All of them were primary partitions.

Now I had to install linux for my studies and I went into the disk manager of windows to fiddle a slight bit with the non-OS partitions. Finally I came up with this which I now still use, although with urgent need of more space:
[LIST]
[*]20GiB for windows - still **primary**.
[*]13GiB for games - I shrank it because I was having some headroom that could be used for linux. Also still **primary**.
[*]12GiB for linux' and shared partitions - **extended**, splitted into 4GiB for linux itself except for /var, 1GiB for swap and 1GiB for /var, with also 6GiB for a FAT32 partition which is obsolete since I discovered ntfs3g to be pretty reliable.
[*]rest which is about 29GiB for data - also still **primary**
[/LIST]

NOW, I have a whopping Western Digital 250GB harddisk which has to replace my old but veteran 80 Hitachi.
I was thinking of these points to take into account:
* I will be installing feisty again, since I have the most knowledge of that version atm. I have a Dell laptop. Are there any reasons I should consider installing Gutsy instead?
* I want /home to be on a seperate partition
* /var also on a seperate partition (or isn't this really necessary?)
* my /home has to be large enough to be able to hold many installed games I would like to play through wine, like steam, Diablo 2, etc
* windows should still be on there, since I still need that for my studies
* I'm thinking of not making any partition larger than 120GB since ntfs3g can have problems with that size of partition

So here is my deal:
[LIST]
[*]20GiB for windows (no questions asked)
[*]20GiB for linux incl swap (should be enough with /home and maybe /var on another partition, no?)
[*]40GiB for windows games (yes I still like games, so what? although 50GiB might be a little much, since I won't be installing those lastgen games like supreme commander and the likes since I wouldn't even think of trying those on my laptop with that crappy onboard intel GMA 900. Half-Life 2 and the lot is the farthest I'd go)
[*]50GiB for linux /home which has to store my games and maybe some other things, because documents will be stored on the last "data" partition.
[*]~110GiB for data (NTFS) which will be used to store files which aren't needed by applications.
[/LIST]

I know that I'm going to make the first partition primary, because of earlier (bad) experiences with windows installed in an extended partition and GRUB not willing to load that installation.
But what with the other partitions? I have linux now installed on an extended partition, and I'm not experiencing any problem whatsoever, so I guess it's safe to put linux again on an extended partition, right?
Also what should I do with the /var and the /swap? Should I use the 20GiB for those aswell as root? Since I manage to have linux WITH /home but without /swap and /var cramped onto a 4GiB partition with no problem, really.
Should /swap be the amount of RAM I have installed in my laptop because of hibernation possibilities, or isn't that related in the way I think it is? I have 1GB RAM atm, but when I'm going to install this harddisk, I will be having 2GB. Now I have 1GiB for /swap, should that be adequate still for use in a 2GB RAM system?

Your plan sounds good to me.  With 2gb RAM, I'd use a 4 gb swap...

Kevin

---

### Post by juamez. on 2007-11-06
> **kshane said:**
> Your plan sounds good to me.  With 2gb RAM, I'd use a 4 gb swap...

Kevin
Thank you!

But just for the sake of knowing it: why would you recommend such amount of /swap? How can you explain the /swap partition in windows-talk? Is /swap = pagefile + hibernatefile?

---

### Post by kshane on 2007-11-06
> **juamez. said:**
> Thank you!

But just for the sake of knowing it: why would you recommend such amount of /swap? How can you explain the /swap partition in windows-talk? Is /swap = pagefile + hibernatefile?

I use the "Rule of Thumb":  1 to 2 times RAM for swap.  Works well for me...  The Ubuntu Docs recommend (I think) 1 to 1.5 times RAM...

Kevin

---

### Post by juamez. on 2007-11-06
> **How much swap do I need?**

If you have n Mb of ram, you need between n and 2*n Mb of swap. 
If you have a disk big enough, just put 2*n Mb swap.
source: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

You, sir, were correct. To think of it: I should have looked for this in the first place. :x

Anyhow, this thread was actually not to ask basic questions but to gain enough "go"-signals to begin installation on the new disk.

Also: what should be the best way to divide up the disk having the choice between primary and extended partitions? If I use all primary partitions for the NTFS partitions and one extended partition with all the linux partitions on it, I would have to delete the entire extended partition to enlarge it with space gained from a primary partition if I would ever want to clip off some space from an ntfs partition and add it to a linux partition. So, what to do in that case?

Maybe I'd just make only one primary partition for windows (due to GRUB complications) and put all the rest in one big extended partition. No? That is IF I don't have to resize my windows partition, which would not be the case though as I have almost 10GB still unused on the current 20GB partition.

---

