---
title: "NTFS drives gone after 7.04-&gt;7.10 upgrade"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by JebJoya on 2007-10-21
Hey all,

I would normally ask this in IRC for a quick response, as I assume this is going to be a quick fix, but...

Basically, just finished my upgrade to Gutsy from Feisty, and my 3 NTFS drives (one partition on my Ubuntu disk, 2 separate drives) have disappeared.  I used to use the ntfs-3g method as outlined on the big thread here, and (presumably thanks to the new support for ntfs drives and the methods conflicting somehow), none of them appear.  I still have /media/hda1 etc, but they are empty.  I also tried running the ntfs configuration tool (as I used to to get it to work), but to no avail.

Any suggestions as to what to do (I did search for answers, but found nothing apparently similar)

Jeb

---

### Post by User101 on 2007-10-25
> **JebJoya said:**
> Hey all,

I would normally ask this in IRC for a quick response, as I assume this is going to be a quick fix, but...

Basically, just finished my upgrade to Gutsy from Feisty, and my 3 NTFS drives (one partition on my Ubuntu disk, 2 separate drives) have disappeared.  I used to use the ntfs-3g method as outlined on the big thread here, and (presumably thanks to the new support for ntfs drives and the methods conflicting somehow), none of them appear.  I still have /media/hda1 etc, but they are empty.  I also tried running the ntfs configuration tool (as I used to to get it to work), but to no avail.

Any suggestions as to what to do (I did search for answers, but found nothing apparently similar)

Jeb

I had what I think is the same problem, and I think I managed to solve it. I have just one NTFS partition (dual-booting Windows XP MCE on the same HD as Ubuntu 7.10 Gutsy). At least Feisty used to read the NTFS partition. After upgrading to Gutsy, Nautilus did not seem to see the NTFS drive at all. CLicking on my old Bookmark for sda2 produced a Nautilus window with nothing listed.

I made sure that Windows is shut down and not hibernating (as suggested in [http://ubuntuforums.org/showpost.php?p=3589645&postcount=9](http://ubuntuforums.org/showpost.php?p=3589645&postcount=9) ). This did not help. (And now I have to spend more time if I need to run Windows again :-(

I installed Gnome Partition Editor using Applications > Add/Remove, and ran it from System > Administration > Partition Editor. which showed a yellow warning triangle with an "!" for the NTFS partition. If I highlighted that partition, and did Partition > Information from the menu, it gave an error message about being unable to access the partition.

I installed NTFS Configuration Tool Applications > Add/Remove. I then ran it from 
Applications > System Tools. I enabled Write Support for both Internal and External devices, and clicked OK. This seemed to change nothing in Nautilus.

Back in Partition Editor, I did GParted > Refresh Devices. At first this did not help either, but after doing GParted > Refresh Devices again, suddenly the triangle with the "!" changed to a more normal-looking padlock next to the NTFS partition. It now said Partition: /dev/sda2, Mountpoint: /media/sda2. 

I opened Places > sca2 (my old Bookmark), and there was my NTFS partition with all the files in good old Nautilus again! 

I created two test text documents in a folder on that partition using Applications > Accessories Text Editor. I was able to save, close, open, edit, resave, reclose and  move the documents between folders as well.

I'm not sure why it didn't work like this right after upgrading to Gutsy, but at least it seems to be fixed now.

---

