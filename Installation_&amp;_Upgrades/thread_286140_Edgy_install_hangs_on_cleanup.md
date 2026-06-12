---
title: "Edgy install hangs on cleanup"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by cholly on 2006-10-27
I installed 6.10 today using the Desktop CD and it hung near 95% (I don't have the exact %. It was removing packages, some libraries I think. Well I rebooted and it appears to work. Grub did fine and I could boot into X OK. 

So my questions: 

1.Should I be concerned that it didn't finish properly? 

2.Once it's gone on to removing packages is it done? 

3.Are there just install pkgs in /var or something I can delete and move on?

4.Did it skip any finalizing process basically?


Note: I had this problem with Dapper too. This a new is AVERATEC Laptop /w 512mb of ram, maybe even 1024, I have to check.

---

### Post by trippyd on 2006-10-27
I would think that as long as
```
sudo aptitude update
``` works, you should be able to get past any problems you might have.

---

### Post by trippyd on 2006-10-27
Oh yeah, to clean up the packages:
```
sudo apt-get clean
sudo apt-get autoclean
```
I don't know if it finished or not, but as long as you can apt, you should be ok.

---

### Post by MrEasy on 2006-10-27
I have a similar problem.
Installation is stuck at 92% saying "Loading module aec62xx (...)".
Tried twice; 6.06 was running smoothly.
Dell Latitude 600

---

### Post by h5n1now on 2006-10-31
I have the problem to.
Installation is stuck at 92% saying "Loading module aec62xx (...)".
If I exit install and restart it don't work.
What should I do?
iMac G3 DVSE.

---

### Post by MrEasy on 2006-11-01
> **h5n1now said:**
> I have the problem to.
Installation is stuck at 92% saying "Loading module aec62xx (...)".
If I exit install and restart it don't work.
What should I do?
iMac G3 DVSE.

Hi,
I opened a bug regarding this issue as I also heard from another guy having the same problem: [https://launchpad.net/distros/ubuntu/+source/hw-detect/+bug/69353](https://launchpad.net/distros/ubuntu/+source/hw-detect/+bug/69353)
I  made it work by first installing 6.06 then upgrading to 6.10. The other guy used the alternate install CD of 6.10 and that was working, too.
Maybe you can post your hardware description to the bug report.

---

