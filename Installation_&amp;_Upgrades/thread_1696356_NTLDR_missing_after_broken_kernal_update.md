---
title: "NTLDR missing after broken kernal update"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by Andy0 on 2011-02-27
Setup: Multi partitioned hard drive with Ubuntu 10.10 and Win 7.

On Ubuntu 10.10 upgrading kernals from 2.6.35-25-generic to 2.6.35-27-generic. Ended up 'hard' shutting down after 2h apt-get upgrade hang. Upon reboot I had 'NTLDR is missing', a message generally associated with Microsoft boot problems.

Ubuntu 10.10 uses 'grub2' aka v1.98. This means no more menu.list. [Read more here]("https://help.ubuntu.com/community/Grub2").

To Fix:
1. Access your hard drive: LiveCD boot / LiveUSB / External attached to your hard drive
Remove half updated kernel files in /boot

2. Boot normally: 
Clean up package listing
```
sudo dpkg --configure -a
```
Retry upgrade
```
sudo apt-get upgrade
```

Upon retrying I was successful :)

---

