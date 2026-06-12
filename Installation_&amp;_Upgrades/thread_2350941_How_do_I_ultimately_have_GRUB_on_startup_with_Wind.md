---
title: "How do I ultimately have GRUB on startup with Windows 10 (long problem, please read)?"
date: 2017-01-29
forum: Installation &amp; Upgrades
---

### Post by vaahtlnirn1 on 2017-01-29
Okay, where shall I start? I installed Ubuntu 14.04 on my laptop using a USB stick on an HP Pavilion Touchsmart that was pre-loaded with Windows 10. I have both OS's on my laptop and they both work fine. But here is my problem: Windows 10 does not recognize Ubuntu in any way at all besides pressing ESC at startup and going to Boot Device Options. I cannot go under Control Panel > System and Security > System > Advanced system settings > Startup and Recovery settings and fix it in any way, as it only lists Windows 10. I tried using boot-repair in Ubuntu with no luck. I tried using the longer "gedit" command I have seen on these forums with no luck after restarting, as well as the fact that "bcdedit" does not even list Ubuntu under it. I am so confused. What I would like as the end result is for GRUB to be my boot manager by default and I would like to be able to select my OS right at startup, but it seems as if Windows gets harder and harder to deal with every time a successor is released. I already found it initially impossible to install Ubuntu by creating a virtual ISO image and virtual disc drive and had to use a USB stick, which I did not have to do with Windows 8 on my last laptop. Any help would be appreciated and let me know if I am missing crucial info that could help in presenting a solution..

---

### Post by ubfan1 on 2017-01-29
When running Ubuntu, run sudo efibootmgr -v to see the boot order -- the shimx64.efi item should be first (or grubx64.efi is OK first if not running with secure boot).  Change the order with efibootmgr if necessary. If you do not see either entry, then you have installed Ubuntu in a different mode than Windows, legacy.  Some machines will automatically switch modes if presented with a boot choice, like a second disk, only set up for the secondary choice.

---

### Post by oldfred on 2017-01-29
Most HP violate UEFI spec that says NOT to use description as part of UEFI boot.
And of course the only valid description is "Windows Boot Manager". 

But many work arounds depending on your configuration.
Most with HP have used the fallback or hard drive UEFI entry at /EFI/Boot/bootx64.efi that still works to boot. With HP the UEFI boot entry may already exist, but is just using a copy of the Windows efi boot file.
We make that a copy of shimx64.efi and boot the hard drive, not ubuntu entry.
Boot-Repair now does the copy of shimx64.efi to bootx64.efi if you check the 'use the Standard efi file' in advanced options. You may have or then need to add an entry to boot the hard drive in UEFI boot menu.
Others have used the BCDedit or rEFInd to boot.

       Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114) 
            Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186) 
            HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)
HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681) 
            HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by yancek on 2017-01-29
> Windows 10 does not recognize Ubuntu in any way at all

True.  That's by design of microsoft as no default windows system has ever been able to read/write to Linux partitions.  You might be able to find third party software you can download which might work to access a Linux partition from windows.

I doubt bcdedit comes into the picture at all with an EFI system which is likely what you have so follow the advice by oldfred above.

---

