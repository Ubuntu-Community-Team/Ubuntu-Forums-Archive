---
title: "Install 6.06 LTS hangs on Supermicro 5013C-MT"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by vaplu on 2006-11-10
I was installing Ubuntu Server 6.06 LTS on a Supermicro 5013C-MT server (with Marvell Sata Hostbased RAID controller), but the setup 'hangs after the "hostname" input window, progressbar: "Detecting all other hardware" and a quick progressbar with something about languages.

But maybe the problem already started with the kernel:
```
Uncompressing Linux... Ok, booting the kernel.
[17179604.864000]ata1: failed to set xfermode, disabled 
```
The installer starts, so the above message shouldn't be that bad.

Then at some point the installer 'hangs'. The last thing that is shown in dmesg:
```
[17179770.544000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17179770.544000] SGI XFS Quota Management subsystem
```

Last lines from syslog:
```
Nov 10 20:03:21 partman:   Reading all physical volumes. This may take a while...
Nov 10 20:03:21 partman:   No volume groups found
Nov 10 20:03:51 init: ^MStarting pid 2065, console /dev/vc/2: `/bin/sh`
```

(all logs typed by hand, so hope i did that right)

Maybe somebody with a clue where to search for a solution? (tried google and this forum ofcourse, already found someone with the same problem: [http://people.ubuntu.com/~fabbione/irclogs/ubuntu-boot-2006-06-21.html](http://people.ubuntu.com/~fabbione/irclogs/ubuntu-boot-2006-06-21.html) , but no solution)

---

### Post by vaplu on 2006-11-12
little kick?

---

### Post by vaplu on 2006-11-15
little kick #2 ?

([https://launchpad.net/distros/ubuntu/+bug/71535](https://launchpad.net/distros/ubuntu/+bug/71535))

---

### Post by vaplu on 2006-11-26
again ... little kick.

---

