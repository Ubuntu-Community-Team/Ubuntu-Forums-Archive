---
title: "Can't install Linux on Lenovo with UEFI"
date: 2014-02-15
forum: Installation &amp; Upgrades
---

### Post by skippsav on 2014-02-15
I've just got a Lenovo Ideapad Y510p with Win 8 (yes, it really is that bad!!!) installed and I want to dual boot with Linux (pref Ubuntu).
The Ideapad has UEFI but I can't see any Secure Boot options and I've set Hibernate to Never in win8; I've followed [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) to no avail. Also, if  I put UEFI into legacy mode then Windows does not work, so I still cannot make a dual boot system. 

When I try to install Ubuntu 12.04 LTS from an EFI booted live USB, I just get the ubi-partman crash error 10 and there is no where I can put "nodmraid" that will recognise it. I can 'try' this from the USB though.

When I try to install (or try) 13.10 from an EFI booted USB, it just hangs very early on and the computer becomes totally unresponsive and I have to force a power off with the power button. 
[B]
Can anyone point me in the direction of a good way to get linux dual booting on a Lenovo Ideapad with UEFI and Windows 8 installed at present?[/B]

I'll be honest, this is more of a moan than an expectation of finding a solution....

---

### Post by fantab on 2014-02-15
The following url links have some useful information with respect to Ideapad:
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

Can you boot with Ubuntu DVD/USB and "Try Ubuntu without installing"? If you can then do so, open Terminal [Ctrl+Alt+T], run the following commands and post the output here:
```
sudo parted -l
sudo fdisk -l
```

Ubuntu 13.10 should work better as it supports newer hardware and techs.

---

### Post by skippsav on 2014-02-15
I'll look at the links in a moment tanks.

The 13.10 USB will not do anything. A few seconds after booting into it the computer freezes...

---

### Post by oldfred on 2014-02-15
Someone posted this, but was probably an older version of Ubuntu. And in legacy you install in BIOS boot, and have to use Boot-Repair to convert to UEFI boot.

 > Lenovo's  buggy EFI Bios is will not boot from a DVD at all unless you enable 'legacy' (which you can't do because it screws with Windows 8!)
 The work around was to turn ON 'Legacy' boot mode in the BIOS and turn OFF "secure-boot" mode from locking out Ubuntu), and also make sure to turn OFF 'Legacy' SATA AHCI to ATA.
Then I installed Ubuntu from a USB stick (because these settings would only boot the Ubuntu installer from USB, but not DVD). 

   

Another lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not anyother entry
[http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470)

Many more links, not sure if they apply to your model. Seems that Lenovo's are not the easiest to work with.
 See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)
 lenovo u310  - install Ubuntu to part of SSD Post #19 
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo U410 How to 
[http://ubuntuforums.org/showthread.php?t=2190980](http://ubuntuforums.org/showthread.php?t=2190980)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.
Lenovo Ideapad z585 Precise Installed wifi OK Dual Boot Win 7 no Sound SOLVED - other issues
[http://ubuntuforums.org/showthread.php?t=2170099](http://ubuntuforums.org/showthread.php?t=2170099)
[https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS](https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS)

---

### Post by Gordonbp531 on 2014-02-16
I have a Lenovo U410 - UEFI, Intel Rapidstart and Windows 8 pre-installed.
13.04 64 bit installed as dual-boot perfectly without having to do anything to any BIOS entries or hardware settings.
I would try 13.04 (there's a bug in 13.10 installer that doesn't see the Windows 8 installation) and wait for 14.04 LTS to appear in April...

---

### Post by Gordonbp531 on 2014-02-16
> **fantab said:**
> 

Ubuntu 13.10 should work better as it supports newer hardware and techs.

There's a bug[1] in the 13.10 installer that doesn't see the Windows 8 installation.
It's better to install 13.04 and then update to 13.10.

[1] [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1249564](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1249564)

---

### Post by oldfred on 2014-02-16
Some others have posted that older versions of installer would only see Windows & SSD if Intel SRT was turned off and RAID meta-data removed from drive. After install it could be re-activated. Somewhat surprised that even 13.04 worked as desktop installer does not have RAID drivers.

Grub still does not install correctly with Desktop installer as it installs differently if RAID and RAID drivers not part of desktop.  But with UEFI it may work in some cases at it should always install boot loader to efi partition.

Some more recent posts have said just changing to AHCI in UEFI/BIOS works now.

---

### Post by skippsav on 2014-02-16
Wow, lots of information there - thanks.

I'll set some time aside to go through them all and maybe try a few. One the did catch my eye is waiting for the next LTS before I get going. 

A short term work around I am also considering (to get rid of the mess that is Win 8) is just clean installing Win 7 to get rid of until I can get a Linux dual boot up and running.

---

### Post by oldfred on 2014-02-16
You have an UEFI system. The Windows 7 DVD installs in BIOS boot mode unless you convert to flash drive and add drivers.
IF you let Windows convert gpt partitioning which is required for UEFI to MBR(msdos) which is required for BIOS boot, which does not do it correctly. It leaves the backup gpt partition table on drive and then Linux tools get confused as they see both MBR & gpt. You can use fixparts. Or install Windows 7 in UEFI mode.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

      
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

### Post by rossumpossum on 2014-05-27
> **oldfred said:**
> You have an UEFI system. The Windows 7 DVD installs in BIOS boot mode unless you convert to flash drive and add drivers.
IF you let Windows convert gpt partitioning which is required for UEFI to MBR(msdos) which is required for BIOS boot, which does not do it correctly. It leaves the backup gpt partition table on drive and then Linux tools get confused as they see both MBR & gpt. You can use fixparts. Or install Windows 7 in UEFI mode.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

      
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

My lenovo y500 came with an ssd and a hard drive in it.  In order to get this laptop dual booting in Legacy mode with windows 7 and Linux you must remove the SSD and format all partitions and then reinstall windows and then Linux once the SSD has been removed from your laptop... Whenever you try to dual boot Linux and windows in legacy mode with the SSD in and you install windows, windows is programmed to install the bootloader or MBR whatever it's called to the SSD in order to speed up the boot time.  In our case grub installs the bootloader to the MBR as it is supposed to but since the mbr is on the SSD, grub cannot find the Linux system when we install it since it is on a different drive and so it doesn't boot.  I figured this out after a year of struggling with my y500 but after removing the SSD I can boot any Linux OS with a few unrelated exceptions in legacy mode.  If you would consider switching to windows 7 in order to dual boot (and I highly recommend it) this is how you would do it.  

EDIT: I think I replied to the wrong user's comment...I'm new to this forum so please forgive me

Source: My own sweat and tears from the course of an entire year.

---

