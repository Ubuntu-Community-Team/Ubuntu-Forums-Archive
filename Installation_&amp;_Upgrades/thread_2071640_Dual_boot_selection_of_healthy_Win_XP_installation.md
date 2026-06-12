---
title: "Dual boot selection of healthy Win XP installation not working"
date: 2012-10-16
forum: Installation &amp; Upgrades
---

### Post by rabidmaddog on 2012-10-16
Hi everyone. I've set up a number of dual and triple boot machines with various Ubuntu variants over the years, but this problem has me a bit stumped. I'm hardly an expert, but more of an experienced enthusiast. Anyway, I've installed Lubuntu onto a dedicated hard drive with an existing Windows XP partition on a different, dedicated drive. I've done this many times and it always works like a champ. However, this time, the resulting GRUB entry for "Windows XP" results in "A drive read error has occurred...". Normally, I would suspect that the MBR or other boot related files of Windows were damaged or overwritten, despite not even touching it in the Lubuntu installation process and specifying GRUB be installed on the same drive as Lubuntu. 

Now, here is what is warping my brain. I can select the BBS popup during start-up, manually select the drive with Windows XP on it, and it boots absolutely fine. I've tried sudo update-grub and sudo update-grub2, both of which quickly locate Lubuntu and Windows XP and create the resulting menu entries, but the problem persists. I'm not clear on the distinction between GRUB and GRUB2 at this point. Updating GRUB has always worked in the past when a second OS is anywhere on the system or a drives location has changed. 

I'm stumped. It's not a huge problem since I can still run XP for my Netflix viewing through booting it with BBS, but it would sure be nice if the GRUB menu would work. 

Any ideas?

Regards,

Dan

---

### Post by oldfred on 2012-10-16
Welcome to the forums.

Please download into Ubuntu liveCD or USB or download full repairCD and run the BootInfo report. Post link it creates to report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.


Are these IDE drives? 

We have seen where drive order is an issue. Windows XP is hard coded to drive & partition. And when booting BIOS writes the drive order onto hard drive. Grub & grub2 when booting from a second drive still see it as hd0 as BIOS has set second drive as boot drive. But both grub & grub2 will add mapping commands so XP thinks it is drive0.
But in some cases the mapping does not seem to work and then the only choice has been to install grub2 to the MBR of the Windows drive so hd0 in grub is also drive0 in Windows.

---

### Post by rabidmaddog on 2012-10-16
Thanks for the reply! I suspect this is a drive order problem as you suggested. It makes sense. I installed WinXP with all other drives (all SATA) physically disconnected, so it should be hard coded as the 1st drive. It's no longer in that position. Interesting. I would actually have no problem putting grub on the XP drive and setting is as first in the BIOS. That sounds like the simplest fix in this case and I'll be interested to see if it works! If not, I'll post the boot report as soon as I'm able.

I'll see if I can set the XP drive as #1 in the BIOS, yet still have it second in the boot order. I don't recall if that's feasible in my BIOS. We shall see.

Thanks again. I appreciate the help.

Dan


> **oldfred said:**
> Welcome to the forums.

Please download into Ubuntu liveCD or USB or download full repairCD and run the BootInfo report. Post link it creates to report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.


Are these IDE drives? 

We have seen where drive order is an issue. Windows XP is hard coded to drive & partition. And when booting BIOS writes the drive order onto hard drive. Grub & grub2 when booting from a second drive still see it as hd0 as BIOS has set second drive as boot drive. But both grub & grub2 will add mapping commands so XP thinks it is drive0.
But in some cases the mapping does not seem to work and then the only choice has been to install grub2 to the MBR of the Windows drive so hd0 in grub is also drive0 in Windows.

---

### Post by oldfred on 2012-10-16
I had (still have but not used) XP in sda, and have booted from sdb, sdc & sdd (flash drive) and grub always added mapping commands & XP booted. All my drives are SATA except flash as USB.

I often use chainloading type entries and drive order would always have the boot drive as hd0. It seemed that drives were then in SATA port order. But sometimes flash drive would be first, last or I have an empty port in the middle of my SATA connections and the flash drive would sometimes be that drive in order. So when my chain entry did not work, I would just start editing the hdX until I found the right number for X.

I took an entry the os-prober made for XP and copied it into my 40_custom and turnoff os_prober. I have used an entry like this for almost all my installs. Yours should be similar except different UUID>

> menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    insmod part_msdos
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 04b05b70b05b6768
    drivemap -s (hd0) ${root}
    chainloader +1
}


---

### Post by rabidmaddog on 2012-10-17
Thanks, I'll give that a shot. My attempt to install GRUB on sda (Windows XP) failed with this, which I've never seen before; nor do I know what it means:

maddog@Lubuntu64:~$ sudo grub-install --recheck /dev/sda
[sudo] password for maddog: 
/usr/sbin/grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it..
/usr/sbin/grub-setup: error: embedding is not possible, but this is required for cross-disk install.
maddog@Lubuntu64:~$

