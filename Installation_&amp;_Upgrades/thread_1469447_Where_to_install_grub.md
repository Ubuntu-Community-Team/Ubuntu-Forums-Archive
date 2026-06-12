---
title: "Where to install grub"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Silvertones on 2010-05-02
I read many mentions that the upgrade askes were to install grub. Everyone says a noob wouldn't know what to do but never say were. So were do you install grub? I haven't a clue. I have Ubuntu 9.1 at this point along side windows XP.

---

### Post by frantid on 2010-05-02
Here's an illustrated guide:

[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by Silvertones on 2010-05-10
I'm still waiting for the CD. Since I first posted I have moved my /home folder to a separate partition as has been mentioned before. I'm going to try an upgrade first. If that fails I'll do a fresh install but I have two questions:
1. I still am not sure were the best place to install GRUB is
2. How do I handle having the separate /home partition
Thanks

---

### Post by darkod on 2010-05-10
> **Silvertones said:**
> I'm still waiting for the CD. Since I first posted I have moved my /home folder to a separate partition as has been mentioned before. I'm going to try an upgrade first. If that fails I'll do a fresh install but I have two questions:
1. I still am not sure were the best place to install GRUB is
2. How do I handle having the separate /home partition
Thanks

Opinions will differ. Mine is: Grub should always be on the MBR of the hdd. In linux terms, on /dev/sda, /dev/sdb, etc. If it has a number like /dev/sda1, /dev/sdb5, that means partition on the specific disk.

With separate /home partition it's much better to do a clean install of 10.04. You avoid upgrade hiccups. All files and settings in /home are safe. All packages/software will need to be installed again, but there are simple ways for that (like here just one example: [http://ubuntuforums.org/showthread.php?t=1479250](http://ubuntuforums.org/showthread.php?t=1479250)).

Don't be afraid to explore and use manual partitioning for example. It's nothing complicated and gives you total control of your computer.

You currently have:
9.10 / partition
swap partition
/home partition

Start the 10.04 installer and select Manual Partitioning (I think it was step 4). It will show you the list of partitions on your disk.

IMPORTANT: Your linux partition will all be marked as Not Used. I think this is what confuses people first time they see it. Linux has a nice feature not to assume where you want to install your OS. It waits for you to say. I guess as protection from unwanted loss of data.

So it knows your 9.10 / partition is there but it will never install 10.04 over it automatically assuming that's what you want. :)

What you will need to do in manual partitioning:
Select the / partition, click on Change button at bottom. Change:
- Do Not Use into ext4 or ext3 if that's your current filesystem
- tick the format box to format it, deleting the previous 9.10
- select mount point as /

Select the swap partition, click on Change:
- check that Swap Area is selected, it should be by default anyway

Select the /home partition, click Change:
- Do Not Use into ext4 or ext3, as above
- [COLOR=Red]DO NOT TICK THE FORMAT BOX!!!![/COLOR] This is what allows you to keep your data in /home untouched. Likewise, format it if you need to do that.
- select mount point /home

It looks like a lot of text but in fact it means: you tell 10.04 what to use for / and what for /home. You format / to get rid of 9.10 and [COLOR=Red]DON'T FORMAT[/COLOR] /home to keep your data. All done!!! :)

Enjoy your 10.04. :)

---

### Post by ronparent on 2010-05-10
1 Grub normally default installs to the /boot/grub location in the file system. For special circumstances some individual might want to install elsewhere.

2 When you do a clean install, at the partitioning step you would select the 3rd option where you get to pick your own location to install. Pick or create the partition where you want the '/' mount point (the location where you install). Also pick your current home partition as the /home mount point. Make sure you **_don't_** fill the check box to format so that your /home files are preserved. When the install is completed you will have the file system for your new install and /home still in it's own separate partition.

---

### Post by Silvertones on 2010-05-10
Okay I'll keep this info bookmarked and wait for the CD.
I'm going to have to redue my dial up connection, network, Samba etc aren't I?

---

### Post by markthecarp on 2010-05-10
I usually dist-upgrade for 18 months then do a fresh install. My Lucid upgrade went well except for this one point. I chose /dev/sda1 when I should have chosen /dev/sda. The latter installs grub to the MBR. Your drives may have other addresses. 

A fresh install will wipe system wide settings.

-mark

---

### Post by darkod on 2010-05-10
> **Silvertones said:**
> Okay I'll keep this info bookmarked and wait for the CD.
I'm going to have to redue my dial up connection, network, Samba etc aren't I?

>  A fresh install will wipe system wide settings. It depends for the settings. I still don't have enough ubuntu experience to give you detailed answer, but I can tell you this.

I also have separate /home created when I first installed ubuntu 9.10 6 months ago. I was aware of the benefit of having it separate for future clean installs. Two days ago I installed 10.04 over it, keeping my /home of course.

My wallpaper was immediately right there in 10.04 without the need to select it again. My firefox bookmarks and add-ons were there. Even for the development platform Netbeans there was a shortcut on the desktop and in Applications-Programming and Netbeans wasn't even installed in 10.04. So of course clicking the shortcut didn't do anything. But it was there.

A lot of software settings go into your Home folder. So the new fresh install can simply pick them up. I'm not sure where dial-up connections are kept, it might even keep them. Because different users can have different dial-up connections so it might be stored under your Home folder.

You don't see a lot of the folders because they are hidden. Open Home and hit Ctrl + H. That will show the hidden folders. All of them will be kept by keeping /home.

And one important thing, when we say keeping /home. Ubuntu installer creates one single user during install. It's better to select the same first user you created with the previous install. Of course it has to be the same username exactly, so the home folder can match.

If you have other users you can add them later, and they can keep their Home folder too, short instructions here:
[http://ubuntuforums.org/showpost.php?p=8211002&postcount=2](http://ubuntuforums.org/showpost.php?p=8211002&postcount=2)

---

### Post by markthecarp on 2010-05-10
> **darkod said:**
> It depends for the settings. I still don't have enough ubuntu experience to give you detailed answer, but I can tell you this.

I also have separate /home created when I first installed ubuntu 9.10 6 months ago. I was aware of the benefit of having it separate for future clean installs. Two days ago I installed 10.04 over it, keeping my /home of course.

My wallpaper was immediately right there in 10.04 without the need to select it again. My firefox bookmarks and add-ons were there. Even for the development platform Netbeans there was a shortcut on the desktop and in Applications-Programming and Netbeans wasn't even installed in 10.04. So of course clicking the shortcut didn't do anything. But it was there.

A lot of software settings go into your Home folder. So the new fresh install can simply pick them up. I'm not sure where dial-up connections are kept, it might even keep them. Because different users can have different dial-up connections so it might be stored under your Home folder.


Good point sir: I come from the days when all system wide settings were in /etc. Ubuntu is geared toward desktop users.

> You don't see a lot of the folders because they are hidden. Open Home and hit Ctrl + H. That will show the hidden folders. All of them will be kept by keeping /home.

And one important thing, when we say keeping /home. Ubuntu installer creates one single user during install. It's better to select the same first user you created with the previous install. Of course it has to be the same username exactly, so the home folder can match.

It's the UID's that don't match; especially nice between apt and rpm. 

> If you have other users you can add them later, and they can keep their Home folder too, short instructions here:
[http://ubuntuforums.org/showpost.php?p=8211002&postcount=2](http://ubuntuforums.org/showpost.php?p=8211002&postcount=2)

/me reading above link...

---

