---
title: "Linux newbie, installing Kubuntu on 64 gb partition"
date: 2019-12-26
forum: Installation &amp; Upgrades
---

### Post by prrprr on 2019-12-26
I've run Kubuntu & Ubuntu from an iso on a flash drive for a few days, I know now that I can run it on my laptop. I have also created 64gb of unallocated space on my SSD (running Windows 10 on C partition, data files on D partition). I am now at the point where I am still in Windows, but trying to figure out what to do with my unallocated space. Total ssd is 500 gigs.

(1) Should I just boot back up into my flash drive, and let Kubuntu format the partition, and then install itself? 
(2) Should I format the partition while still in Windows? 
(3) What file system should I use? Windows is giving me NTFS & exFAT as my options.

(4) I want to primarily boot into Kubuntu, but still with the option of booting into Windows 10 if I need to, so I would like my default boot order to be my Kubuntu partition (F, or whatever letter Windows will give it), but still with an option to boot into C partition. I don't want to blow away my C Windows partition, or the ability to boot into Windows.

Suggestions?

---

### Post by CatKiller on 2019-12-26
> **prrprr said:**
> (1) Should I just boot back up into my flash drive, and let Kubuntu format the partition, and then install itself?  
Yes. You'll need to turn off Fast Startup in Windows, since otherwise Windows will leave the drive dirty. You may also need to set the drive to AHCI in your BIOS; you may need to install an AHCI driver in Windows if you do that. 
> (2) Should I format the partition while still in Windows?  
No. Windows filesystems can't support proper permissions, and Microsoft tries to pretend that Linux filesystems don't exist. 
> (3) What file system should I use? Windows is giving me NTFS & exFAT as my options. 
ext4
> (4) I want to primarily boot into Kubuntu, but still with the option of booting into Windows 10 if I need to, so I would like my default boot order to be my Kubuntu partition (F, or whatever letter Windows will give it), but still with an option to boot into C partition. I don't want to blow away my C Windows partition, or the ability to boot into Windows.
Windows won't assign a drive letter. Microsoft like to pretend that no other OS exists. The installer should give you an "install alongside Windows" option. You'll have your Ubuntu bootloader (Grub) installed in your EFI System Partition along with the Windows bootloader. Grub can also boot Windows.

---

### Post by prrprr on 2019-12-26
I don't have hibernation enabled, so the Fast Startup mode wasn't available for me (it was turned off). 

OK looks like I can just boot back into my flash drive. I do want to save a few files first, and then do a D/documents partition backup, and then I'll boot into my flash drive and then do the actual installation (with the formatting of the drive done first). 

Sounds like a plan.

---

### Post by CatKiller on 2019-12-26
Yep, backups are always a good idea.

---

### Post by prrprr on 2019-12-26
The 64 gigs isn't seen as usuable by Kubuntu. I started the installation process, but chose the manual option, because by default Kubuntu was going to take all 512 gigs and blow away everything on the disk, not what I wanted.

So after choosing the manual option, it showed me all my partitions, including 1 or 2 I didn't know I had (recovery partitions?), and then the 64 gigs that I recovered from shrinking my documents partition was listed--but it was described as unsusable. After selecting it, Kubuntu gave me no option to format it at all. 

Now there was a button that said something like Create New Partition Table. I did click on that, but i panicked when I got some type of message about creating all new partitions. I want to keep the partitions that I already have, but just have Kubuntu format my 64 gigs of free space, and then install Kubuntu into that space.

I did some reading, and have come across the idea that I can only have so many partitions on my hard drive--I think 4 is the limit. OK, I see in Windows' disk management utility, the following:

I am not sure what this smallest, fourth partition is, that is taking up 450 megs of space. If my understanding is correct, it is entirely empty. I very well might have emptied it when I first partitioned this disk (I put in a Documents partition, which is the D partition in the picture). At any rate, would the easiest way for me to drop below the threshold of four partitions, be for me to simply wipe out this 450 mb partition? I can merge it with one of the other partitions, or I can just leave it as unallocated space.

Would this be the easiest way for me to go? I do have a functional Windows 10 partition (C), as well as a flash drive that has Windows 10 installation files on it (I originally bought it with W7).

---

### Post by CatKiller on 2019-12-26
The restriction for MBR partitioning is that you can only have four *primary* partitions; you can have more partitions if you have them in an extended partition that's one of your four primaries.

Windows 10 from an OEM install would be as UEFI with GPT partitions which don't have that limit. If you're running into partition limits then I guess it's from your Windows 7 install. I can't see whatever image you've posted since I'm writing from my phone.

Ubuntu is fine installed within an extended partition. If you shuffle your data around you can probably preserve whatever's on your partitions even as you nuke one to replace it with an extended partition. I understand that Windows is only happy in BIOS mode rather than UEFI if you're using MBR, so you'll want to do the same for Ubuntu.

