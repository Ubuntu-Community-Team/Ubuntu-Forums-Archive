---
title: "Operating System not found"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by galanh on 2010-08-14
Hi

I installed Ubuntu 10.04.1 on a Dell studio with i7 processor
I restarted the machine twice to Ubuntu and then I boot Window7.
Windows7 did a 3-step check of the hard disk new space and started.
The anti-virus started and did a global check.
I re-started again the machine and the following message appeared:

no module found
Aborted. Press any key to exit
Intel UNDI, PXE-2.1 (build 083)
...............................................................................
PXE-E51 No DHC or proxy DHCP offer were received
PXE-M0F-Exiting PXE ROM
Operating System not found

Thanls for any help

---

### Post by galanh on 2010-08-18
Window7 disable my boot loader.
 I am running my Ubuntu 10.04.1 without problem.
 Even I can boot Window7 if I restart my computer.
 But after restart from Window7 I have the following message:
 

 no module found
Aborted. Press any key to exit
Intel UNDI, PXE-2.1 (build 083)
&#8230;........................................................
PXE-M0F-Exiting PXE ROM
Operating System not found


Without operating system I need to use again my CD to reinstall 10.04.1
I don't know how to get out from this point.



 I ran the following scrip:
> 
Boot Info Script 0.55    dated February 15th, 2010                     
  
 ============================= Boot Info Summary: ============================== 
  
  => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in  
     partition #5 for /boot/grub. 
  
 sda1: _________________________________________________________________________ 
  
     File system:       vfat 
     Boot sector type:  Dell Utility: Fat16 
     Boot sector info:  No errors found in the Boot Parameter Block. 
     Operating System:   
     Boot files/dirs:   /COMMAND.COM 
  
 sda2: _________________________________________________________________________ 
  
     File system:       ntfs 
     Boot sector type:  Grub 2 
     Boot sector info:  Grub 2 is installed in the boot sector of sda2 and  
                        looks at sector 948745976 of the same hard drive for  
                        core.img, but core.img can not be found at this  
                        location. No errors found in the Boot Parameter Block. 
     Operating System:   
     Boot files/dirs:   /bootmgr /Boot/BCD 
  
 sda3: _________________________________________________________________________ 
  
     File system:       ntfs 
     Boot sector type:  Windows Vista/7 
     Boot sector info:  No errors found in the Boot Parameter Block. 
     Operating System:  Windows 7 
     Boot files/dirs:    
  
 sda4: _________________________________________________________________________ 
  
     File system:       Extended Partition 
     Boot sector type:  - 
     Boot sector info:   
  
 sda5: _________________________________________________________________________ 
  
     File system:       ext4 
     Boot sector type:  - 
     Boot sector info:   
     Operating System:  Ubuntu 10.04.1 LTS 
     Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img 
  
 sda6: _________________________________________________________________________ 
  
     File system:       swap 
     Boot sector type:  - 
     Boot sector info:   
  
 =========================== Drive/Partition Info: ============================= 
  
 Drive: sda ___________________ _____________________________________________________ 
  
 Disk /dev/sda: 500.1 GB, 500107862016 bytes 
 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
  
 Partition  Boot         Start           End          Size  Id System 
  
 /dev/sda1                  63        80,324        80,262  de Dell Utility 
 /dev/sda2    *         80,325    30,800,324    30,720,000   7 HPFS/NTFS 
 /dev/sda3          30,800,325   529,014,566   498,214,242   7 HPFS/NTFS 
 /dev/sda4         529,014,782   976,773,119   447,758,338   5 Extended 
 /dev/sda5         529,014,784   958,537,727   429,522,944  83 Linux 
 /dev/sda6         958,539,776   976,773,119    18,233,344  82 Linux swap / Solaris 
  
  
 blkid -c /dev/null: ____________________________________________________________


---

