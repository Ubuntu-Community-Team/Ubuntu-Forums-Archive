---
title: "Grub Not Loading After Launching Windows 8"
date: 2014-10-26
forum: Installation &amp; Upgrades
---

### Post by Toufiq_ on 2014-10-26
Hey everyone,

So i have Win 8 installed from factory on my laptop, and I installed Ubuntu on it just today. Installation, and everything went smoothly. I install, shut down, boot into GRUB 2, run Ubuntu perfectly. I shut down again, and boot into Ubuntu again. Works beautifully. But, my issue starts when I boot into Win 8 from GRUB 2. Win 8 loads and all my old files and everything I need is there. Win 8 seems to work perfectly.

BUT when I shut down and turn the computer on again, it doesn't take me to GRUB 2, rather, it boots directly into Win 8. How do I stop this?

I ran boot-repair hoping to fix this, but no luck. This is the link boot-repair created: [http://paste.ubuntu.com/8682094/](http://paste.ubuntu.com/8682094/)

The only way to boot into Ubuntu is to use the live USB, shut down, and then upon reboot, GRUB 2 will come up. But it'll go away and not come back if I boot to Win 8 until I use  the live USB again.

---

### Post by oldfred on 2014-10-26
If you want to dual boot you do have to turn off fast boot or the always on hibernation that Windows 8 uses.
Boot-Repair showed this:
> Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option. Windows is hibernated, refused to mount.


       WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 

What model Sony.
Most Sony have modified UEFI to only boot the Windows entry from UEFI:
Can you boot ubuntu entry in UEFI, or can you boot the hard drive entry in UEFI menu. 
But it is not even showing a Windows entry in summary report at line 9799. UEFI has several boot choices, UEFI with secure boot, UEFI, UEFI one time on reboot, and CSM. Not sure how Sony does the work around to only boot Windows, but it may just bypass UEFI and directly boot it.

---

### Post by Toufiq_ on 2014-10-26
It is a Sony VAIO Fit 14. svf14a15cxb specifically. All the recommended steps when installing Ubuntu on a Win 8 machine were taken. 
Hibernation is always off. I went into command prompt and turned it off with "powercfg /h off".
Secure boot is off.
To access the UEFI menu, there is an assist button that has to be pressed when laptop is shut down. To my knowledge, that is the only way to access the BIOS menu, as well.
From UEFI, there is options to go to recovery mode, assist mode, and normal Win 8 boot. There is no way to boot Ubuntu.

Edit: Even if I held the power button until the machine shut off completely, I could still not boot into GRUB.
I used this guide during installation: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Deepesh_Thapa on 2014-10-26
have a look on this threat at the end and some replies might help you out. [http://ubuntuforums.org/showthread.php?t=2250012](http://ubuntuforums.org/showthread.php?t=2250012)  I had issues with dual boot but found out that using different formated USB stick causes problem. Try making image of UBUNTU in fat32(default) format in the USB this way it will help you to install perfectly into EFI mode. However you need to disable the fast boot in your windows 8 power option.

---

### Post by oldfred on 2014-10-26
Sony's do not boot anything but Windows.

We have to do work arounds. Some rename bootx64.efi and are able to boot hard drive entry. Others rename the Windows efi file. But that requires some maintenance as Windows updates will restore a Windows copy.

Did Windows turn fast boot back on? As Boot-Repair's summary said it was hibernated. Windows likes to reset things to its defaults.

  Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)
Issues on rename
[https://bugs.launchpad.net/boot-repair/+bug/1315490](https://bugs.launchpad.net/boot-repair/+bug/1315490)
UEFI With encryption but you do not have to and with efi file boot rename
[http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/](http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/)
One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)

Reported work arounds, some work better on some systems. 
      
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)

---

