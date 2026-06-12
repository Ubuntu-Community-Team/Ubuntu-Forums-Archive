---
title: "Latest update error - .udevdb or .udev presence implies active udev.  Aborting MAKEDE"
date: 2009-11-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-11-12
Is this ok or do I need to do soemthing. Not seen this before ;).

I'm chrooted doing the update. I guess thats why, not sure.

```
The following packages will be upgraded:
  hdparm powermgmt-base
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 96.2kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com lucid/main hdparm 9.15-1ubuntu5 [84.2kB]
Get: 2 http://gb.archive.ubuntu.com lucid/main powermgmt-base 1.30+nmu1ubuntu1 [12.0kB]
Fetched 96.2kB in 0s (242kB/s)      
(Reading database ... 160652 files and directories currently installed.)
Preparing to replace hdparm 9.15-1ubuntu4 (using .../hdparm_9.15-1ubuntu5_amd64.deb) ...
Unpacking replacement hdparm ...
Preparing to replace powermgmt-base 1.30+nmu1 (using .../powermgmt-base_1.30+nmu1ubuntu1_amd64.deb) ...
Unpacking replacement powermgmt-base ...
Processing triggers for man-db ...
Setting up hdparm (9.15-1ubuntu5) ...

Setting up powermgmt-base (1.30+nmu1ubuntu1) ...
.udevdb or .udev presence implies active udev.  Aborting MAKEDEV invocation.
```

---

### Post by zika on 2009-11-12
Same here```
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com lucid/main powermgmt-base 1.30+nmu1ubuntu1 [12.0kB]
Fetched 12.0kB in 0s (47.5kB/s)     
(Reading database ... 136405 files and directories currently installed.)
Preparing to replace powermgmt-base 1.30+nmu1 (using .../powermgmt-base_1.30+nmu1ubuntu1_amd64.deb) ...
Unpacking replacement powermgmt-base ...
Processing triggers for man-db ...
Setting up powermgmt-base (1.30+nmu1ubuntu1) ...
.udevdb or .udev presence implies active udev.  Aborting MAKEDEV invocation.

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Current status: 0 updates [-1].
```

---

### Post by Kevbert on 2009-11-12
Same for me. Nothing unusual in the log files.

Edit: Just before reboot I had an error message displayed, but didn't get a chance to read it. Can't find it in logs.

---

### Post by philinux on 2009-11-12
Looks benign according to this.

[http://linux.derkeiler.com/Mailing-Lists/Debian/2009-10/msg00438.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2009-10/msg00438.html)

---

### Post by seeker5528 on 2009-11-12
> **philinux said:**
> Looks benign according to this.

[http://linux.derkeiler.com/Mailing-Lists/Debian/2009-10/msg00438.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2009-10/msg00438.html)

Here is more info in makedev, [Link](http://linux.about.com/od/commands/l/blcmdl8_MAKEDEV.htm).

Before udev came along makedev was used to create the device links in /dev, if udev is not installed for some reason, then the system should fall back to using makedev so the majority of hardware still works.

Checking for udev and aborting the use of makedev if it is found is a normal thing.

How complete and functional things are without udev is another question.

Later, Seeker

---

