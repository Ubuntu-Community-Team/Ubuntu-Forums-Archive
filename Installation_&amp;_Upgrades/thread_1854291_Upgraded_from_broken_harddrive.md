---
title: "Upgraded from broken harddrive"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by eddiemot on 2011-10-04
Morning Guys,

This is my first post ):P hi

I will give you a bit of background information as this may help.
I had windows 7 installed on a pc fitted with 2 harddrives, my main harddrive failed. So i decided to install Ubuntu. I sucessfully managed to do this by usb.

Then I noticed it was running slow so I checked the system montior and it said I only had 512 MB Ram installed. I checked my bios screen at start up and that says I have slot one 512MB slots 2 1024Mb slot 3 1024Mb.

I dont have the function to remap memory in the bios screen.

Please can you help out? I need ubuntu to recognise my ram.


Thanks

---

### Post by dino99 on 2011-10-04
check your MB doc to set your ram in the good slot order for identification. Its better to have the same ram sticks, so try without the 512 one. And check for new bios release too.

---

### Post by Grenage on 2011-10-04
You don't need to do anything, it just uses it.  I don't know what section you are looking at in System Monitor, but type this into a terminal, and post the results:

```
free -m
```

The *total* is the available memory.

```
grep MemTotal /proc/meminfo
```

Would also work.

---

### Post by eddiemot on 2011-10-04
home@XXXXX:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           496        481         14          0         13        162
-/+ buffers/cache:        304        191
Swap:         2492         12       2480

---

### Post by eddiemot on 2011-10-04
This is the screenshot of my system monitor

---

### Post by eddiemot on 2011-10-04
I have fixed my problem, i just changed the ram's round and everything is sorted.

Thanks for your help

---

