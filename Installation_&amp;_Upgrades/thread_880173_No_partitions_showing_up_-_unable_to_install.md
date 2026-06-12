---
title: "No partitions showing up - unable to install"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by peacechicken on 2008-08-04
I tried to be nice and upgrade my friend's computer from 7 to 8.04 and somewhere in the process the upgrade never successfully finished. So I burned the 8.04 ISO onto a disc and tried doing a fresh install and everytime it gets to the Partitioning step I get stuck. No partitions are showing up, and the button to make a new one isn't clickable. So now she's totally stuck, aside from running off the CD.

I went into the BIOS settings and the IDE harddrive is recognized, and I also ran the "integrity check" via the install CD so I don't understand what the problem is, it doesn't seem to be hardware-related.

I've been Googling for a while and haven't found any solutions. Here's what I get when I run "df -h":
[INDENT]```
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 506M   17M  490M   4% /lib/modules/2.6.24-19-generic/volatile
tmpfs                 506M   17M  490M   4% /lib/modules/2.6.24-19-generic/volatile
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   36K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
tmpfs                 506M   20K  506M   1% /tmp
gvfs-fuse-daemon      506M   35M  471M   7% /home/ubuntu/.gvfs
```[/INDENT]

How do I get the partitioner to recognize the harddrive? Since that *seems* to be the problem, though I could be wrong...

---

### Post by Pumalite on 2008-08-04
Have you tried: 'Manual'?

---

### Post by peacechicken on 2008-08-04
> **Pumalite said:**
> Have you tried: 'Manual'?

I didn't see that option anywhere..?

---

### Post by Pumalite on 2008-08-04
Burn a new CD (I assume you are using the Live CD). Do md5sum. Burn at 4x or less on CD-R. Do not use CD-RW. Check CD integrity before install

---

