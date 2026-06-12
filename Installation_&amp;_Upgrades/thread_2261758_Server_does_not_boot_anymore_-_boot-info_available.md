---
title: "Server does not boot anymore - boot-info available"
date: 2015-01-20
forum: Installation &amp; Upgrades
---

### Post by christof3 on 2015-01-20
Hi
I have a UEFI based server with two disks which are setup in a software RAID 1. One disk died and now my server does not boot anymore. 

I tried several things to identify the cause of the problem but I am stuck. 

All information about my setup is in this boot-info details:
[http://paste.ubuntu.com/9799712/](http://paste.ubuntu.com/9799712/)

Any help appreciated!!
Thanks.
Christof

---

### Post by oldfred on 2015-01-21
I do not know RAID.

But my understanding is that the 2 is the drive. So it looks like both drives as mirrors were actually using the second drive to boot.

```
Boot0000* ubuntu	HD([COLOR=#ff0000]2[/COLOR],1000,100800,3f86c0dd-5c79-4cb4-a206-a4d65ec1b1f2)File(EFIubuntushimx64.efi)
Boot0001* ubuntu-hdd2	HD([COLOR=#ff0000]2[/COLOR],1000,100800,3f86c0dd-5c79-4cb4-a206-a4d65ec1b1f2)File(EFIubuntu-hdd2shimx64.efi)
```

---

