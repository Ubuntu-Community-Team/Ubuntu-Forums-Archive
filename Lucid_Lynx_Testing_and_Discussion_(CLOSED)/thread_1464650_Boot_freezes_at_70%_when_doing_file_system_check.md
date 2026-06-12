---
title: "Boot freezes at 70% when doing file system check"
date: 2010-04-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by brunogirin on 2010-04-28
Hi all,

I've been using Lucid since beta 2 on my laptop and yesterday was the first time that it forces a file system check at boot. It went all the way to 70% and then froze. I'm sure I've seen posts on the subject but can't remember for the life of me if it was in the forums or the mailing lists.

What procedure should I follow to identify what the problem is and file a sensible bug report? I'm comfortable using things like [netconsole]("https://wiki.ubuntu.com/KernelTeam/Netconsole") to get logs out during boot but I'm not sure how I can trigger a fsck at next boot. And is netconsole a good way to get the information I require anyway?

Thanks

---

### Post by Lollerke on 2010-04-28
Are you sure that it's frozen? I think I have the same problem,but in my case it's extremely slow. It took 1 minute to go up to 71% from 70%.

---

### Post by vredley on 2010-04-28
There's another thread on this subject here: [http://ubuntuforums.org/showthread.php?t=1464339](http://ubuntuforums.org/showthread.php?t=1464339) .

Disabling Plymouth fixed this problem for me.

---

### Post by kansasnoob on 2010-04-28
Try booting into recovery mode and then selecting resume normal boot. If that doesn't work try pressing Ctrl + SysReq + b.

It seemed to me that there were some residual effects from recent updates that resolved themselves after doing the above two or even three times!

---

### Post by Bobhuber on 2010-04-28
> **brunogirin said:**
> Hi all,

I've been using Lucid since beta 2 on my laptop and yesterday was the first time that it forces a file system check at boot. It went all the way to 70% and then froze. I'm sure I've seen posts on the subject but can't remember for the life of me if it was in the forums or the mailing lists.

What procedure should I follow to identify what the problem is and file a sensible bug report? I'm comfortable using things like [netconsole]("https://wiki.ubuntu.com/KernelTeam/Netconsole") to get logs out during boot but I'm not sure how I can trigger a fsck at next boot. And is netconsole a good way to get the information I require anyway?

Thanks

Its a major bug thats already been reported. Not sure what the status is.

---

### Post by vredley on 2010-04-28
> **Bobhuber said:**
> Its a major bug thats already been reported. Not sure what the status is.

The bug was reported here: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/554737](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/554737) . Marked 'Fix Released' on 15/4/2010.

---

### Post by jkxx on 2010-04-28
Only posting to confirm that's definitely been resolved as I had one of these auto-checks run yesterday.

The checker seems to be designed so that it gets to 70% right away and then the really slow stuff happens afterward. Mine stayed at the 70% for a minute or two before proceeding to 71, etc. Finally it got to 90% and spent about 10 minutes there, then suddenly the log in screen appeared.

So, unless you waited more than 10 minutes and it did not progress at all it was probably not broken but simply taking as long as it needs to.

(On the other hand, I haven't seen too many places mention the fact that auto disk checks will run even if there were no errors on previous boot/shutdown..)

---

