---
title: "Problems UEFI, GPT, SSHD"
date: 2013-11-27
forum: Installation &amp; Upgrades
---

### Post by alexcoliveira1 on 2013-11-27
[COLOR=#333333][FONT=HelveticaNeue-Light]Hello everyone,[/FONT][/COLOR]

[COLOR=#333333][FONT=HelveticaNeue-Light]I'm new to this technologies and I find my self struggling so much that i think it is time to ask some help. I bought an Asus S46C series laptop, very good. It came with Windows 8 single language installed, and 500GB HD + 24GB SSD and was working fine.[/FONT][/COLOR]
[COLOR=#333333][FONT=HelveticaNeue-Light]I tried to install Kubuntu with dual boot, but i got a boot error. My kubuntu wasnt installed correctly, i did something wrong or my image was crashed i don't know now. But the fact is i could still access my windows, but after trying some solutions i found around the internet i did something that "crashed" my boot and i found myself without access to both OS's. I was angry and decided to clean EVERYTHING and install from the "zero".[/FONT][/COLOR]
[COLOR=#333333][FONT=HelveticaNeue-Light]I used some methods to access my Windows Serial Number just for precaution(it was saved on my motherboard) and DELETED all the partitions, including the ones in my SSD.[/FONT][/COLOR]
[COLOR=#333333][FONT=HelveticaNeue-Light]Then I tried to install Windows again, but now I just cant make it work. During the installation it says it needs to reboot several times but after the first reboot it starts all over again like nothing happened, and I'm stuck here.[/FONT][/COLOR]

[COLOR=#333333][FONT=HelveticaNeue-Light]I tried during all the steps do the following:[/FONT][/COLOR]
[COLOR=#333333][FONT=HelveticaNeue-Light]* Use boot-repair[/FONT][/COLOR]
[COLOR=#333333][FONT=HelveticaNeue-Light]* Use troubleshooting from Windows Image[/FONT][/COLOR]

[COLOR=#333333][FONT=HelveticaNeue-Light]After getting error by error I saw those words appearing a lot of times during my searches: UEFI, GPT Table, SSD, Windows 8[/FONT][/COLOR]

[COLOR=#333333][FONT=HelveticaNeue-Light]I'm now with a 500GB HD and a 24GB SSD with 0 partitions, I'm with nothing in hands.[/FONT][/COLOR]

[COLOR=#333333][FONT=HelveticaNeue-Light]What I want after all: Install Windows 8 and kubuntu in dual-boot and if possible both SO's taking advantage of the SSD.[/FONT][/COLOR]

---

### Post by oldfred on 2013-11-27
Your vendor recovery probably requires the vendor recovery partition on the hard drive. That usually is an image of hard drive as purchased and the one key or UEFI/BIOS recovery mode just reimages hard drive from that recovery partition. If you deleted that and do not have any backups then you will have to contact vendor and see if they offer a free or low cost replacement. Or purchase a full new copy of Windows.
If you did not overwrite it, there may be a chance you could recover with test disk. But as a recovery partition if even one bit of data was changed it will not work correctly.

With the small SSD it is probably an Ultrabook with Intel SRT. That somehow uses RAID. The standard desktop installer does not support RAID, but you really do not want a RAID install anyway as the grub boot loader should be installed to the existing efi partition.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

Review link in my signature.

If thinking of reinstalling Windows, best to do it first as it has specific partition requirements, or set those up first. Then install Ubuntu. Some turn off fast boot, remove RAID meta-data and install / (root) into SSD. That way Ubuntu is fast, but Windows will not boot as fast. Others install Ubuntu just on hard drive and then turn SRT back on in Windows/UEFI.

      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

      
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[URL="https://help.ubuntu.com/community/DataRecovery#Lost_Partition"]https://help.ubuntu.com/community/DataRecovery#Lost_Partition
[/URL] Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

[URL="https://help.ubuntu.com/community/DataRecovery#Lost_Partition"]
[/URL]

---

### Post by alexcoliveira1 on 2013-11-27
For my bad lucky I have writted on the disk, cause i tried to install Windows and Linux several times in different ways, so my original partition is totally broken. What I need is a way to install any OS with this "configuration". I deleted everything, i have both kubuntu and windows images. Testkdisk showed me my old partitions but they are broken, some partitions was written in the middle. I need a light in the end of the tunnel.
The default installation are not working(both windows and linux). Any tips?

---

### Post by oldfred on 2013-11-27
Testdisk shows all versions of old partitions. You have to select a combination that does not overlap and seems to be what you want to recover. But it does not work in all cases.

Is system UEFI or BIOS. Windows only works from gpt partitioned drives with UEFI. Ubuntu will install in either BIOS or UEFI mode from its live installer, but you want Ubuntu in the same boot mode either UEFI or BIOS as Windows to easily dual boot.

Do you have Windows image or full install disk/flash drive? I have not recovered Windows so I do not know exact procedure. If an image you probably need the partitions Windows suggests as posted above or if you have what partitions you did have before you that configuration.
Then you can use Windows to shrink its c: drive to make room for installing Linux. Windows does not correctly see Linux partitions and often causes issues when installed.

You do need gpt partitioning if Windows is UEFI, or MBR(msdos) partitioning if Windows is BIOS mode.

If drive is totally blank Windows should just install, but if a image it will need partitions to reinstall into.

---

