---
title: "Ubuntu 17.04 on MSi Gaming Laptop"
date: 2017-07-12
forum: Installation &amp; Upgrades
---

### Post by jacksonchris1968 on 2017-07-12
Ok, I got a reply whereby MSi's Rep stated they don't support any other OS than Windows. This blows my mind because EVERY laptop I have ever owned, mostly Toshibas, would allow Linux without issue. But MSi seems to give me fits. My intention is to install 17.04 but my Bios offers these modes: Legacy, UEFI and UEFI+CSM. It has the trusted Platform system in the Bios what do you recommend? MSi stated that they claim most Os'es will install, but they can't even guarantee that. I just want Ubuntu as it is one of the easiest flavors to use in terms of simplicity, it-will-run-out-of-the-box when I install it.

Do you have anyone else with MSi headaches?

Thanks,
-Chris

---

### Post by oldfred on 2017-07-12
These are most of the MSI threads. Several boot options are used, you may have to experiment on which works. 
Also if RAID grub does not correctly install.
Most brands first level support is for only Windows. 

 Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

---

### Post by Bucky Ball on 2017-07-13
My wife has Ubuntu running fine on her MSI laptop with an i7, 8Gb RAM and an M.2 (and a 7200rpm 1Tb storage HDD). Can't remember having any particular major difficulties installing Ubuntu. The machine was just about the only one MSI make that comes with no installed operating system though, so wouldn't blame MSI wholly. Having Windows installed creates a new set of issues specific to Windows being installed, generally to do with UEFI being hobbled in one way or the other.

---

### Post by jacksonchris1968 on 2017-07-13
@oldfred and Bucky Ball. I'm determined! I'm on a conquest to run Ubuntu! lol. I'll be home tomorrow evening and thereafter will pursue my quest to achieve victory. I'll have to downshift my BIOS to Legacy I'm sure. Thanks for the reply and I'll report back my findings

My system MSi GT72VR-6RE Dominator Pro. (what a goofy name!) purchase DEC 2016 with an i7 6700HQ mobile. with of course the Nvidia 1070 as well.

-Chris

---

### Post by oldfred on 2017-07-13
While legacy may work, it still may be better to use UEFI if at all possible.

Microsoft wanted vendors to not even develop drivers for old BIOS or older versions of Windows, so newer hardware would only be supported in newest Windows. But too many large users, corporations want to be able to have same image on newer systems.

Back up Windows, we get many threads where users find one game or one application that they can only run Windows and want to reinstall it. Or later sell system and need Windows on it to make it saleable.

I might partition with gpt but include both the ESP - efi system partition for UEFI boot and the bios_grub for BIOS boot. Then you can easily change only version of grub installed to switch from UEFI to BIOS or vice-versa. If you do a default BIOS/CSM/Legacy install it will probably use the old MBR configuration. While Windows only boots in UEFI from gpt, Ubuntu can boot in UEFI or BIOS from gpt.
       Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI) 
    
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by jacksonchris1968 on 2017-07-16
I figured out how to get MSi laptops setup to install Ubuntu 17.04.
Turn off secure boot
Set boot to UEFI (DO NOT USE CSM)
Set TPM to 2.0 with 1.x compatibility

install and enjoy!

---

### Post by Bucky Ball on 2017-07-17
Excellent news and thanks for sharing. ;)

You will help others by marking the thread as 'solved' using 'Thread Tools' at the top right of this page.

---

