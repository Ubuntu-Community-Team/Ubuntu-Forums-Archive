---
title: "Partition manager problem when attempting to re-size Win 7 Partition"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by tomreid on 2010-02-06
Hi

I bought a new HP pavilion DV6 Laptop today. It came pre-installed with Win 7. 

I've done a number of dual boot installs, but never with Windows 7 (I've done Mac, Win XP and Vista before). 

When I enter the partition manager part of the install programme, I select to "select Ubuntu or Windows 7 on boot", I select the size of the windows and ubuntu partition using the slider, but when the install programme tries to execute the command it just sits at "0%" for around 5 mins and then comes up with an error message. 

When I try again it takes me to the advanced partition manager (which frankly I've never really understood).

I don't have Windows back up media for this machine yet which is a bit of a pain, so I've e-mailed HP tech support aboput that, as there are some more advanced dual boot guides around, which i may try if there is n easy fix to this issue. 

Anyone else having this issue?

cheers

---

### Post by darkod on 2010-02-06
It's better to shrink win7 with its own tool. Open Disk Management (windows button + R, type diskmgmt.msc, hit Enter) and shrink it as much as you want. Leave the space as unallocated.
IMPORTANT: Boot win7 few times to make sure it's happy after the shrink and to do some disk checks. The ubuntu partitioner can't do this step and sometimes it can corrupt the win7 boot process.

After that just boot with ubuntu cd, in step 4 tell it to use Largest Available Free space and that will install it into the unallocated space. Or created partitions manually if you want that.

---

### Post by tomreid on 2010-02-06
Wow, that was probably the fastest fix to what I thought would be a very difficult problem. Thanks, that worked very well. 

One more issue that I have, is that I tried out Ubuntu with the Live CD before I installed it. When running the Live CD when I ran the "hardware drivers" prgramme it corrrectly figured out that it needed a propriatory Boradcom Driver to make the wifi work. 

Frustratingly enough now I am running Ubuntu as an insllated version on the HD, the wifi does not work and when I run the "hardware drivers" programme it does not find any propriatory drivers to install. 

Any ideas?

cheers

---

### Post by darkod on 2010-02-06
> **tomreid said:**
> Wow, that was probably the fastest fix to what I thought would be a very difficult problem. Thanks, that worked very well. 

One more issue that I have, is that I tried out Ubuntu with the Live CD before I installed it. When running the Live CD when I ran the "hardware drivers" prgramme it corrrectly figured out that it needed a propriatory Boradcom Driver to make the wifi work. 

Frustratingly enough now I am running Ubuntu as an insllated version on the HD, the wifi does not work and when I run the "hardware drivers" programme it does not find any propriatory drivers to install. 

Any ideas?

cheers

I don't know much about wifi, but you do have wired internet access to search for drivers right? If you do, I have no idea what the problem might be if it found a driver in live desktop.
Maybe look for the driver yourself? Google your broadcom chipset and you should get loads of tutorials.

---

### Post by tomreid on 2010-02-06
found a fix here:

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

thanks for all your help

cheers

Tom.

---

### Post by Mark Phelps on 2010-02-08
You should check the Backup options in Win7.  Unless HP remove it, there is an option to create a Repair CD.  If you do that, you won't have to worry about reinstalling or restoring Win7 if you run into boot problems down the road.

---

