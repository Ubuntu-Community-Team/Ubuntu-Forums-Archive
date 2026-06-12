---
title: "Dual booting with recoverable OEM Windows 11"
date: 2023-12-15
forum: Installation &amp; Upgrades
---

### Post by agarding on 2023-12-15
Hi,

I have a brand new Lenovo ThinkPad E14 Gen 4 with Windows 11 preinstalled. I am going to install Xubuntu too so that I will have partitions of some tens of GB for Windows and Xubuntu and most of the hard-drive for an ext4 data partition.

Currently, the 256 GB hard-drive has three partitions: 260 MB EFI system partition, 240 GB Windows C and 2 GB recovery partition.

Is it possible to install Xubuntu so that the original recoverable Windows installation is not disturbed or do I need to reinstall Windows? I mean, it should be possible to shrink the Windows partition to free space for Ubuntu and data partitions, but would that inavoidably break the recoverability or is there a way to modify the partitioning and install Xubuntu without breaking anything?

If it is not possible, I will reinstall Windows.

By the way, this question may be too specific to this particular laptop model, but I am trying anyway.

---

### Post by ubfan1 on 2023-12-15
Shrinking the 240GB partition and installing multiple Ubuntu/Lubuntu OSes is not a problem.  Use the Windows tools to shrink, chkdsk, and add Ubuntu OSes to free space. Cannot speak to the way Windows Recovery would act, but haven't heard any problems from others on recovery problems -- not that they would be reported here ;^)

---

### Post by agarding on 2023-12-15
Actually, one of my points here is that if I knew that this can't be done without breaking the recoverability, I would remove the recovery partition as it would be useless and removing it would make the partitioning scheme a little more simple.

---

### Post by yancek on 2023-12-15
I don't see what the problem is.  Your recovery partition is only 2GB of a 256GB drive per your post with 240GB for windows.  Use windows Disk Management to shrink that partition to about half (120GB) and use the other 120GB to install Ubuntu or Xubuntu or whatever you want.  The installer will install to unallocated space and not overwrite the windows partition but you as a user, can overwrite it if you don't know what you are doing.  The install won't change the recovery partition but again, a user unfamiliar with the process can do so.  You would need to select the manual or something else option during the install to tell it what to do and where.

The recovery partition for windows, as I understand it, just resets everything to factory default meaning it will eliminate any other OS install, set any changes you made as a user to the default on install and of course, overwrite and personal data files you have.

I don't really see how it would be simpler removing the recovery partition due to its small size and the fact that the recovery partition is usually at the end of the drive.  If you have never done this before, I would definitely suggest you read some tutorials on installing Ubuntu alongside your windows.

---

### Post by agarding on 2023-12-15
I guess there is no big problem and I am very confident of not removing anything unintentionally. The recovery partition is not big and it contains just a Windows install image bundled with some extra software by Lenovo that you can probably download and install separately too.

I am just wondering if anyone has any experience of this and could point me out if there is something specific to do or to avoid. I do have experience in building custom boot setups, but I haven't done it with Windows 11 and UEFI and I also don't know how exactly the recovery functionality uses the recovery partition.

---

### Post by someguy99 on 2023-12-15
I think that if that large windows partition is only partially used, you should be able to shrink the unused portion without affecting anything, and then create the linux-formated partitions in that new space.
Windows recovery isn't going to "know" that its partition had originally been larger, as long as you haven't disturbed the extant files.

---

### Post by oldfred on 2023-12-15
My Dell laptop had to go back for motherboard replacement (twice). I still like it, but repairs first time worked without issue, keeping my Windows & Ubuntu working.
Repairs second time, only Ubuntu would boot.
Tried every Windows repair, recovery. I had backup that would not work. I tried new install that would not work.

Only thing that then worked was to download a Dell recovery tool. Not sure if data in recovery partition was used, but it totally erased all my Windows data & my Linux partitions. System was restored to just like the day I purchased it. Testdisk does not even show old partition table.

I did have backups of data, product keys for installed Windows software. My Kubuntu install was essentially a copy of my desktop, so eeryting was in effect backed up.

I think second install of motherboard did not have original Windows product key restored. So repairs would not work. I had not backed up Product key as it is in UEFI and should just be automatically used.

---

### Post by agarding on 2023-12-17
I shrank the Windows partition, installed Xubuntu and created a data partition. Everything went smooth, but it's hard to tell if the recovery still works before I actually need it, which I hope to never happen.

Thanks for all points and experiences shared!

---

### Post by tea for one on 2023-12-17
> **agarding said:**
> I shrank the Windows partition, installed Xubuntu and created a data partition. Everything went smooth, but it's hard to tell if the recovery still works before I actually need it, which I hope to never happen.
You have other Windows 11 Repair options:-

Make a Recovery disk [https://support.microsoft.com/en-us/windows/create-a-recovery-drive-abb4691b-5324-6d4a-8766-73fab304c246](https://support.microsoft.com/en-us/windows/create-a-recovery-drive-abb4691b-5324-6d4a-8766-73fab304c246)
Make a Windows 11 Bootable USB [https://www.microsoft.com/en-gb/software-download/windows11/](https://www.microsoft.com/en-gb/software-download/windows11/)

---

