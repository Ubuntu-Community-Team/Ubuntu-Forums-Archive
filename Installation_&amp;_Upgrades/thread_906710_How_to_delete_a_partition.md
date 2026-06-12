---
title: "How to delete a partition??"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by henryjm206 on 2008-08-31
I'm currently dual booting ubuntu 8.04 and vista and I want to remove vista and replace it with linux mint but I don't know how. Help
Also when I boot up linux mint when I go to install it I get a command line
and I don't know how to use that.


Henry

---

### Post by SkonesMickLoud on 2008-08-31
Install GParted:

```
sudo aptitude install gparted
```

Then run it:

```
gksu gparted
```

Right click the partition you want to delete and select "Unmount".  Right click again and select either "Delete" or "Format As..." and select a file system type.

As for your Mint CD, did you download the correct LiveCD .iso?  Check the MD5sum?

---

### Post by Rocket2DMn on 2008-08-31
For information on deleting a windows partition that is already in a dual boot setup, see [uhelp]community/HowToRemoveWindows[/uhelp]

Are you trying to just get rid of everything and start fresh with on an install of Mint?  In that case you just tell the installer to use the entire disk.

It sounds like you have a bad burn of the cd if you are getting dropped at a busybox.

---

