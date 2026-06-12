---
title: "system crash after partial upgrade 10.10"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by Yohai on 2011-04-07
Hi all.

I have a Dell studio running ubuntu for two years now (I'm a semi-newbie). 
I had ubuntu 10.04, but a few days ago, the update manager started to bug me that some stuff don't work properly and that I need to to a partial upgrade. I postponed that for a while, and all worked fine, but I finally had sometime and clicked "yes", all began collapsing:

1) the update manager crashed while updating.
2) I rebooted and ran it again. same crash at the same stage.
3) I decided, god knows why, to do a full upgrade to 10.10, which also crasehd.

Now it won't even boot. It always get stuck at a line saying 
"no IPv6 routers present" 
or something of that sort.
when I switch off manually the wireless switch on the laptop, the boot gets stuck a bit earlier, on a line that says:
"laptop login:"

any ideas?


please save me!
thanks,
yohai

EDIT: I just remembered something which might be important: I had a hibernation problem on the upgrade to 10.04, so I played around a bit with that. now it uses libgcrypt, and I remember I set up something manually then, but I can't remember what.

---

### Post by mörgæs on 2011-04-07
Partial upgrades are dangerous:
[http://ubuntuforums.org/showthread.php?t=1641400](http://ubuntuforums.org/showthread.php?t=1641400)

How does the machine run in a 10.10 live boot?

---

### Post by Yohai on 2011-04-07
yes, but only in recovery mode.
when I try to load other kernels, it gets stuck.

I think I'm gonna simply boot from a cd and reinstall ubuntu, deleting the partition.
(I backed up the files)

seems reasonable?

---

### Post by mörgæs on 2011-04-07
Yes, I was going to suggest the same.
Remember to have wired internet access while installing.

---

