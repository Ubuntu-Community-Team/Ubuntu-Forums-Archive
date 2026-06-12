---
title: "wubi + Ubuntu Install = Windows 7 Won't Boot"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by sietekk on 2013-03-26
I'm in need of some desperate help, because I can't lose my current hard drive data AGAIN. I apologize if this is a lengthy post, but I want to make sure I include as much relevant information as possible.

**Machine:**
Lenovo Y580 (upgraded)
Primary used for physics simulations/GPU computing (Matlab, Mathematica, Maple, Image Processing, etc)
i7-3630QM
16GB ram (G.Skill)
256GB Crucial M4 mSATA (primary drive)
1TB SATA 5400rpm (secondary/extra storage)
GeForce GTX 660M/Intel HD 4000 (switchable; 660M mildly overclocked)
Windows 7 Ultimate (on SSD)
Ubuntu 12.10 (on SSD)
Unlocked Insydeh20 BIOS ([http://forum.techinferno.com/lenovo-ibm/2260-lenovo-y580-y480-unlocked-bios-versions.html](http://forum.techinferno.com/lenovo-ibm/2260-lenovo-y580-y480-unlocked-bios-versions.html))

**My Linux Background:**
I played around with Slackware back in 2000-2003. I got really good at working with hard drives, partitions, reinstalling Linux and Windows 98/XP. I have not played around with Linux since then, and I didn't know UEFI/GPT/GUID existed until I bought my Lenovo and started playing around. I essentially have almost no knowledge of modern Linux, but I have decent knowledge of hardware, software, and Windows.

**History:**
I have had Windows 7 Ult running perfectly fine off the Crucial SSD for awhile now. The unlocked BIOS works exactly as it should. I've had no glitches with anything pertaining to my problem. Up until I tried installing Ubuntu with my Linux knowledgeable friend, my laptop was fine. This sucks, because I was really excited to get into Linux once again with Ubuntu.

**What Happened:**
First, I ran the install program off the Ubuntu DVD I burned. For some reason, I couldn't get past the allocating drive space menu. It didn't matter if I clicked on "Install Alongside Windows 7," "Replace Windows 7 with Ubuntu," or "Something Else," the "Continue" button remained grayed out. We thought that was odd, but decided on a wubi install without actually understanding what that meant. We thought it was a way to initialize or run a full Ubuntu installation under Windows. That was an obviously stupid idea and mistake, because when I rebooted my laptop, Ubuntu wouldn't load, and decided to try to install it on a partition I created on the SSD for Linux when I first installed Windows using "dispart." It was formatted "ntfs," but perhaps the reason wubi failed was that I didn't install it on the Win 7 partition?

Regardless of what the issue was, I went on to wipe that partition, chop out a chunk for swap, and installed a fresh Ubuntu system there. Ubuntu has been running correctly since then, but the Win 7 MSR partition (the 100-150MB partition between the boot and Windows partitions) shows up the Ubuntu task bar on the left side of the screen and in Nautilus under "Devices" where flash drives and other removable media appear. One other oddity during the installation was that the Win 7 partition was listed as "EFI Boot" instead of "ntfs," and I had to manually select "ntfs" in the install or the Ubuntu install program couldn't figure out the correct boot partition.

The bootloader(s) were messed up after the full Ubuntu install. Win 7 still booted at this time, but Ubuntu was listed in its own bootloader. I did a lot of research on GRUB, GRUB2, GPT, GUID, (U)EFI, etc. to fix the bootloader to properly load each OS, but this is where Windows ceased loading... after using "boot-repair." Here's the URLs to the boot repair webpage documenting my issues:
1) [http://paste.ubuntu.com/5649727/](http://paste.ubuntu.com/5649727/) (latest from today)
2) [http://paste.ubuntu.com/5647682/](http://paste.ubuntu.com/5647682/)
3) [http://paste.ubuntu.com/5638672/](http://paste.ubuntu.com/5638672/) (first boot-repair run from a few days ago)

**What I Think Happened:**
I don't know what happened when I first went to install Ubuntu, but the wubi installation failed. Because I misunderstood what wubi is, I just gave up on it to create a full Ubuntu installation. However, the wubi install actually changed the boot loaders (at least Windows' boot loaders), and the second, full Ubuntu install just made the boot situation even worse. Symptoms of this was the odd issue of Ubuntu seeing Windows as "EFI Boot" instead of "ntfs" and the current issue of the Windows MSR partition showing up in Nautilus' devices list. Finally, running boot-repair several times in this situation sealed the deal and messed up Windows. I also think this has caused the problem of diskpart saying "There is no volume associated with this partition" when I select the MSR partition and type "detail part" to get its specs/information.
[B]
What My Current Problem Is:[/B]
I cannot boot into Windows at all whether from the SSD or the Win 7 Install DVD, and that's preventing me from fixing Windows and deleting all the wubi junk. I planned to redo the Ubuntu install after cleaning the SSD of all wubi junk, but I can't do that. The Win 7 recovery program from the install DVD can find the Windows partition but not read from it. diskpart states "There is no volume associated with this partition" when I try to use that. Ubuntu is able to see the partition **and** read the data on the Windows partition, but that doesn't help me fix Windows. So all I can do is get proof that a partition is there, but I can't get into it outside of Ubuntu. Since this also occurs with the MSR partition, this could be the reason Windows is not booting.

The current error I'm getting when I try to run Windows is **at all** from GRUB ("Windows Boot UEFI Loader"):
[I]Windows Boot Manager
Windows failed to start. A recent hardware or software.....blah blah blah
...a bunch of blah here...
File: \EFI\Microsoft\Boot\BCD
Status: 0xc000000f
Info: An error occurred while attempting to read the boot configuration data.[/I]

**PLEASE HELP:**
How do I fix the boot partitions, boot loaders, etc. so Windows works? I really need to rescue this partition and the programs installed within. I know I can do a backup (somehow after I learn how) through the current Ubuntu install, but I've already committed over 12 hours of my life to this. It appears that no one has a proper grasp on UEFI and how it works, UEFI has not been implemented correctly by Lenovo and the InsydeH20 manufacturers, and the lot of us are going to have many problems for the foreseeable future with this idiot system. It shouldn't be this hard, when back in my Linux days, "fixmbr" and it's sub-commands fixed everything.

Thank you everyone,
Mike

---

### Post by oldfred on 2013-03-26
You can only have one efi partition per drive. You have 2. Not sure if that is only problem or not. Even with BIOS booting, you could only have one boot flagged partition. Gparted uses the boot flag to define the efi partition with gpt partitioning. While the efi partition is where all system's boot loader go, it is not like the Windows boot flag in MBR(msdos) partitioning.
Use gparted and remove boot flag from sda3.

You cannot use wubi with gpt partitioned drives, so any system with Windows 8 pre-installed will not work with wubi.
       Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

Wubi does try to edit BCD. Not sure if it got that far, but you may have to use a Windows repair flash drive to edit the BCD.
      
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

I assume editing BCD is the same, but with Windows 8, the BCD is in the efi partition.
    [http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)
You may need to check with Windows 8 forum on editing with Windows 8.
      [http://www.eightforums.com/](http://www.eightforums.com/)

Some other Lenovo
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)

Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)
Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

 
[URL="http://www.eightforums.com/"]
[/URL]

