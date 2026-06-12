---
title: "Dual-boot XP &amp; partitioning"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by Krunktor on 2008-02-18
I'm about to do my first ever installation of Ubuntu (v.7.10) and I want to setup a dual-boot system with Windows XP. I've gone through all of the relevant documentation that I could find, but I still need a bit of help with my partitioning.

I want to create separate partitions for Windows and Ubuntu, as well as my personal files. I also want to allow my files to be accessible to both Windows and Ubuntu. To rephrase that as a question, what sizes should my Windows/Ubuntu partitions be (I've read about 8 and 3 GB, respectively; just looking to confirm) and how do I make my files accessible to both?

I saw a thread here a few weeks ago with some information that would have been useful, but it's obviously been pushed down and I can't find it through the search. 
In the thread, it listed several different partitions, their ideal sizes and filesystem types. This was supposedly the *definitive dual-boot HDD layout*. Could anybody reiterate this to me?

---

### Post by low_impact on 2008-02-18
im only new to ubuntu but i just took the defaults and found still had access to xp files and folders
the install resized the partitions and still left plenty for the xp partition.
other wise use the system/administration/partition editor from a live cd to resize to 8gb and a 500mb swap and install to that goodluck.

---

### Post by Partyboi2 on 2008-02-18
The size of the partitions really depends on the individual person and how big there hard drive is. If you are wanting to use windows still alot you wouldn't want to shrink that partition to small as you will need have space for all your files etc. Ubuntu can run with a partition 3 gig but it doesn't give you much to play with. 5 gig for the /root partition (Where all the system files are) is a reasonable amount. You would also need a /swap partition which is roughly about x2 the amount of ram you have in your system. If you like you can also create a seperate /home partition (as large as you like) which is where all your settings and personnal files are kept, handy if you need to reinstall ubuntu as what ever is in your /home partition will not be touched. 
so if I had a 20 gig parttion and 512 ram to play with I would do something like this:
5 gig /root (ext3)
1 gig /swap
14 gig /home (ext3) (If you do not want a /home partition you would add the 14 gig to /root.)

ubuntu can read/write ntfs file systems, but its native file system is ext
You can install a small [program]("http://fs-driver.org/") for windows that allows you to read/write ext3 which you could use to

---

### Post by Krunktor on 2008-02-18
Thank you. That's really helpful. 

I guess I'm off to defrag and then finally install Ubuntu. Wish me luck.

---

### Post by oilchangeguy on 2008-02-18
> **Krunktor said:**
> Thank you. That's really helpful. 

I guess I'm off to defrag and then finally install Ubuntu. Wish me luck.

BACK UP YOUR IMPORTANT FILES BEFORE YOU START!

---

### Post by sandysandy on 2008-02-18
> **Partyboi2 said:**
> 

ubuntu can read/write ntfs file systems, but its native file system is ext
You can install a small [program]("http://fs-driver.org/") for windows that allows you to read/write ext3 which you could use to

once this program is installed and windows can be used to read / write ext3 files, could virus/ malware destroy the data on linux drives ( when booting from windows  ; When booting from Linux, i suppose there is no problem)

regards

---

### Post by Krunktor on 2008-02-18
> **oilchangeguy said:**
> BACK UP YOUR IMPORTANT FILES BEFORE YOU START!

Already done, of course. ;)

---

### Post by Krunktor on 2008-02-19
Edit: I just realized how stupid this post was, so now it's gone. :D

---

