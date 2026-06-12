---
title: "Problems installing 8.10"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by tbird6820 on 2010-08-18
I have a HP pavilion 526x with 1gig of memory with a 80gig western digital enhanced ide HD as my primary master, model # WD800eb-00DJF0 and a Sony cdrw as my secondary master.

I created a primary dos partition and formatted the drive, installed ubuntu 8.10 desktop edition cd, got to the partition manager and selected the entire disk.

It verified, then following partitions are going to be formatted:
partition #1 of SCSI 1 (0.0.0) (sda) as ext 3
partition # 5  of SCSI 1 (0.0.0) (sda) as swap.

Loads fine, I restart get to log in and enter password and get all I get is a blank screen with just my mouse pointer?

If I disconnect the WD HD and connect it to my HD that has windows xp pro on it, no problems booting.

---

### Post by sanderd17 on 2010-08-18
can you start in a shell mode? 

When ubuntu asks you to log in, press ctrl+alt+F1, log in ans type the command 
```

startx

```

check what errors you see (or where it hangs) on the screen and tell about them here.

---

### Post by tbird6820 on 2010-08-18
ok here it is.

Fatal server error:
server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again

Invalid MIT-MAGIC-1 keygiving up.
xinit:  Interrupted system call (errno 4):  unable to connect to X server
xinit:  No such process  (errno 3) :  Server error.

---

### Post by snowpine on 2010-08-18
8.10 has reached its "end of life" and is no longer supported. Rather than waste time troubleshooting your 8.10 install, I recommend test-driving the current release (10.04).

---

### Post by sanderd17 on 2010-08-18
O, I didn't know 8.10 wasn't supported anymore, I started with 8.04 and it seemed like yesterday.

In that case, you better use 10.04.

---

### Post by tbird6820 on 2010-08-18
I was trying to load 8.10 to upgrade to 10.04 so I'll download the 10.04 iso and try that.

---

### Post by Zorgoth on 2010-08-18
8.10 is not an LTS, so it loses support pretty quickly - I believe 8.04 is still supported until April 2011, as an LTS, but since 10.04 is a new LTS with a lot of upgrades, and will be supported through April 2013, it is a better choice.

---

### Post by tbird6820 on 2010-08-18
Thanks for the help... loaded 10.04 no problems. solved

---

### Post by mörgæs on 2010-08-18
Good. Please mark the thread 'solved'.

You can see the life span of various releases here:
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by tbird6820 on 2010-08-18
Thanks again!

---

