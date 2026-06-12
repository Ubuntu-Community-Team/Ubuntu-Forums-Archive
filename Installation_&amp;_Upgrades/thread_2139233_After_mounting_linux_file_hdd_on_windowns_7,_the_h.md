---
title: "After mounting linux file hdd on windowns 7, the hd partition is gone."
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by mrsousa on 2013-04-26
Hello there, 

I have two hd, one is for systems and the second for files.
I wanted to have a dual boot linux and win7. I have install win7 with success.
On win7 , I tried to "mount" the second hd (linux file hd) and a dialog open asking if I wanted to write on the MBR or GPT. Not knowing that this will create a Windows Reserved Partition I said yes.

The problem:

Now on linux, my partition is gone, I can't see it on my "computer" window. But, if I go to the media folder, and try to open the hdd I can see only 4 files.
On Gparted my hd has only one partition and the rest of the space is marked as unallocated. 

Does anyone have I idea to what should I do?

----- What did not work -----
- Tried Gpart to recover partition table, It sees the old partition, but say that can't recover;
- Tried Testdisk but couldn't recover either. 


Thanks, 
David Sousa

(ESL, sorry if was hard to understand)

------------- Edited ---------
The problem may have been occurred during installation.

---

### Post by oldfred on 2013-04-26
Did you try deeper search with testdisk. If that does not work then the only choice may be photorec. I have used photorec, it is slow, you have to have a lot of recovery space on another drive, it only finds extensions, not full file names. Then the process of sorting files can take a long time. It also finds deleted files. I had saved some text files many times and it found all, I never was sure I found most recent. I had to compare to old backups each copy it found for each and every text file. Photos & music have meta-data to help rename.

Do not use Windows tools on Linux, Windows does not see Linux partitions.
A Windows system reserved partition is a small totally unformatted space Windows requires on gpt partitions just before the main Windows install. So it converted it to unformatted.
       Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Best to use Windows tools on Windows systems and Linux tools on Linux systems.

---

