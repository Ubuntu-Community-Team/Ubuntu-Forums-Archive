---
title: "plymouth and burg"
date: 2011-06-20
forum: Installation &amp; Upgrades
---

### Post by waterloo2005 on 2011-06-20
```
$ plymouth-manager
Traceback (most recent call last):
File "plymouth-manager.py", line 23, in <module>
main.PlymouthManager()
File "/usr/share/plymouth-manager/src/main.py", line 148, in __init__
if value == funcmain.getCurrentRes():
File "/usr/share/plymouth-manager/src/funcmain.py", line 34, in getCurrentRes
tmpBuf = open("/etc/default/" + hwinfo.getBoot(), "r")
IOError: [Errno 2] no such file or directory: '/etc/default/burg'
```
I click that icon about burg . But I do not use burg.
Now I can not start plymouth-manager .
How to do with it ? 
Thanks

---

### Post by rvboutin on 2011-07-04
Hi,
Exactly the same problem for me, I have tried uninstall via Software Centre or Synaptic Manager, does not do anything...
Annoying!!! Why is the uninstall not cleaning the parameters??
Cheers,
Rv

---

### Post by FiveDiamonds on 2011-11-06
In Terminal:

gedit ~/.plymouth-manager.cf

change "BOOT_LOADER=burg" to equal whatever boot loader you are using.

---

### Post by bluexrider on 2011-11-06
Did you use the WAG method for that solution?

---

### Post by bluexrider on 2011-11-06
Boot into a Live CD/DVD and then download the Boot Repair.

Follow these directions

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

