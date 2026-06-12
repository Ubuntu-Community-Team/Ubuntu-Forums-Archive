---
title: "What is the best place in the file system to mount a new hard drive?"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by kacheng on 2008-09-10
Hi,

I just bought a new hard drive and want to use it as a data storage that will be shared to Ubuntu and Windows computers around the house.

Is there a preferred place to mount a disk like this as a best practice?  I know that this doesn't affect the UNC share location, which will always be \\ubuntucomputer\sharename\

I've seen people suggest:
/**home**/newHD
/**mnt**/newHD
/**media**/newHD
/newHD

Thanks

---

### Post by iaculallad on 2008-09-10
> **kacheng said:**
> Hi,

I just bought a new hard drive and want to use it as a data storage that will be shared to Ubuntu and Windows computers around the house.

Is there a preferred place to mount a disk like this as a best practice?  I know that this doesn't affect the UNC share location, which will always be \\ubuntucomputer\sharename\

I've seen people suggest:
/**home**/newHD
/**mnt**/newHD
/**media**/newHD
/newHD

Thanks

Actually, you can mount it anywhere you like. Provided you have the privilege (sudo/gksudo/kdesu/kdesudo) when trying to mount outside your /home folder.

---

### Post by isomer on 2008-09-10
Traditionally /mnt has been used for CD/DVD and floppy drives, and more recently /media for other external media such as USB memory sticks or hard drives.

As iaculallad says, you can mount it anywhere provided you have the correct permissions.  If you are using the whole disk as a new filesystem, I personally would use a separate mount point (your /newHD example).

The choice however, is yours.

---

### Post by kacheng on 2008-09-17
What directory do you mount your new spacious data drive on?

Or would it be better to use LVM?

---

