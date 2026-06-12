---
title: "Can I migrate an old rpool to another system? If yes, how?"
date: 2022-11-02
forum: Installation &amp; Upgrades
---

### Post by anystupidassname on 2022-11-02
I have a non-booting (non UEFI) openzfs-on-root jammy 22.04 on a 1TB SSD. (disk is just over 400GB used) I've tried to fix that one for weeks now.
 [https://ubuntuforums.org/showthread.php?t=2480236](https://ubuntuforums.org/showthread.php?t=2480236)

 I installed jammy with zfs-on-root as close to identically on another system (in legacy BIOS mode although this one CAN do UEFI if useful/necessary) and 500GB SSD. I would like to migrate (using zfs send/recv or clonezilla or anything) just the rpool from the old SSD to the new one. Can I make this work? Will it boot? If yes, specifically what steps are needed?

I have not booted the newly installed system yet but I'm pretty sure there are different dataset (rpool/ROOT/ubuntu_??????) names in the rpool. Details on the old system are available in this other thread or I'm happy to provide whatever other info you might need.

Any help would be much appreciated.

---

### Post by MAFoElffen on 2022-11-03
Why not install the new ZFS with UEFI, since the machine supports booting from UEFI?

You use "sudo zpool import <pool_name>"...

Reference: [Migrating Storage Pools]("https://docs.oracle.com/cd/E19253-01/819-5461/gbchy/index.html")

I told you "Migration" was one of your options, which I recommended...

Another was to make a snapshot of the pool of the chrooted machine and to send/restore the pool snapshot or of an older snapshot on the new machine...
```

sudo zfs snapshot rpool/test@2022Nov031705
sudo zfs send rpool/test@2022Nov031705 | ssh user@server.example.com "zfs receive rpool/test"

sudo import rpool/test

```
*** Though, I'm not sure what happens if the bpool and rpool are out of synch(???)

The problem with you old is the kernel initramsfs in the bpool right?

---

### Post by anystupidassname on 2022-11-06
> **MAFoElffen said:**
> Why not install the new ZFS with UEFI, since the machine supports booting from UEFI?

I guess my thinking was that I wanted to eventually move this drive back to the original computer or even any other computer and most of my hardware is older (non-UEFI).

> Another was to make a snapshot of the pool of the chrooted machine and to send/restore the pool snapshot or of an older snapshot on the new machine...
```

sudo zfs snapshot rpool/test@2022Nov031705
sudo zfs send rpool/test@2022Nov031705 | ssh user@server.example.com "zfs receive rpool/test"
sudo import rpool/test

```
*** Though, I'm not sure what happens if the bpool and rpool are out of synch(???)

Yea, I was trying to avoid just throwing stuff at the wall to see if it sticks but I guess that is where we are now.

> The problem with you old is the kernel initramsfs in the bpool right?

I don't know how to find the answer to that question.

---

### Post by anystupidassname on 2022-11-06
> **MAFoElffen said:**
> 

Another was to make a snapshot of the pool of the chrooted machine and to send/restore the pool snapshot or of an older snapshot on the new machine...
```

sudo zfs snapshot rpool/test@2022Nov031705
sudo zfs send rpool/test@2022Nov031705 | ssh user@server.example.com "zfs receive rpool/test"

sudo import rpool/test

```


OK, so the "destination" machine/drive has not been booted yet (purposely)
Do i chroot into the "source" AND "destination machines/drives and then try this zfs send/recv operation?
How do I tell the destination system to "overwrite" or take the place of the rpool (that has already been created during install) with the source rpool?

---

### Post by MAFoElffen on 2022-11-08
I'm testing this on two VM's to how to explain this, and what works better. It doesn't work on ZFS on Linux as well as it did on Solaris (Send/Receive directly through ssh). Then Trying to sending to a USB drive would be easier.  Then testing if an import or a promote will work best... 

So still working on the instructions for that.

---

### Post by anystupidassname on 2022-11-16
I would like to try this if/when you have any success.

---

### Post by MAFoElffen on 2022-11-16
I have two projects to finish in the next 3 days... Repairing my hot water heater and installing a new server. I have to keep my wife happy and taken care of. I will get back to this very soon.

This is what you will try:
[https://serverfault.com/questions/457270/can-i-move-a-zfs-pool-to-another-computer](https://serverfault.com/questions/457270/can-i-move-a-zfs-pool-to-another-computer)
[https://docs.oracle.com/cd/E19253-01/819-5461/gbchy/index.html](https://docs.oracle.com/cd/E19253-01/819-5461/gbchy/index.html)

---

