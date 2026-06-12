---
title: "Difficulties in manual partitioning, pls help me"
date: 2021-12-03
forum: Installation &amp; Upgrades
---

### Post by pvico89 on 2021-12-03
Hi guys, how are you today?

I'm trying to do manual partitioning to install Lubuntu, but I'm not succeeding. I have Windows 7 installed on my machine, but the option to erase all data did not appear during installation and I need to do manual partitioning to be able to install Lubuntu, but I am having a lot of difficulties.... 

I try to create new partitions, delete current partitions, edit them to new settings, but NOTHING works and I can never hit the "next" button to proceed with the installation. HELP ME, PLEASE :C

Sorry for the spelling mistakes, I'm not fluent in English.

[IMG]https://i.imgur.com/NGYYH2j.jpg[/IMG]

---

### Post by oldfred on 2021-12-03
Do you want to keep Windows?
Best not to keep Windows 7, as it is Obsolete.

And best not to keep any NTFS partitions unless dual booting as NTFS needs chkdsk and defrag which cannot be done from Linux. 
At minimum keep a Windows repair/recovery disk if you have NTFS partitions.

Best to shrink NTFS partitions with Windows tools although gparted can usually do it. Sometimes Windows then complains and users blame Linux, but those cases are also Windows issues.

I prefer to partition in advance using gparted from live installer, but you should be able to do it during install.
[https://gparted.org/index.php](https://gparted.org/index.php)

Older instructions but still same process.
[https://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](https://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

Most systems are now after 2012 when Microsoft changed to requiring UEFI boot from gpt partitioned drives. Windows 7 could be UEFI/gpt, but most Windows 7 installs were the older BIOS using MBR partitioning with 4 primary partition limit.

---

### Post by pvico89 on 2021-12-03
> **oldfred said:**
> Do you want to keep Windows?
Best not to keep Windows 7, as it is Obsolete.

And best not to keep any NTFS partitions unless dual booting as NTFS needs chkdsk and defrag which cannot be done from Linux. 
At minimum keep a Windows repair/recovery disk if you have NTFS partitions.

Best to shrink NTFS partitions with Windows tools although gparted can usually do it. Sometimes Windows then complains and users blame Linux, but those cases are also Windows issues.

I prefer to partition in advance using gparted from live installer, but you should be able to do it during install.
[https://gparted.org/index.php](https://gparted.org/index.php)

Older instructions but still same process.
[https://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](https://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

Most systems are now after 2012 when Microsoft changed to requiring UEFI boot from gpt partitioned drives. Windows 7 could be UEFI/gpt, but most Windows 7 installs were the older BIOS using MBR partitioning with 4 primary partition limit.

Could you specify better what I should do? I'm sorry for the question, I'm a layman on this subject...

and yes, i want to completely delete windows and just stick with lubuntu.

---

### Post by guiverc on 2021-12-03
You haven't provided any release details, but the manual can be found at this link for the latest *stable* version (ie. 21.10) - [https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)

Alas yeah it's in english.

Lubuntu offers some support in non-english languages; eg. at their forum/discourse site you'll find some - [https://discourse.lubuntu.me/](https://discourse.lubuntu.me/) IRC etc found here - [https://lubuntu.me/links/](https://lubuntu.me/links/)

It's a small team, so responses may not be fast.

Once partitions are deleted; a restart of the machine should have the "Erase disk" option, but I'm *guessing* to an extent as you didn't provide release details. In most cases it would have showed already.

---

### Post by GhX6GZMB on 2021-12-03
Good.
You want to do manual partitioning of your drive for a 100% Lubuntu system. No problem.
You've already gotten to the partitioning part.
Click on the "New partition table" bottom left.
Make a new partition that's 20...30 GB in size. Tick "Format", select "Mount point" as /, tick as "boot".
Make a second partition for "SWAP" (this is optional).
Make a third partition using the rest of your disk space. Tick "Format", select "Mount point" as /home

Select file system as ext4 for all partitions.

That's it. Good Luck.

---

