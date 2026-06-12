---
title: "Cannot view HDD on Windows 7"
date: 2015-04-27
forum: Installation &amp; Upgrades
---

### Post by sandeep19 on 2015-04-27
[TABLE]
[TR]
[TD="class: votecell"][CENTER]down vote[favorite]("http://stackoverflow.com/questions/29902472/cannot-view-hard-drive-from-windows-7#")
[/CENTER]
[/TD]
[TD="class: postcell"]Here is my case:
I'm running windows 7 on my laptop and wanted to install Ubuntu to run in dual boot mode. I attempted the installation using the Ubuntu install disk, but I could not get it to work, I'm assuming the reason is because my HDD partitions are all set to dynamic.

In my second attempt, I had my external HDD connected to the laptop and started the installation. I did not realize I was choosing this disk as the installation location and proceeded with the installation. The installation started, and created a 30GB ext partition on the HDD. I realized this was happening half way and pulled the drive out, causing the installation to fail.
Now when I try to read the HDD from Windows7, it does not show up in explorer or disk management, but am able to see the NTFS and EXT partitions and also the files when I boot through the Ubuntu live CD.

Is there a way I can get my HDD to be detected on Windows7? I want to drop the ext partition and just have one NTFS partition on my external HDD.[/TD]
[/TR]
[/TABLE]

---

### Post by Bucky Ball on 2015-04-27
Welcome. Then perhaps boot into Ubuntu, delete the partitions already on it with Gparted, create one large NTFS partition on the drive and then boot into Windows and see if you can see that.

---

### Post by Vladlenin5000 on 2015-04-27
Hi and welcome.

You did something that you shouldn't do no matter what and that is the result. You could have **physically** damaged the external drive!
I don't use Windows but I'm having a hard time believing that it isn't shown in disk management (I would expect it didn't in Windows Explorer but the management snap-in should always show the drive, even if blank/unformatted).
Anyway, you can *probably* recover it from a live session using GParted (search for it in dash, the first icon on the launcher, the bar on the left). It'll show you the partitions you already have (and the crippled partition table) and then you can manage the partitions the way you want. Post back if you need further help.

---

### Post by SeijiSensei on 2015-04-27
Windows has no native support for the ext filesystem.  You can install a [device driver]("http://www.ext2fsd.com/") in Windows that will let you see those filesystems.

You cannot install Linux on an NTFS filesystem because there is no native support for primitives like permissions.  If you want a dual-boot arrangement, you'll need to have a partition formatted as ext3 or ext4.  Alternatively, install [VirtualBox]("http://www.virtualbox.org/") in Windows, create a virtual machine, and install Ubuntu into that.

---

