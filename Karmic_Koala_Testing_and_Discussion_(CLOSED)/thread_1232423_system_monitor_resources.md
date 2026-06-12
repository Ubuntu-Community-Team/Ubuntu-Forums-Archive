---
title: "system monitor resources"
date: 2009-08-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xzero1 on 2009-08-05
Is it just me or is the total memory incorrectly reported? I get 2.7GiB which happens to be the used space on my Karmic partition. I have 4G installed using 512M for IGP.

---

### Post by aamukahvi on 2009-08-05
> **xzero1 said:**
> Is it just me or is the total memory incorrectly reported? I get 2.7GiB which happens to be the used space on my Karmic partition. I have 4G installed using 512M for IGP.

If you're on 32-bit then you might already be seeing only 3GB or 3,5GB. Then there's that IGP. Finally, 3GB != 3GiB.

So that might be correct.

---

### Post by taavikko on 2009-08-05
It's working correctly here,

what does "free -tom ; df -h" say?

and like aamukahvi said, what does "uname -m" say?

---

### Post by xzero1 on 2009-08-05
Its the same in Jaunty but it sounds low so I will investigate further. I just want to make sure I am using all the ram I have installed. I am running Ubuntu 64 bit.
Thanks for the feedback.
Note that the following are Jaunty 64 values:

```
free -tom
             total       used       free     shared    buffers     cached
Mem:          2732        796       1935          0         48        258
Swap:         5820          0       5820
Total:        8552        796       7755
``````
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              92G   15G   73G  18% /
tmpfs                 1.4G     0  1.4G   0% /lib/init/rw
varrun                1.4G  216K  1.4G   1% /var/run
varlock               1.4G     0  1.4G   0% /var/lock
udev                  1.4G  220K  1.4G   1% /dev
tmpfs                 1.4G   76K  1.4G   1% /dev/shm
lrm                   1.4G  2.5M  1.4G   1% /lib/modules/2.6.28-14-generic/volatile
tmpfs                 1.4G  2.0M  1.4G   1% /tmp
/dev/sr0              695M  695M     0 100% /media/cdrom0

``````
uname -m
x86_64
```

---

### Post by xzero1 on 2009-08-05
Now it reports 3.4GiB which sound about right. I had to enable memory hole remapping which I had not done before because it is a relatively new motherboard and I only had 2GiB memory in my old mb. 

Problem solved.:)
Thanks for the help.

---

