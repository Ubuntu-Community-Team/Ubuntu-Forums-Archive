---
title: "LVM install help please?"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by frank18 on 2015-03-28
[COLOR=#000000][FONT=verdana]HI Guys; i installed win 10 first and then i installed Ubuntu in LVM, It boots strait to Ubuntu, how do i set it to boot either Ubuntu or Win 10,[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Normaly in other Machines i installed for exemple Win XP and Linux mint and it offers to install along side Win OPS then i update grub and that's it,[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]here it offers me LVM or others, thanks[/FONT][/COLOR]

---

### Post by oldfred on 2015-03-30
Standard LVM or LVM with encryption are full drive installs. So unless installing to another drive or you used Something else and selected to use LVM for part of drive, you may have erased Windows?

Do not know details of LVM as it is mostly for advanced users or those requiring full drive encryption.

Also is your hardware newer and UEFI or older and only BIOS?
What brand/model system?

Do not run any auto fix, but run Summary report and post link to summary report.
With an advanced install, you should only use one of the advanced mode repairs if required.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by frank18 on 2015-03-30
> **oldfred said:**
> Standard LVM or LVM with encryption are full drive installs. So unless installing to another drive or you used Something else and selected to use LVM for part of drive, you may have erased Windows?

Do not know details of LVM as it is mostly for advanced users or those requiring full drive encryption.

Also is your hardware newer and UEFI or older and only BIOS?
What brand/model system?

Do not run any auto fix, but run Summary report and post link to summary report.
With an advanced install, you should only use one of the advanced mode repairs if required.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks oldfred;you're right,it maybe got erased,  why it shows in partitions menu when i install win first,
Options; erase OPS that is installed or KVM install,and Others= making manual partition?,
 In my other older PC, i install Win Xp then it gives install over it or along side it or others,it seems the only way is to make customer  partitions,which i don't know nothing about,i prefer it to do auto partition.  
at this time as i type i'm installing Win 10 TP again and i'm going to try to make some partition manually to install Ubuntu 14.04

My PC;Lenovo ThinkCenter71;socket 1155
 Intel (core)tm) I5 2400 CPU 3.10GHZ,
Mem 3.8GB,Socket 1155, Video card ATI 6450, HDD Sata 500.

---

### Post by oldfred on 2015-03-30
If system is socket 1155, then it is UEFI with CSM.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

You also then have to boot installers for both Windows & Ubuntu in the mode you want to install, either both UEFI or both BIOS.
UEFI boot menu should show flash drive twice, one UEFI and the other just by flash drive name/label.

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Also partitioning type of drive matches install type. UEFI uses gpt partitioing and BIOS uses MBR(msdos) partitioning.

With UEFI Windows has several required extra partitions. With BIOS it uses a 100MB boot partition & the main install.


 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by Kenneth_Benson on 2015-03-30
Once you have Win installed again, download a utility called EasyBCD. This will allow you to make a menu that you can chose between multiple os's. And when you install LVM, use guided install. Watch for the point at which it asks if it can install the bootloader to /dev/sd{a,b,c,whatever}. if it just has the sda without a number it will kill your windows. Try to get it to do it to sda{1,2,3,4} as one of those is the actual partition and not the master boot record. The numbers by the way are 1st,2nd,3rd,4th partition, so whichever is where you are putting the Ubuntu installation. If this makes sense, good. If not, ask further.

(drat, oldfred beat me to the punch. :rolleyes: )

---

### Post by frank18 on 2015-04-01
Thanks guys i tried but no success,besides i installed Win 10 Tp only  and i'm  getting a  notice that i should backup all my files that HDD is failing. maybe it is. but when i install Ubuntu only i have no HHD error at all.well this was  a  spare Sata HDD that i had in my scrap, that  i installed Win 10  on it and wait for the final  Win 10 RTP so i will swap it and try to update to the final win RTP version and see if i can keep a free Copy,meanwhile i put the Original HDD back with Ubuntu 14.04 that's my main OPS on this Lenovo Desktop and i love it.

---

