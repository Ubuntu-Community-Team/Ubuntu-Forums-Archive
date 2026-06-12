---
title: "Installing Ubuntu on a SSD"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by BloodyDream on 2012-11-23
I recently bought a SSD that I'm going to use as a boot drive with an upcoming computer build. I have a computer already and I was wondering if I could put Ubuntu on a CD and the SSD in the computer, then install Ubuntu onto the SSD from there to use as a boot drive? Or what I would do if not. I want the SSD prepared before I get the computer built so I want have to go through the trouble then. Also if anyone knows where I can get the Ubuntu drivers for the ASRock Z77 Extreme since they aren't on the ASRock Site, that would be appreciated. 
Thanks.

---

### Post by grahammechanical on 2012-11-23
Let me give you some clarification, Please.

When Ubuntu is installed it will put a boot loader program (Grub) into the Master Boot Record (MBR) of the hard disk. You must be careful that when you install Ubuntu to the SSD it puts the boot loader into the SSD MBR and not on to the other hard disk. Otherwise, when you put the SSD into the new computer it will not boot because the SSD does not have a boot loader to tell the machine what OS to boot.

Another point to consider. When Ubuntu installs it detects the hardware and sets up Ubuntu with the right kind of modules for your hardware. If you do what you want to do, then the new machine will have an OS with modules based upon the hardware of the old computer. It may work. It may not work. It may work badly. I did it this way when I built my machine 5 years ago.

I ran the machine without any OS. Then with a floppy disk with DOS 6 on it. Then the Ubuntu Live DVD. Finally I installed Ubuntu.

It is better to wait until you have built the new machine and install Ubuntu at that time.

You will want to test the machine without an OS to make sure that the motherboard is running its POST (Power On System Tests) correctly and that there are no problems. You do not want to be confused by a badly working operating system.

As far as I can tell the only issues you will have with drivers in Ubuntu is with drivers for the video card and the wireless card. Ubuntu has a utility to help install those drivers if needed. It is called Additional Drivers.

So, you need to research Linux compatibility for the video and wireless adapters.

Regards.

---

### Post by oldfred on 2012-11-23
Also new systems are UEFI/BIOS. UEFI is the new replacement for BIOS, but most still boot in BIOS mode. 

Only Ubuntu 64 bit supports UEFI boot. Your old system may not, so the way you install may be greatly different.

some with AsRock have posted these comments.
> AsRock calls BIOS mode AHCI.
"Launch EFI Shell from Filesystem Device" in the Exit tab of Asrock motherboard
Asrock Extreme4 Z77 motherboard, which has 4 SATA3 ports: 2 Intel ports (0 & 1) and 2 Asmedia ports (A0 & A1).Had my DVD drive connected to one of the Asmedia ports (A1), and so I tried switching the connection to one of the Intel SATA2 ports and the errors went away.
    

       [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
    [http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)

The Arch site recommends gpt partitioning for SSDs. Ubuntu works with gpt partitioned drives whether you boot in UEFI or BIOS mode, but Windows will only boot from gpt with UEFI.
       [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
            GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
       
 [https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

---

### Post by BloodyDream on 2012-11-23
Wow guys, thanks so much haha. That was really a lot of help. One thing though, I understand the fact that it would take the settings from my old computer but what if I did it on an up-to-date computer? Also I have an extra hard drive for storage, I don't know if I said that or not. Couldn't I hook just that one up originally to check the BIOS and everything?

---

