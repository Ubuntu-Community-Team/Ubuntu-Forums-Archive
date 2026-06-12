---
title: "Decission about RAID1 / backup"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by madtyn on 2010-05-30
Hi everyone,

I had a great fail with one of my partitions and thanks to the [ironic mode] wonderful partition Windows tool [/ironic mode], I have got to re-install  Ubuntu 10.04.

My problem is that I don't want to lose my data again (most of the info was difficult to find and result of many years downloading). Now I wanted to start doing things better so, if anything happens, I can recover my data. Thus, I would like to use some kind of mirroring system, backup or whatever. The goal is having the same data just equally copied in somewhere else (and well synchronized) .


In the start, I thought making a RAID1, although I haven't got much experience (I only did some easy few examples with mdadm), so I have some doubts.


1) The first one is... ¿which is worth? Making RAID1 or making incremental backup with cron and tar (or similar tool). I think RAID1 is supposed to be instantaneous and well synchronized and it has good performance. The problems about RAID1 are the following doubts:

[INDENT]
[LIST]
[*]Both disks (original and mirror) have to share filesystem?
[*]Can I write data on the disk from Windows or Linux (ntfs)?
[*]Can I expect the data to be synchronized?
[*] Is the same writing in disk 1 or disk 2?
[/LIST]
[/INDENT]

2) I was interered also if I can make RAID1 which a subtree from one disk because I only need a very specific info from one folder in my disk to be safe. 

[INDENT]
[LIST]
[*]I'm forced to make a whole partition o can I tell mdadm to only duplicate the subtree growing from this folder? 
[*]Does any of the partition have to be a special partition (primary, phisical,  logical...)?
[/LIST]
[/INDENT]

3) Any advices would be welcome. Many howtos do tell how to make the raid, but not explain the requirements or don't match my intentions. I'm trying to make the RAID using different physical disks

Very very thank you.

PD: I hoped this forum is right for this post. The HOWTOs I looked didn't helped me with my doubts. Sorry for my poor English.

---

### Post by sites on 2010-05-30
A couple of questions, to help better understand your predicament.

1) Which partition did you lose, or almost lose, data from?  NTFS?  /home?

2) Are you creating a separate /home partition when installing Ubuntu?

---

### Post by madtyn on 2010-05-30
1) I lost my /home partition with a reiserFS filesystem on it.

2) I'm thinking about how to make the new partition scheme/model and how to distribute space among the new partitions but, yes, I want to make again a separate /home partition.

   The point is that I don't know if I should make more partitions in order to make the raid or not. I don't know either if I should use raid1, backup through crontab, or both.

---

### Post by whoop on 2010-05-30
RAID != backup.
If you don't want to lose data, you need to backup....

---

### Post by madtyn on 2010-05-30
I know that RAID != Backup, but when you have a mechanical failure on a disk, you have the mirror with all the latest information, if I'm not wrong.

The backup would mean also leaving always the PC on and I don't want to waste money nor energy when I'm at work. I think it would affect performance too.


If I'm mistaken, just tell me, please.

---

### Post by sites on 2010-06-01
RAID 1 does provide a measure of protection from data loss, but it's not in any way a guarantee.  If corrupted data is written to the mirror, both copies are compromised in real time.  There are many factors to consider, not the least of which is your hard drives.  If they aren't RAID class drives you're chances of failure increase.  Using four hard drives would help, but can become quite expensive.  In any case you should have a backup solution in place, even if you're using a multiple RAID array.  A combination of mirrored disks with something like an rsync backup might be the best solution.  You might also want to consider off-site backups.  Perhaps using two external drives, alternately taken off-site every other day after backing up, for example.  Then you have the cloud option to consider.

The more information you can give about your data, reasons for one file system over another, etc.... the better advice you may get here.  I'm not the best source of advice on the entire topic, but here you have the best advice i can offer at the moment.

---

### Post by madtyn on 2010-06-02
Well. The point is that I have an already used 500GBs disk and a new 500GBs disk. In the old one I have Ubuntu (without the 'broken' /home partition) and WinXP. The new one is completely empty. Both are SATA disks. In the old one I have about 400 GBs free.

About the data I'm interested in preserve and backup, it consists of pdf files mostly. Many sheet music in various formats and extensions, but mainly pdfs with an average size of 1-2 MBs to 10 MBs.

Thus, my interest is to have the 15 GBs (and growing...) data folder being safe against virus, mechanical failures, another partitioning from a tool and anything it could affect the files.

I know that if I delete accidentally a file, it will be lost forever so only the backup would be worth for that case. But if I had a mechanical failure, maybe the backup didn't sinchronyze the last changes (it can't be making backups every minute, it would affect the performance).

So I'm almost sure of making a hybrid decission because I0ve got plenty of disk space now.

If anymore info is needed, just ask for it. Thank you very much.

---

### Post by sites on 2010-06-04
You need a third disk to backup your data before creating a RAID with your two 500GB drives.  When you create the RAID they will both be formatted.  In fact, I'm not too sure you can setup RAID with a dual boot.  There's an old thread on the subject [here]("http://ubuntuforums.org/showthread.php?t=496803").

---

### Post by madtyn on 2010-06-04
It's no possible making raid for an only partition? Have I got to format the whole disk and make the RAID with the whole disk?

This is not what I expected. If this is true, maybe I should change my mind and accept the backup solution alone.


I'm going to look in few minutes the thread you passed me, thanks.

---

### Post by madtyn on 2010-06-04
Ok, I read the issue, but this talks about a window software RAID0 and I want to make a Linux software RAID1.

It's obvious that when I boot windows, the RAID will not be active, because the partition can't be seen. But I want to know whether the Linux RAID1 will recover the complete state when I boot via the Linux OS.

Any ideas out there¿? They will be appreciated. Thanks.

---

### Post by whoop on 2010-06-04
I use software raid1... I have two identical hard drives, I created two identical partitions (not using the entire disk space), created the raid array.

This works fine. I have two distro's using the raid array (both via mdadm), and one distro not using the array, (booting windows is also possible, only you won't be able to use to the array).

---

### Post by madtyn on 2010-06-08
I'm late with my reply, sorry for being so late.

As I thought, you can make two partitions with a RAID1 independently from the others in both disks. It's very valuable for me knowing it.

  If I understood you correctly, I can't make the RAID1 over a NTFS partition, so I'm forced to do it on a ext3/reiserfs one (I'm thinking in reiserfs). And, of course, it would be not possible accessing the linux data with write permission (I already have a Windows program that can read reiserfs: "yareg.exe"). 

   What I'm thinking just now is making a 3-part system. The NTFS partition which I can access from both sides. This data would  backup every week with cron and be copied on the RAID1 on the two disks.

   Maybe I'm a little paranoid, but I would be comfortable about my data. Anyone doesn't agree?

Thanks about your information, it helps me a lot.:KS:KS:KS:KS:KS

---

