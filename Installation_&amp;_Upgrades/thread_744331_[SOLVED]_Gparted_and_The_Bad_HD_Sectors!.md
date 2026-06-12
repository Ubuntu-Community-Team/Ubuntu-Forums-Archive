---
title: "[SOLVED] Gparted and The Bad HD Sectors!"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by theravenproject on 2008-04-03
Hello again community that I love with all of my heart (And yearn to be a bona-fide member of!!)  I just went and took the plunge!  If you are wondering what I am talking about check out my post on this same forum called "Wubi with XP" or something or other along those lines...anyways...I booted up my live cd...went into gparted and began to edit my partition table.  It currently looks as follows(I didn't/wasn't able to go through with editing):
[B]
Partition              Filesystem                     Size                            Flags

/dev/sda1       (Green Box)Fat16                  2 GB                      --boot,lba  
/dev/sda2    (Lightblue Box)Extended         17.08 GB                      --lba
   /dev/sda5   (Blue/Green Box) NTFS         17.07 GB                     -----------
Unallocated                                               7.84 MB                     -----------
[/B]
**All I want to do is edit the partition table as follows:  Delete the Fat16, Resize the NTFS to 10 GB, Put the NTFS at the beginning of the table (The before/after space options escape me), now create a 500 MB FAT 32 swap, and finally take all the remaining space and create an EXT3 so that I can install Xubuntu on it.  The problem is-gparted will not let me.  It will let me delete the Fat16.  It will not let me resize the NTFS/Extended down to 10 GB but it will let me resize it up to 19.08 GB...  What do I have to do?  Just let go of my XP and wipe the whole darn thing and then install Linux?  Is that what I've finally come to?  Also-it says that my HD has a lot of bad sectors and that I should lok into replacing it immediately-is that true?**

---

### Post by prshah on 2008-04-03
> **theravenproject said:**
>  What do I have to do?  Just let go of my XP and wipe the whole darn thing and then install Linux?  Is that what I've finally come to?  Also-it says that my HD has a lot of bad sectors and that I should lok into replacing it immediately-is that true?[/B]

That's a lot of operations; as you have said, better to redo the whole thing from scratch. But this is all academic; if your gparted says you have bad sectors, better leave everything until you get the hard disk checked and replaced.

If you'd like to check it yourself, use ```
sudo badblocks /dev/xda9
``` where "/dev/xda9" is the partition reported to have bad blocks. If you get any number as output, you have bad blocks and need to replace the HDD.

---

### Post by theravenproject on 2008-04-04
Okay-so if I truly had bad sectors then my HD still may work but you are saying that if I goof with it it could be the straw that broke the camels back and then I would be screwed?  That still leaves the question as to why Gparted will not allow me to shrink the NTFS partition...by the way-I do not have Linux installed yet can I still use that command you gave me in terminal on the live cd?  Thanks a million to anyone who answers....

---

### Post by theravenproject on 2008-04-04
What about another partitioning program-why would Gparted not let me shrink (I WANT MY XUBUNTU!!!) and what else could I do to try and force it or what other programs could I use to try and do this?  If I don't replace this "Faulty HD" how long can I get away with it?  I only have about 1 month and I a m buying/building the ultimate dream machine which will probably be at least a quadruple boot system..

---

