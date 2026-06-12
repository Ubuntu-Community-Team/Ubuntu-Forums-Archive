---
title: "Volume /root has 1.5Mb space remaing, so failed to download reposistory information"
date: 2014-06-10
forum: Installation &amp; Upgrades
---

### Post by a.leeming on 2014-06-10
Ubuntu 12.04 x 64 intalled. I tried to update via the Software Updater, but was told that it afailed to download the repo information because /boot had only 1.5Mb space left.  I tried cd /root, but failed - premissions, even after sudo. Disk User Analysis showed: boot 100% size 230.4 Mb 279 items; grub 2.7% 6.3 Mb 245 items.
I tried cd /root, but permission refused; even after sudo.
How can I free up aup enough disk space?
Thank you, a.leeming

---

### Post by Bashing-om on 2014-06-10
a.leeming; Hello !

We often see this as a condition that the '/boot' partition is filled with old kernels. If you are at 100% capacity, then there is no operating head room for the system to operate in. I may be a real pain to correct ( but it can be done).
Let's see if the package manager can work in this situation.
Show us the situation:
Terminal commands:
```

df -h
df -i
cd /
sudo du -sx * | sort -n
dpkg -l | grep linux-image

```
Please post these outputs between code tags to maintain the formatting and promode readability.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
If you need to drill down further, use cd to move to a directory - with that 'du' command - of interest then repeat the du command.
The results are in megabytes.

To return to your home as the Present Working Directory issue the command:
```

cd

```

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by a.leeming on 2014-06-10
Thanks for the quick reply; I ,have actually found a solution: I installed Ubuntu-tweak, which has a magical way of removing old linux kernels,
A.leeming

---

### Post by Bashing-om on 2014-06-10
a.leeming; Great !

Gui tools can make life easier !

Please mark this thread solved;
 aides others seeking the solution, helps keep the forum clean and 
precludes others miss-directing efforts to aid.

and just
[INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT]

---

