---
title: "Help! Botched Ubuntu 12.10 Installation (Win8 boot screen)"
date: 2012-11-03
forum: Installation &amp; Upgrades
---

### Post by nomis101uk on 2012-11-03
Hi people. 
 
Was wondering if anyone could help sort out my botched Ubuntu 12.10 installation on my W8 PC. Here's what happened...
 
I'm running a full OEM retail version of Windows 8 as my main OS. I downloaded WUBI thinking that would do the job. Before using it I created a separate partition within windows. This was the wrong move because a) WUBI's first step is simply to download the image file, not to install, so it was unnecessary, and b) it was an NTFS partition, and therefore not suitable anyway...
 
Nonetheless, after the image had downloaded onto my new (E) drive, I was instructed to restart, which I did. Here's where things went bad.
 
Now, I don't remember which came first - the error message, or the OS boot selection screen (see pics below) - but basically I never even got to the ubuntu installation menu, yet Windows, or my PC, seems to think that there is another OS installed on the system, when there isn't one! So now, even though Ubuntu is not actually installed, I get asked every time I start up which OS I would like to boot into. :(
 
2 things have happened since then. 
1) I was able to successfully install Ubuntu afterwards using a USB stick. BUT selecting the "Ubuntu" option from the OS selector screen just brings up that same error message again! The only way to boot into Ubuntu is go into the BIOS and choose my HDD as the primary boot instead WinBootManager (or whatever it's called):shock:
2) So...In an attempt to wipe the slate clean and start again, I removed all partitions apart from the main one I'm running Windows on. But STILL that damn "Ubuntu" option appears and STILL I get that error message. 
 
So does anyone know a) how to get rid of that second OS option without nuking my HDD, and b) how to neatly install Ubuntu alongside W8, such that I can use that nice, pretty, blue, fancy-shmancy selector screen? 
 
Thank you! 
 
