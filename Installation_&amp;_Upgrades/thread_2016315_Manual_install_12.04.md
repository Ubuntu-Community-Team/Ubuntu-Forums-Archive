---
title: "Manual install 12.04"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by Anger 2 on 2012-07-04
I am attempting to manually install 12.04 as a dual boot with XP. All goes well until setting up the swap partition.If I change the EXT4 file system to swap and click OK then in the next window there is not a tick in the swap partition format box.I am reluctant to proceed in case I have failed to do something.What do I need to do?

---

### Post by msammels on 2012-07-04
How are you partitioning the drive? gparted or something else?

---

### Post by Anger 2 on 2012-07-04
Using gparted of the 12.04 installation cd.

---

### Post by msammels on 2012-07-04
Can you not right click the swap partition and set the flag manually?

---

### Post by Anger 2 on 2012-07-04
I am trying to set up the partition from unallocated space using the installation cd. There is no indication of a flag .Should there be a tick in the format box and if so what is the correct proceedure for setting up the partition?

---

### Post by msammels on 2012-07-04
Please see [this link](https://help.ubuntu.com/community/WindowsDualBoot).

---

### Post by Anger 2 on 2012-07-04
MS,
Thankyou for the link but it does not answer my question.I have followed an old much more comprehensive link and in that setting up the swap partition was different to setting up the others but I cannot recall whether there was a tick in the format box in the next window or not.

---

### Post by RAM SEN on 2012-07-06
Anger, have u seen this ?

1.  
[http://ubuntuforums.org/showthread.php?t=899222](http://ubuntuforums.org/showthread.php?t=899222)

i notice that in the final layout of partitions in this guide - swap has no mount point - cud this be the reason for your problem ?
(sorry total non-techie so excuse me if this sounds stupid !)

2. also wondering if ur life will be easier if u use the Alt CD ?
Hermann has an excellent guide here ...
[http://members.iinet.net.au/~herman546/p2.html](http://members.iinet.net.au/~herman546/p2.html)

3. why not just proceed & see what happens - not being casual - since u r in manual mode & within constraints of live CD installer, shudnt that rule out disaster outcomes if u check screen before hitting cfm/apply ? 

Gud Luck

---

### Post by RoyStrachan on 2012-07-06
> **Anger 2 said:**
> I am attempting to manually install 12.04 as a dual boot with XP. All goes well until setting up the swap partition.If I change the EXT4 file system to swap and click OK then in the next window there is not a tick in the swap partition format box.I am reluctant to proceed in case I have failed to do something.What do I need to do?

You don't need to do anything. swap does not get formatted.  You're good to go.

---

