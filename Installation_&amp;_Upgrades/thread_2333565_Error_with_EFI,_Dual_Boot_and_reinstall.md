---
title: "Error with EFI, Dual Boot and reinstall"
date: 2016-08-11
forum: Installation &amp; Upgrades
---

### Post by drakwen2 on 2016-08-11
I was about to do a clean install for ubuntu (I have Windows 10 pre installed). So as usual (this worked before) I removed all partitions, and fused it back together with the main. Now I can´t even boot Win10 nor can I install the new one due to some incompatibility on the disk table mapping. Please find below my boot-repair message:

[http://paste.ubuntu.com/22983898/](http://paste.ubuntu.com/22983898/)

Im looking for not remove/reinstall my win10, recover its booting and also be able to install Ubuntu in a separate partition. I read its content but Im not that knowleadgeable on this topics, I understood from the report that I did something wrong at some point of the installation by mixing between GPT, MBR and EFI and the suggestion offered is to correct [[COLOR=#000000]repair-filesystems[ but Im not sure what this means or how its done.[/COLOR]

Many thanks!

---

### Post by oldfred on 2016-08-11
It looks like you have damaged Windows.

With UEFI Windows only boots from gpt partitioned drives. And it requires several extra partitions to work well, but minimum is ESP - efi system partition which is the only partition with gpt that can have boot flag. With gpt it is not the same as a boot flag in MBR(msdos). It is just the way gparted knows to assign the very long GUID so UEFI knows that the FAT32 partition is the ESP where efi boot files are. 
With old BIOS the boot flag was for Windows and where Windows boot files were.
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449) 

It looks like you have a BIOS/MBR configuration on a gpt drive. With Windows that will never work.
You have to use UEFI with gpt or BIOS with MBR.

Not knowing what you deleted & moved around, I do not know if you can undo it. Its looks like it would be just easier to reinstall & restore your data from your backups.

Both Windows & Ubuntu install in the mode you boot installer. Or if you boot installer in UEFI mode, it installs in UEFI mode. And Windows in BIOS mode, incorrectly converts a gpt drive to MBR and creates more issues to resolve.

---

