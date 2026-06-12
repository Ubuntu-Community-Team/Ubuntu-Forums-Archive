---
title: "Resize NTFS parition with winxp using gparted"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by Omeil on 2010-01-11
Hi all,

I'm on a work desktop and im just wondering what the chances are of data loss if i resize my paritions i have 2 NTFS 1 10GB and 1 64GB (Not sure why but thats how it is) I want to take 30GB from the 2nd partition and add onto the main 10GB. Is it only Gparted that has a chance of Data Loss or is that with all parition editors, its just that alot of NTFS windows progams indicate that there software is safe like this one for example [http://www.partition-tool.com/resource/resize-ntfs-partition.htm](http://www.partition-tool.com/resource/resize-ntfs-partition.htm) 

Thanks for your time.

Omeil

---

### Post by SuperSonic4 on 2010-01-11
> **Omeil said:**
> Hi all,

I'm on a work desktop and im just wondering what the chances are of data loss if i resize my paritions i have 2 NTFS 1 10GB and 1 64GB (Not sure why but thats how it is) I want to take 30GB from the 2nd partition and add onto the main 10GB. Is it only Gparted that has a chance of Data Loss or is that with all parition editors, its just that alot of NTFS windows progams indicate that there software is safe like this one for example [http://www.partition-tool.com/resource/resize-ntfs-partition.htm](http://www.partition-tool.com/resource/resize-ntfs-partition.htm) 

Thanks for your time.

Omeil

Any partition editor has the chance of causing data loss. However, it is relatively slim.

A better bet would be to defrag the drive in XP and use the native partitioner to shrink it. Also ensure you back up important data

---

### Post by darkod on 2010-01-11
> **SuperSonic4 said:**
> Any partition editor has the chance of causing data loss. However, it is relatively slim.

A better bet would be to defrag the drive in XP and use the native partitioner to shrink it. Also ensure you back up important data

XP doesn't have native partitioner. It was introduced in vista. Yes, any tool has slim chance of data loss. You might as well use Gparted, it's a very good tool.
Make a backup of all important data. Then use Gparted to shrink the 64GB partition for 30GB but you have to shrink it from the front (if the 10GB partition is before it), because that's the only way to add the unallocated 30GB later to the 10GB. They have to "touch" each other.
So if you shrink 30GB from the front of the 64GB you should be able to add them to the 10GB.
One word of advice for XP. It is problematic after a resize sometimes so what I would do is:
- shrink the 30GB from the 64GB. Don't add them to the 10GB right away. Boot XP few times to let it finish its disk checks.
- then again with Gparted add the unallocated space to the 10GB and let XP again do the disk checks if it asks

---

### Post by vinnywright on 2010-01-11
just my 2 cent's worth 

I'v found it's usualey a good idea to chkdsk then defrag then chkdsk the NTFS partition your going to be resizing.

and a Gparted live cd is what I use for the resizing

VINNY

---

