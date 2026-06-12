---
title: "installing 11.10 alongside windows"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by jam888 on 2011-10-21
i recently bought a new laptop and went to install 11.10 but when i install it, it says that there is no other os detected and only gives me 2 options, which are use entire disk, or something else, in any case, i cant seem to install it without erasing windows, which i cant do as quite a few programs i use dont have a ubuntu equivalent or work in wine e.g "UDK"

any help is much appreciated thanks :)

p.s my laptop is an ASUS with windows 7 home premium pre installed

---

### Post by agillator on 2011-10-21
I assume you are using a live cd to install. Run from it, rather than trying to install. Use gparted or the disk utility to see the partition table. There should be two partitions there. A small one will be the one it uses to reinstall windows if necessary (they do that rather than sending you the disks for Windows - I hate that) and then a large one that is the actual system partition. It should take up the rest of the disk. If that is the case, what I think you are being told is that there is no room to install although your message is screwy and I'm not absolutely sure. At any rate, assuming you see what you should (above), try resizing the windows partition so you now have free space. See what install tells you now. BE SURE TO BACK UP YOUR SYSTEM AS IT IS POSSIBLE (EASY!) TO LOSE EVERYTHING WHEN RESIZING A PARTITION. I am assuming, by the way, when you say a 'new' laptop you mean brand spanking new, not just new to you but actually a used machine.

---

### Post by Rubi1200 on 2011-10-21
As mentioned, male full backups BEFORE starting anything!

Also, you need to check in the Windows Disk Management utility and report how many partitions are listed there.

Any other information, such as whether you have RAID, would also be helpful.

---

