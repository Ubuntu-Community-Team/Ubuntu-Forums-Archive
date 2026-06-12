---
title: "Ubuntu boots straight to Windows 7 with no grub menu"
date: 2015-07-26
forum: Installation &amp; Upgrades
---

### Post by amad2 on 2015-07-26
I've tried to install ubuntu yesterday (for the first time ever) and it installed just fine using an install CD of Ubuntu 14.04 64 bit.
Upon restart, my laptop (Acer Travelmate P256) boots straight to Windows 7 instead of showing any sort of menu to choose OS.
This is a dual boot installation with Ubuntu installed on the D: partition and Windows 7 on the C: partition.

I've google'd the problem and found and tried Boot Repair. It didn't work but provided this log:

[http://paste.ubuntu.com/11939000/](http://paste.ubuntu.com/11939000/)

Any help would be appreciated!

---

### Post by yancek on 2015-07-26
Have you changed the boot order in the BIOS as suggested in the last paragraph of the boot repair output?
Or tried running the suggested command from windows?

---

### Post by oldfred on 2015-07-27
Ever model Acer so far has a setting in UEFI to enable trust. And one user indicated it was not the easiest change to make. But you have to create UEFI password (never lose that) and then it opens up more UEFI settings. Then you have to enable trust for ubuntu entry &  files in /EFI/ubuntu folder.

       Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[URL="http://www.youtube.com/watch?v=QGiG1oljjZI"]http://www.youtube.com/watch?v=QGiG1oljjZI

[/URL]
 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[URL="http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot"]http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot

      [/URL]
 Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)
Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

    [URL="http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot"]
[/URL]

[URL="http://www.youtube.com/watch?v=QGiG1oljjZI"]
[/URL]

---

### Post by amad2 on 2015-07-27
Thanks for the replies guys. I've not tried what you've said above oldfred yet but I have learned something that may be of use.

My laptop boots the HDD (Windows 7) in Legacy mode. If I change this setting to boot in UEFI mode then the grub menu appears and Windows 7 no longer works.

From what I gather, Windows 7 is booting using BIOS/Legacy and Ubuntu is booting using UEFI. Maybe this is something worth looking into?

Also, I'm not running Windows 8. I'm running Windows 7.

---

### Post by oldfred on 2015-07-27
If Windows is in BIOS mode, you must have MBR(msdos) partitioning. But if you installed Ubuntu in UEFI mode, it probably converted drive to gpt partitioning and Windows will only boot from gpt with UEFI. But I do not think you can convert Windows, but would have to reinstall.

Best to convert drive back to MBR, if you can and reinstall Ubuntu in BIOS boot mode. 

Best to see details, do not run any fixes as that may make things worse at this point.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

      
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

Windows only boots from MBR with BIOS. It must have boot files on the drive set as bootable if more than one drive, have a primary NTFS formatted partition for its boot files and have boot flag on that partition. Second installs of Windows do not have to follow those rules but will overwrite the boot files on the primary NTFS partition that has other system's boot files and have no boot files of its own.

---

### Post by amad2 on 2015-07-27
Here's the BootInfo summary: [http://paste.ubuntu.com/11948648/](http://paste.ubuntu.com/11948648/)

At this point I decided to uninstall Ubuntu and have cleared the partitions containing it. Not sure where to go from here.

Also, maybe the HDD was gpt before installing Ubuntu? I vaguely remember there was a EFI system partition when first creating unallocated space for Ubuntu.

---

### Post by oldfred on 2015-07-27
Your Windows & Ubuntu are in UEFI boot mode.
At some point either original install or a repair, you did install grub in BIOS mode to the gpt's protective MBR.
Only boot installer media flash drive or DVD and actually installs in UEFI mode.Do not turn on CSM/Legacy/BIOS mode for any boot.
Flash drives usually have two entries in UEFI boot tab or one time boot key. One clearly says UEFI:name and other is just name where name is name or label of flash drive. The only one to use is the UEFI:name.

Another post showing the details required to enable trust to allow Ubuntu to boot on an Acer:
       Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)

Best to turn off fast startup in Windows. Use Windows to shrink the NTFS partition and reboot to let Windows run chkdsk and repair itself for its new size.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

More info in all the links in the link in my signature below.

---

### Post by amad2 on 2015-07-27
Quick question: When I check the boot settings it is already in legacy mode and changing to uefi means windows does not boot. Does this mean Windows is installed in BIOS/legacy mode and not UEFI mode?

Also, I've noticed the guide you linked (on [www.everydaylinuxuser.com]("http://www.everydaylinuxuser.com")) states that an EFI based system will show this screen in the installer:
[ATTACH=CONFIG]263420[/ATTACH]


However, my installer shows the option for installing alongside Windows  7. Doesn't this indicate that Windows is installed in legacy mode?

---

### Post by oldfred on 2015-07-27
Please post screen shots/photos as attachements, not in line. Not all users have high speed Internet.
You can easily attach screen shots with the paperclip icon in the Forum Advanced Editor.

The screen shot you posted is the same for both UEFI & BIOS. And whether it shows other systems may just be if they are in same boot mode as you booted installer.

How you boot installer is the way it installs. UEFI & BIOS are not compatible, once you start booting in one mode you cannot switch. Or only from UEFI/BIOS boot menu can you change boot mode.

Windows will not boot from grub if you leave Windows fast startup on, or if you leave secure boot on.
Fast startup must be off in Windows. And secure boot is not really a current requirement. It may be in future. But for now grub does not seem to be able to boot Windows from grub menu with secure boot on.

With 14.04 be sure to read caution in link in my signature. If it shows Windows it should be ok, but reinstall may say overwriting Ubuntu, but erases entire drive. Always better to use Something Else install option, but you do have to manually create your own partitions. I normally create partitions in advance with gparted, then still use Something else just to choose (change button) those partitions.

Make sure you have good backups of Windows and recovery partition.

---

### Post by amad2 on 2015-07-28
I've managed to get it to work. Thanks for the help guys!

What I did:
-Uninstall Ubuntu
-Undo and redo partitions for new Ubuntu installation
-Install as normal using Something Else install option
-Make sure laptop was booting in UEFI mode and not legacy/BIOS mode
-Set superviser password and disable secure boot
-Change initial boot device from Windows Boot Manager to HDD (containing Ubuntu installation)

Everything worked perfectly after this. Big thanks to oldfred for the help and information.

---

