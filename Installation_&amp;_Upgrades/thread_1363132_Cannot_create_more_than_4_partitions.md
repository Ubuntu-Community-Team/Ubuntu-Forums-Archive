---
title: "Cannot create more than 4 partitions"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by nate91 on 2009-12-24
I just got my new laptop pre-installed with Windows 7. I'm trying to dual-boot it with a shared ntfs partition as described in what would normally be a very helpful article at [[COLOR=blue]http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony[/COLOR]]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony").
 
Unfortunately for me, the method described assumes that your computer comes with two partitions. My computer, however, comes with three: A 1.64GB recovery partition labeled as "HDDRECOVERY", a 10.68GB partition labeled "System", and a third partition labeled "TI102782WOE ( C: )".
 
The article says to shrink C:, which I have done, and now have 409.81GB of unallocated space, leaving the original partition at 43.81GB. With the Live CD in and running GParted, I try to create a 15GB partition for Ubuntu and then have the rest as my shared ntfs. But apparently I cannot have more than four partitions.
 
It will suffice me to know if my recovery disk will still work even if I remove the HDDRECOVERY partition. If it cannot, however, then I don't know what to do.
 
Thanks in advance for your help!

---

### Post by mikewhatever on 2009-12-24
You can not have more then four **primary** partitions, that's the rule, but Ubuntu doesn't need to be on a primary partition at all. You should create and extended partition in the unallocated space and then create logical one inside it (can create as many as you want). 
I wouldn't recommend deleting the recovery partition.

---

### Post by nate91 on 2009-12-24
Oh, well that makes things a lot easier.  Thanks very much.

---

### Post by Mark Phelps on 2009-12-26
> **nate91 said:**
> I just got my new laptop pre-installed with Windows 7. ... It will suffice me to know if my recovery disk will still work even if I remove the HDDRECOVERY partition. If it cannot, however, then I don't know what to do.

Most probably, your recovery disk (if it is a CD, not a DVD) will NOT work if you remove the recovery partition. Why? Because an OEM-customized Win7 image is too big to fit on a CD.  All the CD usually contains is the ability to boot the machine and start the restore process -- using the Win7 image stored in the recovery partition.

---

