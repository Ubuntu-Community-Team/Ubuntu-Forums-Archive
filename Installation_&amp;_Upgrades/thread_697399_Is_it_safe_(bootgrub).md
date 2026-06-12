---
title: "Is it safe? (boot/grub)"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by tbresson on 2008-02-15
Hi.

I was wondering.

Is it safe?
- to remove the boot flag of a disk without messing with the contents of it?
- to install grub on a disk without messing with the contents of it?

---

### Post by Herman on 2008-02-15
No action is safe or dangerous, it depends on how well prepared for it you are.

---

### Post by hyperair on 2008-02-15
Yes it's safe. However, if the boot flag of a disk is removed when that disk is supposed to boot, you will encounter issues with booting.

---

### Post by tbresson on 2008-02-15
Ok, what I meant was does any of the data on the disk gets overwritten If I change boot status on it or install grub on it, e.g. like if you quick format something you simply delete the index that knows where stuff are on the disk.

Hyperair: tnx

---

### Post by Herman on 2008-02-15
No because the Master Boot Record for the hard disk is something different and separate from the partitions.

The Master Boot Record is situated in the first sector of the hard disk.
The rest of the first track (62 sectors) of the hard disk is normally empty and may contain more boot loader code if you use GRUB boot loader or GAG Boot Manager.
The Master Boot Record contains an area where the stage1 code for a boot loader can be written and some other things, and it contains the partition table and a disk signature.

The boot sector and file system blocks for the first sector don't start until sector number 63. GRUB doesn't write anything to any other partitions in your disk.

In 99% of cases GRUB will be installed and set up automatically for you without you having to do anything, but you should still have a [Super Grub Disk]("http://sgd.benjamin-butschko.de/") just in case. They are free and only a small download.

The hard disk partitioning program is GParted and it's a very good hard disk partitioning program.
There is always some risk with partitioning and with all hard disk partitioning work you are still advised to back up your data first.

The risks you might take are more than compensated for when you end up with a successful Ubuntu installation.

If you have some kind of RAID setup then you should get advice from someone who knows about that, or do some studying first.

Regards, Herman :)

---

### Post by tbresson on 2008-02-15
Thank you for taking the time to explain this :)

I'll check out that supergrubdisk program.

---

### Post by Herman on 2008-02-15
You are welcome.
I have noticed you have another thread here, [Grub]("http://ubuntuforums.org/showthread.php?t=697449")

If you have already installed and you are having trouble booting, it could be that GRUB in installed in the hard drive that the BIOS considers your second hard drive. 
If that is the problem then [    Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority"). is the easiest way to fix that problem.

Regards, Herman :)

---

### Post by tbresson on 2008-02-15
Yes.. I tend to split up questions to avoid huge posts with lots of questions that usually never gen answered.

Excellent link again! Thanks! I just skimmed the page and I don't think it applies but I'll look at it again when I get back home.

---

### Post by Herman on 2008-02-15
There has always been some confusion for GRUB when the computer has one PATA (IDE) and one SATA disc. Sometimes in that situation the BIOS and GRUB and the Linux kernel can't seem to agree on which is the first hard disk and which is the second one. GRUB gets installed on the wrong MBR. It's a well known problem.

One solution is to re-install GRUB to the other hard drive's MBR, then you get GRUB Error 17 and your system still won't boot until you edit your /boot/grub/menu.lst file and make some changes. After the appropriate changes are made the operating systems will boot okay. 

Some people who have three or more hard disks report that editing GRUB's /boot/grub/device/map and re-installing GRUB works for them.
For others that doesn't seem to work.
Here is quite a long thread about that,                                                                                                                                           [Grub error 17]("http://ubuntuforums.org/showthread.php?t=442945").

The easiest and best way if you have two hard disk is to try the solution with the BIOS as I already explained.

If that's not what your problem is and if you still need help with GRUB, please post the output from 'sudo fdisk -lu' and the bottom half of your /boot/grub/menu.lst file here and I or someone here will try to help you.
```
sudo fdisk -lu
``````
gksudo gedit /boot/grub/menu.lst
```Regards, Herman :)

---

### Post by tbresson on 2008-02-19
Thanks again.

I'll post it here later today.

---

### Post by tbresson on 2008-02-19
The link provided worked perfect. I was a bit slow on understanding the meaning, but I get it now. 

Thanks!

---

### Post by Herman on 2008-02-20
:) Okay, cool!
Thanks for the feedback too.
Regards, Herman :)

---

