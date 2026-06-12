---
title: "Urgent: Partition / Grub MBR Question - sdb ok?"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by gencon on 2010-04-21
Noob, first time installing Ubuntu.

I have a question about creating disk partitions and where to put GRUB on a MBR, on a new dual boot Windows XP / Ubuntu install (Windows is already there).

In Win XP 'Computer Management->Disk Management' it lists my 3 hard disks:

Disk 0 - First Partition (C drive), Second Partition (E drive)
Disk 1 - First Partition (D drive)
Disk 2 - First Partition (F drive)

My intention is to use GParted to delete the Second Partition (E drive) on Disk 0, create an extended partition in its place and then create 3 logical partitions on which to install Ubuntu (root, swap, home).

I loaded GParted and was expecting to see Disk 0 as sda, instead sda is what windows calls Disk 2, sdb is in fact Disk 0, and sdc is Disk 1.

This is probably because I had my PSU (power supply unit) changed by a fix-it shop a few weeks ago. Presumably while fitting the new PSU the SATA cables connecting to the 3 SATA hard disks got muddled up and placed in different hard disks than they had been in before. Windows XP presumably recognizes whichever hard disk has Windows in the first primary partition and calls it Disk 0.

I am now worried about which disk Ubuntu will install GRUB in the MBR and how to make sure this is sdb.

Can I use GParted to delete the Second Partition (E drive) on sdb aka Disk 0, and then create my extended partition and 3 logical partitions for my Ubuntu install. Will GRUB be placed in the correct place by the Ubuntu installer, how do I make sure of this? 

Are there any other considerations or pitfalls I should watch out for if installing a dual boot Win XP and Ubuntu on what Windows calls Disk 0 and GParted calls sdb?

Or is this all ok, and no problem installing on sdb at all?

Many thanks.

PS. I have a spinal cord injury (wheelchair user) which would make changing the SATA cables of my hard disks around inside my PC a major headache - not quite brain tumour, but certainly a serious migrane. :P

---

### Post by drs305 on 2010-04-21
You can cleanup the "smileys" by using the "[noparse] [noparse] [/noparse][/noparse]" tags around character combinations which create them. It will help clear up the drive/partition designations in your post.

Edit: Looks like the post has been fixed. Thanks. Now to reread it...

---

### Post by gencon on 2010-04-21
Fixed the smiley problem as soon as I saw it after submitting the post - sorry.

---

### Post by drs305 on 2010-04-21
If you are reinstalling Grub 2 you will be asked which drive to install it on. Generally, it's best to put it on the drive designated in the BIOS to boot first. This eliminates delays while Grub 2 searches for its files. It's recommended not to install G2 on a specific partition.

Grub 2 should not effect your Windows install, but if it doesn't pick up Windows, run "sudo update-grub" after the install to see if it recognizes it. If Windows fails to start up, you may need to run the procedures described in this post by talsemgeest:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by P4man on 2010-04-21
> **gencon said:**
> 
I loaded GParted and was expecting to see Disk 0 as sda, instead sda is what windows calls Disk 2, sdb is in fact Disk 0, and sdc is Disk 1.

Is this a mix of sata and pata drives perhaps? If not, then possibly your boot order is misconfigured in the bios, and it tries booting off an different disk first, fails, tries the next which would be windows. This could cause different drive order in windows and ubuntu i think.

> 
I am now worried about which disk Ubuntu will install GRUB in the MBR and how to make sure this is sdb.

At the end of the installation procedure there is an "advanced" button that shows where it will install (and you can change it there, or not have grub installed at all).
> 
Can I use GParted to delete the Second Partition (E drive) on sdb aka Disk 0, and then create my extended partition and 3 logical partitions for my Ubuntu install. Will GRUB be placed in the correct place by the Ubuntu installer, how do I make sure of this? 

The installer provides an option to manually partition. That simply loads gparted editor where you can repartition as you want, and then in the next step you assign a root partition, a swap partition and optionally a /home partition. But you can do it from the installer, or do it before hand and just select those partitions during the installation. Just make sure to select "manual" partitioning.
> 
Are there any other considerations or pitfalls I should watch out for if installing a dual boot Win XP and Ubuntu on what Windows calls Disk 0 and GParted calls sdb?

Probably not, but I would check boot order in bios and make sure its set to boot first from the harddisk you actually want to boot from.

---

### Post by gencon on 2010-04-21
Thanks for the quick replies.

I am now going to reboot and check in BIOS which hard disk is set to boot first, make sure it is what Windows calls Disk 0 and what GParted calls sdb.

