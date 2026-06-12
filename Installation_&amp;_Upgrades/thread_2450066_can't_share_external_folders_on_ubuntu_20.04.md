---
title: "can't share external folders on ubuntu 20.04"
date: 2020-09-06
forum: Installation &amp; Upgrades
---

### Post by mickeyd19652 on 2020-09-06
i have just reinstalled ubuntu 20.04 on my ssd. i use plex media server which can't access my external hdd's . i open up the properties on a hdd and try to enable sharing i need to install the app. installation fails, and the error message is "samba is virtual. i tried to install samba via the terminal which also fails and i'm told it is replaced with samba-libs. i have no ides what to do.

---

### Post by ActionParsnip on 2020-09-07
Is it an NTFS partition you want to share by any remote chance? NTFS and Samba causes headaches and you'd be better formatting to Ext4 then restoring your backups to it (I'm assuming you'd not want to use the drive for anything else)

---

