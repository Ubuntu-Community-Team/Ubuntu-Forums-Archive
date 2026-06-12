---
title: "Win 10 / Ubuntu Studio Dual Boot issues"
date: 2016-03-10
forum: Installation &amp; Upgrades
---

### Post by JamKromium on 2016-03-10
Greetings programs!

I am having issues trying to get Windows 10 / Ubuntu Studio to boot following an upgrade from Windows 7.

Originally I couldn't boot either so I followed the instructions to do a recommended boot repair and that got me back into Windows 10 which was working well (well as well as Windows 10 can work). Following this GRUB disappeared so today I tried to restore it by repeating the repair process however this has resulted in me again being unable to boot into either (just a flashing _ shown).

Here was my boot info with Windows 10 working prior to the boot repair to restore GRUB:
[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]
[http://paste.ubuntu.com/15341371/](http://paste.ubuntu.com/15341371/)

Following the attempted repair this was the boot info:
[http://paste.ubuntu.com/15341384/](http://paste.ubuntu.com/15341384/)

I then tried the repair again (no change, neither bootable and still just a flashing _):
[http://paste.ubuntu.com/15341411/](http://paste.ubuntu.com/15341411/)

I would be most thankful if someone could advise on how I could restore both Windows 10 and Ubuntu Studio. Failing then just restoring Windows 10 again and I can look at sorting/re-installing Ubuntu Studio as I currently have nothing worth saving on it.

Thanks!

---

### Post by oldfred on 2016-03-10
For Windows to boot, boot flag must be on primary NTFS partition with boot files which looks like sda1, but you have boot flag on sda5. Use gparted to move boot flag or Windows repair (set active is what Windows calls boot flag). Grub does not use boot flag.

Install of Windows 10 on BIOS system has same bug Windows has had for years. Any major update in Windows rewrites partition table and it conveniently forgets to include the Linux logical partition. Partition is still there, but not in partition table.
Usually testdisk or parted rescue can restore partition and then Boot-repair or a reinstall of grub works.

Some using testdisk restore incorrect set of partitions, best to have backup of current set of partitions, so worst case you can start over.
 backup before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt 

These all are essentially the same, some may show more info. Some are testdisk others parted rescue, either should work.

 [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by JamKromium on 2016-03-11
Thanks for the advice oldfred, I've managed to get back into Windows 10 by setting the boot flag on sda1 (ended up using fdisk option a).

I am still working through the information in the links you provided but will let you know how I get on.

---

### Post by JamKromium on 2016-03-12
Sorted! Thanks oldfred.
Basically followed the advice above:
1) In linux boot-repair rescue USB set the boot flag off on sda5 and on on sda1 using parted.
2) Used parted rescue option on ext4 which was appearing as unallocated space.
3) Carried out the recommended repair option using boot-repair.

---

### Post by oldfred on 2016-03-12
Glad that worked.

You can change thread to Solved.

---

### Post by goofprog on 2016-03-12
the way I learned how to make a successful dual boot system is to make Windows boot up first and then let grub alter the boot partition for linux.

---

