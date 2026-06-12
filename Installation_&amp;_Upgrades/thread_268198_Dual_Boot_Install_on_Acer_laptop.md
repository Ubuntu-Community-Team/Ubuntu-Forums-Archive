---
title: "Dual Boot Install on Acer laptop"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by fred22 on 2006-09-29
Hi,
I am planning on setting up my new laptop to dual boot XP or Ubuntu. It is an Acer laptop w. 60GB hd and as you may know they tend to come with the hard drive set up in two (or three) partitions. 'C:' has xp on it, 'D:' is used for recovery and there is a mysterious third hidden partition.

I have run Qtparted to look at the hard drive setup and it is as follows if my notes from this morning are correct:

dev /hda1    PRIMARY FAT32                        2.93GB
dev /hda2    PRIMARY FAT32                        26.39GB   boot/lba
dev /hda3    EXTENDED                             26.57GB   lba
dev /hda5    PRIMARY FAT32                        26.57GB

How do I need to go about this? I'm guessing that I should remove hda1 partition, then install Ubuntu into hda5. But I am totally unsure if this will produce a working dual-boot and as the laptop is new and used by family I am anxious not to mess up here.

Thanking anyone in advance who can help out,

Fred

---

### Post by morphodone on 2006-09-29
Deleting hda1 would delete windows.  It appears that's your C: drive.
You would have to see the contents of the drive to verify that.

You shouldn't need to delete any partition.  You only need to 
resize one of them.  If there is enough free space on /dev/hda5 then
that is the best candidate.

Be sure to back up any data on that drive first though.

---

### Post by fred22 on 2006-09-29
No begging your pardon but I believe that hda1 is a ghost (?) image used for recovery without having to load the rubbish recovery cds.
That is why it is only a couple of gigs in size.

---

### Post by morphodone on 2006-09-29
> **fred22 said:**
> No begging your pardon but I believe that hda1 is a ghost (?) image used for recovery without having to load the rubbish recovery cds.
That is why it is only a couple of gigs in size.

You are probably right, although I would still be hesitant to delete it.

---

### Post by Dominus Suus on 2006-09-29
Careful, Fred,

On my Acer Laptop (which is *not* designed for Linux) hda1 should be, in fact, your Windows partition.  I've since gone with a clean Linux box so I'm advising you on memory when I had a dual-boot system.

If you can, run the Ubuntu setup from CD and, when you get to the bit about partitions, ask to do a manual configuration of your partitions.  As long as you don't hit 'write changes to disk' or something to that effect, you won't risk messing up your hard drive.  In that dialog, see how your hard drive is currently set up.  My guess is that hda1 should be designated a boot partition.

The reason why you have to be careful before messing about with hda1 is that I read somewhere (can't remember where now) that Windows *has to* install on the first partition starting at the first sector of your primary disk, which should be hda1.  The reason for this must have something to do with the perfection of Windows' design such that Microsoft never imagined in their wildest dreams that someone possibly ever could want to install another operating system. :-k

---

### Post by fred22 on 2006-09-30
Thanks. I have no problem leaving the first few partitions alone. My problem is trying to understand the boot up process and anticipating how to answer any questions asked during install.

Presumably the current Windows-only setup has its boot record in hda2 as there appears to be a boot 'flag'. 

When doing a dual boot installation how do I add to this existing boot record or create a new (linux) boot record that will 'know' there are two OS on the hard drive?

Maybe this happens automatically if I install Ubuntu to hda5? Maybe not. I would like to have an idea of what questions the installation procedure will ask and how I should answer them correctly to achieve the desired dual boot.

Many thanks again, hope you understand me

---

### Post by JGuru on 2006-09-30
You don't have to do anything. GRUB ( the Linux bootloader) will automatically
List Windows, & Ubuntu in the menu while booting. Choose whichever O.S you 
want to boot & it will be loaded. If you want to load Windows, select 'Windows'
 from the menu, now GRUB passes the control to NTLDR(Windows loader)& Windows
 will be loaded automatically.

---

### Post by fred22 on 2006-09-30
So can I just confirm ( sorry if I am being a little dense here)

I am going to repartition partition hda5. In there I am going to put swap partition, the rest will be ext3 (?) format.

Then I install ubuntu in the ext3 partition just made.

Grub is installed in this ext3 partition and when I reboot the pc GRUB takes charge?

Do I have to (re)set any flag(s) as the windows partition is marked as boot??

Thanks

---

### Post by fred22 on 2006-09-30
It is done. And it was that easy. Thanks to those who offered advice :D

---

