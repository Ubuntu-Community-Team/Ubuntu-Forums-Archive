---
title: "fsck failed help??"
date: 2005-04-20
forum: Installation &amp; Upgrades
---

### Post by mitchellb11 on 2005-04-20
when booting it starts booting up then it gets a error

> /ect/init.d/rcs:line 230: 803 buss error - fsck $spinne force
-T -t $roottype $rootder
fsck failed . please repair manually and reboot .please note
the root file system is currently mounted read only. to remount it read write:
mount -n -o remount,rw /
control -D will exit from this shell and reboot the system
press enter for maintenance
or type control -D for normal startup


what do i do to fix it so it will boot up and run??
thanks for you help

---

### Post by ssam on 2005-04-20
fsck is the File System CHecker. it checks that there are no errors on a disk, and repairs them if it finds any.

to run it manually at the prompt type

```
fsck -y
```

this will check the disk, and fix anything it find wrong. the '-y' option means that it will not ask you whether you want to fix each individual propblem, just assume that you would answer yes to everything.

---

### Post by mitchellb11 on 2005-04-21
ok thanks but i wiped it everything and just installed the hoaty version thanks anyways :)

---

