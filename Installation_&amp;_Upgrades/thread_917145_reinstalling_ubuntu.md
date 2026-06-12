---
title: "reinstalling ubuntu"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by dimeotane on 2008-09-11
I've had ubuntu on my laptop since version 5 or 6 and I've decided it's time for a fresh installation from CD.  There's a few too many unresolved problems with my laptop since I did my last upgrade, so I want to get a fresh CD install this time around from 8.04

So what's the process for doing a fresh CD install without losing completely everything?   Any tips, suggestions or guides will be much appreciated.  I've backed up my system but need a guide for this process, not wanting to turn this into a month long process to get my laptop up and running again on 8.04 with everything intact.
 
Certainly I'm going to lose some unimportant parts of my system setup and thats OK but I'm not sure what to plan on restoring.

I want to have some of the packages I have now but not all.  I can easily do one big 

```
sudo apt-get install package1 package2 package-etc
```
after I've reinstalled.  

But is there anything else I need to backup and restore in the root partition?

My personal data is stored in a separate /home partition.  Do I just copy all the files to a spare hard drive and then recopy them back to my new home partition?  Does the user name need to be the same?

Any help is appreciated, thanks.

---

### Post by oilchangeguy on 2008-09-11
first, please give the laptops specs. it might be able to run 8.04.

---

### Post by dimeotane on 2008-09-11
I'm pretty sure I'll run just fine... it's a duo core with 1gig ram

I'm more wondering about the process of backing up and restoring my user data after a fresh install.

---

### Post by mikewhatever on 2008-09-11
> **dimeotane said:**
> But is there anything else I need to backup and restore in the root partition?

No. Backup /home just in case.

> My personal data is stored in a separate /home partition.  Do I just copy all the files to a spare hard drive and then recopy them back to my new home partition?  Does the user name need to be the same?

You aren't required to format /home during re-installation, unless you decide to redo partitions. Username doesn't really matter, cause you can always chown /home.

---

### Post by dimeotane on 2008-09-18
Wow.  It was actually really easy.  I noted the list of packages that I use frequently and wrote that down. Backed up /home just in case.  Then ran the Hardy install CD, and during install set the /home partition, swap, and the root partition as it was before.  
  I needed to set the wireless divers working again for my broadcom card, but didn't need to use ndiswrapper any more!

 After install I needed to change move my /home/olduser to my /home/newuser  and chmod the permissions.  I could have stuck with the old username, but wanted to change my username. It was pretty simple.

I reboot and my old desktop comes up exactly the way I left it.  Simply amazing.  

Some applications like virtualbox needed to be set up again, but most were reinstalled in one 'sudo apt-get install' list.

One problem I haven't resolved yet is that evolution is looking for the contacts database in the /home/olduser folder, but I haven't found how to redirect it to look for the /home/newuser folder. 

Overall, the time I took to reinstall has be absolutely worth it.  My machine runs now at lightning speed (it used to have an odd pause and delay), and problems with standby and powering up after standby have disappeared.  

If you haven't put your /home in a separate partition, I'd recommend it, because it makes it very easy to reformat and reinstall the OS without wiping your files in the process.

---

