---
title: "Upgrading Ubuntu - is it safe?"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by rhawkes on 2007-04-09
Hi all,

I have played on and off with Linux for a bit now, and have only recently installed it again but with great success in my tweaking to get screen, wireless, VPN support, etc, all working properly.

I am running Edgy Eft at the moment, and see 7.04 is due very soon, but my questions are:

1) Is the upgrade process simple

2) Should I expect the worst, e.g. wireless and VPN not working again, and expect to do lots of tweaking

3) Pre-upgrade, how would you recommend backing up? I have seen this guide here, [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087), however would appreciate thoughts of other members too.

---

### Post by teaker1s on 2007-04-09
UNLESS you have a desperate need for hardware support or feature, then all you need is current system with security updates. I'm still running dapper perfectly

---

### Post by jakev383 on 2007-04-09
> **rhawkes said:**
> Hi all,

I have played on and off with Linux for a bit now, and have only recently installed it again but with great success in my tweaking to get screen, wireless, VPN support, etc, all working properly.

I am running Edgy Eft at the moment, and see 7.04 is due very soon, but my questions are:

1) Is the upgrade process simple

2) Should I expect the worst, e.g. wireless and VPN not working again, and expect to do lots of tweaking

3) Pre-upgrade, how would you recommend backing up? I have seen this guide here, [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087), however would appreciate thoughts of other members too.

Plan for the worst, and it shouldn't be as bad as that. I've upgraded before and oly run into a few issues (yes, wireless did break again), but for the most part it's really easy. Once the new one comes out, change your repos and then just run apt-get dist-upgrade and sit back and have a cup of coffee.
Personally, I have my 2 Ubuntu systems tweaked and setup just the way I like them so I'm not going to upgrade. If it's not broke.....
And I personally use this thread for backing up my systems:
[http://ubuntuforums.org/showthread.php?t=360283&highlight=backup+restore](http://ubuntuforums.org/showthread.php?t=360283&highlight=backup+restore)

---

### Post by rhawkes on 2007-04-10
Hi guys - thanks for sharing that with me, I'll have a look through. For my own experience. I think I'll try running a full backup to an external HDD, then restore it to another hard disk (I'll swap the HDD over in my laptop), and then try upgrading the restored backup.

If all goes well, then I'll upgrade, if not, I'll take the advise that if it isn't broken ;)

Thanks again!

---

### Post by dbrjay on 2007-04-10
upgrading is fine so long as you are upgrading to a stable version. My advise is wait until it is announced as stable and then upgrade  :)  save being the one that finds the problem which erases your whole hard disk  =S

---

### Post by chakkaradeep on 2007-04-10
> **rhawkes said:**
> Hi all,

I have played on and off with Linux for a bit now, and have only recently installed it again but with great success in my tweaking to get screen, wireless, VPN support, etc, all working properly.

I am running Edgy Eft at the moment, and see 7.04 is due very soon, but my questions are:

1) Is the upgrade process simple

2) Should I expect the worst, e.g. wireless and VPN not working again, and expect to do lots of tweaking

3) Pre-upgrade, how would you recommend backing up? I have seen this guide here, [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087), however would appreciate thoughts of other members too.

I did an upgrade from edgy eft to fiesty and my system is good now, enjoying fiesty. This was the only command I executed from terminal,

**sudo update-manager -d -c**

You can see [screenshots here]("http://chakkaradeep.wordpress.com/2007/04/09/here-comes-fiesty-in-my-laptop/")

---

