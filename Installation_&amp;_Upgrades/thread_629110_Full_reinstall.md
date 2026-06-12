---
title: "Full reinstall"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by PeteZA on 2007-12-02
Hi All;

I seem to have completely broken my Gutsy install on my desktop. The mouse and keyboard work intermittently, the wireless is down, and my geforce 6600 will no longer work with the restricted drivers. I am guessing that there are problems with conflicting drivers or something but I am not sure, plus, my complete n00bness prevents me from being able to fix this.

(As I am from a M$ background) My answer to this problem is to reinstall (and yes I know there MUST be a way to fix it, but I am not sure I feel like the frustration), however, there is a fair whack of data on the drive, which I cant backup anywhere else because I dont have sufficient space. Is there anyway to do a reinstall without formatting the drive?

Thanks

Pete

---

### Post by mikewhatever on 2007-12-02
You do not need to format the whole drive, just the root partition to reinstall. Assuming you have separate data partitions that should not be a problem.

---

### Post by PeteZA on 2007-12-02
In my infinite wisdom I only have one partition.

---

### Post by sloggerkhan on 2007-12-02
well, I guess you could always remove stuff except for /home or wherever your data is by manual deletion, use gparted to resize the partition to a new /home and a / and then reinstall accordingly. gparted is the best tool for this, and depending on how much data is on you drive, might take a while.

---

### Post by PeteZA on 2007-12-02
I should have sufficient space to create a new partition on which to put the data. What commands do I need to run to run gparted in recovery mode?

EDIT:

I am being stupid here, I assume I can do all of this from the live CD?

---

### Post by sloggerkhan on 2007-12-02
gparted has its own live cd or USB bootable system.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Paradoxically, one of the steps before doing a HD resize is to back it up first.
In any case,
/  ----> root partition. Can be fairly small. Mine is using 7.3 gb so you're probably good with a 12 of 15 gb partition.
/home ----> rest of space 
would be fairly typical schemes.
Data would be in /home/$username/   right?

---

### Post by mikewhatever on 2007-12-02
> **PeteZA said:**
> In my infinite wisdom I only have one partition.

To install Gutsy, you must have formatted that single partition. Forgive me for asking, but how could you accumulate so much stuff since then? Any way, you'll need to back up, no matter how. Buy or borrow a flash drive, burn files to CD/DVDs, etc.

---

### Post by PeteZA on 2007-12-02
Ok, I have managed to change the partition size, and created a new one. However, I now do not have permission to acces or read/write to the partition, how does one go about getting these permissions?

---

### Post by PmDematagoda on 2007-12-02
Did you mount the partition and as what?

---

### Post by PeteZA on 2007-12-02
As far as I can tell (if I right click it gives me the option to unmount the drive) it has been mounted as disk-1. Remember I am doing this from the LiveCD, as nothing works if I login. As an alternative, maybe I could copy my home directory in recovery mode? I dont know how to do this

---

### Post by sloggerkhan on 2007-12-02
from the live cd, if you mounted it, you should be able to write to it as a super user, so long as you mounted it with write permissions.

---

