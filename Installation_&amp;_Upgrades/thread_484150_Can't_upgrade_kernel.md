---
title: "Can't upgrade kernel"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by happysmileman on 2007-06-25
I've just installed Kubuntu and clicked to install the 64 updated packages available...

It went well until it got to the kernel itself, then crashed... I tried again(deleting the relevant ".deb" files in "/var/cache/apt/archive" first incase they downloaded bad) and I got the following output:

```
Preconfiguring packages ...
(Reading database ...
dpkg: serious warning: files list file for package `linux-image-2.6.20-16-generic' missing, assuming package has no files currently installed.
75275 files and directories currently installed.)
Preparing to replace linux-image-2.6.20-16-generic 2.6.20-16.29 (using .../linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb) ...
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
The directory /lib/modules/2.6.20-16-generic still exists. Continuing as directed.
Done.
Unpacking replacement linux-image-2.6.20-16-generic ...
```

And it hangs on 1% of upgrade... Anyone know what I need to do... I would appreciate a quick reply, and I really don't want to reinstall since I just set up all my settings and all

---

### Post by Pumalite on 2007-06-25
You can boot with your old kernel, can't you?.

---

### Post by happysmileman on 2007-06-25
Yeah I can... And upgrade worked just now... No idea what fixed it... Nothing i previously tried fixed it and then it just worked as normal... Weird

---

### Post by Pumalite on 2007-06-25
Glad you got it fixed. Congrats.

---

