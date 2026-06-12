---
title: "newbie getting i/o read error on hdd"
date: 2005-11-01
forum: Installation &amp; Upgrades
---

### Post by tatt2d26 on 2005-11-01
i've tried to install this thing like 6 times on my amd64 +2800 machine running xp pro....i used a new partition with 32 gB i let the auto install do my partitioning and every time i get the error "buffer i/o error on device hdd, logical block (and the blocks change each time)" after 5 errors it unpacks a crapload of stuff and tries again...over and over and over this happens until it finaly sends me to the packet mangmt util....any ideas>?

---

### Post by poptones on 2005-11-01
Is device hdd a cdrom or a hard drive? It sounds like it could be a bad CD, but if hdd is a hard drive it's also likely you got a failing hard drive.

---

### Post by tatt2d26 on 2005-11-01
its a brand new w/d 80g eide...i installed from a oem cd not a burned image also...i wouldn't think the cd would be bad but who knows

---

### Post by spblueboi88 on 2005-11-02
WIth my experience from WDC, I would say a bad HDD is a definate posibility. I had went through five 80 gig drives under warranty only to have the last fail and have them upgrade me to a new 120 gig drive for free.

But yeah, maybe run some diagnostics on your drive. I'm sure that it came with one of those data lifeguard tools disk. Run it and see what happens.

---

### Post by poptones on 2005-11-03
If you *just* installed the drive it is also possible the cable isn't properly seated or is otherwise defective.

I suggest you run a thorough check of the drive. Boot from the live cd to a command line, mount the drive, and run this command:

dd if=/dev/zero of=/dev/**yourdrive** 

Let it run (probably an hour or two) until it reports it's done. If it completes without reporting a problem, try installing again.

---

### Post by tatt2d26 on 2005-11-14
hdd= my fourth drive hd-d (d being the letter for 4) after getting a new distro cd i installed w/ no problems 4th drive is my cd rom drive...i\o error was refrencing the cd i think... bad disk...no worky....new disk....kikin hoary

---

