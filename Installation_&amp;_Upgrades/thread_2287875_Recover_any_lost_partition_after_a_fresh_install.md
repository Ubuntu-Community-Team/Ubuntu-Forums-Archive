---
title: "Recover any lost partition after a fresh install"
date: 2015-07-22
forum: Installation &amp; Upgrades
---

### Post by Pascal_Paquin on 2015-07-22
SO after my problem with 14.10, I decide to make a fresh install from the dvd I had (13.10) and then update it to 14.04.
In the option when I was installing it, I choose to erase 14.10 and install in new.

All my data was on a separate partition, but it seems that ubuntu decide to remove all partition on my disk and just did 1 big partition, so I lost everything that was on my second partition.
Is there anything that can be done to recover that partition ?

---

### Post by Bucky Ball on 2015-07-23
Do a clean install of 14.04. 13.10 is dead in the water and don't think you'll be able to upgrade to 14.04 from there as the repos are no longer maintained for 13.10.

Stop using that drive/partition immediately and boot from live media to fix. Photorec and Testdisk are your friends. 

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

Testdisk description:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Photorec description:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Good luck.

---

### Post by Pascal_Paquin on 2015-07-23
I was able to recover that partition with Testdrive, what a powerful tool.
Now it's backing up all my data on an usb drive I have, just in case something else happen.

And for the upgrade part, I was able to upgrade up to 14.04 without any problem

---

### Post by Bucky Ball on 2015-07-23
Fantastic news and thanks for marking the thread as solved. Yes, Testdisk is our friend. Enjoy! :)

---

