---
title: "Partitions lost in Gibbon upgrade"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by gulliver on 2008-04-16
Hi all,

Thanks in advance for any ideas

Is there something up with the Gibbon's ability to handle partitions? My family internet PC is set up with accounts and corresponding partitions for multiple users (my partner, my kids and visitors). I had been using my current partition arrangement with Mandrake/Mandriva for several years with no problems, then I tried a clean installation with 7.10. 7.10 would not use the four partitions after /home and /home/[administrator] - There were no UUID's in fstab for these drives so I assumed this was the problem and searched the forums to figure out how to consruct them. I eventually gave up and installed Feisty Fawn instead. No problems with 7.04, all the drives were seen and everything seemed to work as usual. Then my printer/copier/scanner died; I was given a printer and a Canon canoscan N670U. The printer was fine but the scanner only gave black scans and XSane would only start on a sudo command from a terminal. I went online to search in the forums and the best advice for the scanner problem seemed to be to upgrade to 7.10 in order for the scanner to be seen and work correctly. I upgraded live to the Gibbon and scanner problem solved. But, the same drives that were not seen on my first try with 7.10 are again unseen, despite this time having UUID's in fstab... 

The Details:

Boot halts with:-

fsck.ext3: Unable to resolve 'UUID=etc., etc.,....
fsck died with exit status 8
     ...fail
*File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
* A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
bash: no job control in this shell
bash: groups: command not found
bash: dircolors: command not found

