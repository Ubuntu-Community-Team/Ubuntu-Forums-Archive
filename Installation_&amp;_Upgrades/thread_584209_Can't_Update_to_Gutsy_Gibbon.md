---
title: "Can't Update to Gutsy Gibbon"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by bart_simpson on 2007-10-20
Hey, two days ago I attempted to update Ubuntu to Gutsy. It started modifying the software channels when it then posted an error had occurred. After this I decided to download the Alternate CD and try to update from that. After i download all the software and stuff, I got a MD5 checksum error on the CD, so I check the hash and it's different than what it should be. I download two other alternate CD's and get the same problem, both of them had bad MD5 hashes (I didn't burn them to a CD either, I mounted the iso in Linux). So when I try to go back to the regular way to update, sans the alternate CD, it keeps asking for me to insert the CD, and after hitting cancel a couple of times posts errors. So I was wondering how can I get it to basically get over the fact that the CD is gone and to install it regularly?

---

### Post by Pumalite on 2007-10-20
Are you running Feisty now?

---

### Post by bart_simpson on 2007-10-20
Yea

---

### Post by Pumalite on 2007-10-20
[http://ubuntuforums.org/showthread.php?t=286599](http://ubuntuforums.org/showthread.php?t=286599)

---

### Post by bart_simpson on 2007-10-20
Thanks for the help, I finally figured out a way to get the update manager to stop asking for the CD, I opened /etc/apt/sources.list and edited out the top line which has the CD on it. So now I am downloading the updates and will post back here in case of other problems.

---

### Post by FredB on 2007-10-21
> **bart_simpson said:**
> Thanks for the help, I finally figured out a way to get the update manager to stop asking for the CD, I opened /etc/apt/sources.list and edited out the top line which has the CD on it. So now I am downloading the updates and will post back here in case of other problems.

Let's hope it will be a quiet process. But, I always prefer a clean install than an upgrade installation.

---

### Post by bart_simpson on 2007-10-21
Yea...so things didn't go as happy as intended. As it was installing my updates, it says I got a corrupt file and it that the upgrade would abort, possibly making the machine unusable. Well, after restarting since I couldn't use anything after that message, the X server doesn't start so all I'm getting are command prompts...any ideas?

---

### Post by bart_simpson on 2007-12-19
Just for the sake of resolving this post, I figured I'd post back. The problem was I had faulty RAM that kept mucking up my downloads, so when I installed new RAM, everything has downloaded fine and worked.

---

### Post by tech9 on 2007-12-19
> **FredB said:**
> Let's hope it will be a quiet process. But, I always prefer a clean install than an upgrade installation.

+1
clean installs are better than upgrades

---

### Post by Pumalite on 2007-12-19
I agree 100%

---

