---
title: "Inspiron 17r 5737 Dual Boot"
date: 2014-02-01
forum: Installation &amp; Upgrades
---

### Post by GandalfTheNerd on 2014-02-01
I have a brand new Inspiron 17r 5737 that came pre-installed with Windows 8, updated to 8.1. My preference is for Ubuntu 13.10 (64-bit), and I would like to dual boot the machine. Installation of ubuntu was straightforward from a bootable USB stick. All was well until I ran Windows, after which the machine thereafter booted straight into Windows with no GRUB or other option displayed.

Running Boot-Repair give a warning about EFI being detected. Default Boot-Repair options were used. Results are visible at [http://paste.ubuntu.com/6853775/](http://paste.ubuntu.com/6853775/) Now the machine reports no bootable operating systems at all (neither Windows or Ubuntu), though I can make it boot from the Ubuntu USB stick.

Boot-Repair did say "Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!" and I think this is the problem. In the BIOS (version A07 - the latest) there is an option to "Add boot option". I can select a name, and then a file system. I think I need 2776276b-e799-409c-8372-dd8cc02f24f3 here. Next I am prompted by "Input File Path" with a small text field. There does not appear to be a file browser as the various examples I have found seem to show. I have tried various combinations of "sda1/EFI/ubuntu/shimx64.efi", "EFI/ubuntu/shimx64.efi" and others to no effect. The system just refuses to boot to anything on the hard disk. UEFI boot is enabled and secure boot is disabled (as directed by Boot-Repair).

I'm really frustrated, as I can't use my new machine! A complete rebuild from the rescue disks is not appealing, and would in any case likely end up back here after reinstalling Ubuntu. Fortunately as the machine is brand new I have no data on it to lose. Any help would be gratefully received!

---

### Post by slooksterpsv on 2014-02-01
```

BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0004,2003,0000,2001,2002
Boot0000* Windows Boot Manager	HD(1,800,fa000,2776276b-e799-409c-8372-dd8cc02f24f3)File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0001* EFI USB1 PATH1	ACPI(a0341d0,0)PCI(1d,0)USB(0,0)USB(3,0)0311050000HD(1,3e,ef1372,000df1ce)RC
Boot0002* UEFI Onboard LAN IPv4	ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(ecf4bb738278,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot0003* UEFI Onboard LAN IPv6	ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(ecf4bb738278,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0004* ubuntu	HD(1,800,fa000,2776276b-e799-409c-8372-dd8cc02f24f3)File(EFIubuntushimx64.efi)
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC

```

So it's going to try to boot Ubuntu first. From what this information is telling me:
1. Ubuntu
2. EFI Network 
3. Windows Boot Manager 
4. USB 
5. DVD

When you boot the computer can you press DEL, F2, F10, or something to get into the BIOS? If so go look at your boot order. Otherwise, if it's like my Toshiba, you have to Press F12 and select the HDD then select what EFI too boot from (Windows or Ubuntu). Try those, we can change the boot order (not difficult), but I'm wondering why it's giving you the error no os. It may be under the last tab, see if it shows your boot menu options like ubuntu Windows etc.

---

### Post by fantab on 2014-02-01
Have you disabled '[FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")' in Win8? Try booting Windows from UEFI menu, if you can't boot into Windows.

Boot-Repair has renamed the Windows EFI files. Run boot-repair again and check the option "Restore EFI Backups".

Tell us how it goes...

---

### Post by GandalfTheNerd on 2014-02-01
Many thanks for the reply, slooksterpsv. I can get into the BIOS and am familiar with the old-style boot settings, but UEFI,Windows 8.1 and secure boot are all new to me.

With nothing pressed, I get "Checking media" followed by "No boot device found. Press a key to reboot the machine".

If I press F12 (boot options), I can select from Windows Boot Manager or LAN (IPv4 or IPv6). Selecting Windows Boot Manager give me the same as not pressing F12 (no boot device). It looks to me as if the machine runs Windows Boot Manager in either case, and this fails to find anything bootable. My other (older) machines boot to grub first, and this allows me to select between the Windows bootloader and Ubuntu. I had hoped this would be similar. Apparently, Microsoft has other ideas these days.

If I press F2 I get more conventional settings including those for booting the machine. I have:
UEFI boot (rather than legacy)
Secure boot: disabled
Load legacy option ROM: disabled
Boot list option: UEFI

There are also options to add and remove boot options, but if I try to add one I get the "Input File Path" problem described in the OP.

---

### Post by oldfred on 2014-02-01
Boot-Repair says it updated grub.
But you have no ubuntu folder with the grub boot files in your efi partition??
It almost looks like it was deleted. 
Try from the advanced options, total purge/uninstall and reinstall of grub.

Do not say yes to the question on 'buggy' UEFI. Dell's do not need that. And run fantab's suggestion of restore efi backups as that undoes the rename.

This says you should leave legacy option ROM enabled but still boot in UEFI mode. Many Intel i915 Haswell systems. Many models of Dells are similar or identical in configuration. 
       Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)


 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)

 
            Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)

    
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

---

