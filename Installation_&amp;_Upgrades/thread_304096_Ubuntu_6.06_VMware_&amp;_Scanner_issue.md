---
title: "Ubuntu 6.06 VMware &amp; Scanner issue"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by yeseanul on 2006-11-21
Hello,

I am a Linux newbe, and Ubuntu (6.06) is the first distro that a actually install and plan on using for a very long time (for some time now, I have played around with live distros, like Knoppix, DSL, Puppy, Ubuntu, and even installed Mandrake, Slakware and Red Hat).
The thing is that I just do not like dual-booting. And because I need to use 3 pieces of software that I can t at the moment use on Linux, I have to consider a Win environment. The best solution for me is Virtual Machines (when I was using only Win, I tried some Linux distros using VMware Workstation).
To make things easier to understand, I need to say that I have 2 problems.

1. I installed VMware Workstation (using the .rpm downloaded from the web site, after converting it to .deb using ”alien”). The installation was successful. BUT, in a terminal, when I execute ”vmware”, this is what I get:
```
/usr/bin/vmware: line 85: /etc/vmware/locations: No such file or directory
/usr/bin/vmware: line 177: /lib/wrapper-gtk24.sh: No such file or directory
/usr/bin/vmware: line 177: exec: /lib/wrapper-gtk24.sh: cannot execute: No such file or directory
```
/usr/bin/vmware: line 85 is:
```
db_load_from_stdin "$dbvar" < "$dbfile"
```
/usr/bin/vmware: line 177 is:
```
exec "$vm_db_answer_LIBDIR"'/lib/wrapper-gtk24.sh' \
```
I am very confused and frustrated...:( :???: :-k 

2. I have a ”Mustek 1200 UB Plus” scanner. The result for ”lsusb” is:
```
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 05d8:4002 Ultima Electronics Corp. Artec Ultima 2000 (GT6801 based)/Lifetec LT9385 Scanner
Bus 002 Device 003: ID 10ac:10c6 Honeywell, Inc.
Bus 002 Device 001: ID 0000:0000
```
And when I run ”XSane”, I get this error:
```
Failed to open device gt68xx:libusb:002:002:
Invalid argument.
```



I appreciate all the help that I can get.
Thank you.

Yeseanul

---

### Post by yeseanul on 2006-11-22
Somebody?
:?:

---

