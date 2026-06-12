---
title: "Access to Recovery Partitions After Windows 8 Upgrade?"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by Kixtosh on 2013-02-01
I have a few family laptops that are all currently dual booting Windows Vista or 7 alongside Ubuntu. I mostly use Ubuntu, but retain Windows for some infrequent tasks (updating TomTom navigation devices mostly).

These laptops all use a recovery partition to restore them to factory default state, in case of problems. I can see that recovery partition easily in the list of boot options offered by GRUB. This would enable me to restore the Windows installation if necessary by simply accessing the restore procedure from the GRUB menu.

I now want to take advantage of the Windows 8 upgrade pricing to upgrade the Windows installation, but I'm guessing this will mess up GRUB. I understand that it's quite simple to repair GRUB, but I want to know if GRUB will restore access to the prior Windows version recovery procedure or not.

Basically, I want to be able to restore the laptops to Windows 7 (or Vista), using the existing recovery partition, in case I don't like the way they work with Windows 8. If they work well with W8, then I'll just keep W8 and Ubuntu, but with the option to use the recovery partition to restore a previous version of Windows.

Should this be fairly simple, or not?!

Pictured is my current HDD.

---

### Post by Mark Phelps on 2013-02-01
All the Win8 in-place upgrade is going to do is replace the current GRUB code in the MBR with Windows code. The GRUB config file (grub.cfg) is not going to be touched in any way.

Since you'll be overwriting the existing Win7 partitions with Win8, that will not affect the code needed in the GRUB config file -- except it will still say Windows 7.

All you will need to do after that is restore the GRUB code to the MBR.

Should be OK after that.

Actually, now that I think about it, Win8 will ALLOW you to go BACK to Win7 without having to restore to a factory restore.  You should check the Windows 8 forums (eightforums.com) to see how this is done.  I believe it's a simple matter of restoring Win7 from a windows.old file -- but you should check on that to be sure.

---

### Post by Kixtosh on 2013-02-02
Thank you Mr. Phelps! I'll check out the W8 forums. I'm just hoping that if my recovery partitions remain intact I can still use them to restore the laptops to factory condition ... including all the proprietary drivers and stuff, so that all my "fn" function keys work as they're supposed to (turning off trackpads and wireless, switching power schemes ...). I've made system restore disks, but I've learned from experience that they don't always function the way you'd expect, and by the time you "need" them, those cryptic error messages that made Microsoft the butt of Apple jokes in commercials are seldom of any use!

In the meantime, I've been able to download a W7 "clean" disk image. Amazingly, it only takes up 11G on a fresh hard drive (which I used to try it out without messing up my current installation and files). The vendor's version on W7 takes up a whopping 30G! Of course, the image I downloaded from PC World does not include any extras (MS Office etc.).

I've also got my W8 upgrade licenses at the discounted price before it was too late (the last day to order was January 31), so that's all set as well.

[COLOR=DarkRed]**P.S. Congratulations on COMPLETELY BLOWING THE DOORS OFF your 10,000 bean count!**[/COLOR]

---

### Post by Mark Phelps on 2013-02-02
Thanks for the compliment ...

IF you want a restorable Win7 version, my own approach would be to, BEFORE you do the Win8 upgrade, install the FREE version of Macrium Reflect on each PC and image off each Win7 setup to an external drive.  Then, use the option to create and burn a Linux Boot CD (for use with Macrium Reflect).

Not only will that give you the ability to restore each PC in only a few minutes, it will also restore it to a fully-functional state -- one where you won't have to reinstall apps and lots of Windows Updates.

The reason the image is smaller, I'm guessing, is that it is a compressed Windows Image file.  Once you use that for an install, the space actually used on the drive will be considerably larger.

The vendor version might not be compressed, and it could also be loaded up with lots of bloatware -- and contain other stuff as well.

---

### Post by Kixtosh on 2013-02-02
> **Mark Phelps said:**
> ... IF you want a restorable Win7 version, ... install the FREE version of Macrium Reflect on each PC and image off each Win7 setup to an external drive.  Then, use the option to create and burn a Linux Boot CD (for use with Macrium Reflect). ...
Sounds like a good option ... could something like this be achieved from within Ubuntu, since all these laptops are dual boot? What I'm thinking is that I can shrink the Windows O.S. partition to it's smallest size, on each laptop, then use Ubuntu to make images of the Windows partitions to a single hard drive for future use, if ever needed.

---

### Post by presence1960 on 2013-02-02
Macrium Reflect is a very good option. I have tested it and it works very well. However I still use Clonezilla for all my imaging. I tested Macrium Reflect because I will not recommend something unless I know first hand how it actually works. A lot of people in the Windows forum I belong to use it.

---

### Post by Kixtosh on 2013-02-02
I understand that Macrium Reflect is the way to go if I do this using Windows. I'm just wondering if I could achieve the same end using Ubuntu instead, since that's what I use most these days.

---

### Post by presence1960 on 2013-02-02
> **Kixtosh said:**
> I understand that Macrium Reflect is the way to go if I do this using Windows. I'm just wondering if I could achieve the same end using Ubuntu instead, since that's what I use most these days.

Clonzilla is a linux based bootable CD. You boot off the CD and make an image either to an internal or external disk. Download the iso off Clonezilla's home page and burn as an image to CD. You can use the CD to boot off any machine without having to install software to any machine. As from within Ubuntu you can use terminal and dd. I do not use that method preferring Clonezilla instead.

Maybe someone familiar with the dd command can tell you how to do that.

---

### Post by Kixtosh on 2013-02-02
Doesn't seem as though there's any need to use terminal and dd. Both of those solutions (Clonezilla and Macrium Reflect) seem perfect for the job.

---

### Post by presence1960 on 2013-02-02
> **kixtosh said:**
> doesn't seem as though there's any need to use terminal and dd. Both of those solutions (clonezilla and macrium reflect) seem perfect for the job.

+1

---

### Post by Mark Phelps on 2013-02-02
> **Kixtosh said:**
> I understand that Macrium Reflect is the way to go if I do this using Windows. I'm just wondering if I could achieve the same end using Ubuntu instead, since that's what I use most these days.

Basically -- NO.  While Clonezilla can image off partitions, MR has the ability to "mount" its image files so you can browse them and extract any files as needed.  Clonezilla does not have the ability to mount the images it creates.

As with data recovery, I have learned that Windows utilities do better for Windows systems; Linux utilities for Linux systems.

Once you start mixing them, all bets are off.

---

### Post by presence1960 on 2013-02-02
> **Mark Phelps said:**
> Basically -- NO.  While Clonezilla can image off partitions, MR has the ability to "mount" its image files so you can browse them and extract any files as needed.  Clonezilla does not have the ability to mount the images it creates.

As with data recovery, I have learned that Windows utilities do better for Windows systems; Linux utilities for Linux systems.

Once you start mixing them, all bets are off.

For simple imaging for cloning/restoring OSs Clonezilla works fine with Windows. I have imaged and restored countless windows Oss from XP to Windows 8 for my clients.

If you just want a simple image to restore any OS in an emergency Clonezilla will do the job very nicely and as well as macrium Reflect. However as Mark pointed out if you wish to mount and extract files from the image then Macrium is the better solution. It comes down to what you want to do with your images.

---

