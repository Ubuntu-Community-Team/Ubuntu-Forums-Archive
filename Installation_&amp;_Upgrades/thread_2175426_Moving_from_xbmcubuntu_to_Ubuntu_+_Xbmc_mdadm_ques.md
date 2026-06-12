---
title: "Moving from xbmcubuntu to Ubuntu + Xbmc mdadm question"
date: 2013-09-19
forum: Installation &amp; Upgrades
---

### Post by WigginsACK on 2013-09-19
Hi all,

Currently, I have xbmcubuntu installed on an SSD and along side that I have 5x3TB HDDs in RAID0 using mdadm.

I wanted to uninstall xbmcubuntu and then install 13.04 + xbmc. 

My question is, once I remove xbmcubuntu, the configurations holding my raid together are gone too. Will I still be able to assemble this array after I install Ubuntu without losing my data?

Thanks

---

### Post by TheFu on 2013-09-19
Backup the media, ~/.xbmc and /etc.

Then just install 13.04 (BTW, you probably want 12.04 instead for longer support, more stability) and restore the /etc/mdadm/, part of the /etc/fstab that deals with the mdN array, ~/.xbmc/ and media files from your backup.

Be happy.

---

