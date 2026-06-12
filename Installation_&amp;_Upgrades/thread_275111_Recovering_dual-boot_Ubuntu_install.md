---
title: "Recovering dual-boot Ubuntu install"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by xylo on 2006-10-10
Hi,
I'm totally new to linux.
I don't know how much info is required, so I'll start with my precise problem and question, then give the info later.

Ubuntu 6.06 Dapper Beta was installed (text mode installer) on a Windows XP system. [I know it's an old and beta version, but I'd like to learn what went wrong by repairing it]. Unfortunately, I was told it would be easy, so I didn't read up first. I let the installer create space and install itself in the MBR. After install ended, Ubuntu worked fine, but Windows didn't boot any more, saying "Missing or corrupt NTOSKRNL.EXE"[*]. Days and many headaches later, I decided to reinstall windows. Now windows XP boots fine again (and MS-DOS, btw), but of course, Ubuntu doesn't.

I know the Ubuntu partition is still untouched and no reinstall is required, and would like, for the sake of learning more about linux, to fix this problem without having to reinstall linux.
After reading several articles, I I've decided I want the NT loader to handle the boot process.

If I understood correctly, I need to:

1) Boot into linux (how?)
2) Modify /boot/grub/grub.conf  to tell it to install itself on the linux ext3 partition (root?).
3) Run grub so that it installs itself there.
4) Dump that partition's boot sector to a file, and place that file on C:
5) Add an entry to c:\boot.ini pointing to that file so windows can boot linux.

Could anyone tell me how to do steps 1 to 3 in detail (beginner level); I can handle 5, and perhaps even 4 with Bootpart 2.6.

And is it still true that you have to redo steps 3 and 4 whenever you update linux (or the kernel)?

Thanks very much.



Here are the details:

One IDE hard disk only, 80GB, originally with 2 partitions:
1) Primary partition, C:, Active, 4GB, FAT32, called BOOT, containg MSDOS 7.1, some DOS utilities and the windows swap file.
2) Extended partition, all remainder of disk, containing 2 volumes:
- A 20GB volume, NTFS, called WIN where WinXP (actually Win 2003) is installed with a load of applications.
- A 55GB volume, FAT32, called DATA (only very small part used)

After installing Ubuntu 6.06 Dapper Beta: 3 partitions:
1) Same as above
2) Extended partition, reduced in size, containing 3 (one extra) volumes:
- A 20GB NTFS volume (same as above)
- A 26GB volume, FAT32, called DATA (the same as above, truncated to created space)
- A 1GB volume, linux swap (new)
3) Primary partition*, 28GB, ext3, containing Ubuntu (new)


[*] Windows ARC path naming convention when numbering partitions in Boot.ini is to count Primary partitions first, followed by Drive letters (volumes) in the extended partition. It does not reserve the first 4 numbers for Primary Partitions like linux does, this is where the incompatibility between windows and linux comes from in this case. The creation of an extra Primary partition by linux installer caused my windows partition number to change from 2 to 3 (it being in an extended partition).  This was the reason why windows did not boot after installing linux. The boot.ini still had number 2 in it, when in reality the windows partition was now number 3 (according to how windows numbers partitions).  I wish I had discovered this before reinstalling windows and losing all the time I had spent to update it and install applications. ](*,) 

Why can I not see the linux swap partition in any partition table? (neither in the MBR, not the in the table belonging to the extended partition). Where is it defined?

The Grub boot menu only included an option to boot windows XP, whereas I also had an option to boot MDSOS 7.1 before installing linux.  If I may place a feature request here, it would be great if Grub could pick up all the options of the ntloader boot menu.
(Edit: I guess this feature is not necessary, since grub does not actually boot windows, but only transfers control to the windows boot loader, and that one still allows to boot all the previous OS's).

---

### Post by jd65pl on 2006-10-10
You may find the[ wiki entry ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")useful

---

### Post by gn2 on 2006-10-11
If it's not a laptop, you could fit an additional hard drive and try this;

[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

An 80Gb hard drive is less than £30 these days.
.

---

### Post by xylo on 2006-10-12
> **jd65pl said:**
> You may find the[ wiki entry ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")useful

Thanks a lot!  After some head scratching, the solution was indeed in there.  I wish the installer was a bit more intelligent, detected that the partition it created was going to change the number of my windows partition *according to the way that windows counts them*, and changed my boot.ini entry(ies) to keep my previous OS's functional.  That's the least I would expect from a user friendly OS such as Obuntu aspires to be.  Bad marks for that. Lots of bad marks.

---

