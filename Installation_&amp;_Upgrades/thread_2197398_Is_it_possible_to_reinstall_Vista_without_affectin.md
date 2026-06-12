---
title: "Is it possible to reinstall Vista without affecting boot loader?"
date: 2014-01-03
forum: Installation &amp; Upgrades
---

### Post by mike-smith260466 on 2014-01-03
Whilst I am aware this forum is primarily for help with Ubuntu issues and some may say that questions of how to reinstall Windows should be directed elsewhere, I am posting here as I feel my particular question would be better answered by someone with Linux experience.

I am using an MSI PR600 laptop which has had a 1Tb drive fitted. This has been divideded into two 500Gb partitions. I used the system recovery disk which came with the laptop to install Windows Vista before using the Ubuntu LiveCD (Ver 13.04) to partition the drive and install Linux on the second partition. 

My Vista installation has contracted walware viruses which, try as I might, I cannot remove. Whilst I am more than happy with Ubuntu (which is actually my OS of choice) I have some software that will only run in Windows.

Does anybody know of a way in which I can use a Windows system recovery disk to reinstall Vista without causing problems to the bootloader as I understand Windows will want to re-write the MBR of the disk? Obviously I want to protect my Linux installation and don't want to end up screwing up my HDD.

Is there something easy that perhaps I am missing? I'm not a complete noobie but admit to having limited experience in Linux, especially with technical issues.

Sorry if the answer seems obvious to some but I really could do with some help here.

Thanks in advance.

Mike

---

### Post by sudodus on 2014-01-03
The blunt answer is no. Windows will overwrite the boot sector.

But fortunately it is not too hard to rewrite the boot sector and make it point to the installed Ubuntu partition and its grub software. You can do that from a live CD/DVD/USB drive.

See this link [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

---

### Post by TheFu on 2014-01-03
Nope.  Windows doesn't like to play-nice with other OSes.
It isn't as hard today as it used to be previously to recover. Check out **boot-repair** links in my signature. There is no guaranty, but this tool really can handle many things for simple environments. The only time it didn't work for me was when multiple portable HDDs were connected while trying to do the fix.

---

### Post by mike-smith260466 on 2014-01-03
Thanks both. I'll check out the info you've supplied and see if I can fix the problem.

---

### Post by Mark Phelps on 2014-01-04
While not always the case, in general, when you use the Recovery feature on a Windows PC, it erases the hard drive, reformats it, and reinstalls the original version of MS Windows -- leaving the PC in the same state as when you first turned it on.

Thus, if you have repartitioned the drive, there is a strong likelyhood that the Recovery will either (1) wipe out everything on the drive, or (2) fail because the repartitioned drive does not meet the Recovery criteria.

---

