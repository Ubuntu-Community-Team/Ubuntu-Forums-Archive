---
title: "Ubuntu 14.04 won't book on Toshiba Z930"
date: 2014-05-14
forum: Installation &amp; Upgrades
---

### Post by gweinstein on 2014-05-14
Tried Boot-repair several times, to no avail. Please help!

[http://paste.ubuntu.com/7464920](http://paste.ubuntu.com/7464920)

Thanks in advance!

---

### Post by oldfred on 2014-05-14
With only Ubuntu installed you have to go into UEFI and choose to boot the ubuntu entry.
Grub menu will not nomally show with one system. It assumes you want to boot that. Often escape key will give you a grub menu with UEFI.

Have you turned secure boot off in UEFI menu?

---

### Post by gweinstein on 2014-05-15
Thanks oldfred! 

How do you "go into UEFI" to select Ubuntu?

In the BIOS, under Security, I have Secure Boot Disabled. Under Advanced -> System Configuration, I have Boot Mode UEFI Boot. The only other option there is CSM Boot. I don't get the grub menu. All I get is a black screen with a two line message:

```

Insert system disk in drive
Press any key when ready...

```

Seems the system can't find the OS.

---

### Post by oldfred on 2014-05-15
UEFI is the new BIOS, so you are in it.

CSM is BIOS boot mode, and you are configured for UEFI. If UEFI is on, CSM off and secure boot off, your system should boot. And you should set ubuntu as first in boot order.

```
 BootOrder: 0000,0005,0006,0001,0004,0003
Boot0001* HDD/SSD
Boot0002* LAN1
Boot0003* LAN2
Boot0004* LAN1
Boot0005* USB Memory
Boot0006* grub
Boot0000* ubuntu.


```

That is is is first but there are several lists in UEFI, and I do not know differences. It may be secure boot, UEFI boot and BIOS boot orders?
It does look like you also have the signed versions of the kernel so it should also boot with secure boot on if using shim to boot not grub.

Some other Toshiba systems. They usually have worked where HP & Sony need work arounds as they modify UEFI to only boot Windows.

  [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by gweinstein on 2014-05-15
Thanks again oldfred, but I don't understand your message. 

The system indeed **should **boot but as a matter of fact it **doesn't**. 

Where can I set ubuntu as first in boot order? I never get to a boot screen. 

I tried Boot-Repair several times, but it didn't help.

I tried re-installing but it didn't help.

One more clue perhaps. System was running Ubuntu 12.04 happily before. When I tried to upgrade from that it complained about the need for a boot partition which should be at least 35 MB. I do have such a partition (in fact over 537 MB) and it is designated as EFI for boot. I eventually gave up and did a clean install from scratch but I still can't boot.

Thanks in advance.

---

### Post by oldfred on 2014-05-15
I do not understand a 35MB boot partition. An efi partition would be at least 100MB and usually 300 suggested. And a bios_grub partition is 1 or 2MB. And a /boot partition is 300 to 500MB, but not required for most desktops. Boot-Repair may suggest a /boot partition in some cases, but that is for older BIOS based systems and it is just a standard message.

Were you booting in BIOS mode before? System should boot in either BIOS or UEFI boot modes.

Somewhere in your UEFI/BIOS menu is a boot order choice. It may be one entry for both hardware & UEFI or two entries, one hardware and the other the UEFI entries. See extract from BootInfo report showing all your UEFI boot options. You should see something similar in your UEFI/BIOS.

I think every UEFI install I have seen also has an /efi/Boot folder with bootx64.efi to directly boot hard drive, not other folders. You do not seem to have that? 
And some with the Windows boot issues copy grub or shim into the /efi/boot folder as a work around to the Windows only boot. 
Try creating a new folder in your efi partition with /efi/Boot and copy shim into that folder and rename it to bootx64.efi.

 From Boot scripts:
Boot files: 
       /efi/Boot/bootx64.efi 
/efi/ubuntu/grubx64.efi

---

### Post by gweinstein on 2014-05-15
I am afraid that I still don't understand. I feel like we are speaking different languages.

The boot partition is 537 MB.

My system is booting in UEFI mode. The only other option I can choose is CMS. I see no other options in the SETUP menu.

When the system starts up, I press F12 to get a boot menu. The options there are :TOSHIBA SDD etc. LAN1, or LAN2, and further down SETUP MENU.

In the EFI partition I have an EFI folder with grub and ubuntu subfolders. The grub subfolder has only grub.cfg, grubx64.efi, MokManager.efi, and shimx64.efi. The ubuntu subfolder seems to have the same four files.

Thanks in advance.

---

### Post by oldfred on 2014-05-15
Is f12 then just a boot menu and not the full UEFI/BIOS screens?
With my very old Toshiba f2 gets me into BIOS and f12 just a boot choice.
So what does f2 show you?

And I still think it may be worthwhile to create another folder in your efi partition /efi/Boot and add/copy the shimx64.efi and change its name to bootx64.efi.

Some others have posted various UEFI screens. Not sure I have any examples from Toshiba, unless someone in one of the Toshiba threads include one. You have to use camera, shrink to screenshot size and using advanced editor and paperclip icon in edit panel to attach a screen shot.

---

### Post by gweinstein on 2014-05-15
I tried you suggestion regarding moving shimx64.efi and renaming. BTW, the only upmost folder on that partition is /EFI/ (capitalized). Don't know if that makes a difference.

I am also attaching two screenshots, the boot menu, and screen from my setup menu.

[https://drive.google.com/file/d/0By18jQkxAaOUM052azNLNFE0QTA/edit?usp=sharing](https://drive.google.com/file/d/0By18jQkxAaOUM052azNLNFE0QTA/edit?usp=sharing)
[https://drive.google.com/file/d/0By18jQkxAaOUd1pPa3R4VW1PcHM/edit?usp=sharing](https://drive.google.com/file/d/0By18jQkxAaOUd1pPa3R4VW1PcHM/edit?usp=sharing)

---

### Post by oldfred on 2014-05-15
With FAT32 (or NTFS) case is not important. With Linux formatted partitions case is important.

Turn off Intel SRT setting in BIOS. That means it is trying to boot from the Windows hibernated entry in the SRT partition which you do not have.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

---

### Post by gweinstein on 2014-05-15
I don't have Intel SRT in BIOS, only Intel RST (Rapid Start Technology). And I didn't change these BIOS setting from when Ubuntu 12.04 was booting.

---

### Post by oldfred on 2014-05-15
Others with Toshiba's have worked but I do not know details of all UEFI settings, they may need to be different than for BIOS boot.

About the only other thing is to go back to BIOS boot. You can create a 1 or 2MB unformatted partition with the bios_grub flag anywhere on drive and use Boot-Repair to convert to BIOS boot.

---

### Post by ubfan1 on 2014-05-15
In the EFI partition, the /EFI/Boot directory which you have put a copy of shimx64.efi renamed to bootx64.efi should also contain a copy of the grubx64.efi (the signed copy).  Then the shim should run grub, which should pick up the grub.cfg file from /EFI/ubuntu (or maybe these days from /EFI/grub ).  Without secure boot on, the bootx64.efi file may just be a copy of the (unsigned) grubx64.efi.

---

### Post by gweinstein on 2014-05-15
Well, actually turned out to be a lot simpler. All it took was to change the Boot Mode to CSM in the Setup Menu -> Advanced -> System Configuration. Then run a clean install again.

System now booting normally, and pretty fast too.

Thanks anyway.

---

