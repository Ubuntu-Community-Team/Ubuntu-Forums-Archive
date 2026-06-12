---
title: "Ubuntu has totally screwed my partition table- HELP!!!"
date: 2005-05-02
forum: Installation &amp; Upgrades
---

### Post by leezer3 on 2005-05-02
What could be a major problem here- Installed 4.10, formatting the older Linux partition in the process. When Windows didn't boot, I assumed that it was because I had set the bootable flag, & so I restored from recovery CDs. Now I'm getting CRC check errors on my Windows drives. This led me to try & check them, and Partition Magic 8 tells me that 
> The hard-disk partition table contains two inconsistant descriptions of the number of sectors on the hard-disk. This error is serious if both DOS and another operating system use the hard-drive. Because DOS uses one description and other operating systems use the other data loss is likely once the partition is almost full.
Because of this, I then poked around on the net, & found this site, which describes my situation exactly, even down to the number of heads:
[http://lwn.net/Articles/86835](http://lwn.net/Articles/86835) (Note: even though the stuff in there only specifically refers to RedHat, it appears to be a general kernel bug- See later comments)
Trouble is, I can't get the commands listed in the article to do anything :(
Can someone please tell me exactly what I have to type in a Ubuntu root console to put this mess right?

:(

Thanks

-Leezer-

---

### Post by BAshworth on 2005-05-02
I had this problem a few times.  Here are some quick things to check first.  The fix on the page you linked too is particular to Fedora (and didn't work for me when I had this issue.)

1) Quick Fix:  Go into your BIOS, and set your drive access mode to LBA.  It typically is on Auto, and that causes Windows to take a look at the CHS values in the partition table, even though it doesn't use them.

2) If that doesn't work.  Use your Windows recovery CD, and do the fixboot, fixmbr.  Chang the drive access mode to LBA, and then reinstall Grub.

3) Much longer version:  Do above, but reinstall Grub to the first sector of the partition that Ubuntu is in, then you can use Windows' boot.ini to switch between which image to boot.

---

### Post by leezer3 on 2005-05-02
Thanks for the reply.

#1- I don't have access to the 'proper' BIOS of this machine- It's a Tecra S1, & Toshiba only provide a s*** Windoze util, which makes no mention of LBA (Otherwise I would have already done that).[COLOR=Red]Edit:[/COLOR] Finally got into the BIOS- Only mentions IDE & Enhanced IDE (Set to this)

#2- Only a Toshiba restore CD; All it has is Norton Ghost images- No use :(

Thanks

-Leezer-

---

