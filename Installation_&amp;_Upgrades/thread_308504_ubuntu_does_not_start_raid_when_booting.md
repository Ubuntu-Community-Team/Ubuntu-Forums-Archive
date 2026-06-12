---
title: "ubuntu does not start raid when booting"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by gruadp on 2006-11-28
ubuntu 6.10:

I installed ubuntu 6.10 and the manually created a /data-partition as raid1 with mdadm. The partitions for this raid are tagged as linux-auto-raid in fdisk.

Now when booting ubuntu the raid is not assembled automatically and therefore the /data-partitions cannot be mounted and most services that rely on this partition (samba, ldap, apache ...) cannot be started.

I have to manually assemble the raid with mdadm -A -a yes /dev/md0 /dev/hde4 /dev/hdg4 to get the raid and then start all services.

How can I ubuntu make this raid start automatically?

thnx,
peter

---

### Post by richardward101 on 2006-11-28
In system->administration->Services, Selecting mdadm-raid might work, but probably not.
try adding
```
DEVICE /dev/hde4 /dev/hdg4
ARRAY /dev/md0 devices=/dev/hde4,/dev/hdg4 auto=yes
```
to your /etc/mdadm/mdadm.conf file.
Reboot and see what happens.

---

### Post by gruadp on 2006-11-28
> **richardward101 said:**
> In system->administration->Services, Selecting mdadm-raid might work, but probably not.
try adding
```
DEVICE /dev/hde4 /dev/hdg4
ARRAY /dev/md0 devices=/dev/hde4,/dev/hdg4 auto=yes
```
to your /etc/mdadm/mdadm.conf file.
Reboot and see what happens.

The latter did the trick - somehow ...  

the service mdadm-raid is now starting the raid, but very late. The link in rcX.d is S25mdadm-raid and so the raid is assembled only when most other services are already started and ways after fstab is read and the partitions mounted.

While I could put mdadm-raid as S01 or something this still isnt the way I'm used it to be. On my other servers the raid is started much much sooner when booting - I guess its done by a script in initrd (and there is such a script present in the ubuntu-initrd as well) or automagically when loading the md-module.  I mean - thats all the reason for labeling a partition as fd: linux raid-autodetect.

thnx for your advice and additional comments are heavily welcome :)

thnx
peter

---

### Post by richardward101 on 2006-11-28
I'm pretty sure fstab stuff (other than /, proc, etc of course) doesn't get mounted until S35.
TBH I'd say that if its working and your samba etc are starting ok, don't try and fix it.

---

### Post by gruadp on 2006-11-29
> **richardward101 said:**
> I'm pretty sure fstab stuff (other than /, proc, etc of course) doesn't get mounted until S35.
TBH I'd say that if its working and your samba etc are starting ok, don't try and fix it.

IMHO fstab is processed before. its processed in mountall.sh and checkroot.sh which are executed before!! even samba and ldap are processed before. 
Only in single-user-mode this scripts are even listed in rcS.d with S35.
But I really dont know. Anyway : LDAP and SAMBA were still not starting, cause md0 was assembled to late and not mounted as /data.

SOLUTION:

I found the solution and a full report can be found at [http://www.goldfisch.at/knowledge/360](http://www.goldfisch.at/knowledge/360)

but the missing piece was to run

dpkg-reconfigure mdadm

which creates a new initrd (based on mdadm.conf ?? or on scanning the minor-numbers of the raidsuperblocks ??) and now the raid is started when processing initrd and everything is fine.


THNX A LOT

---

