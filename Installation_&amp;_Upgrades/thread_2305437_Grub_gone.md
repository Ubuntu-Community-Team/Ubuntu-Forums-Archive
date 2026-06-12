---
title: "Grub gone"
date: 2015-12-06
forum: Installation &amp; Upgrades
---

### Post by paul242 on 2015-12-06
I have a Dell Precision T7500 which boots to Ubuntu, Windows 7, and Windows 10. This morning Windows 10 upgraded and corrupted Grub. When I booted after the upgrade the grub emergency boot came up. I tried boot repair with and it's report is at [http://paste.ubuntu.com/13728135/](http://paste.ubuntu.com/13728135/). It fixed it so that both Windows will now boot but Ubuntu and Grub will not. In looking at the disks with gparted it shows the partition where Ubuntu was as unallocated. Is there any way to restore the partition and grub or do I need to reinstall Ubuntu?

Thanks,
Paul

---

### Post by efflandt on 2015-12-06
I have heard of Windows 10 "upgrades"(?) deleting Ubuntu partitions. That does not actually remove the data, it just messes with the partition table. I assume that since you also are running Win7 that you are using msdos partitions and BIOS to boot, so testdisk could probably restore your Linux partition(s) and then maybe grub would be able to find the rest of itself, unless boot repair changed the mbr to a DOS/Win mbr, in which case you may need to reinstall grub (unless boot repair can then fix that).

If your computer uses UEFI instead of BIOS and/or gpt partitions, I have no experience with that yet.

---

### Post by yancek on 2015-12-06
Your boot repair output does not show any sign of any Linux filesystem or partition from fdisk or parted command nor are there any Grub files.  Did you actually have Ubuntu on its own partition or were you using wubi?  windows usually corrupts the bootloader by installing its own but I'm surprised that it would overwrite partitions but then I haven't used it for years.  I suppose you could try testdisk but you will probably have to reinstall.

---

### Post by oldfred on 2015-12-06
You do show space in the extended partition:
```
 /dev/sda4         [COLOR=#ff0000]307,286,014[/COLOR]   976,771,071   669,485,058   f W95 Extended (LBA)
/dev/sda5         [COLOR=#b22222]624,091,136[/COLOR]   976,771,071   352,679,936   7 NTFS / exFAT / HPFS


```
Your missing partition is one or more sectors after the start of sda4, the extended and ends some sector(s) before the start of you sda5. Your Linux partition may have been sda5 & got reordered on partition update. But Ubuntu uses UUID and should still be ok. You will have to reinstall grub to boot the Linux partition.

Windows for years on major updates/installs where it rewrites partition table, forgets to include the Linux logical partitions. I somehow doubt it is a bug they even want to work on. 

A few other threads with same issue. It seems parted rescue is easier to use if you know approx start & end sectors. Testdisk works in the old CHS and makes it a bit more difficult to understand, but also works.

 sudo parted /dev/sda unit s print
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

      
 [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)

Reinstall grub:
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

[URL="http://www.gnu.org/software/parted/manual/html_node/rescue.html"]
[/URL]

---

### Post by paul242 on 2015-12-06
Thanks everyone for your help. I decided to just reinstall Ubuntu and it worked.

---

