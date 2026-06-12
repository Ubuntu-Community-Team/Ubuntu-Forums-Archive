---
title: "Ubuntu 18.10 upgrade deleted all my files in /"
date: 2018-11-08
forum: Installation &amp; Upgrades
---

### Post by perplexativekhat on 2018-11-08
Hey, I ran into a pretty big issue. I was preforming an upgrade from 18.04 to 18.10 on my laptop when my battery ended up dieing (I didn't have access to a power cable at the time). When I got it powered on again, the install was horribly messed up to the point of unusability. 

I used a 18.10 LiveUSB in order to try and fix the issue, and used the "Upgrade Ubuntu to 18.10" option to keep my file, not having the mind to back up. During the install, the installer was complaining about not being able to install packages during the "Restoring previously installed packages" stage of the install. It wrapped up with an error related to this, and upon rebooting I found that all the files previously on my root drive were all missing.
Has anyone else ran into this issue?

---

### Post by Impavidus on 2018-11-09
1: Always use mains power when performing a release upgrade. Batteries run empty. I haven't had a mains power failure in 5 years. And when you have both mains and a battery it's even better, as you may be able to properly shut down or restore mains power before the battery runs empty.
2: After a horribly failed release upgrade, try a fresh install. Don't attempt to save it.
3: Before a release upgrade, always make sure you have current backups.

I guess you just learned that the hard way.

Do you still have your valuable documents? If you had a separate /home partition or some sort of data partition, they're probably there. If you indeed accidentally wiped your hard drive, you may try some [data recovery](https://help.ubuntu.com/community/DataRecovery).

Has anyone else run into this issue? Probably. People make mistakes.

---