---

### Post by sietekk on 2013-03-27
Thank you for your reply!

There was only one EFI partition on my drive when Windows fully worked, but right after I tried to install wubi, sda3 (Windows) was marked as EFI. That was probably because wubi doesn't work with UEFI. There is an extra "ubuntu" selection in my bios, which does not correspond with the functional, full Ubuntu installation; there's two Ubuntus listed in my bios. This is either from wubi or boot-repair. Also, I have already attempted to remove the boot flag from the partition with Gparted, but the flag is persistent even though it will no longer appear in Gparted after I remove it.

My problem is that my Windows 7 DVD can't get into C: (sda3). It sees the drive, but access doesn't happen. bcdedit won't function either, because it says it can't find the boot info on the disk. I know it's there, because GRUB boots, the UEFI bios knows of all the installed OSs, and Ubuntu can find everything, including the files on sda3/C:. I've tried with a legit Windows 8 Pro install DVD as well with the same result. Unless there is something intrinsically different with a Windows USB recovery stick, then it won't work as well.

How do I get my GPT tables/boot manager/whatever back in order without the Windows 7 DVD? Clearly wubi must be the culprit, and I need to know how to undo what it did when installation was attempted on a UEFI machine. What did wubi do to the BCD exactly? If I know that, maybe I can figure out a way for the Win 7 Install DVD to run the recovery thing or get bcdedit to work. I'm also going to try working with Gparted again.

