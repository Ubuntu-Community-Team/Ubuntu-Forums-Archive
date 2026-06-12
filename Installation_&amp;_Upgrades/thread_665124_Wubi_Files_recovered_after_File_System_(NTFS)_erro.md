---
title: "Wubi Files recovered after File System (NTFS) error check"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by MichaelAustralia on 2008-01-11
Hey Everyone,

Yes I am new and I have joined your forum for a very specific reason. My Ubuntu (wubi installation) fails to start, and chkdsk on my ntfs drive finds and recovers files. I need some assistance placing these files back under the wubi directory to fix this issue.

here is a cmd print out:

 Directory of C:\found.000\dir0000.chk

08/01/2008  01:39 AM    <DIR>          .
08/01/2008  01:39 AM    <DIR>          ..
03/01/2008  08:33 PM     2,000,000,000 home.virtual.disk
01/12/2007  02:36 AM       511,000,000 swap.virtual.disk
03/01/2008  08:33 PM    12,489,000,000 system.virtual.disk
               3 File(s) 15,000,000,000 bytes
               2 Dir(s)  57,078,394,880 bytes free

can anyone please help?

Cheers,
Michael

---

### Post by MichaelAustralia on 2008-01-12
I discovered the directory those files belong in is the /wubi/disks directory and moved them back now everything is back to how it should be.

Thanks anybody who took the time to read.

---

