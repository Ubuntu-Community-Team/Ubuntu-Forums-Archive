---
title: "Dual boot windows 7 and Xubuntu upgrade to windows 10 crash"
date: 2015-08-03
forum: Installation &amp; Upgrades
---

### Post by Dovid_Baars on 2015-08-03
to the best of my memory I had two partitions one for windows and one for Xubuntu then another one for storage, 
As I don't use Xubuntu that often I was not thinking of it and foolishly ran the upgrade to 10.

After restarting on the process it boots to grub rescue.

I saw others with this issue but I would really appreciate some personal help to avoid complications,
I really don't want to lose the data on the storage partition which was only partly backed up the rest is recoverable and if I end up with only windows and no Xubuntu that is ok I can set that up later as It is not my main os.

I really appreciate the advice!

---

### Post by oldfred on 2015-08-03
Windows is notorious at not re-writing partition table with the Linux partition if BIOS/MBR and Linux is in a logical partition. It is still there & just needs to be added back to partition table.
Testdisk or parted rescue usually work.

But grub will not boot a hibernated Windows and new Windows use a fast startup which is always on hibernation. 

If you just want Windows, and your system is BIOS with MBR partitions, if just boot loader, you can use Boot-Repair or manually install a Windows boot loader. 
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[URL="https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader"]https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader
[/URL]
 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[URL="http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8"]http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8

[/URL]Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[URL="http://gparted.sourceforge.net/faq.php/#faq-22"]http://gparted.sourceforge.net/faq.php/#faq-22

      [/URL]Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

You want to be sure to keep all existing partitions with boot, primary or logical setting, but add the one missing that is shown as D.
[URL="https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader"]
[/URL]

---

### Post by prshah on 2015-08-03
The first thing you should check is to see if your storage partition is intact. Boot off a live CD, and mount and check if your partitions are undisturbed.

Then, backup.

To boot Windows normally, you will need to remove GRUB.

For this, you will need Windows media. See more information at [http://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader](http://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader)

Don't hesitate to post back if you need more guidance.

---

