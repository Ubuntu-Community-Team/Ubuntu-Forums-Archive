---
title: "Install 11.04 on sdb"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by PenguinLust on 2011-06-07
I have two PATA drives and I wanted to install Ubuntu 11.04 on the 2nd one. For some reason, when the install program showed me the drives it could install on, it didn't show me sdb. It just showed me sda (including its partition table) and what I suspect is my SATA drive. The SATA drive wouldn't interfere w/it, would it?

---

### Post by eltonw on 2011-06-07
> **PenguinLust said:**
> I have two PATA drives and I wanted to install Ubuntu 11.04 on the 2nd one. For some reason, when the install program showed me the drives it could install on, it didn't show me sdb. It just showed me sda (including its partition table) and what I suspect is my SATA drive. The SATA drive wouldn't interfere w/it, would it?
If you select manual install instead of automatic install, you will get a section where the installer will show all your drives, and there you select which one you want as your primary partition, define your swap partition, etc.

---

### Post by PenguinLust on 2011-06-07
I did, and it didn't.
It detected my XP instalation and gave me the option of:
[LIST]
[*]Install Ubuntu alongside XP
[*]Install Ubuntu over XP
[*]Something else
[/LIST]I selected something else and it only acknowledged sda and what I believe is my SATA drive--even in the combo box where it asked for the boot partition.

---

### Post by wildmanne39 on 2011-06-07
> **PenguinLust said:**
> I did, and it didn't.
It detected my XP instalation and gave me the option of:
[LIST]
[*]Install Ubuntu alongside XP
[*]Install Ubuntu over XP
[*]Something else
[/LIST]I selected something else and it only acknowledged sda and what I believe is my SATA drive--even in the combo box where it asked for the boot partition.

Hi, boot up the livecd and click try then open gparted and look at the disks and see what is shows, if you need to do any partitioning you will have to unmount the drive first.

---

### Post by PenguinLust on 2011-06-07
Yes, I did that, too. It correctly shows all the drives the way I expect them, and also their partition tables. My sdb is already partitioned the way I want (and unmounted) so there's nothing to do there.

---

### Post by wildmanne39 on 2011-06-07
> **PenguinLust said:**
> Yes, I did that, too. It correctly shows all the drives the way I expect them, and also their partition tables. My sdb is already partitioned the way I want (and unmounted) so there's nothing to do there.Hi, you will want to make a root, swap and home partiton, so go ahead and select install then click on the something different and see if it shows you the sdb drive this time. Close gparted first and anything else that might be using that drive.

---

### Post by PenguinLust on 2011-06-07
Umm... one of us isn't understanding the other. I've already run gparted and it tells me what I expect to see: all 3 drives (2 PATAs, 1 SATA) and their partition tables. I've already got everything partitioned the way I want it.
The problem comes when I run the install program. It asks me where to install Ubuntu (and gives me the option of partitioning) but only shows me sda at this point (and what I think is the SATA). I want the install program to give me the option of installing to sdb, but it doesn't even acknowledge that drive.

---

### Post by wildmanne39 on 2011-06-07
> **PenguinLust said:**
> Umm... one of us isn't understanding the other. I've already run gparted and it tells me what I expect to see: all 3 drives (2 PATAs, 1 SATA) and their partition tables. I've already got everything partitioned the way I want it.
The problem comes when I run the install program. It asks me where to install Ubuntu (and gives me the option of partitioning) but only shows me sda at this point (and what I think is the SATA). I want the install program to give me the option of installing to sdb, but it doesn't even acknowledge that drive.
Hi,when I installed to my second drive a few days ago on the right side of the window after you click on something different to select the drive you want to put it on it had a small scroll bar very tiny on the right side of that window so I could scroll down and see the sdb drive does yours have one on the side that you need to scroll down to see it, if not I am out off ideas, it should just be there. If you see it in gparted you should have the option to install to it.

---

### Post by PenguinLust on 2011-06-07
Yes, it has that rather annoying scroll bar on the right side. I've been up and down it. And, like I mentioned, I looked in that combo box that was about where to install the boot thing. Neither acknowledged sdb.

---

### Post by Mark Phelps on 2011-06-07
From experience, I've found that the SAFEST thing to do in a multi-drive system (safe, as in preventing accidental overwriting) is to disconnect ALL drives except the one to which you intend to install Ubuntu.

After that, you can reconnect the other drives, but still boot using the Ubuntu drive.

Then, open a terminal in Ubuntu and enter "sudo update-grub".  That will regenerate the GRUB menu and create entries for your other OSs.

---

### Post by PenguinLust on 2011-06-07
Don't I need to boot using sda? I would need to have that present when installing. I have a small partition there for /boot.

---

### Post by PenguinLust on 2011-06-08
I just pulled the cables on the SATA drives and that mysterious device disappeared from the install menu and sdb appeared. So, it looks like the presence of the SATA drives/controller was a problem for the install program. *Fortunately*, I don't intend to put anything Linux on those SATAs. But I would be very annoyed if that was the case.

---

