---
title: "install new version of ubuntu on 2nd hard drive and transfer data from old drive"
date: 2018-12-09
forum: Installation &amp; Upgrades
---

### Post by a2231 on 2018-12-09
Hi.  I have a new, unformatted hard drive in a hot swap bay where I'd like to install the latest version of Ubuntu and transfer ~300gb of data from my old drive to the new.  Also, the old drive has an earlier Ubuntu version and both drives will be encrypted.  What's the best way to go about this?  If I use an ISO to install ubuntu in the new dive and boot from the new drive, is it straight forward to see data from the old drive and transfer it?

---

### Post by oldfred on 2018-12-09
If it is encrypted, you will have to separately mount it and use the passphrase for it to unencrypt it.

       Recover files on encrypted drive
[https://ubuntuforums.org/showthread.php?t=2382995](https://ubuntuforums.org/showthread.php?t=2382995)
[https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line](https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line)

---

