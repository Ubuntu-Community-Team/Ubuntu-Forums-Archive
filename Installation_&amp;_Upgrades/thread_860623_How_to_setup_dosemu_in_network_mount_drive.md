---
title: "How to setup dosemu in network mount drive"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by newbie618 on 2008-07-15
Hi,

I am having trouble to get a dos program to work on a network mounted drive.  No problem using dosbox.  Local drive works but not network across a samba linux server.

the local Ubuntu 8.04 desktop fstab is like this

//192.168.0.1/dos /home/user/dos  smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0

Are there special protocol for dosemu with samba?  How do I go about finding what the bug is?

Newbie

---

### Post by fox_misionero on 2008-10-19
Hi, I have the same problem...

Did you find the solution? Can you share it? How you make it?

If I find it, i´m going to share here...

Thanks

---

### Post by emendelson on 2008-10-21
See reply to similar question in another thread:

[http://ubuntuforums.org/showthread.php?p=6005318#post6005318](http://ubuntuforums.org/showthread.php?p=6005318#post6005318)

---

