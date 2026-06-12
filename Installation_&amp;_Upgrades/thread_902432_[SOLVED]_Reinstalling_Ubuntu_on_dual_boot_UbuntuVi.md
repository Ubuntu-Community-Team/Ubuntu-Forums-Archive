---
title: "[SOLVED] Reinstalling Ubuntu on dual boot Ubuntu/Vista. How do I keep Vista as is?"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by Persida on 2008-08-27
I'm sure this has already been covered somewhere but that are so many threads on similiar topics I couldn't find it, so apologies. 

I am currently dual booting Vista and Ubuntu. I made some changes in permissions to Ubuntu and have been told it would be best to just reinstall it now before I start running into major problems. 

When I insert the Ubuntu CD to reinstall I get only two options for partioning, one is to use the whole disc and the other is manual. I don't want to use the whole disc as I'd like to keep the Vista partition unchanged if possible. 

I'm assuming the easiest way to do this would be through the Vista disk managment tool. I have 4 partitions displaying; the c: drive where Vista is installed, the Vista recovery partition and two "healthy" primary partitions, one of 5.43 GB and the other of 128 GB, I'm unsure which one Ubuntu is installed to, but I'm assuming the 5.43GB (on a side note does that mean I have 128G of wasted space?).

Would deleting these two non-NTFS partitions and then trying to reinstall Ubuntu give me the option in the install to use 'the most available space' again like it did in the original set up? and if so would that mess with the ability of Vista to boot when those partitions have been deleted considering I'm using the Ubuntu bootloader (I know nothing about bootloaders, I just know I didn't do the extra steps to revert back to the Vista bootloader :P)

Hopefully that makes sense to someone :s 

Thank you for any help you can provide. 

Persida.

---

### Post by sephiroth2212 on 2008-08-27
If you boot from the live CD theres a partitioning tool under 
System > Administration > Partition Manager
You can edit delete your Ubuntu partition there and then just configure it manually when installing.
And upon finishing installation the Grub bootloader will recognize vista automatically.
If you want more detailed instructions just PM me. :)

---

### Post by mikewhatever on 2008-08-27
See if this helps you [http://ubuntuforums.org/showthread.php?t=900678](http://ubuntuforums.org/showthread.php?t=900678).
You definitely don't need Vista tools to reinstall Ubuntu.

---

### Post by Persida on 2008-08-27
Oh, I probably should have added that it's Ubuntu 8.04.

---

### Post by Persida on 2008-08-27
lol, wow thanks for the quick replies, two while I was just adding something to my post. 

I'll try using the live CD first. 

Thanks again :)

---

### Post by Persida on 2008-08-27
Got it all worked out, thanks for all the help.

---