Otherwise you could nuke everything by installing Windows 10 as UEFI/GPT and then install Ubuntu in UEFI. It depends how attached you are to your existing install.

---

### Post by prrprr on 2019-12-26
I tried to get it validated but failed. This is taking more time than I thought it would.

OK I am seeing online, a quick method to extend a partition. I will try to do that with my unallocated space. 

**Now when you say "you'll want to do the same for Ubuntu," what do you mean?** 

I suppose, given the options you've outlined for me, my approach will be to keep using BIOS and MBR, and then turn my unallocated space into an extended/logical partition, andn then install Kubuntu on that. 


> **CatKiller said:**
>  I understand that Windows is only happy in BIOS mode rather than UEFI if you're using MBR, so you'll want to do the same for Ubuntu.

Otherwise you could nuke everything by installing Windows 10 as UEFI/GPT and then install Ubuntu in UEFI. It depends how attached you are to your existing install.

At this point, I'm simply trying to save time. This entire process has taken a lot more time than I thought it would. 

Do you think it would take more time reinstalling W10 and converting it as UEFI/GPT, then extending the partition? An OS reinstall sounds like it would take more time.

---

### Post by CelticWarrior on 2019-12-26
The problem is you have the maximum number of partitions already. If you had only 3 primary partitions then byou would be able to create a forth and inside as many logical partitions as needed for Ubuntu. With 4 you can't, it doesn't matter how many unallocated space is there, it can't be used.

With GPT - implies Windows (and then Ubuntu) in UEFI mode - there's no such limit.


For modern hardware, and by that I mean anything newer than ~10 years, **always install in UEFI mode.**

---

### Post by prrprr on 2019-12-26
Ok, from here on out I'll focus on trying to convert my drive from MBR to GPT. I see some online articles. 

Here is one: [https://www.thewindowsclub.com/convert-mbr-to-gpt-disk](https://www.thewindowsclub.com/convert-mbr-to-gpt-disk)

The second option looks like what I want. I could simply back up all my D partition (data files), and then totally reinstall Windows 10 and set it up at GPT--it sounds like Catkiller was suggesting I could do that--but it looks like just keeping my current install & data would be the easiest way.

---

### Post by prrprr on 2019-12-26
Another way to do this--correct me if I'm overlooking something--is just to totally copy over all the files on my D/data partition. Then I [SIZE=2]would delete that partition. Then I could go back and use the MBR2GPT Disk Conversion Tool that failed on me before. Then, I would go back and copy my data back again, after creating a new partition for my Data. Finally, I could then install Kubuntu.[/SIZE]


Does this latest plan sound best? I already have a backup USB drive with more than enough space to temporarily hold my data.

---

### Post by oldfred on 2019-12-26
If keeping Windows in BIOS boot mode, you do not convert to gpt.
Windows only boots in BIOS boot mode from MBR. It has to have primary NTFS partition to boot from.

You can just backup your "d:" partition, create new extended & then restore most of d: into new partition and shrink to make space for Ubuntu.

---

### Post by CatKiller on 2019-12-26
To clarify: the last version of Windows I installed was Windows 2000. The last time I had a dual boot was 2005. So I can't tell you what you *should* do, or offer advice from experience because I don't have any. I *can*, hopefully, provide some insight on how the tech works, and relate the experiences of others that have passed through the forums whose posts I happen to remember.

So, from that perspective: Windows 10 appears to be working fine for you currently in BIOS mode. Keeping it in BIOS mode seems to be a viable option, but you'll need to work within the MBR limits, which means that one of your partitions has to go; potentially to be born again as a logical partition within a new extended partition.

Automatically converting from MBR to GPT sounds to me like exactly the kind of thing that might go horribly wrong, which means you'll need backups. But if you've got backups then you might as well do a fresh install. 

*If* you do a fresh install you should install as UEFI. The limited number of partitions is just one of the things that you don't have to worry about with a UEFI install; it is just generally better than BIOS mode. 

A first-time Ubuntu install takes about 20 minutes. I have no idea how long it takes to install Windows. If you reinstall you should do Windows first: Windows does not play nicely with others.

---

### Post by prrprr on 2019-12-26
OK, i just found out I don't have enough space to copy over my D partition. Tomorrow, I'll go out and buy a 2 tb backup USB drive (BestBuy has one on sale), copy over my entire D partition, then delete it, convert to GPT, and then copy over my data files, and then finally install Kubuntu. 

OK I'll report back at some point in that process tomorrow, and bring folks here up to speed. 

Thanks for the input.

---

### Post by CelticWarrior on 2019-12-27
Once you have your backup it's much easier to use Gparted from a Ubuntu live session to reinitialize the drive. Device > New Partition table and then choose GPT. It takes effect immediately and also deletes all the existing partitions. After that the drive is automatically ready for Windows and Ubuntu in UEFI mode.

---

