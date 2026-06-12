---
title: "Dual boot Windows 8 and Ubuntu on UEFI/GPT/Secure-boot HP laptop"
date: 2014-03-24
forum: Installation &amp; Upgrades
---

### Post by ahpitre on 2014-03-24
After 2 weeks, and multiple tries (yes, including, wiping out the entire hard disk twice,and installing Windows 8, and Ubuntu 13.04). This is what worked on my new HP Pavilion Touch-smart 15 Notebook PC (a Touch enabled laptop). This laptop comes by default with UEFI, uses GPT partitions, and comes loaded with Windows 8 64 bits). The trick for this to work is the order in which things are installed. This is what worked for me :
 

 
[LIST=1]
[*]Leave your BIOS     default options (do not change them, they should be Secure Boot =     enabled). Use recovery disks or recovery partition tools that come     pre-loaded. Running these will wipe out the entire hard drive,     repartition drive into 4 partitions (1 for UEFI boot, 1 for Windows     PE (Windows recovery tools), 1 for HP recovery tools, and 1 for     Windows). 
[*]After Windows 8     successfully boots, install a partition manager (I use Paragon     Partition Manager 14, costs $39.99 but it's worth every penny of     it). Using Partition Manager, I reduce the Windows partition (left     about 150GBs). After rebooting, the partition shrink takes place. 
[*]Windows 8 boots, I     run Partition Manager again, this time, I use the empty space to     create 2 partitions, 1 for Ubuntu Linux (aprox. 130GB), and 1 for     Linux Swap (aprox. 20GB, should be about 1 ½ times your RAM,     although this the standard). 
[*]Reboot with Ubuntu     13.04 installation disk. If nothing is displayed on the screen, try     pressing the F3 key  multiple times (increases screen brightness).     Install Ubuntu by using the other option (last on the install menu     “something else...”). Do not use the other options as they may     wipe out your entire drive (again). 
[*]Select the partition     created in step 3 (the 130GB partition). Select format to EXT4 and     mount at /. Install LINUX. 
[*]When computer     reboots, it will reboot to Windows 8. No surprise as the LINUX     installation did install GRUB2, but, UEFI boot doesn't like it. 
[*]Reboot, press F9,     select the boot from UEFI file option. Select Ubuntu from the menu. 
[*]Ubuntu is loaded. 
[*]Install Boot Repair     (find out more on [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)).     Although you can create a Boot Disk, this Boot Disk doesn't work in     HP laptops (simply doesn't boot). Follow the instructions on how to     install Boot-repair in Ubuntu. 
[*]Run Boot-Repair,     leave all the defaults and run till the end. Answer no to the     question on backing up Windows 8 files. Now, Boot-repair will tell     you that somethings are not correct. 
[*]Reboot into Ubuntu     again by following steps 7 – 8. 
[*]Run Boot-repair a     2[SUP]nd[/SUP] time, same options as before. This 2[SUP]nd[/SUP]     time, despite warnings, GRUB 2 will actually be fixed. 
[*]Reboot a 3[SUP]rd[/SUP]     time, surprise GRUB2 is now the default boot loader, and, it has     options to boot Windows and Ubuntu. Notice, there might be multiple     options for booting into Windows 8, including using EFI files and an     option that boots straight into /dev/windows partition (in my case     this was /dev/sda4). This option doesn't work and generate a bunc of     errors before taking you back to GRUB2 menu. The Windows 8 option     that works are the ones with UEFI files. 
[*]Finally, the GRUB2     menu will have a lot of entries, some of them duplicates. You can     install Grub Customizer to clean and edit the GRUB2 menu. You can     even set the order and which option boots 1[SUP]st[/SUP] (default). 
[*]So there it is,     after 2 weeks and multiple hours, I finally got it right. I hope     this can be of value to others. 
[/LIST]
 

 Take care, and God bless you all!

---

