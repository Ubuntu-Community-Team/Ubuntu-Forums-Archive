---
title: "Install Ubuntu as dual boot but shared /home?"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by germanix on 2011-03-08
I currently run Linux Mint as sole OS and with a separate /home partition. I have a small (12GB) unused partition on my HDD where I would like to install Ubuntu 10.10. I have a lot of data on my /home partition and instead of giving Ubuntu its own separate /home partition I just want it to share the same /home partition as Mint.
I realize that I can get access to all my home files from Ubuntu anyway but I thought it would make more sense to have both OS´s use the same /home partition.
Then I got to thinking that perhaps this may not be a good idea at all. I am not sure how this all works but I got worried that this may cause some incompatibilities that I do not know about.
Question: Is this a good idea? If yes, how do I need to go about installing Ubuntu, meaning that should I then during the installing process choose the empty partition to be used as / only and the current /home also as the Ubuntu /home? without formatting it so as not to loose my data? Or is there a correct/safer way to do this?
(Just as explanation, I like both Mint 10 and Ubuntu 10,10, and both run very stable on my system. I use my computer for work and need a stable system, but as we all know sometimes things can go wrong and mostly after a new update. So my thinking is that when I have both Distro`s on my laptop and one crashes I could still boot from the other and save the day.)
Appreciate all your help and advice. Thanks.

---

### Post by lncoll on 2011-03-08
I'm using Ubuntu 10.04 and Fedora 14 with the same /home and swap partitions.
Some times there is a little interaction between them (some user settings in one affect the other) but not a big problem.

The way I installed it:
1st, backup
2nd, another backup ;-)
3rd, test backups.
4th, install Ubuntu, setting manual partitioning. Format your free HD space and select it as / , DO NOT format your /home partition and set it as /home.
5th, install GRUB in sda (hd0), GRUB2 does the rest.

If the two SOs interact too much between them, you can create a different user at the beginning, this way can test ubuntu without affect Mint. every one with a different user.

---

### Post by germanix on 2011-03-08
> **lncoll said:**
> I'm using Ubuntu 10.04 and Fedora 14 with the same /home and swap partitions.
Some times there is a little interaction between them (some user settings in one affect the other) but not a big problem.

The way I installed it:
1st, backup
2nd, another backup ;-)
3rd, test backups.
4th, install Ubuntu, setting manual partitioning. Format your free HD space and select it as / , DO NOT format your /home partition and set it as /home.
5th, install GRUB in sda (hd0), GRUB2 does the rest.

If the two SOs interact too much between them, you can create a different user at the beginning, this way can test ubuntu without affect Mint. every one with a different user.

Thank you very much for this well explained information. One thing I am not sure of is step 5 (install GRUB in sda, I am not sure how you do that?

---

### Post by oldfred on 2011-03-08
Those that say you can use same /home partition always suggest a separate user. Which to me defeats the purpose. 

I use a shared data partition and copy some settings from /home. But I have only so far installed Ubuntu. but have 3 versions old, current & alpha/beta all sharing my same data partition. I also have a NTFS shared partition for my old XP install and have Firefox & Thunderbird profiles in that shared across all 4 systems. It is convenient to have same bookmarks & email in all systems.

Without data my /home is about 1GB, but I found it is mostly my .wine which I have not yet moved to /data.

---

### Post by germanix on 2011-03-08
Hi oldfred, thank you for your input. I do understand your arguments and you are right, it would make things simpler. I for one however would no know how to go about setting such a system up. For one I would not know which settings files to copy, and where to, and I guess it would also mean that I would have to re-format my drive to get a data partition etc ect. However I think this is a great idea when you start from fresh and plan your system like that from the start.. The next time I get around to that I will certainly build that in.
For the moment however I think what Incoll suggested will work fine for me.

---

### Post by lncoll on 2011-03-08
> **germanix said:**
> Thank you very much for this well explained information. One thing I am not sure of is step 5 (install GRUB in sda, I am not sure how you do that?

The installation program asks you where to install GRUB, the best (as I see) is install it at the MBR of the first hd, this way there are not problems when upgrading kernel because GRUB looks for all the kernels in all the partitions.

About a different user, I've proposed it just for testing. I'm using the same user in both installs and think is the best way.

---

### Post by germanix on 2011-03-08
Thanks Incoll, I am going to try it now and will report the outcome here.

---

### Post by germanix on 2011-03-08
Well I am afraid something has gone wrong. Ubuntu was installed as discussed. Grub is fine, it allows me to choose which Distro to boot from. Ubuntu starts the booting process then gets to the point where the desktop is presented, but instead of the Ubuntu desktop it starts to present me with the Mint desktop instead and then just freezes.
Linux Mint on the other hand boots up fine
Any ideas how to fix this?
(Edit) I tried to boot Ubuntu in "recovery mode", I opted to "repair packages" and somethings were repaired. I then got the following message:
"could not open lock file /var/lib/apt/lists/lock -open (13: permission denied)

---

### Post by germanix on 2011-03-08
I have just realised that the Ubuntu desktop that I mentioned looks like the Mint desktop and is frozen, is not actually frozen. It is just that the Gnome panel has no icons on it but I can add to the panel. I now have a possibility to get to admin or system etc but do not know how to get the Ubuntu desktop to load?
need help please!

---

### Post by Hakunka-Matata on 2011-03-08
germanix, "nichts?"

Modifying an existing Ubuntu installation to create and use a separate /home partition is outlined in [https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving") link.

Installing Ubuntu whilst already having an existing /home partition is of course another matter.  

the file /etc/fstab (Back up existing /etc/fstab first - of course) must have the new /home/partition information added to it, so it mounts automatically on boot.  Attached Thumbnail shows mine.

I also saw in a post somewhere here (oldfred?), that both OSes should have the same userid, otherwise permission problems are creating when trying to access /home

---

### Post by germanix on 2011-03-08
Well I thank you for this information but to tell the truth this is all chinese to me.
I now have the Ubuntu desktop up and running. The problem is however that in order to get it to load correctly I had to create "another user". When I boot up as the "other user" all goes fine, but when I boot in as "myself" I do not get the Ubuntu desktop (or only a part of it), only one panel at the top and no icons but I can add normal gnome icons.
I saw that I was locked in as a "custom" user and I guess that this is the conflict that I was worried about right in the beginning. I gave the "other user" admin rights and then deleted myself as a user to see if I could solve this problem.  I am now logged in as the "other user" and as "administrator" which is not ok, but when I change that to "custom user" I am back to the old problem again with the "custom" desktop which is half a desktop.
I really just need to be able to change the "custom" desktop to normal and then I can change my status back from administrator to custom?
But here I am stuck. Ido not know how to do this!

(Edit) I now noticed that any changes I do to the gnome panel in Ubuntu also appears on the gnome panel in Mint! This is really dumm.

---

### Post by Hakunka-Matata on 2011-03-08
```
cat /etc/fstab > fstab-original && gedit fstab-original
```

if you execute that code, you'll produce a copy of your /etc/fstab file and open the text editor 'gedit' to look at it.  You must close the text editor to finish the Terminal session.

post the results and we'll have a look.. if you wish..

---

### Post by germanix on 2011-03-08
I thank you for your offer to help me. This is much appreciated. I am however in the process of re-installing Ubuntu, and this time I decided not to have both OS´s use the same /home partition. It would have been nice but it seems to me it creates more problems than what it is worth. (for me at least). I will just use the Mint /home for all my files leaving the Ubuntu /home empty but I did make a small separate /home for Ubuntu to make future install somewhat easier.
I thank you all for your help. You have all been very kind. I wish you all a nice day.

---