This is Linux. There's got to be some way to fix my GPT woes without resorting to Microsoft help or Windows forums full of morons.

Mike

---

### Post by oldfred on 2013-03-27
BCD is a hive and cannot be directly edited from Linux. Also you have to run chkdsk from Windows as there are no tools in LInux to run that.
The Windows 8 repair flash drive is UEFI, so it is a lot different than a BIOS/MBR system. Some Windows 7 systems were installed in UEFI mode, but you had to convert a standard repair to UEFI repair for Windows 7. 

I saved these links but have no idea if they will help.
  You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx]("http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx")
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

---

### Post by sietekk on 2013-03-27
It's fixed! (Ostensibly....)

I am currently booted into my Windows partition. I will document here what I did for whoever else accidentally tries installing Wubi on their UEFI system or has similar issues for whatever reason.

First, oldfred, I have not had to convert Win 7 to UEFI. I did a lot of research for the second time I installed it and did so in UEFI mode. I haven't had to convert anything to UEFI for the steps below. If Windows 8 repair flash drives are intrinsically UEFI, then I will check that out as another tool in case Windows goes south again. Thank you very much for your help!

I ran gparted AGAIN, but for some reason the boot flag stayed removed. The final boot-repair run I ran (the 3rd boot repair webpage listed in my initial post) involved using the advanced features tab, checking some different options I cannot remember, and running it. Not running boot-repair in the default mode (the first selection in the gui) may have fixed the boot flag issue. I am not sure, and I have no idea what else could have happened to permanently remove that boot flag. After the boot flag was removed, the Windows 7 Recovery/Install DVD finally accessed my Win 7 install partition (sda3). The boot flag placed on that partition was the reason why any recovery media could not find the Windows system. I booted up the Windows 7 DVD and went into System Restore to restore to a point before the Wubi install.

I was still having issues getting into Windows after the restore. I kept getting a BSOD screen with this error:
**STOP 0x0000007B (0xFFFFF880009A97E8**[FONT=arial]** 0xFFFFFFFFC0000034 0x0000000000 0x0000000000)**
It turns out this error has to do with IDE vs AHCI mode for the drive controller. I remembered the bios was set to IDE mode for installation and repair reasons, and I changed it back to AHCI. Also, the bios boot setup was set to legacy mode so Recovery/Installation media could be booted from. Setting the UEFI boot settings and boot order back to the way it was when I installed Windows finally fixed the BSOD allowing me into Windows.

I have NOT restarted since I got in. I am backing up the entire drive before I do that. I still don't know for sure how the boot flag was removed from the Windows partition, but removing that was key here besides setting the UEFI bios to the correct IDE/AHCI and boot/boot order settings. Third, Windows Disk Management does not show the MSR partition (market msftres in gparted), but Windows is running. That may be a problem, but I don't know. At least I can back up everything if I end up wiping the drive and starting over.

I will report back if I have any more issues, but no more replies to this post means everything has run well from this point forward.

Mike[/FONT]

---

### Post by oldfred on 2013-03-27
The Microsoft reserved partition is required by Windows and must be unformatted (will not show in gparted or will show as error) and must be just before main Windows install.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)

---

### Post by bcbc on 2013-03-29
> **sietekk said:**
> How do I get my GPT tables/boot manager/whatever back in order without the Windows 7 DVD? Clearly wubi must be the culprit...
No it's not clear at all. Many people have tried and failed to install Wubi on UEFI systems and that is the end of that. They boot Windows, and uninstall Wubi. There's **no way it can change your partitions**. All it does is add an entry in the BCD store, which does nothing (if you don't select it) or fails with that wubildr.mbr error (if you do). And you can remove it either by uninstalling Wubi from the Windows control panel, or even manually removing using bcdedit if you have to. But that's the end of it.

If you also ran boot-repair, then it's highly more likely that it modified your partitions - I'm not saying it did, but it does make partition changes if necessary - and you can easily verify this as it stores it's logs on every partition of your computer. So dig them up and check those.

---

