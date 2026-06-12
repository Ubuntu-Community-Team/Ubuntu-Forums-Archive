---
title: "Problem booting after installing Ubuntu 13.10 alongside Windows 8.1"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by Tyner on 2014-02-11
For the longest time I  wanted to switch to Linux, and after some research, Ubuntu seemed the  best bet. The last straw was when I bought an Asus X75A-DS51 Notebook,  even after the free upgrade from Windows 8 to 8.1, I still could not  stand it. Here are the laptop's specifications: [http://www.newegg.com/Product/Product.aspx?Item=N82E16834231037](http://www.newegg.com/Product/Product.aspx?Item=N82E16834231037)

  After using an Ubuntu 13.10 install disk and installing it on  seperate partitions than my Windows 8.1 partitions, I get no boot menu  when I start my laptop. I can only use it by puting the disc back in and  running the live version. So I ran Boot-Repair and got this:
  Boot successfully repaired. (Note: It's not.)
  A new file (~/Boot-Info*2014-02-11*_17h44.txt) will open in your text viewer. 
Link to my Boot-Info*2014-02-11*_17h44.txt : [https://www.dropbox.com/s/ybi6t296eu2wzx0/Boot-Info*2014-02-11*_17h44.txt]("https://www.dropbox.com/s/ybi6t296eu2wzx0/Boot-Info_2014-02-11__17h44.txt")

  In case you still experience boot problem, indicate its content to: [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] (Note: I emailed them but they won't help me because I have not contributed to them even though I just now heard of them.)
  You can now reboot your computer.
  A broken Wubi has been detected. Please fix it this way: [https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu) (Note: I didn't use Wubi.)

**EDIT: Now I am getting this from Boot Repair:**

EFI detected. Please check the options.

The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Do you want to continue?

sudo chroot "/mnt/boot-sav/sda11" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda11" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda11" apt-get purge -y --force-yes grub*-common shim-signed linux-signed*

sudo chroot "/mnt/boot-sav/sda11" apt-get install -y --force-yes grub-efi linux

Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/6918513/](http://paste.ubuntu.com/6918513/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/grubx64.efi file
A broken Wubi has been detected. Please fix it this way:
[https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)



--------------------------------------------------------------------------------------------------

**** EDIT ****

This is the error screen I am now getting when I try to boot: [https://www.dropbox.com/s/r6ibqu4p7dofuce/100_8497.JPG](https://www.dropbox.com/s/r6ibqu4p7dofuce/100_8497.JPG)

---

### Post by oldfred on 2014-02-12
Your last error message is from a network boot. Did you set network first in UEFI/BIOS boot order. ubuntu should be first, but Windows may keep resetting itself to be first. See below.

You do show wubi in sda5 and wubi does not work with gpt partitioned drives which all UEFI systems are. You should delete wubi.

You also show grub installed to MBR, which is a BIOS boot, not UEFI boot. Boot-Repair can convert to UEFI from BIOS by uninstalling grub-pc(BIOS) and installing grub-efi(UEFI).

You also installed grub to the Windows NTFS partition. Windows has to have its boot info and specific partition start & size info in all NTFS partition. Even Windows repairs will not work as now Windows will not see it as a NTFS partition.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR similar instructions:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

You also have done Boot-Repairs' "buggy" UEFI fix. That is only required for those systems that modify UEFI to only boot Windows. Best to undo that until we confirm if yours is one of those systems. What brand/model is your system?

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

After all those fixes, rerun BootInfo report and post back. Besure to always boot in UEFI mode with fast boot off in Windows, and usually better with secure boot off.

      Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

If Windows 8 resets to always be first, you may need to add Ubuntu to BCD.
 Remove Duplicate Firmware Objects in BCD and NVRAM
[http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx)
UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

