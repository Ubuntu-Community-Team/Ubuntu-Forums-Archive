---
title: "Should I optimize my SSD after installing Ubuntu ?"
date: 2018-11-21
forum: MINT
---

### Post by automate-stuff on 2018-11-21
should i follow the steps here: [http://goinglinux.com/articles/Optimize_Linux_For_SSD_Drive_en.htm](http://goinglinux.com/articles/Optimize_Linux_For_SSD_Drive_en.htm)


to optimize my SSD ? or should I leave it alone ?

---

### Post by oldfred on 2018-11-21
I would not use a link from 2013, unless updated. Things change a lot.

       cfq may be better for SSD
[https://www.phoronix.com/scan.php?page=article&item=linux-415-iosched&num=1](https://www.phoronix.com/scan.php?page=article&item=linux-415-iosched&num=1)
My 18.04 uses cfq:
fred@bionic-z97:~$  cat /sys/block/sda/queue/scheduler
noop deadline [cfq] 

I do most of this:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

You only want noatime. see this:
man mount
>        noatime
              Do  not  update  inode access times on this filesystem (e.g. for
              faster access on the news spool to speed up news servers).  This
              works  for  all  inode  types  (directories  too), so it implies
              nodiratime.


I do use a daily trim, but that is only for / (root) as if system totally crashes I plan a new install.
With trim, then old data is erased, and data recovery is not possible, so have good backup procedures.

Since my SSD is only for Ubuntu and I do multiple / (root) of 25GB on SSD, but data on HDD, I in effect over provision as I have not used all of SSD.

I do add a mount of tmpfs to fstab.

But newer SSD have lives similar to HDD, but not forever.
       
 [http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash](http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash)
SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead) 
    
Some hard drives last longer than others. Or whether SSD or HDD, you need backups.
       hard drive life 
[https://www.backblaze.com/blog/hard-drive-stats-for-q1-2018/](https://www.backblaze.com/blog/hard-drive-stats-for-q1-2018/)

---

### Post by automate-stuff on 2018-11-21
Very informative, thanks alot...I should Follow the Linux mint 19 guide....

Another quick question, Will the method in the Linux mint 19 link, work for all Ubuntu based OSes ?

---

### Post by howefield on 2018-11-21
Thread moved tot he "*MINT*" forum.

---

### Post by deadflowr on 2018-11-21
trim should already be enabled via systemd
look at 
```
systemctl status fstrim
```
should be set to run weekly.

(Looking at the systemd fstrim file at
/lib/systemd/system/fstrim.timer
it should show
```
[Unit]
Description=Discard unused blocks once a week
Documentation=man:fstrim

[Timer]
OnCalendar=weekly
AccuracySec=1h
Persistent=true

[Install]
WantedBy=timers.target
```

Though I'm not sure what mint does to thing like that.
But that's the default on Ubuntu. ((or at least Ubuntu 18.04, and I think 16.04 as well.)

---

