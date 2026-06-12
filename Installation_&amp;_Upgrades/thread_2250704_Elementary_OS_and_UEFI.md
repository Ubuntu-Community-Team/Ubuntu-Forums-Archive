---
title: "Elementary OS and UEFI"
date: 2014-10-30
forum: Installation &amp; Upgrades
---

### Post by rasmus91 on 2014-10-30
Hello

Been Dualbooting Ubuntu and Windows 7 on my Asus UX32VD for a while now, but i finally had a look at Elementary OS, and i really want to try it out.

At the same time i've been considering trying to do an UEFI install of Ubuntu, mostly because i've read that UEFI booting is faster than BIOS, so i really want to try it out.

Anyhow, I'm uncertain of how to do this however, since most UEFI guides are for Dual booting, and i do not wish to Dualboot anymore.

Can someone provide such a guide? preferrably one that works for both Ubuntu and Elementary OS. 

Thanks for your time. :)

---

### Post by oldfred on 2014-10-30
Your hardware has to be UEFI capable.
And if your current installs are BIOS the hard drive is MBR(msdos). But to work with UEFI drive must be partitioned with gpt. And that will erase drive.
Best to make full backups just in case you want to revert.
Windows 7 can be installed in UEFI mode.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

 ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1)
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

> 
 EFI-mode booting can be faster. The difference can be several seconds, contrary to what K. Darien Freeheart wrote, but the difference also varies from one computer to another; on some computers, the speed benefit can be non-existent. The effect is felt mainly in the firmware initialization, not in the Linux boot process itself.
    
An EFI-mode boot gives the OS access to certain EFI features. Today, the biggest of these is the ability to control the firmware's built-in boot manager, via the Linux efibootmgr utility. The kernel can also log crash data in NVRAM, but that's mainly of interest to developers. In the future, the number of things that can be done with an EFI-mode boot from a booted Linux distribution may increase.
    
The much-maligned Secure Boot can actually provide some security benefits, if you choose to configure it properly. You might never need or notice these benefits, but if, at some point in the future, some pre-boot malware spreads and can infect Linux-based computers, you might be glad to have Secure Boot active.
    
EFI provides new and different boot manager and boot loader options. In addition to GRUB, which is available for both BIOS and EFI, you can use rEFInd or gummiboot to choose the OS, and ELILO or the EFI stub loader to boot the kernel. See my page on EFI boot loaders for Linux for more on this topic.
    
On some computers, booting from a GPT disk in BIOS mode requires jumping through some extra hoops. Thus, booting in EFI mode may save you a bit of effort if you've got an over-2TiB disk or if you just plain like GPT.

   Overall, these benefits are unlikely to be compelling for most people. 




---

