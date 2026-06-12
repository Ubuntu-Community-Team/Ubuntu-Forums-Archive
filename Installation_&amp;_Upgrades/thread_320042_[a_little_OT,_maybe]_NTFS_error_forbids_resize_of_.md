---
title: "[a little OT, maybe] NTFS error forbids resize of partition..."
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by MadeR on 2006-12-16
...and thus I can't install Kubuntu on my Travelmate C102Ti :(

K- and g-parted do not success resizing the windows NTFS partition.
So I installed Partition Magic 8.1 and tried to resize the windows partition.
I get the following [error](http://service1.symantec.com/SUPPORT/powerquest.nsf/6c360f88152ecfce88256e91005066ac/e6223d1630e8ad8388256e8d006a841e?OpenDocument&prod=Norton%20PartitionMagic&ver=8.x&src=sg&pcode=npmagic&svy=&csm=no) (from symantec site)

***[B]#1529 Information mismatch in directory entry***[/B][I]
A file attribute stored in a file record is different from the attribute stored in its directory entry. If this error is in a system file (file 0&#8211;10), Windows NT CHKDSK does not fix it, but Windows NT rebuilds the root directory on the partition the next time the operating system is started.[/I]

Google tells me that someone suggests running the *chkdsk /f* program to fix the problem, but, of course, chkdsk doesn't solve the problem.

Now the linux questions:
is there a linux better tool than windows chkdsk to fix a ntfs partition?
is there a less kind program to resize a windows partition or a way to find the file with the attribute error and delete it?

thanks!

---

