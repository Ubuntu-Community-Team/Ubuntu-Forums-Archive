---
title: "install 12.04 alongside win 7 - partition faq"
date: 2012-07-19
forum: Installation &amp; Upgrades
---

### Post by rowntreerob on 2012-07-19
i have a new, windows 7 ultrabook ( no dvd ) that has 4 existing partitions:
 
```
 
name       size          type 
 
SYSTEM   100MB      NTFS system primary partition
C:            208GB       NTFS Primary, boot, page , c-drive
               21GB        basic    Recovery 
                 8GB         basic   Hibernate partition

``` 
I intend to use ubuntu most of the time for software development. 
I will put a win7 system backup on a USB prior to working on ubuntu install.
 
My FAQ:
 
The 21 GB Recovery ?? since i can recover from the USB , why do i need this? Can i reclaim the space or is that taking a dumb risk?
 
The 8GB Hibernate - i will change the windows power manager to sleep only ( NO HIBERNATE ) . Can i reclaim this 8 GB?
 
The 208GB , i will try to resize this in win7 disk manager prior to the install of ubuntu. ( 55 GB for win7, 153GB for ubuntu ).
 
Please advise...

---

### Post by Quackers on 2012-07-19
Welcome to UF :-)

It will pay dividends to defragment the Windows C: drive before shrinking it.

There is likely to be a procedure available to make a copy of your recovery partition and burn that to disc. Make that copy first (or two copies even).
I would verify them also.
You can then reclaim the recovery partition space by deleting that partition.

The hibernate space can be recovered by deleting it.

It is imperative that you at no time exceed the maximum number of PRIMARY partitions on the disc (which is 4). If you need more than 4 partitions you should have a maximum of 3 primary partitions and one extended partition, which can hold as many LOGICAL partitions as you wish.

---

### Post by darkod on 2012-07-20
Your plan is good.

After you create the system backup, you can delete the restore partition.
If you disable hibernation, you could delete that partition too.
Shrink C: in windows Disk Management and reboot few times in case it wants to do any disk checks. Leave the space as unallocated, don't create any partitions from windows, it can create only ntfs which linux doesn't install onto.

After that you are good to install ubuntu.

---

### Post by rowntreerob on 2012-07-20
thank you darkod , quakers

---

