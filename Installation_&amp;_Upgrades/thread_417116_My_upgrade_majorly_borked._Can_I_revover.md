---
title: "My upgrade majorly borked. Can I revover?"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by BomanAJeff on 2007-04-21
I was running the Upgrade to Feisty, but the power to my cable modem fell out, and the upgrade was frozen. Now I can't get back into X.

Is there a way to come back from this short of wiping everything out and reinstalling from scratch?

---

### Post by solar george on 2007-04-21
If you can get to an ordinary terminal try,
```
sudo apt-get -f install
```

---

### Post by BomanAJeff on 2007-04-21
> **solar george said:**
> If you can get to an ordinary terminal try,
The problem is that I can't get beyond a screen full of text No terminal available.

---

### Post by Daishiman on 2007-04-21
Boot from the cd. Find the device that corresponds to the drive with the borked install and mount it. Then do 

chroot /borked_root_drive /bin/bash

That shold switch the environment to your old drive, but running the livecd kernel. From there see if you can run the upgrade again through apt-get -f install.

---

### Post by solar george on 2007-04-22
Try booting into recovery mode and running
```
apt-get -f install
```

---

### Post by BomanAJeff on 2007-04-23
> **solar george said:**
> Try booting into recovery mode and running
```
apt-get -f install
```

I attempted all 3 recovery modes (I have 3 Linux kernels listed, though I don't know why) in two of them it may change a few files for less than a minute, but won't do anything from them.

The third (I'm guessing it's the latest kernel) doesn't even lead to a command line.

---

### Post by solar george on 2007-04-24
Do what Daishiman suggested

---

### Post by BomanAJeff on 2007-04-24
Do I find the device via Nautilus or some other app?

---

### Post by solar george on 2007-04-25
Open a terminal and type,

```
sudo mount /dev/*rootdrive* /mnt
```

Where *rootdrive* is the partition that you selected as / during the install (eg. sda1), if you have a seperate /home do



Then type
```
sudo chroot /mnt/ /bin/bash
mount -a 
apt-get -f install
aptitude dist-upgrade
```

---

### Post by BomanAJeff on 2007-04-28
Me again. Sorry to be a pest...

I tried this. dist-upgrade runs for less than a minute - then it says it's aborting on a file it can't handle. It recovers to stop.

---

### Post by solar george on 2007-04-28
Can you post the exact error.

---

### Post by BomanAJeff on 2007-04-28
This time it ran a little longer, then this message:

Setting up apport (0.76.1) ...
 * Starting automatic crash report generation: apport                           /etc/init.d/apport: 127: cannot create /proc/sys/kernel/core_pattern: Directory nonexistent
                                                                         [fail]

---

### Post by solar george on 2007-04-28
Try,

Open a terminal and type,


```
sudo mount /dev/rootdrive /mnt
sudo mount -t proc proc /mnt/proc


```
Where rootdrive is the partition that you selected as / during the install (eg. sda1), if you have a seperate /home do



Then type

```
sudo chroot /mnt/ /bin/bash
mount -a 
apt-get -f install
aptitude dist-upgrade
```

---

### Post by BomanAJeff on 2007-04-29
These roadblocks are really getting annoying. The latest errors on attempt:

Starting Sendmail milter plugin for SpamAssassin: /usr/sbin/spamass-milter
Errors were encountered while processing:
 /var/cache/apt/archives/spamass-milter_0.3.1-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by solar george on 2007-04-29
It may be best just to do a clean install, you'll need to backup your /home some how.

I would suggest that during the install you should create a separate /home partiton to prevent data loss if you have to do this again.

---

