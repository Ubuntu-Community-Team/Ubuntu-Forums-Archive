---
title: "I made a boo-boo... (revert back to Hardy)"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2010-03-16
I think I deleted obsolete packages when I did the upgrade FROM HH 8.04. Does this mean I cannot go back to HH kernel?

Do I have to burn a Hardy disk and re-install?

My X-server keeps re-starting, and I have NO clue where to begin... I had a tough time with it the other night at upgrade, which I thought I solved:

[http://ubuntuforums.org/showthread.php?t=1430165](http://ubuntuforums.org/showthread.php?t=1430165)

---

### Post by dstew on 2010-03-16
> Do I have to burn a Hardy disk and re-install?I think so.

Maybe I do not understand what you have tried to do, but perhaps you were hoping that you could have grub menu items to boot a Hardy kernel, or Jaunty, or Karmic, all sharing the same file system. I do not know of a case where two separate installations share the same file system. That is because a lot of the executable files for Hardy share the same file names as those for later distributions, but the newer executables may not work well with the older kernel. If you booted a Hardy kernel, the rest of the system would load executables and modules that were appropriate to the later kernel, and things would not work. Usually, separate distributions need to be on separate filesystems (separate partitions).

You can sometimes share a /home partition, because it usually has data, and not a lot of executables. However, even here, there can be trouble, because your home folder has lots of hidden configuration files, that may be replaced by newer ones, with the result that some programs on the older distribution may not work. If you want to keep a same /home partition, it is probably best to have separate user names for each distribution. That is, if your Hardy user name was moozillaaa, then when you upgrade, create a new user such as moozillaaa_jaunty so that your old configuration files do not get replaced. Sign in as moozillaaa_jaunty when you boot into your new distribution, but moozillaaa when running your old distribution.

I don't have any advice for you regarding your X-server. Maybe try to re-configure it from a command line (Recovery boot).

---

### Post by Moozillaaa on 2010-03-16
Good explanation... 

Now the problem is downloading 8.04 to burn - 4 failed attempts.

Can I load 7.10, and do upgrade to 8.04?

---

### Post by dstew on 2010-03-16
Do you mean the download fails, or that the burned CD fails?

---

### Post by Moozillaaa on 2010-03-16
> **dstew said:**
> Do you mean the download fails, or that the burned CD fails?

Download fails to complete every time. Download speed is 180KBs.

[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

---

### Post by dstew on 2010-03-17
Have you tried to download it using a BitTorrent client? These can stop and start, so they are more reliable if you are having connection problems, like network lag, or if your computer locks up. You don't have to start all over again if you lose your connection for some reason. If you look down the Releases site screen, there are .iso files set up for torrents.

---

