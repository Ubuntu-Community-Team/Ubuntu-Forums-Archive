---
title: "Win7 can not boot!"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by haikon on 2012-04-27
Hi there,

I have a pre-installed laptop. Because of fastboot and recovery-function, there are several partitions.

I have installed Ubuntu 12.4 via Live-CD, with shrinking the main-partition(win7) to get space for ubuntu.
ubuntu works fine. grub-menu is general. I have 2 entries for ubuntu, normal and recovery. I have one entry for win7 and one for win-recovery. 

when I choose win7, screen gets black for 2 seconds and I get back to grub-menu.
the enttry for win-recovery works, but i can't use it, because it will set default-settings.

I have installed bootrepair, and tried the recommended auto-repair, where grub is re-installed. but the problem is the same.

I'm not sure how to change MBR or FIXMBR, because I read different things about it.
also I think, I can't do fixmbr with WIN-cd because it's a pre-installed system...


THX for helping me.

here's the log of boot-repair:

[http://paste.ubuntu.com/949453/](http://paste.ubuntu.com/949453/)
(wanted to paste it, but doesn't look fine ;-)

---

### Post by darkod on 2012-04-27
You installed grub2 also the win7 boot partition. You can remove it with this:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

It should be fine after that.

---

### Post by haikon on 2012-04-27
I tried testdisk.

but wasn't sure what to do, because there is no option "Backup.."

should I choose 'Dump"??

_[http://media.cdn.ubuntu-de.org/forum/attachments/56/17/4276962-003testdisk.png](http://media.cdn.ubuntu-de.org/forum/attachments/56/17/4276962-003testdisk.png)_[]("http://ubuntuforums.org/showthread.php?p=11878677#post11878677")

---

### Post by darkod on 2012-04-27
I can't be 100% sure, but in this case the Rebuild BS option might be able to rebuild the boot sector.

If that doesn't work, the Boot-Repair is another option that I think might work. In the Advanced options it should have option to repair the partition boot sectors.

---

### Post by haikon on 2012-04-27
have to excuse me. the entry 'BackupBS' in testdisk was missing because I chose the wrong partition ;-)

so I choose the right one and restored the boot-sector.

then I re-installed Grub via doing auto-repair with bootrepair.

restart, everything is running fine ;-)

my log looks now this way:
[http://paste.ubuntu.com/949669/](http://paste.ubuntu.com/949669/)

thx for help!!

------------------CASE CLOSED--------------------

---

