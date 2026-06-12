---
title: "root directory full - disk usage analyser"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by aBitLater on 2008-02-02
Regarding my fresh new install on my laptop:

Disk Usage Analyzer, at the top of the tree "/" (root)  is showing my usage with a red bar that says "100%".  the size says, "3.6GB" with 20 items

I partitioned root to have 15 GB.  

Also, I went to nautilus, right-clicked the 'filesystem' icon and the permissions show an 'unknown' owner

Except for a seemingly innocuous error at boot, things are running fast and smooth, so I'm lost on the 100% bar... is / an auto-expanding partition? (ok, yes, I'm a complete newb) :)

my /usr partition was set to 10GB on install.  DUA was showing 57% full when I started this email, and after scanning 3 or 4 more times, it has gone to 70% and is now at 82%.  root partition remains at 100%

---

### Post by taurus on 2008-02-02
Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

p.s.  You don't happen to run any antivirus like clamav on your machine?

---

### Post by aBitLater on 2008-02-02
thank you taurus

when I rebooted, after posting that message, I got a warning about the disk being full, and it wouldn't let me log on.  Since it was a (mostly) fresh install, I decided to reinstall.  

I'll watch this installation to see how it goes

I don't have any AV products unless they are installed by default.

Here is the output for my fresh install:

```

/dev/sda1   *           1       11661    93666951   83  Linux
/dev/sda2           11662       12161     4016250    5  Extended
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris

```

I put it here because I used "guided install - use entire disk" option this time.  Last time, I manually partitioned and I don't remember seeing a partition number for the extended partition like I see about.  swap was on a primary partition.

---