Then I'll get back to you... 5-10 mins or so...

PS. No sata and pata hard drive mix, all 3 drives are sata.

---

### Post by gencon on 2010-04-21
OK, got a bit of an ID problem.

2 hard disks appear identical in BIOS, because when I had the PC built I had 2 500 GB hard disks installed (I added a 3rd later).

The 2 hard disks in BIOS are both listed as: Samsung HD501LJ

I can specify in BIOS the boot order: basically choose between hard discs, optical drives, and removable. There is no way to set individual device ordering, so can't set 1st as HDD1, 2nd as DVD1, 3rd, HDD2, 4th DVD2.

But in a separate BIOS boot page menu I can specify the order the hard discs and optical drives are booted in. In the hard disk ordering the 2 disks are listed as: 'HDD 3M' and 'HDD 4M'.

One of the hard disks has 2 partitions, the other 1. But with no partitions listed by BIOS how do I tell which disk is which?

Thanks again guys.

---

### Post by drs305 on 2010-04-21
As far as Grub is concerned, the boot order isn't critical. You can choose one and if it appears that you have a lengthy delay before the menu displays you could simply go back and change the order in BIOS. This isn't a showstopper - it's just a bit of an annoyance caused by the delay. I can't speak to the effect it would have on Windows.

---

### Post by gencon on 2010-04-21
> **drs305 said:**
> As far as Grub is concerned, the boot order isn't critical. You can choose one and if it appears that you have a lengthy delay before the menu displays you could simply go back and change the order in BIOS. This isn't a showstopper - it's just a bit of an annoyance caused by the delay.
Ok cool, didn't realize it wasn't a problem.

But what about which drive's MBR Grub should be set to? That's what I don't get. If I install Ubuntu in the extended partition I will create in sdb, how do I make sure Grub gets saved on that physical disk?

Thanks again, and sorry to be such an obvious noob.

---

### Post by drs305 on 2010-04-21
Grub 2 will operate on whatever MBR you select (if they are internal drives). I don't remember if you are given the option on an initial install, but on a reinstall you can even choose to install it on *every* MBR.  G2 will point to the installed partition's boot files wherever they are during the initial install. Again, what I am saying doesn't consider Windows own requirements.

---

### Post by gencon on 2010-04-21
Ok. Many thanks for all your replies drs305. I really appreciate it. 

I'll bite the bullet and go for it now... :)

---

### Post by P4man on 2010-04-21
> **gencon said:**
> Ok cool, didn't realize it wasn't a problem.

But what about which drive's MBR Grub should be set to? That's what I don't get. If I install Ubuntu in the extended partition I will create in sdb, how do I make sure Grub gets saved on that physical disk?

Thanks again, and sorry to be such an obvious noob.

Grub is split in two parts. Stage one sits on the MBR of a harddisk, stage2 usually resides just on your ubuntu partition (in /boot/grub).

Stage 1 must be on the harddisk your bios boots from, it can be the windows drive or any other. Drive, not partition. Since its small and only occupies the MBR, it doesnt affect partitions. You could put it on any of your 3 drives and point the bios to boot from that drive and it should work, even if ubuntu itself is installed on a different drive.

If you put grub stage 1 on the drive windows is installed on, it will overwrite the windows bootloader, and create a dualboot option. If you put it on a different drive, it wouldnt affect windows, but you would have to select the OS you want to boot by selecting a different boot drive from the bios menu. A small advantage of that is that you dont risk at all messing up windows since you dont touch it. A downside is that it can become confusing as each OS will use a different drive ordering scheme and the bios menu isnt as easy to use or configure as grub menu. Either approach should work though, but each will have a different result if a drive dies or is removed.

Personally I like having windows on its own harddrive, and its own bootloader and  i put ubuntu and grub on a different drive, and configure grub to chainload the windows one. That way, i have grub dualboot, but I can pull out either drive, and still have a bootable system.

BTW, those are NOT noob questions. What noob even knows about grub or extended partitions?

---

### Post by gencon on 2010-04-21
Thanks P4man.

I finally understand what's going on. Thanks for taking the time to explain exactly what's happening with Grub. I couldn't work out how anything as substantial could fit in such a small area as the MBR.


> **P4man said:**
> BTW, those are NOT noob questions. What noob even knows about grub or extended partitions?
Ok but relative noob, and a long way from competent. :)

Cheers all, I'm going to try installing shortly... fingers crossed.

---

