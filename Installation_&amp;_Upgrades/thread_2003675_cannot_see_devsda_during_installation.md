---
title: "cannot see /dev/sda during installation"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by cncsc on 2012-06-14
Hi guys, 

I am currently having a problem with installing Ubuntu 12.04. I have a PC running Windows 7 and with 4 hard drives. 

All partitions listed below:

> Hard Drive A
[INDENT]	Partition 1: 100MB, System Reserved (Win7 Required)
	Partition 2: 100GB, Windows 7 OS
	Partition 3: 670GB, Data 1
	[COLOR="Red"]Partition 4: 162GB, free space for UBUNTU[/COLOR][/INDENT]
Hard Drive B
	[INDENT]Partition 1: 1TB, Data 2[/INDENT]
Hard Drive C
	[INDENT]Partition 1: 500GB, Windows Backup[/INDENT]
Hard Drive D
	[INDENT]Partition 1: 750GB, Data 3[/INDENT]


The problem is when I go to the partition step and select "Something else" during installation, all partions are displayed as a list **except partitions on HARD DRIVE A (there is no /dev/sda)**. So I am unable to get ubuntu installed. /dev/sda can be diplayed by using Gparted. It is really weird, because everything was fine on ubuntu 11.04 and earlier versions. Please help me.

---

### Post by darkod on 2012-06-14
If the disk has been used in raid, it has raid meta data remains. In this case ubuntu ignores it thinking you are using it in a raid array.

If you ARE NOT using any raid, remove the meta data from live mode with:
sudo dmraid -E -r /dev/sda

After that it should be fine. Usually this is the problem with these symptoms.

---

### Post by cncsc on 2012-06-14
> **darkod said:**
> If the disk has been used in raid, it has raid meta data remains. In this case ubuntu ignores it thinking you are using it in a raid array.

If you ARE NOT using any raid, remove the meta data from live mode with:
sudo dmraid -E -r /dev/sda

After that it should be fine. Usually this is the problem with these symptoms.

Thanks for your reply. I will try this once i'm back home.

---

### Post by cncsc on 2012-06-15
> **darkod said:**
> If the disk has been used in raid, it has raid meta data remains. In this case ubuntu ignores it thinking you are using it in a raid array.

If you ARE NOT using any raid, remove the meta data from live mode with:
sudo dmraid -E -r /dev/sda

After that it should be fine. Usually this is the problem with these symptoms.

This command works for me! Everything is OK now! Thank you again!:guitar::guitar:

---

