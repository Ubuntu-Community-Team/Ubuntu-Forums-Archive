---
title: "Grub problems."
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by Alex N on 2007-02-26
I installed Ubuntu 6.10 on the following hardware :

disk0 - IDE master - Windows 2000 single partition
disk1 - IDE slave - initially empty, all partition info deleted by installer, default partitioning accepted.

The result is : ruined MBR, grub fails with Error 17.

I fixed boot record and now I can boot Win2000.

Then I searched this forum and found how to reinstall grub. did it.
Now grub starts from the SECOND drive - disk1 - displays menu, but unable
to boot ANY OS. Linux boot fails with message 'cannot mount volume',
Win boot fails with message 'wrong executable'.

I think there's something wrong with the installer.
What to do now ? Repeating install will trash MBR again, I think.

---

### Post by confused57 on 2007-02-26
> **Alex N said:**
> I installed Ubuntu 6.10 on the following hardware :

disk0 - IDE master - Windows 2000 single partition
disk1 - IDE slave - initially empty, all partition info deleted by installer, default partitioning accepted.

The result is : ruined MBR, grub fails with Error 17.

I fixed boot record and now I can boot Win2000.

Then I searched this forum and found how to reinstall grub. did it.
Now grub starts from the SECOND drive - disk1 - displays menu, but unable
to boot ANY OS. Linux boot fails with message 'cannot mount volume',
Win boot fails with message 'wrong executable'.

I think there's something wrong with the installer.
What to do now ? Repeating install will trash MBR again, I think.
You should be able to boot Windows by selecting your master drive to boot first, that's a good option to have.
Selecting your slave drive to boot first gives you a grub menu, right?   Booting first to your slave drive changes the way grub sees your hard drives, instead of hd1, grub sees it as hd0.
What you can do is at the bootup grub menu, highlight your Ubuntu entry, press "e" to edit, then change the line with root from (hd1,0) to (hd0,0), then press "b" to boot...if Ubuntu boots, this change is only temporary, you'll need to make it permanent in your /boot/grub/menu.lst.
Your grub entry to boot Windows will need to be changed, something like this:
title              Windows 2000
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

See this thread for instructions on editing your /boot/grub/menu.lst:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by Alex N on 2007-02-26
Thank you for advice. As I can understand so far, those tutorials are about
installing Ubuntu and Win on the same disk or about choosing boot disk by
setting jumpers etc. 

What I want to have : Windows on first drive, Linux on the second,
and menu for choosing OS to boot. 

Is booting from Linux drive the only option ? I understand the problem is
the following : GRUB needs menu.lst to work and can not find it on ntfs
partition. And the only place where GRUB can look for it is the same partition
from which it has been started. Am I right ?

---

### Post by confused57 on 2007-02-26
> **Alex N said:**
> Thank you for advice. As I can understand so far, those tutorials are about
installing Ubuntu and Win on the same disk or about choosing boot disk by
setting jumpers etc. 

What I want to have : Windows on first drive, Linux on the second,
and menu for choosing OS to boot. 

Is booting from Linux drive the only option ? I understand the problem is
the following : GRUB needs menu.lst to work and can not find it on ntfs
partition. And the only place where GRUB can look for it is the same partition
from which it has been started. Am I right ?
You are correct, grub needs to be installed to the mbr of the drive that you're booting to first.
When you first installed Ubuntu, grub installed to mbr of your Windows drive, but you received an error 17 & had to restore your Windows mbr.  You could try to reinstall grub to the Windows mbr, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
however, you may end up with same problem & have to restore your Windows mbr again, then again grub may work correctly if reinstalled to the Windows mbr.

You could always switch Ubuntu to master & Windows to slave, but as you said, you'd need to open up your case & switch the jumpers on the hard drive.

I believe that booting first to your Ubuntu drive is your best option...then try the suggestions I mentioned in my first reply.

What you can do before you try anything is boot up the live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

This will show your partition table on both hard drives & help determine possible entries needed in grub to boot your OS.

---

