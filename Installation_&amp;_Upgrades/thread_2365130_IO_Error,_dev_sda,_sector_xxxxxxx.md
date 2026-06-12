---
title: "I/O Error, dev sda, sector xxxxxxx"
date: 2017-07-03
forum: Installation &amp; Upgrades
---

### Post by dcpifhq on 2017-07-03
Hi, so I have the same problem like this post: [https://askubuntu.com/questions/424580/i-o-error-dev-sda-sector-xxxxxxxxxx](https://askubuntu.com/questions/424580/i-o-error-dev-sda-sector-xxxxxxxxxx)

Except that this happens when I try to run the setup/installation on Ubuntu.

And also it says that the hard disk is faulty. So is that true? Because this is a laptop of my friend's, so should I tell him that his hard disk is no good (and that he should buy a new one) or no?

---

### Post by Autodave on 2017-07-03
It certainly sounds like the HD is on its way out.

---

### Post by CatKiller on 2017-07-03
> **Autodave said:**
> It certainly sounds like the HD is on its way out.

It does to me, too.

Some hard drive manufacturers have a diagnostic utility that you can run to check it, though.

---

### Post by dcpifhq on 2017-07-03
> **Autodave said:**
> It certainly sounds like the HD is on its way out.

It's that bad...? Wow... Alright. Thanks for the info!
And CatKiller, idk the process of that xD so I'll just get a new HD.

---

### Post by deadflowr on 2017-07-03
Without seeing what SMART says about your hard drive (and not some random hard drive's output from someone else)
We cannot be totally sure of anything.
You can run smartctl for the hard drive from a live session.
(You need to install smartmontools in the live session)
see: [https://help.ubuntu.com/community/Smartmontools]("https://help.ubuntu.com/community/Smartmontools")

---

