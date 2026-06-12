---
title: "Best flags and partitions for a dual boot?"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by Toci on 2010-12-19
Hello, I need help deciding how to partition for a dual boot.

 The 298GB hard drive has:

1. DellUtility 39 MB (FAT 16)
2. Recovery partition 11 GB (NTFS)
3. Windows 7  (Now 97GB because I resized it)

 Then I created
4. Extended partition 134 GB (no flag)
 a) Linux swap 6GB
 b) Linux  / 88GB (ext3, no flag)
 c) Shared folder for Linux and Windows 39GB (FAT32 LBA)

 But based on something I read elsewhere I'm wondering if I should use GParted Live to now make the linux partition smaller, add a /home partition and add an LBA flag to it as well, specially because I plan on installing a VirtualBox.

 Any help would be very much appreciated.
 Thanks.

---

### Post by sikander3786 on 2010-12-19
First of all, Dell Utility is known to cause some problems I believe and an experienced member on that might advise better.

Secondly, you shared partition for Windows doesn't need to be FAT32. You can use NTFS as Linux supports NTFS and there are many advantages while comparing NTFS to FAT32.

Adding a separate /home partition is a very good idea as it saves all your personal files + all the application settings so all that data persists even after you re-install Ubuntu and can use the same /home partition then.

But I couldn't get this statement. Can you explain a bit?

> specially because I plan on installing a VirtualBox.

You mean you want to install Virtualbox inside Ubuntu. If so, nothing wrong then. Or...?

---

### Post by Toci on 2010-12-19
Thanks for the reply sikander.

 From what you know, do you think it would be better to wipe off DellUtility?

 And yes, I want to install a VirtualBox inside Ubuntu so it can run Windows XP, Do I need to add any special flags to the partition because of that?

---

### Post by sikander3786 on 2010-12-20
I have requested another senior member to take a look at your thread regarding the Dell Utility. Please hang in there.

And regarding Virtualbox, you don't need any extra boot flags or whatever for Virtualbox. That uses a Virtual HDD on the same partition and flags it bootable itself ;-)

---

### Post by wilee-nilee on 2010-12-20
There is one problem we run into with dells at times. dell data safe is it's name and is in the control panel add remove programs remove it before doing anything if its there.

As far as a secondary home partition I don't do that, a extra flag I don't think that is needed, and would have nothing that I know of to do with a virtual.

 If you would give us a screen shot of gparted if you can just to make sure your partitions are correct but I think your on the right track.

W7 has a great imaging/back tool that will make a copy of the whole thing onto a external HD for later reloading I would get the back up set, and a recovery disc set before any installs. It will back up to dvd's as well but I like the HD better.

I just noticed sikander3786's comment on the fat as well they are correct ntfs is better.

I have XP in virtualbox, no flags it runs inside of Ubuntu.

---

### Post by Toci on 2010-12-20
Hello, thank you both very much for the reply and information.

 I attach a screenshot of how the partitions look like at the moment. 
 I will be doing the Win7 back up you suggested Wilee-nilee, as for the partition I will probably leave that until the very end just in case something goes wrong.

 So, I guess I'm going to change the Files partition to NTFS, as for the /home one I might make it just to use the extra space.

 I have another question, the Files partition doesn't appear listed with the rest of them, How do I change that?

 Thank you again.

---

### Post by Toci on 2010-12-20
I thought I should add an update.

 I partitioned and it all went magnificently, resized the linux one, made a /home partition, a FAT32 LBA and a NTFS.

 Then as I tried to move /home to it's new location I ruined linux, I didn't know how to fix it (tried for a little while but couldn't) so I decided to reinstall.

 Ubuntu now lists all of the partitions perfectly and everything is working properly.

---

### Post by sikander3786 on 2010-12-21
> **Toci said:**
> I thought I should add an update.

 I partitioned and it all went magnificently, resized the linux one, made a /home partition, a FAT32 LBA and a NTFS.

 Then as I tried to move /home to it's new location I ruined linux, I didn't know how to fix it (tried for a little while but couldn't) so I decided to reinstall.

 Ubuntu now lists all of the partitions perfectly and everything is working properly.
Glad to know it is all working :-)

Happy Ubuntu-ing!

---

