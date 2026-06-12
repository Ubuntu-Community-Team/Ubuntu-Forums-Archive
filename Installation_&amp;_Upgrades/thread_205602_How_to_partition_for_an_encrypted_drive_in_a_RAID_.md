---
title: "How to partition for an encrypted drive in a RAID 1 system??"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by endokrin on 2006-06-28
I posted this question in the beginner's forum but got no replies so I am posting it here.. [http://ubuntuforums.org/showthread.php?t=204841](http://ubuntuforums.org/showthread.php?t=204841)
*******
I'm going to do a new install on a computer with (2) 250GB hard drives.

I plan on setting them up as a RAID 1 system.
I want to have a small partition to store encrypted data on.. say about 5 GB.

I was going through the alternate install CD, and when I enter software RAID configuration, it says once the changes are written, no additional changes are allowed.... so I should set up an extra partition on each disk for the encrypted data now as I won't be able to later?

I am following these basic instructions: [https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

This is what I was thinking, please adjust and correct as necessary..
The following applies to both/each disk:
/ 10GB
/swap 2GB
/encrypt 5GB
/home max GB remaining

Does this look right? Will it work? I won't be setting up the encrypted stuff yet... just need to get the system up and running.

---

