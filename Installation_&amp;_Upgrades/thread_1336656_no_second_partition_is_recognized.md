---
title: "no second partition is recognized"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by restless on 2009-11-24
Hey,
I just installed 9.10, and I partitioned the 60Gb hard drive of my laptop as such:

$ fdisk -l

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        7296    39070080    5  Extended
/dev/sda5            2433        7174    38090083+  83  Linux
/dev/sda6            7175        7296      979933+  82  Linux swap / Solaris


now linux is nicely running, but I can't see the second partitions as hard drives...
any idea why?

thank you
Lorenzo

---

### Post by lloyd_b on 2009-11-24
> **restless said:**
> Hey,
I just installed 9.10, and I partitioned the 60Gb hard drive of my laptop as such:

$ fdisk -l

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        7296    39070080    5  Extended
/dev/sda5            2433        7174    38090083+  83  Linux
/dev/sda6            7175        7296      979933+  82  Linux swap / Solaris


now linux is nicely running, but I can't see the second partitions as hard drives...
any idea why?

thank you
Lorenzo

Under Linux, you will *not* see anything like "Drive D" or the equivalent.  Instead, other partitions are "mounted" to subdirectories of the root ("/") filesystem.

One of two things probably happened - either that second partition is mounted (probably at "/home"), or no mount point was specified for it.

If you run the command "df" in a terminal window, you'll see something like the following:```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             24027656   2704532  20102588  12% /
udev                    253824       252    253572   1% /dev
none                    253824       148    253676   1% /dev/shm
none                    253824        76    253748   1% /var/run
none                    253824         0    253824   0% /var/lock
none                    253824         0    253824   0% /lib/init/rw
/dev/sda4             43129672  21185896  19752912  52% /home
```As you can see from this, I have one partition of my drive (/dev/sda3) mounted as "/", and a second partition of that drive (/dev/sda4) mounted at "/home".

Lloyd B.

---

### Post by restless on 2009-11-24
Lloyd,

thanx for your message.
I've been using ubuntu for a while, so i wasn't expecting a d: drive ;)

thing is that I can see the partition
/dev/sda1             19228276   2167600  16083928  12% /
udev                    771256       280    770976   1% /dev
none                    771256      1200    770056   1% /dev/shm
none                    771256        88    771168   1% /var/run
none                    771256         0    771256   0% /var/lock
none                    771256         0    771256   0% /lib/init/rw
/dev/sda5             37491592   2136972  33450116   7% /home

and I selected /home when i formatted the HD, thing is that this partition doesn't appear in the list of available drives. I can see if i go up to /home, but is not int the "places" and I cannot find it as an hard drive.
is that normal?

thing is that with 9.04 I had the 2 hard drives listed...hmm
anyways..

thanx
Lorenzo

---

