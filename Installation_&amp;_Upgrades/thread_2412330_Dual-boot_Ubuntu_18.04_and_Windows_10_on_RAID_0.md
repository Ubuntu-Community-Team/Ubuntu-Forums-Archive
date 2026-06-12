---
title: "Dual-boot Ubuntu 18.04 and Windows 10 on RAID 0"
date: 2019-02-11
forum: Installation &amp; Upgrades
---

### Post by ishraqiyun77 on 2019-02-11
[COLOR=#242729][FONT=Arial]Have a 2TB SSD RAID 0 configuration. About 75% of the disc space is taken up with sample libraries, so there are files on both SSD. Wanting to use about 80GB of the free space for Ubuntu 18.04.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I start the bootable USB, but it isn't seeing any discs:
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][[IMG]https://i.stack.imgur.com/zWVya.png[/IMG]]("https://i.stack.imgur.com/zWVya.png")[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
Some causes that have come up in my searches: hibernation mode being enabled on the Windows partition and not freeing up the space. Hibernation mode is disabled in Windows 10 and there is 80GB of unallocated space.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The other issue, and probably the real cause, is that Ubuntu 18.04 doesn't see RAID 0 during the install process. The "fix" seems to be to switch RAID to AHCI in the BIOS. This breaks the RAID so not sure how that will affect my files given they are distributed across both drives.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Plenty of posts out there about fixing the Windows install since it will fail after changing to RAID 0, so not concerned about that so much. Just not keen having the same type of files distributed across two volumes even if they are already across two physical drives... maybe just OCD. Also, worried about corruption of files, for example, if it splits a library between C:\ and D:\ after switching to AHCI and fixing Windows.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How do you get Ubuntu to recognize a RAID 0 during install?[/FONT][/COLOR]

---

### Post by oldfred on 2019-02-11
Can you add mdadm driver and mount drives? If so I would expect server installer to work.
[https://ubuntuforums.org/showthread.php?t=833653&highlight=dynamic+disk](https://ubuntuforums.org/showthread.php?t=833653&highlight=dynamic+disk)

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

See also on this other site.
[https://askubuntu.com/questions/1117283/dual-boot-ubuntu-18-04-and-windows-10-on-raid-0](https://askubuntu.com/questions/1117283/dual-boot-ubuntu-18-04-and-windows-10-on-raid-0)

---

