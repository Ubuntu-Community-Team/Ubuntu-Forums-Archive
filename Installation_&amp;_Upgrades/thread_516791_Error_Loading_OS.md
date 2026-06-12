---
title: "Error Loading OS"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by zacdl on 2007-08-03
I tried to install the latest Server edition of Ubuntu. 
After ripping the disk off I did the disk check- no problems.

Seemed to install fine, but when it rebooted at the end it said no OS detected.

I thought the boot loader didn't get installed properly, so then I just did a rescue option and reinstalled it (It DID see the install I just did BTW), rebooted again and it still didn't work.

BIOS settings are set to boot from the Hard Disk. Tried the grub-install command on sda1 (If I remember the name of the drive correctly) and it said it completed with no errors. Same thing.

What could be causing this?

---

### Post by ccalvinfowler@aol.com on 2007-08-03
how many hard drives do you have

---

### Post by zacdl on 2007-08-03
> **ccalvinfowler@aol.com said:**
> how many hard drives do you have

Two, it found both, I just installed it on the first.

---

### Post by Pumalite on 2007-08-03
Post specs. Post fdisk -l(smallL)

---

### Post by ccalvinfowler@aol.com on 2007-08-03
that is the problem.  you must unplug one , install ubuntu or whatever linux distro, then after restart it will work fine.  after this you can replug second hard drive.  it took me the longest tme to figure this out as i had the same problem

---

### Post by ccalvinfowler@aol.com on 2007-08-03
let me know if this works for you.

---

### Post by zacdl on 2007-08-03
> **Pumalite said:**
> Post specs. Post fdisk -l(smallL)

It's a P4 system. 1GB RAM. The hard drives are plugged into a RAID card which is mirroring them.


Whenever I go into rescue mode, it does give me these devices to use as my root file system:
/dev/sda1
/dev/sda2
/dev/sda5
/dev/sdb1
/dev/sdb2
/dev/sdb5
I chose the first.

fdisk-l gives me for /dev/sda
/dev/sda1 (boot) Start=1 End=4689 ID=83 System=Linux
/dev/sda2 Start=4690 End=4865 ID=5 System=Extended
/dev/sda5 Start= 4690 End= 4865 ID=82 System=Linux Swap/Solaris

Then an exact duplicate of that is on /dev/sdb, just replacing the above with "sdb" rather than "sda".

HTH

> **ccalvinfowler@aol.com said:**
> that is the problem.  you must unplug one , install ubuntu or whatever linux distro, then after restart it will work fine.  after this you can replug second hard drive.  it took me the longest tme to figure this out as i had the same problem
Even with a mirror?

---

### Post by Pumalite on 2007-08-03
[http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

---

### Post by zacdl on 2007-08-03
> **Pumalite said:**
> [http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

That's for software RAID, though. My card is doing all the work, but is the problem the way this is RAIDing itself?

---

### Post by Pumalite on 2007-08-03
You are right; Ubuntu does support hardware Raid. I have no experience in that though. ( not much in software Raids either).

---

### Post by ccalvinfowler@aol.com on 2007-08-03
All that other stuff is fne and dandy, unplug second HD and it will work perfectly for you.  yOU CAN PLUG IT BACK IN LATER.

---

### Post by zacdl on 2007-08-06
Alright, will give that a shot, thanks!

---

### Post by zacdl on 2007-08-06
Seems to have worked, but is Ubuntu Server not a GUI interface?

---

### Post by ccalvinfowler@aol.com on 2007-08-06
No, Ubuntu server does not come with a GUI, I originally installed that on my Desktop.  Since I am new to linux, I need to be able to visualize what i am doing.  Someone left me a post that shows how you can install a gui. let me find it and i'll post the link

---

### Post by Pumalite on 2007-08-06
sudo apt-get install gnome-desktop ( or KDE-desktop)

---

### Post by merlinus on 2007-08-06
If you use aptitude instead of apt-get, it will be easier to uninstall if you decide you want xfce or kde instead.

```

sudo aptitude update && sudo aptitude install gnome-desktop

```-merlin

---

