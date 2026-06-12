---
title: "What if I have a Windows OS I don't want to loose?"
date: 2022-08-19
forum: Installation &amp; Upgrades
---

### Post by Complete on 2022-08-19
i have a beautiful laptop computer I bought yeas ago in China.  It has Microsoft Word on it.  It is the only computer I have with Microsoft Word.  I love it because it is high resolution  But it also reminds me of my trip to China and the wonderful culture there.  Anyway I  want to have it back the way it is after I use Ubuntu it and I do not want to use a Virtual Machine (for completely different reasons).  Is there REALLY a way to back up the complete image of my system and restore it after I use Ubuntu?

---

### Post by mikewhatever on 2022-08-19
Yes. Use Macrium or Paragon or any other tool, and next time search before asking.
PS: You can also swap an HDD, which could be much easier.

---

### Post by ActionParsnip on 2022-08-19
Setup a dual boot and you can choose at bootup time. Be sure to backup any important data BEFORE you start this process. I suggest you resize the NTFS in Windows to make free space to install Ubuntu to

---

### Post by pbear42 on 2022-08-19
There's also a good system backup tool built into Windows.  See Control Panel > Backup & Restore > Create a system image.  No compression, but backup image will be only as large as space-in-use.

To restore, you need a way to boot a recovery environment, e.g., a recovery USB, a system repair disc, or an installation medium.

---

### Post by mIk3_08 on 2022-08-20
> **Complete said:**
> i have a beautiful laptop computer I bought yeas ago in China.  It has Microsoft Word on it.  It is the only computer I have with Microsoft Word.  I love it because it is high resolution  But it also reminds me of my trip to China and the wonderful culture there.  Anyway I  want to have it back the way it is after I use Ubuntu it and I do not want to use a Virtual Machine (for completely different reasons).  Is there REALLY a way to back up the complete image of my system and restore it after I use Ubuntu?
Just make a partition space for Ubuntu. Ex. Drive Letter c is for your MS Windows system and another partition drive for your Linux Ubuntu. just make it unallocated yet so that you will be able to find the partition when you start to install the new Linux Ubuntu System. Regards and cheers.

---

### Post by QIII on 2022-08-20
Is the machine able to boot from USB?

The best way to have it back the way it was is to refrain from doing anything to the current disk.

---

### Post by ubfan1 on 2022-08-20
If choosing the USB install and you have a UEFI system, do be aware of bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379) "installer users first EFI partition found even if directed otherwise"
There are several workarounds to prevent the modification of your internal disk's EFI -- remove the internal disk, disable it in UEFI settings, remove boot/EFI flags on the partition. Disk removal seems to be the one that cannot fail. **Do add yourself to the "Does this affect me" list in the bug's upper left hand corner. **Old as the bug is Nov 2014, it supersetted an even older bug 1173457 specifically for USB (loosing the "...affects me" list count in the process).

---

### Post by kurt18947 on 2022-08-20
> **QIII said:**
> Is the machine able to boot from USB?

The best way to have it back the way it was is to refrain from doing anything to the current disk.

The surest way for certain, though some hard drives are not easily accessible. I'd still make at least one backup to any files difficult or impossible to replace. I've had good luck dual booting, making sure Windows was installed first. Of course having said that assures that next time I try to make a dual boot it will be a catastrophe.:lolflag:

---

