---
title: "There is no cdromupgrade in the Ubuntu cd?"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by cscat on 2008-09-11
Hi,

Recently I order a Hardy Desktop Edition from shipit (not "alternate" CD)? I want to upgrede my gutsy to hardy.

I typed: gksu "sh /cdrom/cdromupgrade"
but nothing happened. So I went to the cdrom and browsed it. I carefully looked for it. I found that no such directory or file (cdromupgrade) exists? Is it because my cd is not an an alternate CD?! So what should I do now?!!!

thx

---

### Post by forger on 2008-09-11
The image links state it clearly:
[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

> Alternate install CD

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    **[COLOR="Red"]* upgrading from older installations without network access;[/COLOR]**
    * LVM and/or RAID partitioning;
    * installs on systems with less than about 384MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably). 

> Desktop CD
The desktop CD allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. This type of CD is what most people will want to use. You will need at least 384MB of RAM to install from this CD.

You have to get the alternate cd if you want to upgrade.
FYI, you could backup somewhere your /home/ directory, do a clean install (format the root partition), and copy the /home/ directory back - You wouldn't lose any custom configuration in /home/, but you might have to install some application packages again.

---

### Post by cscat on 2008-09-11
oooops! thx.

But isn't it possible for someone to upload "cdromupgrade" file and then change it in some way to point to the content of the CD I got now? You know some tricky things, etc.!!!:)

---

### Post by forger on 2008-09-11
> **cscat said:**
> 
But isn't it possible for someone to upload "cdromupgrade" file and then change it in some way to point to the content of the CD I got now? You know some tricky things, etc.!!!:)

By the time you find out you would have downloaded the alternate cd :)
If you know someone that has the alternate cd, why not ask him to simply send it to you or make a copy of it?

---

### Post by cscat on 2008-09-12
My internet connection bandwidth is low and I don't know anyone who has this CD unfortunately!

---

