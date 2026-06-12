---
title: "Windows 7 and ubuntu Dual boot issues"
date: 2016-03-25
forum: Installation &amp; Upgrades
---

### Post by sahashinjan on 2016-03-25
Hi,

I have a lenovo G50-80 laptop. I have fresh installed Windows 7 Ultimate 64 bit and Ubuntu 14.04 for dual booting. Ubuntu boots fine. Now the issue is, when I select Windows 7 from Grub 2 menu, the 'Starting Windows' screen does not appear. Instead, I can see a screen with distorted colors all around the screen. After some time the screen goes blank and I can hear the windows Login sound.

I understand that windows is booting fine but the question is _Why can't i see anything on the screen_?? I can press Alt+F4 and Enter to shut down the computer as well.


I have tried to resolve it the following way:-

Deleted all partitions from the hard disk -> Recreated the partitions -> Installed Windows 7 -> Restarted the computer number of times to check if Windows boots normally.

Windows successfully booted and I could work on windows without any issues.

Now I installed ubuntu 14.04 again (this OS has GRUB 2).

After this re-installation ubuntu 14.04 boots absolutely fine but the _issue with Windows 7 comes back_. I am unable to understand why this is happening and how to resolve this issue.

I have installed Windows 7 and Ubuntu 14.04 (same installation iso in both cases) in my desktop as well. There is no issue in the desktop computer.

Any help will be much appreciated.

---

### Post by oldfred on 2016-03-25
How are you resizing the NTFS partition to install Ubuntu?
Best to only use Windows own tools to shrink NTFS & reboot immediately so it can run chkdsk.

Then install Ubuntu.
Grub really only boots working Windows.

You can try reinstalling a Windows boot loader using your Windows repair flash drive or installer's repair console.
And once Windows is working restore grub2's boot loader.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

[/URL]
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

### Post by sahashinjan on 2016-03-25
Thanks oldfred for the reply.

I have created the Windows partitions during Windows 7 installation using the Windows installation disk. The Ext4 partitions are only created by GParted.

But as I mentioned earlier, when I tried to resolve the issue, I installed Windows first and booted it several times.
It was booting absolutely fine. Which implies that it was [B]working Windows.

[/B]Then I installed Ubuntu.According to what you mentioned Grub should load Windows properly as it was working Windows. But after this installation booting into Windows got screwed up.Also I can hear the Windows login sound after sometime of booting into Windows. But there is no display!!!!!!This is a brand new laptop.The point that I have not mentioned earlier is that sometimes Windows boots absolutely fine from Grub. Odds is 2 successful out of 5 attempts.But I have to try again and again to get it booted.Any idea why this is happening and how it can be resolved?

---

### Post by oldfred on 2016-03-25
It sounds like Windows issue.

Are you installing in BIOS or UEFI boot mode?
But either way all grub does is pass boot to Windows.

Is Windows hibernated? Windows 8 or later is always hibernated which causes issues.

---

### Post by sahashinjan on 2016-03-25
I'm using Windows 7. I always shut down Windows, I don't make it hibernate.

My BIOS has settings as 'Legacy Support' in Boot Mode. I have installed both the OSes in this mode.
Once I changed the Boot Mode to 'UEFI', the machine tried to boot from LAN and boot failed. I could not open 'Boot Menu'. So I reverted back to 'Legacy Support'.

I am newbie to this UEFI system. Do Windows 7 and Ubuntu 14.04 support UEFI? Or installing them in UEFI mode will solve the issue?

Do you think Windows 8 will work properly in this machine?

---

### Post by oldfred on 2016-03-25
If you have UEFI hardware, you can run UEFI.
Some UEFI do require some work arounds as it is set for Windows.

       How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[URL="http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html"]http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html
[/URL]
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx) 

Windows 7 does not support UEFI Secure boot. If system has "Windows" and "Other" as setting that is really secure boot and for Windows 7 must use "Other".

Microsoft tried to get vendors of newer hardware to not write drivers that worked in Windows 7, only new versions of Windows. But so many, particularly companies have Windows 7 but want newer hardware that seems to have failed. If you system works with Windows 7 then not an issue.

[URL="http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html"]
[/URL]

---

