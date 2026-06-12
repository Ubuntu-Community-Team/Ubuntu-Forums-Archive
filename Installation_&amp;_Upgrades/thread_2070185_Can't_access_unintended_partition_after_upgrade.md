---
title: "Can't access unintended partition after upgrade"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by collapsing wave on 2012-10-12
I backed up my important data.  Then upgraded to 12.04 LTS through update manager.
The process didn't work. I managed to get 12.04 on what was left of the drive space (about 35 GB), but now I have a 81 GB file system showing that I can't access. It shows a lost+found folder in it, but I can't open it 
"you do not have the permissions neccessary to view the contents of 'lost+found'"

Is there a way to find out if the file system has been wiped? 

Please be advised that I use Ubuntu because I love open source. I do not know how to use it properly and therefore need clear instructions. ;-)

Thanks

---

### Post by darkod on 2012-10-12
So, you reinstalled on another partition? You didn't try to fix the original installation?

If you did install a second version, you should still be able to read the other partition. Try opening it using gksu.

Open terminal and run Nautilus with gksu:
gksu nautilus

When it opens, try opening the 81GB partition and see if it lets you.

But you could still possibly save the original install so be careful what you do.

---

### Post by collapsing wave on 2012-10-12
Thanks. Looks like it's empty, properties read 4 gb used 80 gb empty.
Why would the update wipe the HDD?

---

### Post by darkod on 2012-10-12
It shouldn't. Have you tried running fsck on that partition? Maybe it just needs few fixes.

---

