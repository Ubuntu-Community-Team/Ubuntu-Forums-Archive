---
title: "Replacing 13.10 with 14.04  What settings to carry over"
date: 2014-02-08
forum: Installation &amp; Upgrades
---

### Post by SurfaceUnits on 2014-02-08
I will be replacing my 13.10 Gnome with 14.04 and I'm wondering what settings to carry over. I'll have my sources.list and some Plymouth themes and configs. What else, if any should I look at? I have separate / and /home partitions.
Thanks

---

### Post by Frogs Hair on 2014-02-08
First , are you doing this now or in April when 14.04 is released?  Unofficial software sources should be disabled before any upgrade. There is often a delay before PPA software is updated for new releases and this can lead to broken dependencies . If using a proprietary graphics driver you may want revert to the default driver prior to upgrade. I can't  comment on the Plymouth configuration.

---

### Post by SurfaceUnits on 2014-02-08
Thank you for your reply. This won't be an upgrade. I never upgrade to a LTS release, only fresh installs. I am currently running a system that started out on the unofficial 12.04 Ubuntu Gnome Shell Remix and has been upgraded with every release since then. So it has been a while since I moved to a new install and I'm wondering what I should take with me.

---

### Post by Frogs Hair on 2014-02-08
I use Ubuntu One and move only files from one installation to the other so I can't tell you what configurations would survive to be useful  . There is also an official Ubuntu Gnome flavor now which will be based gnome 3.10 . Unofficial software and sources won't be any benefit on a new installation until updated and Plymouth has changed somewhat on every release  since started using Ubuntu 9.10. You would know better if your custom configuration will survive since I have no home partition.

---

### Post by fantab on 2014-02-09
> **SurfaceUnits said:**
> Thank you for your reply. This won't be an upgrade. I never upgrade to a LTS release, only fresh installs. I am currently running a system that started out on the unofficial 12.04 Ubuntu Gnome Shell Remix and has been upgraded with every release since then. So it has been a while since I moved to a new install and I'm wondering what I should take with me.

What do you want to take with you?
This post has some useful tips on how and what to back up. [http://ubuntuforums.org/showthread.php?t=1748541&p=10765330#post10765330](http://ubuntuforums.org/showthread.php?t=1748541&p=10765330#post10765330)

I usually carry over to my new install:
Firefox Preferences/Data
Thunderbird Preferences/Data
my Conky file
All three are stored as hidden dot files in /home directory. 
I just copy these to my USB pendrive and reuse them with my new install, replacing the new .mozilla with the one I have on my USB drive.

---

