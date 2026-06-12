---
title: "Moving everything except &quot;/home&quot; to new partition?"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by beow on 2007-04-02
I have these main partitions on my laptop HD.

```
$ df | grep hda
/dev/hda2             16208992   5945744   9604584  39% /
/dev/hda1             15361888   9839416   5522472  65% /media/hda1
/dev/hda3              6965536    131228   6480480   2% /media/hda3

```

/media/hda1 is the Windows partition

/media/hda3 is a new "un-touched" partition:

```
$ sudo ls -laR /media/hda3
Password:
/media/hda3:
total 24
drwxr-xr-x  3 root root  4096 2007-04-02 12:33 .
drwxr-xr-x 10 root root  4096 2007-02-27 09:20 ..
drwx------  2 root root 16384 2007-04-02 12:33 lost+found

/media/hda3/lost+found:
total 20
drwx------ 2 root root 16384 2007-04-02 12:33 .
drwxr-xr-x 3 root root  4096 2007-04-02 12:33 ..
```

(Don't know what the 131 MB, from df above, are allocated to since it can't be seen by the ls command above)

Now, I want to use my old large partition as a /home partition and move the system (/) to the new 7 GB partition (which is /media/hd3 today). Or install feisty on the new partition and somehow remove everything but /home from my large partition. BTW the installed system is dapper.

I've read how to move the /home to its own partition, but it doesn't make sense for me to move /home to the 7 GB partition and then have the system on the large 16 GB partition. I want it the other way around.

Any suggestion how to go about this?

Cheers :)

---

### Post by dcstar on 2007-04-03
> **beow said:**
> 
.........
I've read how to move the /home to its own partition, but it doesn't make sense for me to move /home to the 7 GB partition and then have the system on the large 16 GB partition. I want it the other way around.

Any suggestion how to go about this?

Cheers :)

Easiest thing may be to boot off a CD with **gparted** on it (like the 5.10 Live CD) and resize your existing system partition down to a reasonable size.

You could then resize/expand your other partitions to suit your requirements.

---

### Post by beow on 2007-04-03
> **dcstar said:**
> Easiest thing may be to boot off a CD with **gparted** on it (like the 5.10 Live CD) and resize your existing system partition down to a reasonable size.

You could then resize/expand your other partitions to suit your requirements.

Thought about that a couple of minutes after posting... That is what I will do. Thanks, David.

---