[[IMG]http://s9.postimage.org/sh1b0abgr/IMG_20121104_012924.jpg[/IMG]]("http://postimage.org/image/sh1b0abgr/")
[[IMG]http://s16.postimage.org/7lzjxyett/IMG_20121104_012446.jpg[/IMG]]("http://postimage.org/image/7lzjxyett/")
 
**Update: Half the problem fixed. See below.**

---

### Post by bcbc on 2012-11-03
Wubi doesn't work on new computers using full UEFI boot. It seems like that applies to you. To remove Wubi, go to the Control Panel, Add/remove programs, and uninstall Ubuntu - it will remove the entry from the Windows boot manager (that's the menu you're seeing in the second pic)

PS if that doesn't work because you've deleted bits of the install (and the uninstall exe), then just remove the boot manager entry as described here:
[http://askubuntu.com/a/145605/14916](http://askubuntu.com/a/145605/14916)

On windows 8, enter "CMD", right-click, and then select "Run as administrator" from the bottom. Then run "bcdedit"
> 

This will list the Windows Boot Manager entries:

C:\Windows\system32>bcdedit

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume2
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {1476af5e-e5bc-11de-b180-0024543ae029}
displayorder            {current}
                        {1476af63-e5bc-11de-b180-0024543ae029}
toolsdisplayorder       {memdiag}
timeout                 10

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \windows\system32\winload.exe
description             Windows 7
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {1476af60-e5bc-11de-b180-0024543ae029}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \windows
resumeobject            {1476af5e-e5bc-11de-b180-0024543ae029}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {1476af63-e5bc-11de-b180-0024543ae029}
device                  partition=C:
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu

C:\windows\system32>
Note the Real-mode Boot Sector entry that has a description of Ubuntu. Copy and paste the identifier and then delete it as follows (in my case):

bcdedit /delete {1476af63-e5bc-11de-b180-0024543ae029}

---

### Post by nomis101uk on 2012-11-04
> **bcbc said:**
> Wubi doesn't work on new computers using full UEFI boot. It seems like that applies to you. To remove Wubi, go to the Control Panel, Add/remove programs, and uninstall Ubuntu - it will remove the entry from the Windows boot manager (that's the menu you're seeing in the second pic)

PS if that doesn't work because you've deleted bits of the install (and the uninstall exe), then just remove the boot manager entry as described here:
[http://askubuntu.com/a/145605/14916](http://askubuntu.com/a/145605/14916)

On windows 8, enter "CMD", right-click, and then select "Run as administrator" from the bottom. Then run "bcdedit"

Ah ha, thank you! Worked nicely. Now for the next step: Is there an established way of cleanly installing Ubuntu along side Windows 8, whereby it works with the Windows Boot Manager? As I said, installing it the old fashioned sorta worked, just not with the WBM. (unless that's because I cocked up the first time?)

---

### Post by uclugLee on 2012-11-04
When you boot from the CD or USB drive and install, do you get the option to install next to Windows 8, like with other Windows versions?

---

### Post by grahammechanical on 2012-11-04
Rather than repeat what I have elsewhere suggested as the issue, I give this link. Please read the seventh post and the links it gives.

[http://ubuntuforums.org/showthread.php?t=2079168]("http://ubuntuforums.org/showthread.php?t=2079168")

We should note, that Windows 8 is where OEMs start using secure boot and Ubuntu 12.10 can cope with it after a certain fashion. But how to fix problems is very much uncharted territory.

I suggest that you study the motherboard user guide and see what it says about secure boot. Be careful that you do not loose or wipe out the Windows certification key that was put into the UEFI BIOS as part of secure boot.

Regards.

---

### Post by nomis101uk on 2012-11-04
> **uclugLee said:**
> When you boot from the CD or USB drive and install, do you get the option to install next to Windows 8, like with other Windows versions?
 
No. And this seems to be the problem. When I did successfully install Ubuntu before, I had to choose the "Something Else" option, which made things messy when booting.
 
I was under the impression that Canonical had got some kind of approval\certification from MS, which would allow Ubuntu to be properly installed along side...Looks like I'll just have to wait until this is sorted out by the Linux community. But seeing as Consumer Preview\Release Preview have been out for a very, *very* long time, I'm kinda surprised there are problems of this sort.

---

### Post by bcbc on 2012-11-04
> **nomis101uk said:**
> No. And this seems to be the problem. When I did successfully install Ubuntu before, I had to choose the "Something Else" option, which made things messy when booting.
 
I was under the impression that Canonical had got some kind of approval\certification from MS, which would allow Ubuntu to be properly installed along side...Looks like I'll just have to wait until this is sorted out by the Linux community. But seeing as Consumer Preview\Release Preview have been out for a very, *very* long time, I'm kinda surprised there are problems of this sort.

It is supposed to be supported:
[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop#QuantalQuetzal.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure.Secure_Boot](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop#QuantalQuetzal.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure.Secure_Boot)
> Secure Boot

Ubuntu 12.10 is the first Ubuntu release to support UEFI Secure Boot, a standard for controlling what software can be run on a computer. Supporting Secure Boot, a part of the Windows 8 certification requirements for client systems, ensures that Ubuntu will continue to provide an "it just works" experience on new hardware.

Due to time pressures, only some flavors released with 12.10 will install and boot on Secure Boot hardware:

Ubuntu desktop
Ubuntu server
Edubuntu
We expect to enable all other flavors in 13.04.

Having said that, most people using the beta version of Windows 8 wouldn't have secure boot activated even if they did have a UEFI computer. So I'm guessing testing has been limited, and community support even moreso.

---

### Post by Mark Phelps on 2012-11-05
If Win8 works anything like Win7 (and that is questionable!) then do NOT make the mistake of installing alongside using the SLIDER to shrink the Win8 OS partition; instead, use ONLY the Win8 Disk Management utility to shrink the OS partition.

Then, leave the unallocated space empty (do not format it in Win8) and use "something else" in the Ubuntu installer.

---

### Post by oldfred on 2012-11-05
You have to use the 64bit version of Ubuntu. And whichever way you boot installer either UEFI or BIOS is how it will install. So you want to boot install CD or USB in UEFI mode.
Grub2's os-prober creates a BIOS version Windows chain entry which does not work. Boot-Repair will automatically create the correct entries so you can default to grub/Ubuntu & have a chain back to the Windows efi entry.

Some references:
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Some successful installs. (not secure boot).

GUIDE: (U)EFI installation Also full install post #52 superfreak on pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)

UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)
Dual Video Intel & nVidia
[http://ubuntuforums.org/showthread.php?t=1994622](http://ubuntuforums.org/showthread.php?t=1994622)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
(Phoenix Tiano). The every-other boot problem is a bit deceiving: What happens is it hangs on a warm/reboot. Boots work every time from cold/power-up. Yes, a stand-alone install of Win 7 SP1 has the exact same problem as Ubuntu. I suspect this is a Phoenix/Acer issue but who knows.
Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi](http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi)
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)

---

### Post by bcbc on 2012-11-05
oldfred... ouch. That seems like a real pain setting up a dual boot for UEFI.

Good information though (as always)

---

### Post by oldfred on 2012-11-05
Most of the UEFI installs when partitioned in advance, just work. But a lot of users do not understand gpt partitioning which adds to the level of change.
But with same issues with video as any install in BIOS, which often complicates it.

But you have to use the UEFI menu (kinda like BIOS selecting boot device) to choose which system to boot. 
But Boot-Repair will easily fix the Windows chain entry and then it is ok.

---

