---
title: "Upgrade to 3.2.0-39-generic: Kernel executes NX-protected page - exploit attempt ?"
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by lptr on 2013-03-20
LTS1204
Symptoms since upgrade to 3.2.0-39-generic two days ago: 
System does not shutdown correctly (need to hard shutdown by powerdown). Login lasts horribly long. 

This morning I looked into /var/log/syslog and later into dmesg. So I detected this 'BUG' message in snippet below. 

[   66.097491] RIP  [<ffff8804045e4020>] 0xffff8804045e401f
[   66.097493]  RSP <ffff8803e3d83dd0>
[   66.097494] CR2: ffff8804045e4020
[   66.097495] ---[ end trace e001f6e1c8ef305d ]---
[   70.390811] kernel tried to execute NX-protected page - exploit attempt? (uid: 1000)
[   70.390816] BUG: unable to handle kernel paging request at ffff8804045e4020
[   70.390819] IP: [<ffff8804045e4020>] 0xffff8804045e401f
[   70.390825] PGD 1c06063 PUD df7fe067 PMD 4024aa063 PTE 80000004045e4163
[   70.390830] Oops: 0011 [#5] SMP 

Anyone with similar problems?

[update]<br><br><a  href="http://blog.flowblok.id.au/2012-11/gvfs-gphoto2-volume-monitor-memory-usage.html"   data-cke-saved-href="http://blog.flowblok.id.au/2012-11/gvfs-gphoto2-volume-monitor-memory-usage.html">found  this</a> hint<br><br>As it seems Rhythmbox is dead.  It crashes permanently on this machine.<br>

---

### Post by lptr on 2013-03-20
[update]

[found this]("http://blog.flowblok.id.au/2012-11/gvfs-gphoto2-volume-monitor-memory-usage.html") hint

As it seems Rhythmbox is dead. It crashes permanently on this machine.

---

### Post by lptr on 2013-03-20
[SOLVED] -- (quick fix -- not permanently)
Don't know what is going on here in detail. Seems that Rhythmbox is broken. 
Anyways: I purged Rhthmbox 

```
$ sudo apt-get purge rhythmbox 
```
and this strange symptoms are gone.

---

