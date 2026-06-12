---
title: "Windows 8.1 boot problems after removing ubuntu disk partitions"
date: 2014-12-12
forum: Installation &amp; Upgrades
---

### Post by jonas16 on 2014-12-12
**Situation:** 
Laptop with windows 8.1 installed got ubuntu installed next to it as second OS. This was done by shrinking the main data partition with 50GB, and creating \ and \home partions with that new free space. At a later period in time these two partitions were removed again using disk manager in windows, and the empty space was added again to the main data partition. Now, when booting a BSOD appears showing error code 0xc0000225.

**Solution attempt:**
Attempted to run boot repair in the "try ubuntu" OS, but did not solve the problem. Returned the following link: [http://paste.ubuntu.com/9487912/](http://paste.ubuntu.com/9487912/)

Can anyone help me with this? Thanks!

---

### Post by ajgreeny on 2014-12-12
Oh dear!

I hope you have either a DVD install disk for Win 8 or made the recovery DVDs that are suggested when you first boot to Win 8 on a new machine.

What you did was to remove the partition that contained the grub configuration folders and files, so grub-efi is still trying to boot but has no files to act on.
I am not sure if Boot-Repair is able to overcome this problem, though your experience suggests it can't.  I am sure there are ways around this but no longer running windows in this household I can not give you any useful details of how.  Hopefully oldfred, one of the forum's UEFI dual boot experts will find this thread and come to your rescue.

There is a thread at [http://ubuntuforums.org/showthread.php?t=2181062](http://ubuntuforums.org/showthread.php?t=2181062) of a very similar situation to yours which may give you some clues of what to try.

---

### Post by jonas16 on 2014-12-12
Thanks for your reply.

I did manage to get my hands on a Windows 8.1 installation disk, but all efforts of (advanced) restoring have failed so far. Also running chkdsk on both c:/ and d:/ did not solve it. Refreshing returns that the windows installed drive is locked. I also see this in Ubuntu, since I can't access the C:/ drive there as well.

I'm going to go through your suggested thread now. If anything should come to mind, don't hesitate to suggest!

---

### Post by jonas16 on 2014-12-12
Fixed it! 

After applying the info in the thread provided (reinstall ubuntu, run lilo), it still didn't work.

After some more online digging, I found the following solution.

Source: [http://www.thewindowsclub.com/repair-master-boot-record-mbr-windows](http://www.thewindowsclub.com/repair-master-boot-record-mbr-windows)

Using the repair disk of Windows 8.1, I opened the command prompt to repair the master boot record. 

Followed steps:
bootrec/RebuildBcd -> finds the installed OS, toggle "y" to add it to the MBC when prompted
bootrec/fixMbr
bootrec/fixboot

After these steps close the command prompt and reboot with fingers crossed.

Done!

Thanks for a quick respond though [**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747")!

---

