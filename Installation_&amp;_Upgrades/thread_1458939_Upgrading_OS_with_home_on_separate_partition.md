---
title: "Upgrading OS with /home on separate partition"
date: 2010-04-20
forum: Installation &amp; Upgrades
---

### Post by akand074 on 2010-04-20
Hey guys,

The full release of Lucid is going to be released soon and I just wanted to prepare for it soon and I had a few questions. 

First, I have /home on a separate partition, and when I do a clean install of Lucid I'll set /home to the same partition without checking the "format" box it so I don't lose anything. Would that cause any problems seeing as I'll have configuration files for applications in Karmic? I don't think it will. 

Also I was considering to use this:
[http://ubuntuforums.org/showpost.php?p=8113316&postcount=3](http://ubuntuforums.org/showpost.php?p=8113316&postcount=3)

to save all my applications so I don't have to manually run around to reinstall all of them, but wouldn't that be a problem because all my software sources are for Karmic, also would not not save old Karmic applications (ones that came preinstalled in Karmic) that are no longer needed/supported? 

Perhaps it will be easier if I just did the clean install and reinstalling everything manually, I just didn't want to lose any of my data in /home by accident but if I don't format that shouldn't be a problem, though I could put all my data from /home onto my external hard drive and then format /home again and just put my data back and start from scratch but that is a lot more work. 

Any ideas on what would be the best way to do this?

---

### Post by snowpine on 2010-04-20
> **akand074 said:**
> First, I have /home on a separate partition, and when I do a clean install of Lucid I'll set /home to the same partition without checking the "format" box it so I don't lose anything. Would that cause any problems seeing as I'll have configuration files for applications in Karmic? I don't think it will. 

This is the best and easiest option, in my opinion.

You should have an external backup of your /home at all times, for peace of mind, regardless of whether or not you're upgrading (but especially if you are). :)

---

### Post by akand074 on 2010-04-21
> **snowpine said:**
> This is the best and easiest option, in my opinion.

You should have an external backup of your /home at all times, for peace of mind, regardless of whether or not you're upgrading (but especially if you are). :)

Yeah I'll probably do that. So seeing as my configuration files will be untouched, wouldn't my firefox profile and things like personal screenlet settings remain the same after I reinstall them?

---

### Post by snowpine on 2010-04-21
> **akand074 said:**
> Yeah I'll probably do that. So seeing as my configuration files will be untouched, wouldn't my firefox profile and things like personal screenlet settings remain the same after I reinstall them?

Exactly, that is the benefit of a separate /home partition. :)

---

### Post by nothingspecial on 2010-04-21
Assuming you have 2 partitions (forget swap, just don`t touch it), one /home and one /

And assuming / is /dev/sda1 and /home is /dev/sda2

When you get to the partitioning bit of the install

Select /dev/sda1 and check the format box, choose to use it as an ext4 file system and choose a mount point of /

Then select /dev/sda2, choose to use it as whatever file system it happens to be (probably ext3 or ext4), choose to mount it as /home

**[SIZE="5"][COLOR="Red"]BUT DO NOT CHECK THE FORMAT BOX[/COLOR][/SIZE]**

Job done.

---

### Post by akand074 on 2010-04-22
Perfect, thanks guys :)

---

### Post by Kom-Si on 2010-11-14
> **nothingspecial said:**
> Assuming you have 2 partitions (forget swap, just don`t touch it), one /home and one /

And assuming / is /dev/sda1 and /home is /dev/sda2

When you get to the partitioning bit of the install

Select /dev/sda1 and check the format box, choose to use it as an ext4 file system and choose a mount point of /

Then select /dev/sda2, choose to use it as whatever file system it happens to be (probably ext3 or ext4), choose to mount it as /home

**[SIZE="5"][COLOR="Red"]BUT DO NOT CHECK THE FORMAT BOX[/COLOR][/SIZE]**

Job done.

Hey, I did just that last night re-installing Maverick. And it worked.... mmm... sort of. The system installed, booted, but the only user I could see was my newly created self (during setup process). Then I tried to manually re-create users I had on my /home partition, and again it worked... sort of.

I think that's not right - Ubuntu ought to have picked up user accounts I had on my /home partition, eh?

Any comments on that?

---

### Post by nothingspecial on 2010-11-15
Suggest it

[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

The thing to remember is that linux recognises each user by the uid rather than user name.

Ubuntu assigns uids for users from 1000 up, so if you create "bob" when you install, then "bill" then "tom. Their uids will be

bob 1000
bill  1001 
tom 1002

If you then create them in a different order on a fresh install, with a seperate /home, things won`t work.

---

