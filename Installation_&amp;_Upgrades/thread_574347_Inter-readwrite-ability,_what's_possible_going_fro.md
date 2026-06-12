---
title: "Inter-read/write-ability, what's possible going from Vista to Vista/Kubuntu dual?"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by Eoghanalbar on 2007-10-12
I know HOW to set up the dual boot, but before I do, what's possible as far as read/writing files on the other OS's partition after I add linux, and how might I increase the possibilities? 

For example, all my music files are gonna be in the vista partition. Will I be able to find and play them from  kubuntu? Would it be straightforward, or would it involve having two copies of each file on the computer?

 If I wrote an essay in kubuntu and wanted to access if while under vista for some reason,  would that be possible?

Stuff like that.

My vista partition is NTFS (no further specifications offered under computer management in vista).
Could/should I format the kubuntu partition as any particular file type or something to make for better communication possibilities or something?

Am I even asking the right questions here?

---

### Post by Pumalite on 2007-10-12
Out of the box you'll have 'read' rights to ntfs partitions. You need to install ntfs-3g to have 'read and write' rights to your ntfs partitions. That's it.

---

### Post by Jose Catre-Vandis on 2007-10-12
And to go the "other way", i.e. read / writing from Vista onto Ubuntu (ext3), install Ext2_ifs on Vista (it will complain a bit but you eventually get there!)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

I also use nfs from my remote servers, and nfs compatibility is available in Vista (Features)

---

