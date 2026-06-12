---
title: "Installed 14.04 over 13.10, contents of home folder erased"
date: 2014-05-25
forum: Installation &amp; Upgrades
---

### Post by remn on 2014-05-25
I just updated from 13.10 to 14.04 by way of a fresh install. I had separate partitions for the / and /home folders and only formatted the root partition, so I assumed that the contents of the /home folder would be saved. However, when I booted up under the new installation all my /home files were gone. I had most of my important files backed up but some of the back-ups are out of date. I'm wondering what would be the best way to recover as much of my /home files as possible? I'm running a dual boot of Ubuntu and Windows, so I could try the recovery under either OS.

EDIT: One thing I just realized is that I changed the username on the new installation, if that matters.

---

### Post by papibe on 2014-05-25
Hi remn.

I think there's a chance that the partition is there but it hasn't been mounted.

Could you open a terminal run these commands, and post back the results (you can copy/paste the text)?
```
sudo fdisk -l

df -h

cat /etc/fstab

sudo blkid
```
Regards.

---

### Post by remn on 2014-05-26
Thanks for your reply. I just re-installed 14.04 with my old username and my home folder is there again. The weird thing is now the wifi doesn't work. I'm going to start a new thread for the wifi issue.

---