In any case, here's my bootinfo summary. As you can see, I also installed GRUB to sdc in hopes that might work when setting that drive first, but the same problem occurs in that case.

[http://paste.ubuntu.com/1285119/](http://paste.ubuntu.com/1285119/)

Thanks again,

Dan

 




> **oldfred said:**
> I had (still have but not used) XP in sda, and have booted from sdb, sdc & sdd (flash drive) and grub always added mapping commands & XP booted. All my drives are SATA except flash as USB.

I often use chainloading type entries and drive order would always have the boot drive as hd0. It seemed that drives were then in SATA port order. But sometimes flash drive would be first, last or I have an empty port in the middle of my SATA connections and the flash drive would sometimes be that drive in order. So when my chain entry did not work, I would just start editing the hdX until I found the right number for X.

I took an entry the os-prober made for XP and copied it into my 40_custom and turnoff os_prober. I have used an entry like this for almost all my installs. Yours should be similar except different UUID>

---

### Post by oldfred on 2012-10-17
Your sda drive starts at sector 40 which if very unusual(probably due to drive sector/track see below). When grub installs, it installs boot code to the MBR, but since MBR is tiny, it also installs core.img to the sectors after the MBR. Or you do not have enough room for all of grub.

XP and older versions of Ubuntu (actually partition tools) defaulted to the first partition at 63 for the first sector like your sdb drive. 

All new partitioning tools and since Vista Windows start first partiton  at sector 2048 for better compatibility with the new 4K and SSD drives. Your sdc drive starts at 2048.

Your sda drive has this: 28 heads, 40 sectors/track which is a bit unusual. LBA or large block allocation usually uses 255 heads, 63 cylinders and whatever number of sectors is needed for the drive size. Flash drives often have different settings but hard drives have not had CHS settings in BIOS since drives went over 8GB. Larger drives then had to use LBA.

Is sda an older IDE drive?

I do not like moving Windows partitions as they have internal settings for start & size that must match partition table. Changes always require chkdsk and sometimes moving start then does not reset correctly. 

Your unusal configuration and drive may be why grub has issues. What setting is BIOS set to? Large or LBA or older IDE?

---

### Post by rabidmaddog on 2012-10-18
It's an older SATA drive. If it's an oddball, that would certainly explain the strange behavior. I can always pick up a newer drive, not to mention larger, and either clone or install XP on that and give it another go. However, given that its purpose is solely to watch Netflix and that it's never destined to be the primary OS, I may just stick with using the BBS to get to Windows. Even if the GRUB menu gave me access to it, I'd still have to press a key anyway. No big deal. I'm not sure we can officially call this solved, at least in the context of my current configuration, but I think it certainly falls into the category of "not worth the hassle". Seems to me it's a problem caused by my goofy hard drive layout. I've set up this same scenario on other machines and GRUB has always worked just fine, even on this machine for that matter, just not with the hard drive in question.

Thanks for the help nonetheless.

Dan 


> **oldfred said:**
> Your sda drive starts at sector 40 which if very unusual(probably due to drive sector/track see below). When grub installs, it installs boot code to the MBR, but since MBR is tiny, it also installs core.img to the sectors after the MBR. Or you do not have enough room for all of grub.

XP and older versions of Ubuntu (actually partition tools) defaulted to the first partition at 63 for the first sector like your sdb drive. 

All new partitioning tools and since Vista Windows start first partiton  at sector 2048 for better compatibility with the new 4K and SSD drives. Your sdc drive starts at 2048.

Your sda drive has this: 28 heads, 40 sectors/track which is a bit unusual. LBA or large block allocation usually uses 255 heads, 63 cylinders and whatever number of sectors is needed for the drive size. Flash drives often have different settings but hard drives have not had CHS settings in BIOS since drives went over 8GB. Larger drives then had to use LBA.

Is sda an older IDE drive?

I do not like moving Windows partitions as they have internal settings for start & size that must match partition table. Changes always require chkdsk and sometimes moving start then does not reset correctly. 

Your unusal configuration and drive may be why grub has issues. What setting is BIOS set to? Large or LBA or older IDE?

---

### Post by oldfred on 2012-10-18
If you want to experiment:

If it is not a huge concern, then you can with gparted just move the partition start to the right to sector 63 or it may only let you change to sector 2048. Immediately run chkdsk and see if Windows will boot.

If you have any of the Window partition tools you can use that also. The only issue I have seen is some NTFS partitions have the MFT near the beginning, often changing some things move it to the middle of the partition. But if partition change gets in the way of the MFT then the NTFS partition can be corrupted.

You could also do a full backup. change partition and then restore.

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by darkod on 2012-10-18
If you are willing to clone, no need to spend money on new disk.

First clone the XP partition to some external or to another internat disk.
Then boot ubuntu and delete that partition. Create new one in its place, Gparted should make it start at sector 2048 (1MiB) automatically.

Clone XP back to the partition.

You will need to run update-grub because the partition UUID will be changed, but apart from that it should work. And provided this is the issue. :)

---

