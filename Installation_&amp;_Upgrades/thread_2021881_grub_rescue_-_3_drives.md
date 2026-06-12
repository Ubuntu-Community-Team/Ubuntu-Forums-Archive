---
title: "grub rescue - 3 drives"
date: 2012-07-09
forum: Installation &amp; Upgrades
---

### Post by s_raghu20 on 2012-07-09
HELP PLEASE !!!!!!

sorry, but I am sweating here...

I have three hard disks, and the boot partition was sdb2.
As I remember the configuration, the cd drive is primary master (therefore sda in my understanding), and then the 2TB one (sdb) in my understanding, and then there are two smaller ones, 500GB and a 250GB.

Now, when I am at grub rescue prompt, it confirms that hd0 is my 2tb disk, but doesnt list any partition with number 2. when i ask for ls (hd0,2) (which should have been my boot partition), it says no such partition.  Other partitions from the same disk are visible and listed, but not the boot partition...

what can I do to recover my partition ?

---

### Post by oldfred on 2012-07-10
Moved to your own thread. Original was wubi installed into a RAID which is not your issue.

From liveCD or USB download and run the Boot-Info:

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

That will give us the additional info we need to make better suggestions.

---

