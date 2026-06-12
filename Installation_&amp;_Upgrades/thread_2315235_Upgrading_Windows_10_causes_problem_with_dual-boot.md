---
title: "Upgrading Windows 10 causes problem with dual-boot :("
date: 2016-02-27
forum: Installation &amp; Upgrades
---

### Post by manu4u on 2016-02-27
Hi I had a system working fine with dual-boot - Windows 10 + Ubuntu. But the latest update from MS caused the screen to go blank. By mistake I clicked on Windows 7 recover procedure and that caused me to get to grub-recover> screen.

Ran boot-repair and I could not even see that said that could not find a bootable drive :(

Tried to install grub using Ubuntu Live-CD and now opens grub> but am not stuck.

Can someone please help.

---

### Post by manu4u on 2016-02-27
Got windows restored, but the extended partition containing the Linux is no longer visible to grafted (shows up as unallocated memory). Was running Ubuntu using a live CD to see this.

---

### Post by manu4u on 2016-02-27
Correction gparted and not grafted

---

### Post by oldfred on 2016-02-27
Windows bug on partition updates with major upgrades or installs. It forgets to write Linux logical partitions. Partition is still there, just not in partition table.

Most can restore partition to partition table with parted rescue or testdisk. Some just then work, others have to reinstall grub.

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

---

