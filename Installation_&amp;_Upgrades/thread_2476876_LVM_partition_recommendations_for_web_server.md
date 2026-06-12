---
title: "LVM partition recommendations for web server?"
date: 2022-07-10
forum: Installation &amp; Upgrades
---

### Post by edflecko on 2022-07-10
I like the idea of using individual partitions for web servers. 

I want to use LVM for a new web server installation so some partitions (such as /var for log files, etc.) could be expanded if they run out of space. I'm looking for some recommendations.

1.) Is it overkill to create all typical partitions (i.e., /, /boot, /swap, /var, /tmp, /usr, etc.) within the logical volume during installation or should I only create some of the partitions, that I think *might* run out of space and need to be expanded (i.e., /var) within the logical volume?

2.) For potential, future partition resizing, does it make any difference in which order the partitions need to be created?

3.) Does LVM allow you to expand partitions by a % rather than by Mb, Gb, etc.?

Thank you!

Ed

---

### Post by TheFu on 2022-07-10
> **edflecko said:**
> I like the idea of using individual partitions for web servers. 
Why?  Partitions are a huge hassle and after 25+ yrs running servers, I've never, ever, guessed correctly about the amount of storage needed for any specific location.
However, having separate mounts for different locations DOES make sense from a security standpoint.  Certain areas should allow executable, setuid, or any scripts and others shouldn't allow devices.  Mount options let us control those things.

> **edflecko said:**
> 
I want to use LVM for a new web server installation so some partitions (such as /var for log files, etc.) could be expanded if they run out of space. I'm looking for some recommendations.

The key to LVM is to only allocation storage for 2-3 months at a time and to leave as much unallocated as possible for use in snapshots for backups and future needs that cannot be known ... until the future.

Do not plan on spanning LVs across different storage devices. That's asking for failure and a really, really, bad day.


> **edflecko said:**
> 
1.) Is it overkill to create all typical partitions (i.e., /, /boot, /swap, /var, /tmp, /usr, etc.) within the logical volume during installation or should I only create some of the partitions, that I think *might* run out of space and need to be expanded (i.e., /var) within the logical volume?

Sometimes it is. Other times it isn't.  Just depends.  An LV is where the file system is laid down. Think of them as smart partitions. You'll need a separate LV for each file system and mount you plan to manage separately.  Maybe read up on LVM, PVs, VGs, and LVs, before you do anything more.  The manpages for each command is quite excellent, with all the options AND with all the caveats about using each option.  Reading the manpages - COMPLETEY - for LVM is mandatory so you don't get into trouble.


> **edflecko said:**
> 
2.) For potential, future partition resizing, does it make any difference in which order the partitions need to be created?


Partitions?  Huh?  While would you have more than 1 partition for everything under LVM management?  Are you trying to make more work?  When you see multiple devices and/or multiple partitions used in LVM and not used for expansion 3 yrs later, you are seeing poor planning by the admin.

> **edflecko said:**
> 
3.) Does LVM allow you to expand partitions by a % rather than by Mb, Gb, etc.?


LVM doesn't work with partitions.  That's a fundamental understanding thing to be resolved.  We can use lvextend with a %, MB and GB, if we like.  I have to say that I've ***never*** used the % or 100%FREE options, unless I was trying to show what a lazy admin would do in a lesson for how NOT to use LVM.  I've used MB only for toy and trial "play" areas to test LVM techniques that I haven't used previously. Typically, I use +5G at a time when expanding data areas.

Search these forums for example outputs from pvs, vgs, and lvs commands, so you can see what is really used.  But also note that most posts here are for desktops, not servers.  I've also posted an LVM diagram in these forums before. Due to forum/browser issues, I cannot just link that diagram here (or I would). Sorry.  If you visit my profile, go into the album, there should be a fairly simple block with green and blue squares that is labeled for how different parts of disks, partitions, PV, VG, and LVs are related in a simple configuration.

When I'm doing storage layouts, I'm mainly thinking about backup and restore techniques, assuming sufficient space for any need is available.  I try to leave at least 20% of the PV/VG unused and on most systems, I'm closer to 50% unused for the OS areas.  Data is different. The LVs on those are usually fit inside 4TB PVs (partitions) with each PV, VG, and LV being sized for very little expansion - just enough for a few months of use so we can get budget and additional storage purchased for the server (or the NAS).  2 very different goals, but mainly to avoid surprises at the last minute without having some trigger to get management.

---

### Post by Impavidus on 2022-07-11
On some recent releases of Ubuntu, the /lib, /sbin and /bin directories have been replaced by symlinks to /usr/lib, /usr/sbin and /usr/bin. As /lib, /sbin and /bin have the tools needed in single-user mode (including the tools needed to mount filesystems), this means that /usr must be on the root filesystem. There may be a way to avoid this.

---

### Post by TheFu on 2022-07-11
What goes where on Linux is spelled out in the *Linux File System Hierarchy Standards*.  In the old days, it was common for everything in /usr/ to be on NFS storage.  Only /etc/ and /var/ and /bin/ had to be local to boot the OS, basically single user runlevel. Everything else would be on network storage.  

Systemd removed the idea if runlevels, which were built up in an additive way.  Runlevel 3 would do everything that Runlevel 1 and 2 had first, then add the specific stuff in /etc/rc3.d/  rc3 was multi-user, but without any GUI.  This all worked nicely for 30+ yrs, before systemd.  Simple, elegant, easy to understand.  The systemd guys thought they knew a better way. Have each task know it's dependencies and let the computer figure out the best order to start things.  That is a great idea, when it works.  It is hard to troubleshoot, however, since the startup order isn't controlled by the admin. It is controlled by the systemd dependency ordering software.  In practice, we humans still think in terms of perhaps 4 major events as dependencies for each of the daemons we start, which can lead to many programs all being started 
a) after the local file systems are mounted
b) after networking is full up
c) after network file systems are mounted
d) last

Last is when we used to run /etc/rc.local, so that is where most custom daemons would be dropped.  Server applications would be run after "c" - all the network storage was mounted ... so things like apache and nginx and the dbms would startup then with the dbms starting just prior to the web servers.  Each runlevel had 98 "slots" for ordering when things in that runlevel would start, controlled with a simplistic numeric order that was very easy to understand just by looking at a directory listing.  With systemd, I bet there is some tool which will spell out the startup order based on all the "unit files" in /etc/systemd/ ... I just don't know what that command is.  
```
sudo systemctl status
```
and 
```
sudo systemctl list-dependencies 
```
are NOT the correct answer. Neither is 
```
 systemd-analyze  {whatever}  
```
Just want a text output tree that shows which unit files are dependent on others.

---

