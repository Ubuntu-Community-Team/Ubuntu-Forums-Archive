---
title: "How to do a fresh install without loosing data"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by tag on 2005-10-18
I want to reinstall hoary, but i'd hate to loose my home directory. What do I have to do to accomplish that. Since i have no sencond disk on which I could backup my 120 Gbyte of data in my home dir I am terrified of the danger that hoary might just overwrite it.

---

### Post by Vinze on 2005-10-18
I got my home directory on a separate partition, but I can't imagine you accomplish this without having done that... Sorry.

---

### Post by Biased turkey on 2005-10-18
As Vinze said, if your /home directory is not on a separate partition I don't see how you could reinstall without loosing your /home dir

---

### Post by SickTwist on 2005-10-18
[QUOTE=tag]I want to reinstall hoary, but i'd hate to loose my home directory. What do I have to do to accomplish that. Since i have no sencond disk on which I could backup my 120 Gbyte of data in my home dir I am terrified of the danger that hoary might just overwrite it.[/QUOTE]

Unless you have your /home directory on a separate partition, this will not be possible without storing your data somewhere else temporarily. If you're not sure how your HDD is set up, run this command from a terminal and post the results:

**cat /etc/fstab**

By the way, why do you want to reinstall Hoary? Is there something wrong that perhaps we could help you to correct to avoid doing a complete reinstallation?

---

### Post by Vinze on 2005-10-18
[QUOTE=SickTwist]
By the way, why do you want to reinstall Hoary? Is there something wrong that perhaps we could help you to correct to avoid doing a complete reinstallation?[/QUOTE]

I guess he wants to upgrade to Breezy?

---

### Post by tag on 2005-10-18
No, i really want my hoary back. It was just working fine until i upgraded to breezy ( see details on why i want to do that on bottom of this post: [http://ubuntuforums.org/showthread.php?p=417934#post417934](http://ubuntuforums.org/showthread.php?p=417934#post417934) ). Well i guess i'll have to borrow a second harddisk then. Boy - that will teach me to never upgrade early!!!

---

### Post by Vinze on 2005-10-18
[QUOTE=tag]No, i really want my hoary back. It was just working fine until i upgraded to breezy ( see details on why i want to do that on bottom of this post: [http://ubuntuforums.org/showthread.php?p=417934#post417934](http://ubuntuforums.org/showthread.php?p=417934#post417934) ). Well i guess i'll have to borrow a second harddisk then. Boy - that will teach me to never upgrade early!!![/QUOTE]

You can also upload your stuff to a file hoster...

Anyway, when doing your fresh install, remember to put your /home on a seperate partition.

---

### Post by SickTwist on 2005-10-18
[QUOTE=tag]No, i really want my hoary back. It was just working fine until i upgraded to breezy ( see details on why i want to do that on bottom of this post: [http://ubuntuforums.org/showthread.php?p=417934#post417934](http://ubuntuforums.org/showthread.php?p=417934#post417934) ). Well i guess i'll have to borrow a second harddisk then. Boy - that will teach me to never upgrade early!!![/QUOTE]

The main lesson here should be to use separate paritions for / and /home--not to worry about trying new distros. That way you can wipe out the / partition as many times as you want without having to alter the data stored in /home. This has the added benefit of saving all of your desktop preferences as well since they are stored in hidden files in your home directory. If you decide to re-install keep this in mind when you use the partitioning utility during the Ubuntu installation.

---

