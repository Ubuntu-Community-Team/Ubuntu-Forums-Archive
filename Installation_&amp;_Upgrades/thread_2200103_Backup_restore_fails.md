---
title: "Backup restore fails"
date: 2014-01-17
forum: Installation &amp; Upgrades
---

### Post by SteveTyrer on 2014-01-17
I am restoring all my data from my old Ubuntu 12.04 32bit system to a new Ubuntu 13.10 64bit system (on the same computer but a full reinstall)
deja dub keeps stopping with this warning

"Invalid data - SHA1 hash mismatch for file:
 duplicity-full.20131206T092901Z.vol133.difftar.gz
 Calculated hash: d7010d8ca5b368b9c34c97de2fe729473a7f38bd
 Manifest hash: eeab0b2d4620c9a8f4f09ee2591a9d26f44bad0f"

Any thoughts on what is happening

---

### Post by tgalati4 on 2014-01-18
The data is probably OK.  I would guess a mismatch between 32-bit and 64-bit.  This is a use case that I'm sure *deja-dup* was not designed to handle.  Find (or build) a 32-bit machine and perform the restore and if that is OK then simply transfer the files manually to the 64-bit machine.

---

### Post by SteveTyrer on 2014-01-18
Thanks for that I will give it a try, and report back

---

### Post by SteveTyrer on 2014-01-18
Tried importing to 12.04 32bit but it failed at the same point, so looks like the backup is corrupt, I have retrieved 90% of my data so no big problem, but I would like
to understand what went wrong.

---

### Post by tgalati4 on 2014-01-18
This may be your first experience with [bit rot]("http://en.wikipedia.org/wiki/Bit_rot").  Since the file was dated December 2013, it's most likely a hard disk problem.  Check the SMART status of the drive to see if any errors were logged.

---

