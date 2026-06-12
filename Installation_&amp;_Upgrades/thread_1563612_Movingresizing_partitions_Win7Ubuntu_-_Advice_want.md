---
title: "Moving/resizing partitions Win7/Ubuntu - Advice wanted"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by Llyrnion on 2010-08-29
Hello.

I have 1 HD with the following OSes, each on his own partition:
p1 WinXP
p2 Win7
p3 Ubuntu
p4 Ubuntu Studio
p5 Unallocated (not actually a partition)

I intended to create a 5th partition, formatted as NTFS, for data. That's when I found out that Windows only supports 4 partitions per disk (yeah, I know, should've looked it up first). On Win7 Disk Management applet, they're all listed as "Primary Partition".

I've come up with a few possible solutions:
s1. Move partitions p3 & p4 down towards the end of the HD, and add half of the available  space to partition p2 (Win7) and the other half to partition p4 (Ubuntu Studio).

s2. Move partitions p3 & p4 to the end of the HD, and add all available space to partition p2 (Win7).

s3. Increase partition p4 (Ubuntu Studio) to take up all the available space.

My questions:
q1. Win7  Disk Management applet gives me no option to move or resize (other than shrink) the partitions. Does this mean I'll have to use another partition manager (e.g., gparted)?

q2. If I move the partitions p3 & p4 (both Ubuntu), will there be any impact on grub?

q3. Is there any way to turn partition p4 to extended instead of primary? If so, what are the consequences?

Any option/advice/alternate solution is welcome.

Many thanks.

---

### Post by conradin on 2010-08-29
I think the limit youre reffering to is 4 primary volumes per disk. you could make a logical volume, akin to a flash memory device, except its on your hard drive. read this:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by srs5694 on 2010-08-29
As conradin suggests, the limit is in the Master Boot Record (MBR) partition table, not in Windows.

I know of three possible solutions to this problem:


[list=1]
[*]Use an exotic boot loader that modifies the MBR with each boot, effectively hiding one or more primary partitions at each boot and presenting a different set of four primary partitions to each OS. I don't know of any modern boot loader that does this, but I've heard of boot loaders from a decade or so ago that work in this way. IMHO, this is a very risky approach, so I don't recommend you pursue it, even if you find a modern boot loader that does it. I mention this option only for completeness.
[*]Convert one or both of the Linux partitions into logical partitions, with an extended partition that encompasses the converted partition(s) and the free space. It will then be possible to add more logical partition(s) in the free space. This approach is conceptually simple, but it requires at least one free (unallocated) sector before each to-be-logical partition. At least as bad, I don't know of any utility that will do this job in a simple point-and-click way. If the free-space requirement is satisfied, it can be done with Linux sfdisk, or in a roundabout (but in some ways simpler) way with my [GPT fdisk (gdisk).](http://www.rodsbooks.com/gdisk/) There may be a tool that will do it more directly, but if so, I don't know what it is. There's a good chance that you'll need to re-install GRUB after you make such a change.
[*]Convert the disk to use the GUID Partition Table (GPT), but with a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) to satisfy Windows. The actual MBR-to-GPT conversion, including creating a hybrid MBR, can be done fairly easily with GPT fdisk; however, you'll alsmost certainly need to reinstall GRUB 2 using an emergency disk after this task is done. Also, hybrid MBRs are ugly and dangerous things, as detailed on the hybrid MBR link I provided. You shouldn't need to resize or move any partitions with this approach, but you may need to create a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) before you re-install GRUB.
[/list]


If you're interested in exploring option #2, check my [Web page on "missing" partitions in GParted.](http://nessus.rodsbooks.com/missing-parts/index.html) Although the issues aren't the same, the use of sfdisk is similar. The difference is that you'd need to create a new extended partition and change the partition number of /dev/sda4 (and perhaps /dev/sda3) to valid logical partition numbers (/dev/sda5 and above), rather than change the size of the extended partition. To use GPT fdisk to convert partitions from primary to logical, you'd load the existing partition table and then use the "g" option on the recovery & transformation menu to convert from the in-memory GPT representation of the disk back to MBR. Chances are you'll need to resize one or two partitions to create a bit of free space before at least one partition before you take either action.

---

### Post by Capt_Scribble on 2010-08-30
1-up on using LVM. They'll be a lot easier to change/resize afterwords too.

---

### Post by Llyrnion on 2010-08-31
First of all, thanks for your replies.

If I understand correctly, there is a consensus towards converting the Linux partitions (one of both) into extended and adding the remaining space as a logical volume. I'm a bit out of my depth here, so if I'm missing some important detail, just let me know.

Ubuntu Studio (US) is a fresh install, I've installed it over the weekend. I can just delete that partition, create a new one (extended), create the logical volume with the remaining free space (it'll be NTFS, as I don't trust Windows with write access to Linux FSs), and install US again.

Will this work?

However, I have a doubt about GRUB.

I had Win7 as my default OS. When I installed US, it became my default  OS. Running Startup Manager (SM) on "Standard" Ubuntu still showed Win7 as default and none of the boot menu options for US. I had to install and run SM on US to change the default back to Win7.

So, apparently US is "in charge" of the GRUB config. What do I need to do to ensure that GRUB keeps working after I remove  the US partition?

Many thanks.

---

### Post by srs5694 on 2010-08-31
> **Llyrnion said:**
> Ubuntu Studio (US) is a fresh install, I've installed it over the weekend. I can just delete that partition, create a new one (extended), create the logical volume with the remaining free space (it'll be NTFS, as I don't trust Windows with write access to Linux FSs), and install US again.

Will this work?

Yes, if you're willing to completely delete and re-install one Linux system, this approach will certainly work.

> However, I have a doubt about GRUB.

I had Win7 as my default OS. When I installed US, it became my default  OS. Running Startup Manager (SM) on "Standard" Ubuntu still showed Win7 as default and none of the boot menu options for US. I had to install and run SM on US to change the default back to Win7.

So, apparently US is "in charge" of the GRUB config. What do I need to do to ensure that GRUB keeps working after I remove  the US partition?

As a general rule, whatever OS you install last installs its boot loader, and that boot loader then controls how the computer boots. This isn't always true, since well-designed installers give you the option of not installing a boot loader, but the default is usually to install a boot loader.

In any event, this means that you can just ignore the issue and, when you've re-installed US, you'll have a fresh boot loader installed and ready to go. Alternatively, you could boot into your SM installation and re-install its version of GRUB (typing "sudo grub-install" at a shell prompt will probably do this) to keep the system bootable in the meantime. You'd then either not install US's boot loader to keep the SM boot loader instact or install US's boot loader to have it override SM's boot loader.

---

### Post by Llyrnion on 2010-08-31
OK, it's solved.

I made a few searches regarding GRUB and found a script called "Boot Info Script". I ran it and noticed the results mentioned an **extended **partition with only 1 logical drive in it.

I checked Win7's Disk manager, but saw no mention to any extended partition. So I booted Ubuntu, installed gparted, which correctly showed the partition as extended. I resized it to take up the rest of the free space, and created another logical drive, following your suggestions.

So, here's to a happy ending, and thanks for pushing me in the right direction.

---

