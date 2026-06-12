---
title: "My upgrade destroyed my '/home' partition"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by adm1968 on 2010-08-29
[FONT="Georgia"][SIZE="2"]I have just upgraded my desktop from 9.10 to 10.04.

I have followed exactly the same steps I always stick to when upgrading:

Manual partitioning,
Reformatting my '/' partition, and
Leaving my '/home' untouched

I have done this maybe 20-30 times, and have always found my /home partition with all existing documents/setups (those in the hard drive before the upgrade)

However, on this ocassion, NOTHING can be found
My '/home' partition is now EMPTY, with no traces of existing documents/setups

I am positive about NOT checking the 'format' partition during the installation process using the Live CD

Any ideas, please??
This could me a major disaster[/SIZE][/FONT]

---

### Post by akoskm on 2010-08-29
Is it possible that you've missed the mount points for your partitions?
I mean, there are 2 partitions: sda1 - with ubuntu installed, and sda2 - with your home directory.
You have formatted sda1 and set the mount point to /home, and left sda2 unchanged and set the mount point to /?
Such a thing happened with me once, it hardly imaginable but it's possible...
But here is another way to find out is it really wiped or just mounted somewhere else, do a *find* for some unique filename what you know that it was 100% in your home directory.
Also make sure that all of your drives are mounted!

---

### Post by adm1968 on 2010-08-29
> **akoskm said:**
> Is it possible that you've missed the mount points for your partitions?
I mean, there are 2 partitions: sda1 - with ubuntu installed, and sda2 - with your home directory.
You have formatted sda1 and set the mount point to /home, and left sda2 unchanged and set the mount point to /?
Such a thing happened with me once, it hardly imaginable but it's possible...
But here is another way to find out is it really wiped or just mounted somewhere else, do a *find* for some unique filename what you know that it was 100% in your home directory.
Also make sure that all of your drives are mounted!
[FONT="Georgia"][SIZE="2"]Not possible, I'm afraid; I am extremely careful whenever I handle partitions.
This time I clearly remember checking the box to format the '/' partition, but leaving the box unchecked for '/home'.

I also checked it out following your advice, searching for known files (using the Live CD: no luck)

Any tools/methods out there to recover the information in the old '/home' partition?

Many thanks for your help, much appreciated[/SIZE][/FONT]

---

### Post by arrange on 2010-08-29
If you are sure the partition has been erased/formatted, then TestDisk (and PhotoRec, which is part of the *testdisk* package) is the way to go. Good luck.

---

### Post by akoskm on 2010-08-29
> **adm1968 said:**
> 
...
I also checked it out following your advice, searching for known files (using the Live CD: no luck)
...


So, you booted using the LiveCD and did the search in this LiveCD-mode. Because in this case you searched for the unique file in the LiveCD's temporary filesystem, where the existing filesystems (/ and the unformatted /home) weren't mounted at all - it's possible.
I suggest you to reboot the system, without any LiveCD tricks and first time when you reach the command line do a search:
```

find -name <unique file>

```,
replace the <unique file>.
It would be also good to post the output of
```

sudo fdisk -l

```, and we can see if something is missing or isn't mounted.

---

### Post by adm1968 on 2010-08-29
[FONT="Georgia"][SIZE="2"]Will try both methods
Thank you, both of you![/SIZE][/FONT]

---

### Post by adm1968 on 2010-09-07
[FONT="Georgia"][SIZE="2"]Hi again.
With the search method nothing could be found.
With PhotoRec I did manage to recover a huge amount of files (some 100 GB).
The main drawback: I lost file names. I will need quite a few hours to assign the correct names to so many different things
BTW, I also gave EraseUs Wizard Professional a go. This app was rather powerful, but file names were equally messed up.

Many thanks indeed for all your help!
;)[/SIZE][/FONT]

---