### Post by oldfred on 2010-04-21
What you are doing is fine for starting out with Ubuntu but I agree with P4man and like having different operating systems on different drives.

I now have 4 operating systems - 3 ubuntus and XP on three drives each boots different systems. I also have two identical drives and when I added the third I did not know which 160GB was which so if it booted windows I knew it was sda and if it booted grub I knew it was sdb. It is one real advantage of SATA, in the old days we were moving tiny jumpers around on the hard drives to change boot order.

---

### Post by gencon on 2010-04-21
Update:

Ok guys, bit of a problem.

I booted with the 9.10 Karmic install CD and followed the menu until I reached the disk menu.

The installer said: "This computer has no operating system on it."

As you know from my earlier posts that is wrong, and I am writing this on the Win XP SP2 OS on the same PC.

However I selected manual or partition (I think, sorry should have written it down) and on the next page it displayed a list of my drives and partitions.

This was different from what GParted displayed. Earlier GParted showed what Win XP calls Disk 0 as sdb, that's the disk with XP in the first primary partition taking up 100 GB and the same disk that I intend to create a 367 extended partition for 3 logical partitions for my Ubuntu installation (Root, Swap, Home). But now the partition section of the Ubuntu install program displays that same disk as sda, it's definitely the same disk, the partitions are shown correctly showing the right sizes.

So I've got GParted and the Ubuntu install program partition section displaying the disk I'm going to install on with different sd letters, sdb and sda respectively. Probably more importantly I've got the Ubuntu installer saying "This computer has no operating system on it", which is scary. I am afraid that with that message I won't be able to boot into Windows after installing Ubuntu. Nor do I know where I should create my partitions for the install - with GParted or with the Ubuntu install program?

No idea at all how to proceed - please advise me.

Thanks.

---

### Post by P4man on 2010-04-21
Hmm. ive never had the installer not detect my windows. Is it possible you hibernated windows, or somehow didnt close the filesystem properly?

Anyway, there is a very good chance windows will not boot if you continue the install. Thats not so terribly hard to fix, but still a bit of a gamble for a "noob". Mind you, even if the installer detects windows, it happens that it doesnt show up in grub and needs some tweaking. 

Be sure to have a windows CD at hand (you can run the windows recovery to reinstall windows bootloader if all else fails) and make sure ubuntu can connect to the internet from the liveCD so you can always get help here.

---

### Post by gencon on 2010-04-21
> **P4man said:**
> Hmm. ive never had the installer not detect my windows. Is it possible you hibernated windows, or somehow didnt close the filesystem properly?
No hibernation, don't know how I could not close the filesystem properly, I did a reboot to boot from the Karmic install CD.

> **P4man said:**
>  Anyway, there is a very good chance windows will not boot if you continue the install. Thats not so terribly hard to fix, but still a bit of a gamble for a "noob". Mind you, even if the installer detects windows, it happens that it doesnt show up in grub and needs some tweaking.
I'm frightened about this !!

> **P4man said:**
>  Be sure to have a windows CD at hand (you can run the windows recovery to reinstall windows bootloader if all else fails) and make sure ubuntu can connect to the internet from the liveCD so you can always get help here.
I've my Win CD, and Ubuntu connects to the internet fine from the LiveCD and did so happily after I cancelled the install and the install program continued on to the Live CD version of Ubuntu.

Has anyone else got any ideas about the ominous message "This computer has no operating system on it." and how I should proceed?

Thanks all.

---

### Post by P4man on 2010-04-21
If you're too worried, then use the very safe approach. install ubuntu on a different physical disk. Disable your windows disk in the bios (or unplug it even). Use trial and error if you dont know which of your 500GB drives it is. 

Then install ubuntu (and grub) on one of the other drives. ubuntu needs less than 10GB for the OS, and later you can move your /home to the existing windows drive with the linux partitions.

Just a thought.

---

### Post by gencon on 2010-04-22
Just to let you all know that my Ubuntu install went about as smoothly as I could possible expect, no problems at all. I manually set the partitions and filesystems required in the Ubuntu installer with no difficulty, Grub was installed correctly, I manually set it to sda, on rebooting after the installation was complete it spotted my Win XP OS and offered me a dual boot which boots perfectly into both Ubuntu and Windows.

Many thanks for all your help, it's really appreciated.

I'm sure I'll need help with other things but this thread can be considered solved.

---

### Post by drs305 on 2010-04-22
gencon,

Congratulations. Hope you enjoy your new install. And you even know  about the 'Solved' button, so you are well on your way. :-)

---

