---
title: "Windows 8 programs can't start after Ubuntu 12.10 installation"
date: 2013-03-08
forum: Installation &amp; Upgrades
---

### Post by trasmussen on 2013-03-08
Hey

The situation is this. I was running Window 8 but I needed to install an Ubuntu partition for work. I went ahead and installed Ubuntu 12.10 without knowing anything about EFI mode and legacy mode. I chose the 32 bit version of Ubuntu 12.10 because my computer is old (<2010 and running 32bit Windows 8).
The installation went well. I am able to choose between Windows 8 and Ubuntu 12.10 and both systems boots. However, when I try to open programs in Windows 8 they open and immediately shuts down again. Besides, in Ubuntu 12.10, when I try to access the drive for Windows 8 I get an error alert saying that "The NTFS partition is hibernated. Please resume and shutdown Windows properly". But I have already shut down Windows (!)

I tried re-installing Ubuntu from my DVD, but the same problems as described above, occured again. 

I don't want to re-install Windows 8, because at the moment I don't want to spend time re-installing different programs and setting up diferent code projects. 
Therefore my question is, 
1) How do I solve the problem with Windows 8 shutting down programs without effecting the programs/files on the Windows 8 partition? 
2) Or how do I get rid of Ubuntu 12.10 without effecting the programs/files on the Windows 8 partition. The Ubuntu installation (on DVD) will not let me just un-install, the only option is to un-install and re-install. 

Thx.

---

### Post by oldfred on 2013-03-09
Windows 8 is always hibernated. That is how it gets a fast boot. 

If your system is older and you installed yourself, you do not have UEFI. But unless system is real old or has less than 2GB of RAM, the 64bit version of Ubuntu may be better.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Reboot/mount issues
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)

---

### Post by p_code on 2013-03-09
I also had a hard time installing 12.04 on a new laptop because the  Lenovo's crappy buggy EFI Bios is TOO STUPID to boot from a DVD at all  unless I enabled 'legacy' SATA AHCI mode (which you can't do because it  screws with Windows 8!)   There is no reason you should have to muck  around with 'legacy' mode just to boot from a DVD so the BIOS was  obviously written by idiots, but after having to restore Windows 8 from a  backup partition, I learned my lesson - DON'T RUN IN 'LEGACY' SATA/AHCI  MODE IN WINDOWS 8 OR YOU WILL END UP WITH A CORRUPTED FILE SYSTEM!

The "legacy" settings tell the bios to make your SATA AHCI (Serial ATA) drives look like old style parallel ATA, and may also change other settings to change from UEFI/GPT boot mode back to the older original BIOS/MBR boot.

Both these options were needed to install XP from older media which hasn't been patched to have the required SATA drivers and can't support GPT partitioning, but they cause nothing but heartache for 64bit Windows 8.

The SATA AHCI legacy settings are also NOT needed for Ubuntu, which already has proper SATA drivers - but you may need to muck around with OTHER 'legacy' settings if you are dealing with Microsoft's 'secure boot' UEFI/GPT boot mode.

 In that case you may need to either turn on 'Legacy Boot' support, or alternately, DISABLE 'secure boot', or BOTH (BIOS's vary on how these options are named and handled).

**But, again, do _NOT_ enable any 'Legacy' mode associated with the _SATA/AHCI_ because it can cause massive disk corruption issues with Windows 8**.
 
For me, the magic combination was to turn ON 'Legacy' boot mode in the BIOS, turn OFF "secure-boot" mode, and also to make sure NOT to enable 'Legacy' SATA AHCI.

Then I installed Ubuntu from a USB stick because these settings would only boot the Ubuntu installer from USB, but not DVD (but that issue may be spicific to the crappy BIOS in my Lenovo G580).

But don't get too discouraged, after really horrible initial problems, after I found the right BIOS settings, my laptop is now working very nicely, with both Ubuntu and Windows working perfectly, as well as being able to seamlessly boot a half dozen other distros via USB just by plugging in their respective thumb drives before powering up.

---