(Control-D doesn't work, but ENTER, control-D does)
/var/log/fsck/checkfs produces this file which hasn't been overwriten since april 7th when I upgraded

Log of fsck -C -R -A -a 
Mon Apr  7 21:53:11 2008
fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb2: 2065 files, 76517/1048190 clusters
/dev/sda1: clean, 37/16064 files, 34838/64228 blocks
/dev/sda14: clean, 3393/396800 files, 45122/793201 blocks
fsck.ext3: Unable to resolve 'UUID=d4a4fe2a-ad3c-41b4-9d77-f0ec76d10e4c'
/dev/sda15: clean, 31046/3760960 files, 3146182/7512387 blocks (check in 5 mounts)
fsck.ext3: Unable to resolve 'UUID=17f93fd8-8b05-4cad-9463-8cf1cf427de3'
fsck.ext3: Unable to resolve 'UUID=d06b9db4-5e21-4ced-b09f-703624c704fd'
fsck.ext3: Unable to resolve 'UUID=19a0b026-e1f3-4d73-9346-88a499df501d'
/dev/sda13: clean, 17/794976 files, 63599/1588419 blocks
/dev/sda10: clean, 11/264384 files, 25484/528129 blocks
/dev/sda7: clean, 1452/530112 files, 59993/1058274 blocks (check in 4 mounts)
/dev/sda11: clean, 197922/1060800 files, 1150974/2118564 blocks
/dev/sda12: clean, 51/530112 files, 51559/1058274 blocks
/dev/sda8: clean, 15349/530112 files, 460612/1058274 blocks
/dev/sda9: clean, 11/131616 files, 12669/263056 blocks
fsck died with exit status 8
Mon Apr  7 21:53:16 2008

NB All partitions seem to be designated as sda despite the fact that the PC has only IDE hard drives
So I tried to rename /var/log/fsck/checkfs to /var/log/fsck/checkfs.bak to see if boot would write a new file but got this:- 

root@ariadne-desktop:/var/log/fsck# rename checkfs checkfs.bak
Bareword "checkfs" not allowed while "strict subs" in use at (eval 1) line 1.

Which from my searching about online seems to be something to do with perl-script. at this point things are beyond my competence. If I ask GParted for info on these drves I get:-

Attention
e2label: No such file or directory while trying to open /dev/sda16
Couldn't find valid system superblock.
Couldn't find valid system superblock.
dumpe2fs 1.40.2 (12-jul-2007)
dumpe2fs: No such file or directory while trying to open /dev/sda16
Impossible de lire le conteu du système de fichiers!
Pour cette raison quelques opérations peuvent être indisponibles.

If I open QTParted on a sudo command I get this in the terminal:-

X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Error: Le système de fichiers n'a pas été démonté proprement ! Vous devriez exécuter e2fsck. La modification de ce système de fichiers pourrait provoquer de sérieux problèmes de corruption.
Error: Le système de fichiers n'a pas été démonté proprement ! Vous devriez exécuter e2fsck. La modification de ce système de fichiers pourrait provoquer de sérieux problèmes de corruption.
Error: Le système de fichiers n'a pas été démonté proprement ! Vous devriez exécuter e2fsck. La modification de ce système de fichiers pourrait provoquer de sérieux problèmes de corruption.
Error: Le système de fichiers n'a pas été démonté proprement ! Vous devriez exécuter e2fsck. La modification de ce système de fichiers pourrait provoquer de sérieux problèmes de corruption.
Error: Le système de fichiers n'a pas été démonté proprement ! Vous devriez exécuter e2fsck. La modification de ce système de fichiers pourrait provoquer de sérieux problèmes de corruption.
Error: Le système de fichiers n'a pas été démonté proprement ! Vous devriez exécuter e2fsck. La modification de ce système de fichiers pourrait provoquer de sérieux problèmes de corruption.
Error: Le système de fichiers n'a pas été démonté proprement ! Vous devriez exécuter e2fsck. La modification de ce système de fichiers pourrait provoquer de sérieux problèmes de corruption.
Error: Le système de fichiers n'a pas été démonté proprement ! Vous devriez exécuter e2fsck. La modification de ce système de fichiers pourrait provoquer de sérieux problèmes de corruption.
Error: Le système de fichiers n'a pas été démonté proprement ! Vous devriez exécuter e2fsck. La modification de ce système de fichiers pourrait provoquer de sérieux problèmes de corruption.
Error: Le système de fichiers n'a pas été démonté proprement ! Vous devriez exécuter e2fsck. La modification de ce système de fichiers pourrait provoquer de sérieux problèmes de corruption.
Error: Le système de fichiers n'a pas été démonté proprement ! Vous devriez exécuter e2fsck. La modification de ce système de fichiers pourrait provoquer de sérieux problèmes de corruption.
Error: Le système de fichiers a une option incompatible d'activée.

BUT!!! If after all these horror messages that make me think I've lost all my kid's files, I put the Feisty Fawn live cd back in the drive and reboot, all four problem drives (sda16 through sda19) are immediately seen, the file systems are intact and usable and the files themselves seem fine. Nothing at all seems to have happened to them since before I upgraded!
Sorry if the answer should be obvious to anyone who knows what they are doing but I have searched the help files (at least those that I could understand) and the forums and I am lost and completely out of my depth with a situation where I can either acess a scanner or my family's partitions but would have to continuously change between the Gibbon to the Fawn to acess both. Help please! I'm not a tech-head, nor exactly a newbie, just an end user who has been loving the idea of Linux but struggling with and swearing at it in reality for the last 15 years.

---

### Post by dstew on 2008-04-16
This sounds like a bug in the Gutsy fsck or other program responsible for file system maintanence. You have a lot of partitions, and maybe something in your unusual system has provoked this. Probably fewer than one in a hundred regular users has this complex a partition setup, so it might be very rare to see this bug. Maybe it is only seen when you have more than 10 partitions.  I suggest you post a bug report on launchpad. The fact that it works OK in Feisty smells of bugginess in Gutsy.

---

### Post by gulliver on 2008-04-16
Thanks for your prompt reply dstew. Wow! I never thought of my system as unusual! I found that if I kept win, boot files, programs and user files on separate partitions back in the days of 3.11 then I could keep the whole thing more stable. The kids were let loose on a c64 at 6 months old so when they got at the family PC it seemed safer to give them their own partitions to mess up. I suppose I just got into the habit of multi-partitioning as I seemed to have a lot less re-installs of any OS than my friends. I'll do a bug report and see what happens.

---

