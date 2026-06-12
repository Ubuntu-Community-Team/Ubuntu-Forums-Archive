---
title: "Intallation  and upgrades"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by zandakers on 2008-07-10
[B][COLOR="Blue"]Hi, i've been using Ubuntu for about three years now, and i usually do a dual boot with Windows XP, but i seem to have a problem with this new HP Vista Home Premium computer....when the installation comes to the point where it does the partitioning it tells me that i can not  as it is illegal............i don't want to use the entire HD as i want to keep Windows for gaming purposes. can someone please help...............i want to run Ubuntu along side of Windows.

Maybe this is just a problem with HP computers.

Thanks

[/COLOR][/B]

---

### Post by SkonesMickLoud on 2008-07-10
If it is a new computer, partitioning it may void your warranty, but it is certainly not illegal.  It is after all, your property.

_Try PmDematagoda's advice first!_

You could boot to the Ubuntu LiveCD, but select the "Try Ubuntu" option.  When it is all booted up, go to Systems >> Admin >> GParted and do your partitioning there.

Failing that, you could download [GParted](http://gparted.sourceforge.net/) itself, burn it to a disk as an .iso, boot to it and do your partitioning there.

---

### Post by PmDematagoda on 2008-07-10
You are advised to not partition a Vista partition using the Ubuntu partitioner since it has been known to cause problems, so you should first partition the Vista partition as needed using Vista's own partition manager and then install Ubuntu on the newly created partition.

---

