---
title: "Just cannot get Ubuntu and Windows 8 to work together."
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by Beauenheim on 2013-05-11
Yeah another one of these threads, last resort here.

So, I have a ASROCK 970 Extreme3
My Bios Settings are
ACHI Enabled
UEFI Enabled
Fast Boot (NOT Secure Boot, my video card cannot support it.) Fast boot is just skipping some post tests.
Windows 8 Pro x64 w/Media Center is installed on my 1TB harddrive.

I just can't get ubuntu 13.04 to install right at all, I've been looking at some guides, and the partitioning is weird (Why so complicated?) but I followed those guides to the T.
I've had mix results each install. After installing, Ubuntu is frozen with a low res picture of the desktop, mouse moves but nothing can be clicked on, with my second monitor flashing like crazy.
Then, I reboot and can only boot into windows 8, I've edited the boot loader to choose ubuntu, but no matter what option I chose for that, it just loops until I chose Windows 8.

A LOT of different options, yet I just can't do it.

So, people who are running this combination successfully, what have you done?

---

### Post by fantab on 2013-05-11
"Why so complicated?" Ask OEM manufacturer and definitely contact Microsoft. :D

Did Windows 8 come pre-installed?
What Graphics are you using?
Post a screen-shot of your partitioning from Windows.

If winodws 8 come pre-installed in UEFI, then perhaps you need [**BOOT REPAIR**]("https://help.ubuntu.com/community/Boot-Repair") to fix your Boot issues. Boot Repair, when run, scans your computer and suggests 'Recommend Repairs'. Most of the times 'recommended repars' should fix your boot issues.

---

### Post by oldfred on 2013-05-11
+1 on Boot-Repair
If it does not resolve issues of booting, you can post the link to the Boot-info report.

But if you can get it to boot in low resolution, then you are booting and Boot-Repair may not have much to fix. You do need to to fix the chainload to Windows bug and do have to have both Windows & Ubuntu in either UEFI or both in BIOS mode to dual boot.

If multiple monitors you need the proprietary video drivers and some settings, but I have not done that.
        
 ARandR Screen Layout Editor 0.1.4 - Dual screens
[http://christian.amsuess.com/tools/arandr/](http://christian.amsuess.com/tools/arandr/)
Dual nVidia cards - 2013
[http://ubuntuforums.org/showthread.php?t=2129190](http://ubuntuforums.org/showthread.php?t=2129190)
12 monitors Natty Warhal - now older
This is a success story for installing 3 ATI Firepro 2260's and 1 Radeon HD 5870 in the same computer. 
[http://ubuntuforums.org/showthread.php?t=1850517](http://ubuntuforums.org/showthread.php?t=1850517)

---

### Post by Beauenheim on 2013-05-11
> **fantab said:**
> "Why so complicated?" Ask OEM manufacturer and definitely contact Microsoft. :D

Did Windows 8 come pre-installed?
What Graphics are you using?
Post a screen-shot of your partitioning from Windows.

If winodws 8 come pre-installed in UEFI, then perhaps you need [**BOOT REPAIR**]("https://help.ubuntu.com/community/Boot-Repair") to fix your Boot issues. Boot Repair, when run, scans your computer and suggests 'Recommend Repairs'. Most of the times 'recommended repars' should fix your boot issues.

Actually it's a custom built PC, I installed a copy of Windows 8.
I have a AMD RAEDON HD 6850

I've reformatted as somehow my partitioning ruined my copy of Windows 8 in the first place.
It's now on a clean install, ready to be tried again, any suggestions for a step by step on how to do it? I plan on installing it with a USB drive as I did last time, with LiLi.
In the boot menu for the BIOS, I chose UEFI: Flashdrive
Rather than the standard legacy boot.

---

### Post by fantab on 2013-05-12
Did you partition your HDD with 'msdos' parttiton table or with 'GPT'?
Did you install Windows in UEFI mode? Did you create EFI partition?

---

### Post by oldfred on 2013-05-12
Windows will only install in UEFI mode from a flash drive.
       Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx]("http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx")
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

But if drive was gpt and you install Windows in BIOS/MBR mode it converts a gpt partitioned drive to MBR, but only deletes the primary gpt partition table. gpt also has a backup which it forgets to delete. Then Linux sees both a MBR partition table and a backup gpt partition table and gets confused. You have to erase backup gpt partition table with fixparts.
      
 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

The main requirement is that both Windows and Ubuntu need to be either UEFI or both BIOS. BIOS is the 30 year old standard we all know well. UEFI is relatively new, used by Apple since changing to Intel and now by Windows 8 as pre-installed with secure boot. But if installing yourself you do not have UEFI secure boot issues and do not have to install in UEFI mode.
Windows only boots from gpt drives in UEFI. 
Windows only boots with BIOS from MBR partitioned drives.
Ubuntu will boot from gpt partitioned drives with either BIOS or UEFI, but if dual booting you need both in same boot mode.

---

### Post by Beauenheim on 2013-05-12
Windows is installed correctly. It is on a GPT partition, with a UEFI BIOS, I did install it with the UEFI option on my flash drive. Ubuntu was set in the same boot mode. The problem seemed to be related to a boot menu issue, but I used EasyBCD and it would just not boot.

---

### Post by Beauenheim on 2013-05-12
Update: Just tried to boot from linux live usb. If I just do "Try Ubuntu" it doesn't let me click anything after it loads, just being able to move a mouse, with a flashing screen.

---

### Post by oldfred on 2013-05-12
You do not need EasyBCD with UEFI. It was upgraded to work with it but I think it adds a Ubuntu entry to BCD somehow. You would have to look in their formums.
       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

Grub has a bug and os-prober does not create correct chain load entries back to Windows efi file in the efi partition. It does the old style BIOS entries. Boot-Repair adds correct entries.
      
 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

Post a link to the BootInfo report that Boot-Repair creates.

Did try Ubuntu work before? Did you test that video works. Many have video issues.
What video card are you using?

---

### Post by Beauenheim on 2013-05-12
I unfortunately cannot even do boot repair my live usb isn't responsive. It could be video, but then I'm a technician for Windows, and know absolutely nothing about Ubunu. The install would go through and then freeze up and be unresponsive, after it's installed, exactly like using the Try Ubuntu option.

I did neglect to say this information before.

As I said in a previous post, I have the AMD Raedon HD 6850, is it possible to install the graphics drivers on a live usb to install? Maybe I'll get a responsive Ubuntu.

---

### Post by fantab on 2013-05-13
For video card, add "nomodeset": [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

