---
title: "New hard disk - problems ..????"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by wiresquire on 2006-07-14
Hi

I just upgraded my laptop with a new hard disk. And so I have a brand new install of 6.06. The HD is a Seagate ST980825A 7200rpm.

Things seem a little quicker ;) but I'm a bit worried. The activity (read/write) light is on for 55 secs then turns off for 5 secs. This happens very often. And when I am not even doing anything.

There's no unusual messages in dmesg or /var/log/messages

Is there anyone who can tell me how to work out what's going on?

TIA
ws

---

### Post by wiresquire on 2006-07-14
Admins: I think this may belong in the hardware section...

More investigation...

1. There's no processes obvious sitting in top that co-incides with the activity.

2. I put the system monitor on my tray panel and set preferences to show the reads and writes. Strange, but the h/d activity lights up for the 55s without the monitor showing any read or write!!

3. The activity light goes back to 'correctly' indicating if there is actually any read/write disk access.


I'll have to see if this behaviour happens in Winblows as well. 

My partitions look like:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        2805    12289725    5  Extended
/dev/hda3            2806        3442     5116702+  83  Linux
/dev/hda4            3443        9729    50500327+  83  Linux
/dev/hda5            1276        2550    10241406   83  Linux
/dev/hda6            2551        2805     2048256   82  Linux swap / Solaris

```
hda5/6 are the part of the extended partition hda2.
hda3 is where ubuntu lives, and hda4 is basically for data.
hda1, 4 and 5 are mounted and there seems to be no errors anywhere in logs.

Appreciate if anyone has seen this before or has any ideas or opinions on it. Is it defective? 

TIA
ws

---

### Post by wiresquire on 2006-08-02
Just in case anyone runs into the same problem, I returned it to the supplier who diagnosed it as a fault. And replaced it :D 

There's a very similar type of problem (and result!) [here](http://forums.whirlpool.net.au/forum-replies-archive.cfm/544345.html).

---

