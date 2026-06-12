---
title: "Update manager failing,,,"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by fneergaard on 2011-10-26
I havnt started my old server for the first time in a year and I ran in to serious trouble.

I allowed the update manager to start and I must have been allowing the update to overwrite som files. 

First it seems ok, but the Update Manager is failing.

After shuting down the server I cannot start it up again:

Mountall is failing I think. Process (2560) is killed by abrt signal.

I am asked to enter the root password for maintenance. When I do so I get a root promt! What do I do next?

Ragards,

Frank

---

### Post by fneergaard on 2011-10-27
Please

---

### Post by fneergaard on 2011-10-27
Here is the full text when I boot:

init: ureadahead main process (2557)terminate with status 5
libudev: udev_monitor_new_from_netlink: error getting socket:Invalid argument
mountall:mountall.c:3304:Assertion failed in main: udev_monitor = udev_monitor.
new_from_netlink (udev, "udev")
init: mountall main process (2560) killed by ABRT signal
General Error mounting filesystems
A maintenance shell will now be started.
CONTROL-D wil terminate this shell and reboot the system.
Give root password for maintenance
(or type Control-D to continue):

Hope it helps

---

### Post by hakermania on 2011-10-27
Hello, please bump your thread only after 24 hours at least!

That's not such an rare problem when having to update an old system for so long. As I searched for this problem in Google I found out that the best solution is the usual one:
Create a live USB/CD so as to backup any important data and clean re-install a newer version of Ubuntu :)

---

### Post by fneergaard on 2011-10-27
Can I do so without loosing my data?

---

### Post by oldos2er on 2011-10-27
Which version of Ubuntu do you have installed?

---

### Post by fneergaard on 2011-10-31
I dont see ant version number!

Can I get that info from the root prompt?

Frank

---

### Post by raja.genupula on 2011-10-31
Hi man 

   Please give me the output of 
```
cat /etc/lsb-release; uname -a
```

---

### Post by fneergaard on 2011-11-08
Version 10.04

---

### Post by fneergaard on 2011-11-21
I gave up and installed 10.11 on top. Meaning that I think that I gave instructions to override all. Now I do not understand how some the old data has survived?

Can I delete all the old data during installation? Was thinking to fdisk, but didnt want to spoil something...

Regards

Frank

---

### Post by steve7777777 on 2011-11-21
I think you would have been better off staying with the 10.04 LTS - either fixing or re-installing.

---

