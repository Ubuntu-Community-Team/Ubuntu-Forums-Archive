---
title: "Hardy Heron won't recognize HDD"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by Birbe on 2008-08-27
Built a barebones system recently to install Ubuntu 8.04 and escape the evil Microsoft.

System details :
AMD Athlon 64x2 5000+, XFX GeForce 8200 MoBo, 
XFX GeForce 8500GT Video card, 
3 g RAM, 
Seagate 500g Sata HDD   

The Problem:
So when I fired the system up for the first time I got to step 4 of the install (partition HDD), except no HDD is recognized so I had to proceed as a live user and abandon the install.  

Rebooted system and before I get to the initial screen it crashes giving me a busybox error.  Restart same thing and so on.  It seems I can only boot up the live version 1 out of 6 or 8 tries and Ubuntu can never detect the HDD.  Any suggestions?  I have searched this extensively but can't find a solution, there seems to be some problems with seagate hard drives, I am thinking of trying a Western Digital, but before I do I would like to know if I am missing something.

TIA

---

### Post by confused57 on 2008-08-27
> **Birbe said:**
> Built a barebones system recently to install Ubuntu 8.04 and escape the evil Microsoft.

System details :
AMD Athlon 64x2 5000+, XFX GeForce 8200 MoBo, 
XFX GeForce 8500GT Video card, 
3 g RAM, 
Seagate 500g Sata HDD   

The Problem:
So when I fired the system up for the first time I got to step 4 of the install (partition HDD), except no HDD is recognized so I had to proceed as a live user and abandon the install.  

Rebooted system and before I get to the initial screen it crashes giving me a busybox error.  Restart same thing and so on.  It seems I can only boot up the live version 1 out of 6 or 8 tries and Ubuntu can never detect the HDD.  Any suggestions?  I have searched this extensively but can't find a solution, there seems to be some problems with seagate hard drives, I am thinking of trying a Western Digital, but before I do I would like to know if I am missing something.

TIA

You might try going into your bios setup and check the settings on your SATA controller...if it's set to AHCI, try setting it to IDE, or vice-versa.

If this doesn't work, when you boot the live cd, press "F6", this should give the kernel boot options...add "all_generic_ide", without quotes, to the very end of the kernel boot options line.

---

### Post by Birbe on 2008-08-28
Many thanks, for the very clear advice, unable to switch sata to ide from bios, but all_generic_ide worked like a champ.  

Does this mean I lose the benefits of having a Sata drive?

Linux, is now up and running, all I need now is to find a driver for my Dell 1125 multifunction printer (they do not support linux) and I believe I have full functionality.  Off to search the internet.   Many many thanks

---

### Post by b-morgan on 2008-08-29
I'm having the same problem as the OP. I built a system using:

ASUS A8V-X motherboard (BIOS 0703, the latest)
AMD Athlon 64 X2 3800 processor
4GB RAM
ATI Radeon X1600 Pro (AGP)
Maxtor 80GB EIDE disk (primary master)
Sony DRU-840A DVD RW (secondary master)

Ubuntu 8.04 x86 CD and Ubuntu 8.04 AMD64 CD both fail to recognize the HD.

Knoppix 5.1.1 (Kernel 2.6.19 SMP) and Knoppix 5.3.1 (Kernel 2.6.24.4 SMP) both recognize the HD.

Ubuntu 7.10 has graphics problems (including Safe Graphics mode)

Ubuntu 7.04 (Kernel 2.6.20-15 SMP) finds the HD and successfully installs. It has yet to offer an Upgrade option.

I tried the suggested "all_generic_ide" but this failed to correct the situation. The motherboard has 4 SATA ports which I'm not using (no spare SATA drives).

Any suggestions?

Thanks,

Brad

---

### Post by putte30 on 2008-09-06
Any solution to the problem? I have the same motherboard and are unable to install ubuntu.

---

### Post by b-morgan on 2008-09-06
If by same motherboard you mean the ASUS A8V-X, then my solution to the problem was to return the motherboard for a refund. According to ASUS (US), this motherboard was built for an (Overseas) OEM and they don't support it nor do they have any documentation about what it supports.

Regards,

Brad

---

### Post by Birbe on 2008-09-08
And I you meant my problem, the all_generic_ide allowed me access to my hard drive.  Currently Hardy's kernel doesn't support the 8200 mobo, good news apparently interpids new kernal will :).

---

### Post by tydfil on 2008-10-09
Hope the final release will.  I can assure the latest beta does not.

---

### Post by baDluC on 2008-10-12
> **confused57 said:**
> You might try going into your bios setup and check the settings on your SATA controller...if it's set to AHCI, try setting it to IDE, or vice-versa.

If this doesn't work, when you boot the live cd, press "F6", this should give the kernel boot options...add "all_generic_ide", without quotes, to the very end of the kernel boot options line.

I bought this d*mn board (Nvidia 8200) as well and have tried the all_generic_ide line without any luck. I saw somewhere else to put in "qc timeout cmd 0xec" but I'm at work and will have to wait to try it. In the bios when "on board devices" is set to SATA the SATA 1 will have the drive info for my hdd but it says "disabled" in the dialog for it. I haven't been able to get it to show anything else but disabled. 

I have ordered a P-ATA drive that will solve the problem if nothing else will. I hope.

---

### Post by Ahmedmb on 2009-03-08
try this

[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface#Common_problems_switching_to_AHCI_under_Linux](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface#Common_problems_switching_to_AHCI_under_Linux)

Common problems switching to AHCI under Linux

The AHCI controller does not work on AMD/ATI RS400-200, and RS480 HBA; and Nvidia nForce 560 chipset[citation needed] when MSI is enabled due to a hardware error. In order for AHCI to work users must provide the "pci=nomsi" kernel boot parameter. With MSI disabled in this way, the PCIe bus can only act as a faster PCI bus with hotplug capabilities.
The AHCI controller on AMD/ATI SB600 HBA can't do 64-bit DMA transfers. 64-bit addressing is optional in AHCI 1.1 and the chip claims it can do them, but, in reality, it can't so it is disabled. After that it will be forced to do 32-bit DMA transfers. Thus DMA transfers will occur in the lower 4 GiB region of the memory, and bounce buffers must be used sometimes if there is more than 4 GiB of RAM.[9]
The VIA VT8251 South bridge suffers the same fate but it can be circumvented with the "pci=nomsi" option to force detection of the chip. This has been tested to work on 2.6.26, 2.6.24 and 2.6.20 kernels.
Under RHEL, CentOS and similar, if you change your BIOS to AHCI mode and do not have the ahci drivers in your initrd then you will not be able to boot. To solve this
Set you BIOS to IDE/ATA/Original setting mode
boot into linux
edit /etc/modprobe.conf and add the line alias scsi_hostadapter2 ahci
run mkinitrd -f /boot/initrd-`uname -r`.img `uname -r`
reboot in to you BIOS and set to AHCI/RAID mode
boot into linux
check your vendors manual for more details

---

