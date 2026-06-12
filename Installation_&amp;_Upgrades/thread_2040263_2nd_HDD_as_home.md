---
title: "2nd HDD as /home"
date: 2012-08-10
forum: Installation &amp; Upgrades
---

### Post by Xswitch on 2012-08-10
Hi all...  I have a system that I installed 12.04 on.  The system has a 2nd Hard drive that we want to make **/home**.  Is there a way to make it /home without it changing the settings on the new install ... ie changing the wallpaper, browser bookmarks, favorites, etc...  ?

Has a lot of hidden folders on it, like **.scribus**, etc...  We want to reinstall all of these apps from scratch.  _Can I just rename the hidden folders_?  Can I just delete the hidden folders to the apps that I want to reinstall?

Thanks all...

---

### Post by cortman on 2012-08-10
Hi, [this thread]("http://ubuntuforums.org/showthread.php?t=1635637") may help you in moving /home.
Apps that you want to reinstall from scratch- the command

```
apt-get purge program_name
```

will remove all config files as well. Double check your home directory for any folders pertaining to the removed program though, just to be sure. You can safely remove them.

---

### Post by oldfred on 2012-08-10
Another link on ways to move /home to another partition, you do have to make sure to maintain ownership & permissions:

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I had a separate /home for all of about 5 minutes when I realized the hidden files & folders are relatively small and most of /home is just my data in Documents, Music, Downloads, etc. So I moved all of my data to another partition, but not /home. I also have a bootable install on every hard drive, but mount same data in each. That way if any one drive fails, I can boot another as it has all the system folders including /home. Hopefully when drive does fail I do have recent backup of /home and/or data.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

---

### Post by Xswitch on 2012-08-10
Thanks cortman and oldfred ...  digging into this now.

---

