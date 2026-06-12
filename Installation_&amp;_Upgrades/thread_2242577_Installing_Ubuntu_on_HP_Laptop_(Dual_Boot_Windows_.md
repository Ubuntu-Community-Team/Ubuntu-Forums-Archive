---
title: "Installing Ubuntu on HP Laptop (Dual Boot Windows 7)"
date: 2014-09-02
forum: Installation &amp; Upgrades
---

### Post by NoFriends on 2014-09-02
Hey all,

It's been more than 4 years since last running Ubuntu, i have a HP laptop running Windows 7, problem i am facing is extra partitions that HP install from factory.

The Partitions are shown in the picture below: 

[IMG]http://i61.tinypic.com/npl3d0.png[/IMG]

If someone could advise in some detail how to go about doing this without causing any error or loss of data.


Cheers.

---

### Post by Bucky Ball on 2014-09-02
Shrink 'My Passport'. Plenty of room on that drive. Use the Win7 software to do it and create free space. When installing Ubuntu, choose 'Something Else' when you get the partitioning section of the install ... use the free space and leave the Win7 (ntfs) partitions alone. That shouldn't be a problem as there are none on that drive.

---

### Post by Mark Phelps on 2014-09-02
I would hesitate to use "Passport" -- if that is, as the name implies, an external drive. (WD brands some of their drives as "Passport").  

If it's an internal drive, then you are OK to use it.

HOWEVER, that said, BEFORE you do that, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You will need that later to restore the Win7 MBR, since installing Ubuntu is most likely going to overwrite that by default.

---

### Post by NoFriends on 2014-09-02
> **Bucky Ball said:**
> Shrink 'My Passport'. Plenty of room on that drive. Use the Win7 software to do it and create free space. When installing Ubuntu, choose 'Something Else' when you get the partitioning section of the install ... use the free space and leave the Win7 (ntfs) partitions alone. That shouldn't be a problem as there are none on that drive.My Passport is an external Hardrive i use for personal and work data connected via USB port so that would have to be excluded in the list of Partitions.Sorry for causing some confusion there.

---

### Post by NoFriends on 2014-09-02
> **Mark Phelps said:**
> I would hesitate to use "Passport" -- if that is, as the name implies, an external drive. (WD brands some of their drives as "Passport").  If it's an internal drive, then you are OK to use it.HOWEVER, that said, BEFORE you do that, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You will need that later to restore the Win7 MBR, since installing Ubuntu is most likely going to overwrite that by default.Hi Mark,Thanks for you're reply, you are correct, that is an external WD hard drive.

---

### Post by Bucky Ball on 2014-09-02
> **Mark Phelps said:**
> I would hesitate to use "Passport" -- if that is, as the name implies, an external drive. (WD brands some of their drives as "Passport").  

If it's an internal drive, then you are OK to use it.

HOWEVER, that said, BEFORE you do that, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You will need that later to restore the Win7 MBR, since installing Ubuntu is most likely going to overwrite that by default.

All good points from Mark Phelps. I would personally make the backup disks (two copies wouldn't hurt) then kill some of the partitions on what Win calls HD0. As Mark says, the 'Passpost' is probably your external WD drive. You don't want to go there, unless you are looking for an exotic install of some sort. Best to keep Win and Ubuntu on the same drive in the box in your situation, by the looks ...

---

### Post by NoFriends on 2014-09-02
> **Bucky Ball said:**
> All good points from Mark Phelps. I would personally make the backup disks (two copies wouldn't hurt) then kill some of the partitions on what Win calls HD0. As Mark says, the 'Passpost' is probably your external WD drive. You don't want to go there, unless you are looking for an exotic install of some sort. Best to keep Win and Ubuntu on the same drive in the box in your situation, by the looks ...

Hi Bucky,

Thank you for you're input.

When you say 2 backup disks, would you recommend creating a system image and a system repair disc ? 

Once i do this, i need to either delete 1 of the 4 partitions, or move HP Tools & Recovery onto 1 partition. 

I'm not sure which one would be safe to delete without causing any system issues.

---

### Post by Bucky Ball on 2014-09-02
If you boot into Win7 there should be some kind of generic HP back up thing that will create a backup of the system. I meant make two copies using that. It generally uses three or four DVDs, though.

And yes, you could use something like Clonezilla to create a clone (image) of the entire drive so if things go pear-shaped you can get back to how it is now. Trouble with that is you really need to make sure your clone has worked, and that means plopping it on another drive and testing it out. That, in itself, can be problematic, unless you have another computer with the same size, or bigger, drive that you don't mind wiping for a test ...

---

### Post by NoFriends on 2014-09-02
> **Bucky Ball said:**
> If you boot into Win7 there should be some kind of generic HP back up thing that will create a backup of the system. I meant make two copies using that. It generally uses three or four DVDs, though.

And yes, you could use something like Clonezilla to create a clone (image) of the entire drive so if things go pear-shaped you can get back to how it is now. Trouble with that is you really need to make sure your clone has worked, and that means plopping it on another drive and testing it out. That, in itself, can be problematic, unless you have another computer with the same size, or bigger, drive that you don't mind wiping for a test ...

Cheers Bucky.

I will load up HP Recovery Manager and create a set of recovery media disc's.

Once i have done this, which route do you recommend would be easiest (less problematic) ?

Appreciate you're help.

---

### Post by Bucky Ball on 2014-09-02
> **NoFriends said:**
> Cheers Bucky.

I will load up HP Recovery Manager and create a set of recovery media disc's.

Once i have done this, which route do you recommend would be easiest (less problematic) ?


Depends what you intend to do and what you want the drive to look like at the end of the install. Best to have a beverage and grab a piece of paper and writing implement and make a plan before proceeding. Any data on the drive you don't want to lose? Not that you will, but back that up, too, before proceeding.

Guess you could shrink 'C' partition and stick Ubuntu there, but be aware that if you want to share data between Win and Ubuntu you are going to need an NTFS partition. 

Another alternative is to put Ubuntu on the 'D' partition and keep your data on the 'C' partition, which Ubuntu will read without a problem.

---

### Post by NoFriends on 2014-09-02
> **Bucky Ball said:**
> Depends what you intend to do and what you want the drive to look like at the end of the install. Best to have a beverage and grab a piece of paper and writing implement and make a plan before proceeding. Any data on the drive you don't want to lose? Not that you will, but back that up, too, before proceeding.

I'm not after anything too fancy mate.

I'm just after a basic dual boot of Windows 7 & Ubuntu, with the option of choosing on start up. my total Local disk size C: drive is 913GB.

I would like to shrink that and give Ubuntu around 100 - 200GB, which i think is more than enough.

---

### Post by Bucky Ball on 2014-09-02
In that case, shrink C and leave 100-200Gb free space, and use that for the Ubuntu install. It's plenty, depending, again, on how much data you want to store in Ubuntu. Circling back to the previous advice; you can use an NTFS partition for sharing data between Win and Ubuntu without issue ... ;)

---

### Post by NoFriends on 2014-09-02
> **Bucky Ball said:**
> In that case, shrink C and leave 100-200Gb free space, and use that for the Ubuntu install. It's plenty, depending, again, on how much data you want to store in Ubuntu. Circling back to the previous advice; you can use an NTFS partition for sharing data between Win and Ubuntu without issue ... ;)

Hi Bucky,

Thanks for the help, just to confirm and get my head around this...I can leave the rest of the partitions alone, such as HP TOOLS & RECOVERY and just shrink the Local Disk C: by say 200GB. How would i then go about installing Ubuntu alongside Windows on C: ? i wouldn't be putting much data on Ubuntu.

---

### Post by Mark Phelps on 2014-09-02
The HP Recovery Media is almost certainly going to be a "Factory Restore" set of discs, which is really NOT what you want to save, because using them would wipe out everything you have done since you first activated the PC.  A better solution (IMHO) would be to use the free version of Macrium Reflect to image off the OS to an external drive.  When doing that, be sure to pick the first two partitions, as you will need the "boot" partition if you want to do a restore later.  Also use the option to create and burn the Linux Boot CD.  This will have a Macrium program on it that can later be used to restore your Windows partitions from the image backup.

Once you do that, you no longer need the Recovery partition and can remove it.

---

### Post by Bucky Ball on 2014-09-04
Like Mark said, but another option, as I mentioned earlier, is to just clone the lot with Clonezilla (and the software MP mentions may do the same thing but not familiar with it).

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

Probably too much info, but you get the picture. Then just boot from the Ubuntu install disk, choose 'Something Else' when you get to that bit, wipe the drive and install as required. I must admit, doing much with Windows is a bit alien to me now. Mark Phelps may be a little more familiar and his direction may be safer and more productive ... ;)

---

