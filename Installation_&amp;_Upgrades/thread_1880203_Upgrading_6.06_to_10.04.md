---
title: "Upgrading 6.06 to 10.04"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by the_new_z on 2011-11-13
I am running an Ubuntu 6.06 LTS home server, which I haven't upgraded through time. Now, since 6.06 has run its course, I have to upgrade.  From what I gather, I can go from LTS to LTS, meaning that I can do 6.06 > 8.04 > 10.04 (and maybe 12.04 next year).

Should I expect any problems doing this?  Anything important before I start (I have backups)?

I am using this machine mostly as a file server on the local network, as a torrent client (with torrentflux), and as a webserver.

---

### Post by lechien73 on 2011-11-13
The issues likely depend on your hardware configuration and software you have installed on the server. Maybe do a clonezilla backup of the partition first.

Is your data stored on a separate partition/drive to the operating system itself? If so, maybe a fresh install might be better.

As regards upgrading the operating system, you're correct that you can go LTS -> LTS. The server version of Hardy is still supported, so 8.04 -> 10.04 is regarded as a regular upgrade.

This page: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) gives details on how to upgrade Dapper to Hardy.

---

### Post by coffeecat on 2011-11-13
You will not be able to upgrade 6.06 to 8.04 without a workaround. Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1822086](http://ubuntuforums.org/showthread.php?t=1822086)

The first post has all you need for a server install. You should then be able to 8.04 -> 10.04.

---

### Post by the_new_z on 2011-11-13
Thank you for the quick replies, guys.

I read the workaround thread and it seems to me that the upgrade won't be smooth because of the repository mess. So, I'd probably go with a fresh install.  

Good: The OS is on a separate drive.
Bad: There's stuff from back in 2006 in there. I am sure to miss something out in a fresh install and then waste a lot of time rebuilding :o/

As I see it, I'll (hopefully) gradually work my way to a fresh 12.04 install.

---

### Post by coffeecat on 2011-11-13
> **the_new_z said:**
> 
I read the workaround thread and it seems to me that the upgrade won't be smooth because of the repository mess.

I have no idea what you mean by that. The repositories are not in a mess. The workaround in the OP of the posted link is simply needed because you are trying to upgrade from one obsolete version of Ubuntu to another obsolete version of Ubuntu. At least three people in that thread were able to upgrade their servers with the workaround and I was able to upgrade a desktop system with a slight modification for desktops, which I posted.

---

### Post by jerrrys on 2011-11-13
edBad: There's stuff from back in 2006 in there. I am sure to miss  something out in a fresh install and then waste a lot of time rebuilding

and theres a lot of changes too, i say avoid conflicts and do a fresh install

edit: theres 35000 packages in synaptics these days, how many you got?

---

### Post by the_new_z on 2011-11-13
@coffeecat: I was referring to the last [comment]("http://ubuntuforums.org/showpost.php?p=11360580&postcount=10") in the thread
> The problem is (1) that the /etc/apt/sources.list must be changed from us.archive.ubuntu.com to old-releases.ubuntu.com and (2) that the upgrade process rewrites the apt/sources.list file, removing the "old-releases" changes that you made
I don't know if this guy knows what he is talking about, but if chances are that I will mess it up, I'd better not do it now, because the computer is at the neighbor's and I'll be working remotely.

@jerrys: How many packages I have installed? 486.

---

### Post by the_new_z on 2011-11-13
Well, I did the upgrade to 8.04 LTS and it went mostly fine. Only the switch to UUID didn't go too well and it failed to boot. So I had to manually update GRUB's menu.lst with the UUID where the old notation used to stand. Then it was fine.

Also, for an unknown reason, at the first successful boot I got a warning (Unable to resolve UUID=xxx). But everything seemed to be working fine - all drives and partitions were mounted.

Thanks for the encouragement, coffeecat.

---

### Post by the_new_z on 2011-11-14
The upgrade from 8.04 to 10.04 also had a problem booting. This time GRUB was missing the new kernel. I fixed it manually and then upgraded to GRUB2. Maybe the next upgrade will go without a hitch.

Anyway, thank you guys for the help. Everything seems to be working fine after the upgrades. If I don't get any angry calls by the end of the month, I'll consider it a success :P

EDIT: Is it true that the [server kernel was renamed generic-pae]("http://ubuntuforums.org/showpost.php?p=10237662&postcount=3")? I mean, I see that after the 8.04 to 10.04 upgrade I am running a generic-pae kernel but is there any difference with the server version?

---

