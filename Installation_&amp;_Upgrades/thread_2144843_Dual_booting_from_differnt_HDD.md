---
title: "Dual booting from differnt HDD"
date: 2013-05-13
forum: Installation &amp; Upgrades
---

### Post by dabigreddog on 2013-05-13
hi guys i have recently installed Ubuntu again on my desktop V10.10 lol and i had no proplems doing this.
 then upgrading Ubuntu using anouther disc i burned in 10.10 and upgraded to 12.04 good times.

 so i lent a pal my 12.04 disc and he has tried to install on a sperate Hdd to where Windows is and after install it just keeps booting staight to Windows 7 even if you tell it to boot from other Hdd where ubuntu 12.04 is.

im just woundering is there something he needs to do with Grub/Grub2 or maybe a Boot manager he needs for Windows so that the Primey Hdd where Windows is knows to load a Boot manager where he can select to boot Ubuntu or Windows 7 

I have also tried just using My 10.10 disc and this doesnt work eaither I have used ubuntu meny times installing along side windows but not on Sperate HDD's

please help :confused::confused::confused:

meny thanks
 Dabigreddog

---

### Post by oldfred on 2013-05-13
Did you do a default install or Something Else manual install?
All the default options install grub2's boot loader to the MBR of sda. (If BIOS, not the new UEFI).
And which drive is sda may not always be the Windows drive, some BIOS make a install flash drive sda.
But with manual install you get to choose which drive to install grub into and then you select that drive to boot from in BIOS.

Really best to post BootInfo report.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

