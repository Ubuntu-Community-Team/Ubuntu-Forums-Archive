---
title: "Win 7 RAID + Ubuntu 9.10"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by nakednorman on 2010-02-26
Hello Gurus,

Since October I have been running Windows 7 on a 4 disk RAID 10 set-up (fakeraid).  It's been very stable - will run for weeks, or cold start every day with no problems.

But I got bored & wanted to try Ubuntu 9,10 :p

I installed 9.10 onto a separate, 5th disk (IDE) and with the help of 'Darkod' and EasyBCD got it dual booting.

Now the problem:
I can switch fron Win7 to Ubuntu with no trouble and Ubuntu runs well.  But whenever I try to switch back to Win7 after I have been into Ubuntu then my RAID 10 disks come up as "Offline Members" (I can recover from this but it is rather annoying).  It fails whether it is a restart or a cold start.

If I don't use Ubuntu then my RAID disks _***always***_ come up in "Normal" mode, whether it's a restart or a cold start.

My question is, "Would installing 'dmraid' help with this?"
I don't actually need Ubuntu to read my RAID disks - I would just be grateful if it left them alone :p

Regards,
NN

---

### Post by Objekt on 2010-02-26
Are you in any way accessing any of the Windows 7 RAID members while you run Ubuntu?  I've found that fakeRAIDs will force you to spend half an hour - if not longer - "rebuilding" the RAID, if you so much as mounted one of the disks in a different OS, which wasn't running on the RAID.  This irritation, along with the basic impossibility of getting Ubuntu installed on my fakeRAID, lead me to give up using the RAID features of my ICH9R chipset with Windows XP.

Generally Ubuntu will refuse to touch NTFS volumes by default, unless explicitly told to do so.  

Where is GRUB's bootloader installed?  If it is on the MBR of the 5th disk, the one on which you installed Ubuntu, you shouldn't have this problem.  If, however, the bootloader was installed on one of the RAID members, this may explain your issue.

---

### Post by nakednorman on 2010-02-26
Thanks for the reply.

All other disks were disconnected when I installed Ubuntu on the "5th disk" because the bootloader trod all over the first disk in my RAID on my first iattempt.  The (Grub?) loader is on the 5th disk and I used EastBCD from Win 7 to set up the dual booting.

When Ubuntu is running, it doesn't appear to see my RAID disks at all, only itself on the 5th disk and the 6th & 7th IDE data disks. But the RAID disks always come back as "Offline Members" after I have been into Ubuntu.

NN

---

