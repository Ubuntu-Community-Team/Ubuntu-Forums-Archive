---
title: "loading of latest patches caused system to crash"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by jadcox on 2009-12-14
running 9.10 for some time now on my laptop, and have the system set up to automatically load latest updates.
 
last night, it performed the update, and then when it rebooted, it would not complete the boot sequence.
 
Boot from (hd0,0) ext3 df48#################### (a long number)
 
it finally times out and give the following error
 
"Gave up waiting for the root device. Common problems:7be20c06802
 
Boot args (cat /proc/cmdline)
check rootdelay= (did the system wait long enough?)
check root= (did the system wait for the right device?)
Missing modules (cat /proc/modules; ls /dev)
 
ALERT! /dev/disk/by-uuid/df48e556-ae87-4afc-bc06-d7be20c06802 done not exist. Dropping to a shell!
 
I rebooted and hit the esc key to go to the options of selecting what I wanted to boot. I used the edit option to look at all the old boot loaders and all of them have this same non-existing uuid reference.
 
I went to the /dev/disk/by-uuid director and found another id, but not the one listed in the boot loaders.
 
I am not an experenced user, but am willing to learn! :D

---

### Post by Angrylemur on 2009-12-15
man I had this exact same problem the other night!  Before the update everything was fine, but once I restarted I got the same message when I tried booting from safe mode.  I thought it was a harddisk problem, because I tried reloading the Ubuntu software and it gives me a similar error message claiming my harddrive is bad and cannot complete the new installation.

So now I have no way to install a new OS even after reformatting.  So my advice would be don't reformat just yet - there might be a way to fix this without doing so.  I don't know how, but hopefully someone here does.

^^

---

