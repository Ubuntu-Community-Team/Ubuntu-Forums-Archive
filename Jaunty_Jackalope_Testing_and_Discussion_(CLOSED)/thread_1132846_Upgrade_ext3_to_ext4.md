---
title: "Upgrade ext3 to ext4"
date: 2009-04-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dox_drum on 2009-04-22
Hi guys.

A.f.a. I know it is possible to upgrade from ext3 to ext4. How may I do that? Should I upgrade to intrepid first and then change the extension of the partitions?

Thank you so much.

[CENTER]Enjoy![/CENTER]

---

### Post by Sef on 2009-04-22
> A.f.a. I know it is possible to upgrade from ext3 to ext4. How may I do that? Should I upgrade to intrepid first and then change the extension of the partitions?

It would best to do a clean install.   You need to add a boot partition; otherwise, the current stable grub will not see ext4.

---

### Post by MadCow108 on 2009-04-22
tutorial to convert from ext3 to ext4:
[http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)

---

### Post by taavikko on 2009-04-22
> **Sef said:**
> It would best to do a clean install.   You need to add a boot partition; otherwise, the current stable grub will not see ext4.

Converting fs is also possible, [http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4](http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4)
But would recommend using clean install
also for partitioning /home on separate partition if there wasn't one before

Also, separate /boot isn't necessary.

---

### Post by matthew.ball on 2009-04-22
I was reading a thread earlier* (how many people ask this question :p) about a poor guy who was running an earlier version of Ubuntu and converted his partition to ext4 - whenever he tried to access it he got an error message saying "cannot read ext4"... I'm not sure what this means entirely, but the suggested fixes were more or less along the lines of "use a jaunty live cd and convert the partition back" - I don't remember if they said it was jaunty specific, or perhaps kernel specific.

I suggest going to intrepid, then to jaunty, then convert your partition to ext4 - but don't ask why I say this, it just seems to be the "path of least resistance" :)

Edit:
*Here: [http://ubuntuforums.org/showthread.php?t=1118205](http://ubuntuforums.org/showthread.php?t=1118205)

---

### Post by dox_drum on 2009-04-22
Thank you very much to all of you.

I guess the best way is to do a clean installation... specially 'cause I don't have a separate /home partition.

[CENTER]Enjoy![/CENTER]

---

