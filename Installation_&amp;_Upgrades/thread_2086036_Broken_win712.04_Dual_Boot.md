---
title: "Broken win7/12.04 Dual Boot"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by IanGP on 2012-11-19
Hi there,
So I decided to dual boot Win7 and 12.04, and on doing this I managed to break something... guessing MBR (hoping it's not the entire partition). Menu shows Ubuntu, Win7 and vista boot options, but get errors on the Win options.

[http://paste.ubuntu.com/1371207/](http://paste.ubuntu.com/1371207/) shows the output from Boot-Repair.

Any ideas as to what I can do to fix this?

Cheers.
Ian

---

### Post by darkod on 2012-11-19
STOP using the computer RIGHT AWAY!

You overwrote your win7 partition with ubuntu. The more you boot ubuntu, the less data you can save.

Use only the ubuntu cd in live mode, do not boot from the hdd.

In live mode, download testdisk and run it. Do the deeper search as explained, and post the screenshot of the results.

If you can figure out which partition you need to restore, you can continue, otherwise ask for help before you do anything.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

It looks like you used the manual partitioning to install and you told it to use the win7 partition so it installed over it.

Usually testdisk can help, but if it doesn't, do you have backup of your data?

---

### Post by darkod on 2012-11-19
PS. On second look it mght not be as bad as I thought, but the win7 partition is not shown. Still, there is some space after the ubuntu partition so it might be there.

In any case, I would work only from the ubuntu live mode until this is sorted out, and I would scan the disk with testdisk to see what it shows.

---