### Post by GandalfTheNerd on 2014-02-01
Fast boot is still enabled, and I can see how that might cause trouble. Since Windows (or ubuntu) won't book, I have tried running boot-repair again with the option "Restore EFI Backups" selected as suggested by fantab. If I can get Windows to run even once, I can turn off fast boot.

[http://paste.ubuntu.com/6855619/](http://paste.ubuntu.com/6855619/) - after "Restore EFI Backups" set and leaving "backup and rename Windows EFI files" option at the default "yes". This latter was almost certainly a mistake.

[http://paste.ubuntu.com/6855661/](http://paste.ubuntu.com/6855661/) - now with "Restore EFI Backups" set and "backup and rename Windows EFI files" option at "no".

I still get "Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!" which I don't know how to do. I still can't boot either OS, and F12 allows me to select Windows Boot Manager as before.

---

### Post by oldfred on 2014-02-01
There still is no ubuntu folder in efi partition. But the /EFI/Microsoft/Boot/bkpbootmgfw.efi is not shown even though grub menu has that as an entry. So some updates must not be happening.

You can also restore an original Windows boot file from Windows.
       Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.
backup entire efi partition (even though Boot-Repair may have done that) & then copy c: original file to this file in efi partition.
 /EFI/Microsoft/Boot/bootmgfw.efi

Some UEFI are modified to only boot Windows. For those systems the only way to boot is to rename Windows efi file, and make the original file name really be grub or grub's shim file. But then you can only boot the bkpbootmgfw.efi file (original Windows file) from grub menu as both Windows or ubuntu entry in UEFI menu actually boot grub.

You usually do not see details of entry in UEFI menu. It often just shows ubuntu and you do not see the details as Boot-Repair is suggesting. So it maybe should just suggest ubuntu entry. See post #2 which showed what UEFI has but what you see in UEFI menu is not that detailed.

---

### Post by GandalfTheNerd on 2014-02-01
Trying oldfred's suggestions.

Turned on legacy option ROM option in the BIOS.
Re-ran boot-repair.
"Purge GRUB before reinstalling it" turned on.
Ran the various apt-get commands as prompted by boot-repair. Last message was "installation finished. No error reported.", which is encouraging.
I'm assuming that the "buggy UEFI" refers to the "backup and rename Windows EFI files" question, so I answered "no" (default is "yes").
Now I get [http://paste.ubuntu.com/6855829/](http://paste.ubuntu.com/6855829/) and
"Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB-250MB, start of the disk, boot flag) ... Then select this partition via the [Separate /boot/efi partition:] option of [boot-repair].

Now I get older-style boot messages including:
Realtek PCIe FE Family Controller Series V1.34 (10/7/13).
PXE-E61: Media test failure, check cable
No Boot Device Found...

I am not that keen on trying to create a partation at the beginning of the disk due to the risk of upsetting the Dell things. After a break from this, I'll have a read of oldfred's links.

---

### Post by oldfred on 2014-02-01
Locked ESP is some issue with efi partition. 
There is a bug, but no easy work around other than full backup of efi partition, erase efi partition. Then recreate new efi partition. Use gparted. efi partition must be FAT32 formatted and have boot flag. Then restore Windows files and rerun Boot-Repair's full reinstall of grub.

       grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477)

---

### Post by GandalfTheNerd on 2014-02-02
Oh dear, that's torn it. I decided to do a Dell system restore of the Windows partition, which should at least allow Windows to boot so I can turn off fast boot. Since I haven't used the machine for anything, there is no data to lose at this point.

Unfortunately, the restore hangs at the point where it asks me to insert the second DVD (of three). So, now I have a machine with a corrupt (partially restored) hard disk and no usable restore disk set.  Dell do allow you to download a restore image, but only to the machine for which it is intended. So now I'm stuck. The only option would appear to be to call Dell for support.

Now I hate Windows 8 with a passion, and I haven't even used it yet! Thanks for all of the helpful comments. I'll have another go when I get the machine running to some extent.

---

### Post by oldfred on 2014-02-02
Since you installed Linux, the extra Linux partition, or the locked efi partition may be why reinstall fails. You can use gparted to remove Linux partition from live installer and erase efi and recreate efi partition as above.
Windows expects these partitions, so if any are missing that also could be an issue. Then recovery may work.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

I know the horse is already out of the barn, but to close the barn door:

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by GandalfTheNerd on 2014-02-03
One call to Dell later, and they have promised to send me a "recovery CD". That's an awful lot of data for one CD, so presumably that isn't quite right. In any case, I'll report back when I see what arrives.

---

### Post by GandalfTheNerd on 2014-02-07
Dell sent me a Windows 8 DVD, and it was pretty easy to get Windows running again. Since I now had a clean sheet, I followed these steps: [http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html) No boot-repair was necessary. Now I can boot both Windows and Ubuntu at will!

Lessons learned:
1) Always turn off "fast boot" in Windows 8 or above.
2) Upgrading to Windows 8.1 turns fast boot back on, so you need to turn it off again!
3) Don't trust Dell's recovery media.

Dell's technical help was actually very good, and quickly agreed to send me the required media without much fuss, making me do unnecessary steps or charging me money beyond the initial telephone call.

Thanks for all the help. Reading up on UEFI, EFI partitions and the like has prepared me for any future problems.

---

