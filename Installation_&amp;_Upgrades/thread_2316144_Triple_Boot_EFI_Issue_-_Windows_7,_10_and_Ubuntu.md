---
title: "Triple Boot EFI Issue - Windows 7, 10 and Ubuntu"
date: 2016-03-05
forum: Installation &amp; Upgrades
---

### Post by jed4 on 2016-03-05
Firstly, sorry if this has been covered all ready but I've search high and low for an answer and cannot find one....

In the old days of BIOS/MBR install we could have say Windows 7, Windows 10 and Ubuntu on separate partitions and GRUB would add them nicely to the start menu, however, with EFI, it seems GRUB can only add the Windows Boot Manager to the menu and so to boot either Windows 7 or 10 requires that second level of boot menu that was not needed with MBR schemes and so, in this regard EFI is a bit of a backward step and so what I am trying to do is to add separate Windows 7 and Windows 10 entries to the GRUB boot menu - and/or to the EFI/NVRAM Boot Menu such that there is only a single level of Boot Menu. I am sure that this is possible as the Windows 10 BCD Store knows about the Windows 7 installation and so there must be some way to add the Windows 7 entry to either GRUB and/or EFI/NVRAM. The partition scheme I have is:

GPT Disk
partition 1 EFI FAT32
partition 2 NTFS Windows 7
partition 3 NTFS Windows 10
partition 4 ext4  Ubuntu
partition 5 SWAP
then some unallocated space

My install order was Windows 7 then Windows 10 then Ubuntu.

One thing I noticed is that although there is Win7 and Win10 on the system, there is only one windows directory on the EFI partition. If there were 2, then this might be easier. So what I want to do is to have GRUB and/or EFI/NVRAM show both Windows 7 and Windows 10 directly and separately in the boot menu (much like it was with the MBR scheme).

Can this be done ? and if so how please ? (please be gentle, I am fairly new to linux). Thanks.

---

### Post by oldfred on 2016-03-05
I do not know Windows, and that issue may be in some Windows forum. You would look for directly dual booting from UEFI boot menu not BCD.
And Windows 10 tries to sync UEFI entries & BCD, so may cause issues.

I have multiple installs of Ubuntu, and have tried creating multiple UEFI entries and separate folders like /EFI/ubuntu and /EFI/trusty.
But grub is hard coded somewhere to find the grub.cfg only in /EFI/ubuntu. That grub is just a config file to link to real grub.cfg in install. So it does not work.
Windows may do something similar.

You could experiment with a new Microsoft folder in the ESP - efi system partition.
Back up entire ESP before doing anything. You can copy back if necessary.
And export list of UEFI entries the -v shows details.
sudo efibootmgr -v
Grub chains to this:
chainloader /EFI/Microsoft/Boot/bootmgfw.efi
You may be able to create copy of /EFI/Microsoft or even another name and chain to it. Descriptions and boot files do not have to match. Systems only booting Ubuntu can use "Windows Boot Manager" as entry in UEFI to boot /EFI/ubuntu/shimx64.efi.
chainloader /EFI/Microsoft/Boot2/bootmgfw.efi
And edit BCD in that version.
And add another entry to UEFI.
This is a standard restore of standard Windows entry, you may be able to edit to new path/folder:
 New Windows entry - assumes default sda1  add -p 2 if sda2:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" 

Also some brands of systems like HP & Sony only boot from Windows entry. Others will directly boot an Ubuntu entry. But if system is looking for exact Windows entry even a minor change to description of Windows may not work.

---

### Post by jed4 on 2016-03-05
Thanks @oldfred I managed to do something along those lines to add extra EFI/NVRAM entries by booting Windows 7 from the chained windows boot manager and then used EasyBCD to adjust the BCD to boot just Windows 7 (without menu or delay) and then booted Ubuntu and copied /EFI/Microsoft stuff to /EFI/Microsoft Windows 7 and then created the EFI/NVRAM entry pointing to that for Windows 7. I then reboot Windows (7) and using EasyBCD I again adjusted the BCD to just boot Windows 10 and then rebooted into Ubuntu and then copied /EFI/Microsoft stuff to /EFI/Microsoft Windows 10 and then created the EFI/NVRAM entry pointing to that for Windows 10. I then rebooted into Windows(10) and readjusted the BCD back to where it was to start with.

So now I have 3 NVRAM/EFI entries: Windows BootManager, Windows 7 and Windows 10 and they all work as expected. However, I tried updated GRUB (sudo update-grub) but it still only found the single Windows BootManager entry. So I have the separate boot possibilities in the NVRAM/EFI menu itself but not yet on GRUB. I guess I would have to add those manually, now that I have the correct /EFI/(directories) but do not know how to do that part (yet!). I'm sure I will find out, and any pointers to the simplest way to do that would be gratefully received :-)

Interestingly, and probably as exepected, even when I boot either the Windows 10 or Windows 7 entry, I still only get the original BCD store (if I fire up EasyBCD) but the new /EFI/Microsoft Windows 7/ and /EFI/Microsoft Windows 10/ have enough (now frozen) info to just boot those separate Windows 7 and Windows 10 respectively but they do not have separate BCD stores once booted, which is not a problem really as there is no need to edit it again, but if I did, regardless of which EFI/NVRAM entry I booted, I will only get the original /EFI/Microsoft/ BCD store once booted.

---

### Post by oldfred on 2016-03-05
Not sure I understand BCD, is it really only using one?

Grub2's os-prober may only find entires it expect.

If you now have seperate folders in ESP, you should be able to add new entries into 40_custom to chain to each.

Copy Windows entry into 40_custom and edit to match your new paths in /EFI/Microsoft.

       Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy Windows boot stanza to and edit descriptions & paths to have only entries you want:
sudo nano /etc/grub.d/40_custom
Then do:
sudo update-grub 

If new entries work we can turn off os-prober to not find default Winodws and you only have the new one's you have added.

---

