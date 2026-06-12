---
title: "Upgrade went horribly wrong"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by The_Cougar_Kid on 2011-05-28
I was doing a standard update of 11.04 on my dual boot XP / Ubuntu PC, and something went horribly wrong, I think because my wireless connection dropped in the midst of the update.  I can't now run 'Update manager' as I get the message below:

 E: Problem parsing dependency Conflicts
  E: Error occurred while processing gnome-user-guide (NewVersion2)
  E: Problem with MergeList /var/lib/dpkg/status
  E: The package lists or status file could not be parsed or opened.
  E: _cache->open() failed, please report.
  
Also, I can't run 'Package manager' - I get some similarly serious-sounding error message.

Otherwise, the machine boots, and runs - albeit with warnings - for about 5 minutes, and then freezes solid.  XP still boots and runs OK.

Any ideas?  I am in the fortunate position, perhaps, of using the XP partition as a 'file server', so if necessary I could wipe off UBUNTU and start again as I don't have anything critical held within the Ubuntu Partition, apart from the system itself.  I am unsure as to how to go about a safe wipe.  I suspect that if I just try to reinstall it will put the new installation alongside the corrupt one and waste a lot of precious hard drive space.

---

### Post by kansasnoob on 2011-05-28
From terminal try:

```
sudo apt-get clean
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

```
sudo apt-get -f install
```

Please copy-n-paste any error messages back here.

---

### Post by The_Cougar_Kid on 2011-05-28
It appears I had two different problems here:
Problem 1: Inability to run Update manager, package manager, and the associated error messages.  That appears now to be fixed - thank you.
Problem 2: system freezes.  that appears to be something different.  With the machine booted and nothing other than the system monitor running, the machine eats up both physical and swap memory.  It has 1 Gb of physical memory and 1.5 GB of swap.  On up the monitor shows that it is using about 25% of both.  But without doing anything the memory in use steadily climbs and when both reach 100% the machine freezes.  I have looked at the running processes and nothing particularly memory-hungry shows up.  I have tried the same test under Windows XP and though it has much more memory in use when 'idling', it doesn't 'eat memory'.  the problem therefore appears to be software-related and nothing to do with, e.g., failed / failing memory chips.  Any ideas?

---

### Post by mörgæs on 2011-05-28
> **The_Cougar_Kid said:**
> I suspect that if I just try to reinstall it will put the new installation alongside the corrupt one and waste a lot of precious hard drive space.

You can run Gparted from a live boot and delete the Ubuntu partitions. After that you can install Ubuntu in the free space.

---

### Post by The_Cougar_Kid on 2011-05-29
Thank you.  that is a very helpful comment.  I was always scared simply to delete unwanted Ubuntu partitions for fear of screwing up the grub boot loader, but it appears that if I do a re-install it will all sort itself out.

Actually the other response has avoided the need for a reinstall, but this tip from you will be a very useful bit of knowledge for future reference.  Thanks

---

### Post by mörgæs on 2011-05-29
You are welcome, Kid. Have fun with your Cougar ;-)

---

### Post by kansasnoob on 2011-05-29
I'm not sure what may be eating your RAM and SWAP :confused:

Maybe start a new thread with an appropriate title and someone with more knowledge regarding that will have a look.

You can use the command:

```
top
```

To view all running programs but I've not messed with it very much.

---

