---
title: "Computer goes to grub then reboots after 17.10 upgrade"
date: 2018-01-19
forum: Installation &amp; Upgrades
---

### Post by eddugo on 2018-01-19
I just upgraded to 17.10 as 17.04 is no longer supported and now my machine goes to grub and then reboots over and over.  Thank you in advance for your help solving this.

Ed

---

### Post by eddugo on 2018-01-24
Just tried Boot Repair.  Didn't fix the problem and windows option is no longer there

---

### Post by oldfred on 2018-01-24
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by eddugo on 2018-01-25
Here is the link;

[http://paste.ubuntu.com/26457474/]("http://paste.ubuntu.com/26457474/")

---

### Post by oldfred on 2018-01-25
It looks like you have an Acer computer that is UEFI, but both Windows & Ubuntu are installed in BIOS boot mode.

You also have a grub installed to the partition boot sector (PBR). That (almost) never should be done. Systems only boot from MBR, so boot loader must be in MBR.

So update may have not installed grub to MBR and then you have a mis-match of grub versions.
In Boot-Repair run from advanced mode and the full uninstall/reinstall of grub in BIOS mode.

You also have a lot of old kernels.
You should always regularly houseclean. But now after an upgrade your kernels may not be in dpkg for normal removal. 
Kernels may have bits and pieces in other places than /boot so more effort to manually houseclean.
Also if upgrading you may have lots of old now obsolete log files from old system.

       [https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean)
Do yourself a favor and avoid bleachbit. 
   Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)
[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels) 
   RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by eddugo on 2018-01-26
"So update may have not installed grub to MBR and then you have a mis-match of grub versions.
In Boot-Repair run from advanced mode and the full uninstall/reinstall of grub in BIOS mode."


Hi Olfred;

I'm doing something wrong.

Went to ppa version,advanced, didn't really see an option for "uninstall/reinstall", ticked restore MBA and the reinstall box un-ticked.  Tried that and it booted into windows with no grub. [http://paste.ubuntu.com/26463575]("http://paste.ubuntu.com/26463575")

Ran it again with reinstall ticked and it's back where I started. [http://paste.ubuntu.com/26463679]("http://paste.ubuntu.com/26463679")

What should I have ticked in advanced?

Sorry for my inexperience.  This computer is old and has intermittent cooling fans so it has be relegated to a parts look up machine on my bench in my shop - runs, prob about 3 hours a week and sits in suspend the rest of the time.  It was my first experience with UEFI and I didn't do it right.

Thank you.

Ed

---

### Post by oldfred on 2018-01-26
On first screen you click on advanced options and then you get these screens.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

One one screen is reinstall grub.
And on another screen is totally purge grub before reinstall.

---

### Post by eddugo on 2018-01-26
It's stops at a screen that says to open a terminal and type 3 commands; configure -a, install -fy, purge y grub common i386.  I added them, nothing happens, pushed forward on the type 3 commands screen and I get 'Grub is still present try again" that keeps coming back

---

### Post by oldfred on 2018-01-26
Which command fails?

Do you have working Internet as it has to download a new copy of grub2.

You are adding them one at a time?

---

### Post by eddugo on 2018-01-26
The commands don't do anything - it just sits there.  I don't think what is happening in terminal has finished at that point so adding a command does nothing.
Have working internet.
When I untick re-install (main options tab), then the grub options tabs where I need to go to purge, go dim and they are empty.  I tried ticking the purge first then unticking the reinstall and all it does is create a report. ??????????????????  And of course, it stops and displays that eror message when I have them both ticked.

---

### Post by oldfred on 2018-01-27
Are you using a 17.10 (or 16.04LTS) version of live installer and adding Boot-Repair to that?

If running from 17.04, the repositories are closed and it cannot download a new copy of grub.
And the Boot-Repair live installer also is now old, only install using ppa to a current Ubuntu live installer.

---

### Post by eddugo on 2018-01-31
I am using 17.10 - should I try it with 16.04?

---

### Post by oldfred on 2018-01-31
Either one should be good, just as long as a current version of Ubuntu.

Post a new report or look for the error log from Boot-Repair. It often is in /var/log/boot-sav.
But from live installer it may not get saved to system, so you have to just see what it has.

---

### Post by eddugo on 2018-02-04
Hi Olfred;

I couldn't figure out how to get to the error log in a live distro - looked in hidden files and tried to search.  I did however get the purge and reinstall to work.  Went through and did not fix the problem.  Here is the report. [http://paste.ubuntu.com/26518641/](http://paste.ubuntu.com/26518641/)

The page that gives the pastebin address has a new error message at the bottom.  I have attached it - says the boot files are far from the start of the disk and the BIOS may not detect them..................

Thank You

Ed

Update:  Did findboot repair log in /VAR/. ;
```
=================== log of boot-repair 20180204_1412 ===================
boot-repair version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Scanning systems. This may require several minutes...''')
[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Scanning systems (os-prober). This may require several minutes...''')
[debug]Delete the content of TMP_FOLDER_TO_BE_CLEARED and put os-prober in memory
Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1 has been opened read-only.
Partition 4 does not start on physical sector boundary.
[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Scanning systems (mount). This may require several minutes...''')
boot-repair is executed in live-session (Ubuntu 17.10, artful, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
ls: cannot access '/home/usr/.config': No such file or directory
[debug]BIOSBOOT of sda2 is notbiosboot
[debug]BIOSBOOT of sda3 is notbiosboot
[debug]BIOSBOOT of sda5 is notbiosboot
[debug]BIOSBOOT of sda1 is notbiosboot
[debug]Mount all blkid partitions except the ones already mounted and BIOS_Boot
[debug]BLKID Mount point of sda2 is: /mnt/boot-sav/sda2
[debug]BLKID Mount point of sda3 is: /mnt/boot-sav/sda3
[debug]BLKID Mount point of sda5 is: /mnt/boot-sav/sda5
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/sda1 : Error code 12
mount -r /dev/sda1 /mnt/boot-sav/sda1
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/sda1 : Error code 12
[debug]BLKID Mount point of sda1 is: /mnt/boot-sav/sda1
[debug]Remove_mislocated_stage1
[debug]PART_UUID of sda2 is F8EADC17EADBD04C
[debug]PART_UUID of sda3 is 644AE3F94AE3C5C0
[debug]PART_UUID of sda5 is 691291b8-d3ce-41e3-bec2-3200a9e8c44b
[debug]PART_UUID of sda1 is eb1d4960-01
[debug] BYTES_BEFORE_PART[1] (sda) = 2048 sectors * 512 bytes = 1048576 bytes.

=================== os-prober:
/dev/sda5:Ubuntu 17.10 (17.10):Ubuntu:linux

=================== blkid:
/dev/sda2: LABEL="SYSTEM RESERVED" UUID="F8EADC17EADBD04C" TYPE="ntfs" PARTUUID="eb1d4960-02"
/dev/sda3: LABEL="Windows" UUID="644AE3F94AE3C5C0" TYPE="ntfs" PARTUUID="eb1d4960-03"
/dev/sda5: UUID="691291b8-d3ce-41e3-bec2-3200a9e8c44b" TYPE="ext4" PTTYPE="dos" PARTUUID="eb1d4960-05"
/dev/sr1: UUID="2018-01-05-20-55-44-00" LABEL="Ubuntu 17.10 amd64" TYPE="iso9660" PTUUID="126c99e0" PTTYPE="dos"
/dev/loop0: TYPE="squashfs"
/dev/sda6: UUID="5d22b3ef-eaa7-4a45-9391-d88fa15137b7" TYPE="swap" PARTUUID="eb1d4960-06"
/dev/sda1: PARTUUID="eb1d4960-01"

[debug]sda5 contains Ubuntu 17.10 (linux)

1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.
    
[debug]Mount all blkid partitions except the ones already mounted and BIOS_Boot
[debug]DF/dev/sda2         102396 24960     77436  25% /mnt/boot-sav/sda2
[debug]BLKID Mount point of sda2 is: /mnt/boot-sav/sda2
[debug]DF/dev/sda3       73410124 44524428  28885696  61% /mnt/boot-sav/sda3
[debug]BLKID Mount point of sda3 is: /mnt/boot-sav/sda3
[debug]DF/dev/sda5      389644012 72779448 297048680  20% /mnt/boot-sav/sda5
[debug]BLKID Mount point of sda5 is: /mnt/boot-sav/sda5
[debug]Mount path of sda5 is: /mnt/boot-sav/sda5
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/sda1 : Error code 12
mount -r /dev/sda1 /mnt/boot-sav/sda1
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/sda1 : Error code 12
[debug]BLKID Mount point of sda1 is: /mnt/boot-sav/sda1
[debug]PART_WITH_OS of sda2 : no-os
Windows not detected by os-prober on sda3.
[debug]PART_WITH_OS of sda3 : is-os
[debug]PART_WITH_OS of sda5 : is-os
[debug]PART_WITH_OS of sda1 : no-os
[debug]sda contains minimum one OS
1+0 records in
1+0 records out
1048576 bytes (1.0 MB, 1.0 MiB) copied, 0.0172368 s, 60.8 MB/s
[debug]/var/log/boot-repair/20180204_141205/sda/partition_table.dmp created
[debug]CREATES A LIST OF DISKS CONTAINING BACKUP
[debug] Total of 1 OS detected on sda disk.
[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Scanning systems. This may require several minutes...''')
Partition 4 does not start on physical sector boundary.
Partition 4 does not start on physical sector boundary.
[debug] sda2 ends at 13213105664GB. not-far
[debug] sda2 ends at 13213105664GB. not-far
[debug] sda3 ends at 88385076736GB. not-far
[debug] sda3 ends at 88385076736GB. not-far

=================== sda5/etc/grub.d/ :
drwxr-xr-x  2 root root              4096 Feb  4 13:17 grub.d
drwxr-xr-x  2 root root              4096 Apr 29  2017 grub.d.bak
total 76
-rwxr-xr-x 1 root root  9783 Oct 12 13:41 00_header
-rwxr-xr-x 1 root root  6258 Apr 24  2017 05_debian_theme
-rwxr-xr-x 1 root root 12676 Oct 12 13:41 10_linux
-rwxr-xr-x 1 root root 11281 Oct 12 13:41 20_linux_xen
-rwxr-xr-x 1 root root 12059 Oct 12 13:41 30_os-prober
-rwxr-xr-x 1 root root  1418 Oct 12 13:41 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 12 13:41 40_custom
-rwxr-xr-x 1 root root   216 Oct 12 13:41 41_custom
-rw-r--r-- 1 root root   483 Oct 12 13:41 README




=================== sda5/etc/default/grub :
        
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== sda5recordfail=1/grub/grubenv :
recordfail=1



[debug] sda5 ends at 493879295488GB. farbios
[debug] sda5 ends at 493879295488GB. farbios
[debug] sda1 ends at 13108248064GB. not-far
[debug] sda1 ends at 13108248064GB. not-far
ls /sys/firmware/efi/vars : new_var,del_var,UserManagerVar-1ef17197-2cce-49d6-a6ce-4012f338a76e,UCR-14a22a97-8424-489e-9ead-dc09255658b5,TpmSaveState-5e724c0c-5c03-4543-bcb6-c1e23de24136,TpmAcpiData-6403753b-abde-4da2-aa11-6983ef2a7a69,Timeout-8be4df61-93ca-11d2-aa0d-00e098032b8c,Time-470733de-df43-448b-8b45-4eeb0df8c812,System-e947fcf9-dd01-4965-b808-32a7b6815657,SplashLogoPackage-e5bbf7be-2417-499b-97db-39f4896391bc,SmramCpuDataVar-429501d9-e447-40f4-867b-75c93a1db54e,SimpleBootFlag-8be4df61-93ca-11d2-aa0d-00e098032b8c,Setup-4dfbbaab-1392-4fde-abb8-c41cc5ad7d5d,SctHotkey-4650c401-93f1-4aeb-b87d-c8204c047dec,ScramblerSeedCmosLocation-8be7835f-ade6-4bed-9777-3ec4ce1f6044,SaProtocolSetupVar-34f73d4d-963e-4c65-b3b3-515e720175d6,SaPpiSetupVar-7da81437-866b-4143-8e08-a25c6ef0fa5b,SaPegData-c4975200-64f1-4fb6-9773-f6a9f89d985e,SaDataBase-889cb747-7223-43ea-b198-af2826e2aeb5,SMBIOSMEMSIZE-c3eeae98-23bf-412b-ab60-efcbb48e1534,SMBIOSLEN-c3eeae98-23bf-412b-ab60-efcbb48e1534,SMBIOSELOGNUMBER-c3eeae98-23bf-412b-ab60-efcbb48e1534,SMBIOSELOG000-c3eeae98-23bf-412b-ab60-efcbb48e1534,RoSmbios-e5bbf7be-2417-499b-97db-39f4896391bc,Recovery-8be4df61-93ca-11d2-aa0d-00e098032b8c,ProtectedBootOptions-8be4df61-93ca-11d2-aa0d-00e098032b8c,PreDefinedBootOptions-8be4df61-93ca-11d2-aa0d-00e098032b8c,PpmProtocolSetupVar-e2d1e5c4-68d0-4078-be7b-9035ea7f9be3,PlatformLangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c,PlatformLang-8be4df61-93ca-11d2-aa0d-00e098032b8c,PchS3Peim-e6c2f70a-b604-4877-85ba-deec89e117eb,PchProtocolSetupVar-04bd8413-15f9-43f3-9675-4618e03240e3,PchPpiSetupVar-e274d08e-69b6-4497-a4eb-d39c4b2f9fcb,PchInit-e6c2f70a-b604-4877-85ba-deec89e117eb,PbaStatusVar-0ec1a7f5-4904-40a0-8eab-4bcc4666da45,PartNumber-e5bbf7be-2417-499b-97db-39f4896391bc,OpromDevicePath-8be4df61-93ca-11d2-aa0d-00e098032b8c,OilSystemConfig-3e4794ab-aa64-4619-a8d6-2a1803ed8efe,OilHiddenPageConfig-1510c75e-0334-4a2c-9385-4da850e0ac65,OemVersionNumber-e5bbf7be-2417-499b-97db-39f4896391bc,OemSetup-ed845f15-5faa-42fa-9efb-ab595c9b941c,MokListRT-605dab50-e046-4300-abb6-3dd810dd8b23,MemRestoreVariable-608dc793-15de-4a7f-a0c5-6c29beaf5d23,MeSetup-fb7b1de3-295b-433c-95a2-091fe3218bf9,MTC-eb704011-1402-11d3-8e77-00a0c969723b,LastBootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c,Key0003-8be4df61-93ca-11d2-aa0d-00e098032b8c,Key0002-8be4df61-93ca-11d2-aa0d-00e098032b8c,Key0001-8be4df61-93ca-11d2-aa0d-00e098032b8c,Key0000-8be4df61-93ca-11d2-aa0d-00e098032b8c,IffsHashData-b84a95d8-3592-4e3c-a02e-3b474a1f1dab,IffsFlag-5073de12-a4c1-457d-ba99-f16fb0e3ce97,IffsConfig-180093b0-12a5-4a96-9eb7-2510afdf39a5,HDD_Password_Status-0dffc7df-49b6-4562-b9bf-e51c2b6e1b1c,HDDPWD-8be4df61-93ca-11d2-aa0d-00e098032b8c,FlashCommand-e5bbf7be-2417-499b-97db-39f4896391bc,FirmwarePerformanceDataTable-9dab39a4-3f8a-47ac-80c3-400729332c81,ErrOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,DtsProtocolSetupVar-10aeabdb-bdcc-441e-889b-a8df33a9c16a,DptfProtocolSetupVar-1054354b-b543-4dfe-558b-a7ad6351c9d8,DIAGSPLSHSCRN-8be4df61-93ca-11d2-aa0d-00e098032b8c,CustomizeModule-80e4ecbe-0672-4de0-9a12-205c7276a77e,CpuRatio-320c081f-b8ca-40ad-a6bf-30211e51ec0e,CpuProtocolSetupVar-7d4adce1-930d-40c7-9cd2-6d2148413dc7,CpuPpiSetupVar-d1b99f1a-084b-49c3-b88e-378abefa118b,CpuOnlyReset-0382f3df-35d3-4716-8219-3f6f8275848e,CpuCmpSmt-f31bce44-4db9-40fc-93ab-4de140657b91,ConOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConOut-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConInDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConIn-8be4df61-93ca-11d2-aa0d-00e098032b8c,BuildTime-e5bbf7be-2417-499b-97db-39f4896391bc,BuildDate-e5bbf7be-2417-499b-97db-39f4896391bc,BootState-60b5e939-0fcf-4227-ba83-6bbed45bc0e3,BootOrderDefault-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootOptionSupport-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootNextBootOption-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootMenu-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootAllPciLan-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootAllCDROM-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot000A-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0009-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0008-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0007-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0006-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0005-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0004-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0003-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0002-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0001-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0000-8be4df61-93ca-11d2-aa0d-00e098032b8c,BiosSetup-8be4df61-93ca-11d2-aa0d-00e098032b8c,Backup0009-8be4df61-93ca-11d2-aa0d-00e098032b8c,Backup0008-8be4df61-93ca-11d2-aa0d-00e098032b8c,Backup0007-8be4df61-93ca-11d2-aa0d-00e098032b8c,Backup0006-8be4df61-93ca-11d2-aa0d-00e098032b8c,Backup0005-8be4df61-93ca-11d2-aa0d-00e098032b8c,Backup0004-8be4df61-93ca-11d2-aa0d-00e098032b8c,AoacWakeStatus-23771b23-e15a-4805-920a-4f1e84b54abc,AdvancedPage-d10c2ba8-855e-4166-bdc0-ca247a331868,AdvancedPage-be27c0e1-2046-41b7-8bc4-5db18aa779d1,AdvancedPage-aa17e444-82ad-4eee-9e38-71f965de4793,AdvancedPage-8b84baef-c467-4973-bbcc-0e790d2e0a76,AdvancedPage-81e29592-d505-416b-9113-8e95343c8194,AdvancedPage-7c2f01c2-1486-4347-bbc2-a8a8d7b1fcb8,AdvancedPage-5ed3915b-5575-4efd-ab8d-c455dd439a2e,AdvancedPage-5bb720c3-e550-42c2-9662-f440345a309e,AdvancedPage-3b3c2158-22b2-4cef-98f4-c79f8d7b266e,AdvancedPage-397faf4e-893e-468f-992d-9acf30c52142,AcpiGlobalVariable-af9ffd67-ec10-488a-9dfc-6cbf5ee22c2e,AcerRuntimePassword-0997fb62-c849-4d91-9266-05333bc55ce7,AcerOa-434b8dbb-8b4d-4056-9673-72381afcb03a,AcerD2d-4fee3d67-18f4-4217-ba7b-bc538148382a,
Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

=================== efibootmgr -v
BootCurrent: 0009
Timeout: 0 seconds
BootOrder: 0009,0004,0005,0008,0006,0007
Boot0000  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0001  Boot Menu    FvFile(86488440-41bb-42c7-93ac-450fbf7766bf)
Boot0002  Diagnostic Splash    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0003  Acer D2D:    FvFile(bcc93540-7ea9-11df-8c4a-0800200c9a66)
Boot0004* HDD 0: Hitachi HTS545050A7E380                     PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,0,0)..bYVD.A...O.*..
Boot0005* ATAPI CD/DVD: HL-DT-ST DVDRAM GU61N                       PciRoot(0x0)/Pci(0x1f,0x2)/Sata(4,0,0)......!N.:^G.V.T
Boot0006* USB FDD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0007* Network Boot: Realtek PXE B02 D00    BBS(Network,Realtek PXE B02 D00,0x0)............................................................................A.................. ...
Boot0008* USB HDD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot0009* USB CD/DVD: Slimtype DVD A  DS8A5S    PciRoot(0x0)/Pci(0x1d,0x0)/USB(0,0)/USB(1,0).p...ZxH.l....jU
Boot000A* Internal Shell:    FvFile(c57ad6b7-0515-40a8-9d21-551652854e37)

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot maybe enabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda3.
sda5    : sda,    not-sepboot,    grubenv-ng    grub2,    grub-pc ,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sda5.
sda1    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:msdos:ATA Hitachi HTS54505:;
1:1049kB:13.1GB:13.1GB:::diag;
2:13.1GB:13.2GB:105MB:ntfs::;
3:13.2GB:88.4GB:75.2GB:ntfs::boot;
4:88.4GB:500GB:412GB:::;
5:88.4GB:494GB:405GB:ext4::;
6:494GB:500GB:6226MB:linux-swap(v1)::;

BYT;
/dev/sr1:1503MB:unknown:2048:2048:mac:Unknown:;
1:2048B:6143B:4096B::Apple:;
2:1474MB:1477MB:2359kB::EFI:;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
loop0 loop squashfs   1.3G 
sda   disk          465.8G 
sda1  part           12.2G 
sda2  part ntfs       100M SYSTEM RESERVED
sda3  part ntfs        70G Windows
sda4  part              1K 
sda5  part ext4     377.7G 
sda6  part swap       5.8G 
sr0   rom            1024M 
sr1   rom  iso9660    1.4G Ubuntu 17.10 amd64
 
KNAME ROTA RO RM STATE   MOUNTPOINT
loop0    1  1  0         /rofs
sda      1  0  0 running 
sda1     1  0  0         
sda2     1  0  0         /mnt/boot-sav/sda2
sda3     1  0  0         /mnt/boot-sav/sda3
sda4     1  0  0         
sda5     1  0  0         /mnt/boot-sav/sda5
sda6     1  0  0         [SWAP]
sr0      1  0  1 running 
sr1      1  0  1 running /cdrom


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=2932224k,nr_inodes=733056,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=590004k,mode=755)
/dev/sr1 on /cdrom type iso9660 (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=30,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=15449)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=590000k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw,relatime,data=ordered)


[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Scanning systems. Please wait few seconds...''')
=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 initctl input kmsg kvm lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sg0 sg1 sg2 shm snapshot snd sr0 sr1 stderr stdin stdout uhid uinput urandom usb userio v4l vfio vga_arbiter vhci vhost-net vhost-vsock video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 86 01  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 1f 03 00 00 00 00 00  |................|
00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|
00000040  f6 00 00 00 01 00 00 00  4c d0 db ea 17 dc ea f8  |........L.......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 c8 89 01  |........?.......|
00000020  00 00 00 00 80 00 80 00  98 4c c0 08 00 00 00 00  |.........L......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  c0 c5 e3 4a f9 e3 4a 64  |...........J..Jd|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200
[debug]TARGET_PARTITION_IS_AVAILABLE[sda] is : yes
[debug]MBR that can be restored nb 1 : sda (generic mbr)
[debug]MBR that can be restored nb 2 : sda (generic altmbr)
[debug]MBR that can be restored nb 3 : sda (generic gptmbr)
Partition 4 does not start on physical sector boundary.

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  2.8G     0  2.8G   0% /dev
tmpfs          tmpfs     577M  8.8M  568M   2% /run
/dev/sr1       iso9660   1.4G  1.4G     0 100% /cdrom
/dev/loop0     squashfs  1.4G  1.4G     0 100% /rofs
/cow           overlay   2.9G   74M  2.8G   3% /
tmpfs          tmpfs     2.9G   23M  2.8G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.9G     0  2.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     2.9G  516K  2.9G   1% /tmp
tmpfs          tmpfs     577M   44K  577M   1% /run/user/999
/dev/sda2      fuseblk   100M   25M   76M  25% /mnt/boot-sav/sda2
/dev/sda3      fuseblk    71G   43G   28G  61% /mnt/boot-sav/sda3
/dev/sda5      ext4      372G   70G  284G  20% /mnt/boot-sav/sda5

=================== fdisk -l:
Disk /dev/loop0: 1.3 GiB, 1427259392 bytes, 2787616 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xeb1d4960

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048  25602047  25600000  12.2G 27 Hidden NTFS WinRE
/dev/sda2        25602048  25806847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda3  *     25806848 172627103 146820256    70G  7 HPFS/NTFS/exFAT
/dev/sda4       172627966 976771071 804143106 383.5G  5 Extended
/dev/sda5       172627968 964607999 791980032 377.7G 83 Linux
/dev/sda6       964610048 976771071  12161024   5.8G 82 Linux swap / Solaris


[debug]Logs saved into /mnt/boot-sav/sda5/var/log/boot-repair/20180204_141205
[EMAIL="SET@_vbox_bootrepairmenu.show"]SET@_vbox_bootrepairmenu.show[/EMAIL]()
[EMAIL="SET@_label_bootrepairsubtitle.set"]SET@_label_bootrepairsubtitle.set[/EMAIL]_markup('''<b>Repair the boot of the computer</b>''')
[EMAIL="SET@_label_recommendedrepair.set"]SET@_label_recommendedrepair.set[/EMAIL]_text('''Recommended repair\n(repairs most frequent problems)''')
[EMAIL="SET@_label_justbootinfo.set"]SET@_label_justbootinfo.set[/EMAIL]_text('''Create a BootInfo summary\n(to get help by email or forum)''')
[EMAIL="SET@_label_pastebin.set"]SET@_label_pastebin.set[/EMAIL]_text('''Create a BootInfo summary (to get help by email or forum)''')
[EMAIL="SET@_vbox_pastebin.show"]SET@_vbox_pastebin.show[/EMAIL]()
[EMAIL="SET@_label_appname.set"]SET@_label_appname.set[/EMAIL]_markup('''<b><big>Boot-Repair</big></b>''')
[EMAIL="SET@_label_appdescription.set"]SET@_label_appdescription.set[/EMAIL]_text('''Repair the boot of the computer''')
[EMAIL="SET@_logobr.show"]SET@_logobr.show[/EMAIL]()
[EMAIL="SET@_logo_brmenu.show"]SET@_logo_brmenu.show[/EMAIL]()
[EMAIL="SET@_linkbutton_websitebr.show"]SET@_linkbutton_websitebr.show[/EMAIL]()
[EMAIL="SET@_label_repairfilesystems.set"]SET@_label_repairfilesystems.set[/EMAIL]_text('''Repair file systems''')
[EMAIL="SET@_checkbutton_repairfilesystems.show"]SET@_checkbutton_repairfilesystems.show[/EMAIL]()
[EMAIL="SET@_label_wubi.set"]SET@_label_wubi.set[/EMAIL]_text('''Repair Wubi filesystems''')
[EMAIL="SET@_checkbutton_wubi.show"]SET@_checkbutton_wubi.show[/EMAIL]()
[EMAIL="SET@_mainwindow.set"]SET@_mainwindow.set[/EMAIL]_title('''Boot Repair''')
[email]SET@_mainwindow.set_icon_from_file('''x-boot-repair.png[/email]''')
[EMAIL="SET@_label_advanced_options.set"]SET@_label_advanced_options.set[/EMAIL]_text('''Advanced options''')
[EMAIL="SET@_tab_main_options.set"]SET@_tab_main_options.set[/EMAIL]_text('''Main options''')
[EMAIL="SET@_tab_grub_location.set"]SET@_tab_grub_location.set[/EMAIL]_text('''GRUB location''')
[EMAIL="SET@_tab_grub_options.set"]SET@_tab_grub_options.set[/EMAIL]_text('''GRUB options''')
[EMAIL="SET@_tab_mbr_options.set"]SET@_tab_mbr_options.set[/EMAIL]_text('''MBR options''')
[EMAIL="SET@_tab_other_options.set"]SET@_tab_other_options.set[/EMAIL]_text('''Other options''')
[EMAIL="SET@_label_unhide_boot_menu.set"]SET@_label_unhide_boot_menu.set[/EMAIL]_text('''Unhide boot menu :''')
[EMAIL="SET@_label_seconds.set"]SET@_label_seconds.set[/EMAIL]_text('''seconds''')
[EMAIL="SET@_label_reinstall_grub.set"]SET@_label_reinstall_grub.set[/EMAIL]_text('''Reinstall GRUB''')
[EMAIL="SET@_label_restore_mbr.set"]SET@_label_restore_mbr.set[/EMAIL]_text('''Restore MBR''')
[EMAIL="SET@_label_restore_bkp.set"]SET@_label_restore_bkp.set[/EMAIL]_text('''Restore EFI backups''')
[EMAIL="SET@_label_create_bkp.set"]SET@_label_create_bkp.set[/EMAIL]_text('''Use the standard EFI file''')
[EMAIL="SET@_label_winefi_bkp.set"]SET@_label_winefi_bkp.set[/EMAIL]_text('''Backup and rename Windows EFI files (solves the [hard-coded-EFI] error)''')
[EMAIL="SET@_label_bootflag.set"]SET@_label_bootflag.set[/EMAIL]_text('''Place the boot flag on:''')
COMBO@@CLEAR@@_combobox_bootflag
[EMAIL="SET@_label_restore_mbrof.set"]SET@_label_restore_mbrof.set[/EMAIL]_text('''Restore the MBR of:''')
COMBO@@END@@_combobox_restore_mbrof@@sda (generic mbr)
COMBO@@END@@_combobox_restore_mbrof@@sda (generic altmbr)
COMBO@@END@@_combobox_restore_mbrof@@sda (generic gptmbr)
[EMAIL="SET@_label_ostoboot_bydefault.set"]SET@_label_ostoboot_bydefault.set[/EMAIL]_text('''OS to boot by default:''')
[EMAIL="SET@_label_signed.set"]SET@_label_signed.set[/EMAIL]_text('''SecureBoot''')
[EMAIL="SET@_label_purge_grub.set"]SET@_label_purge_grub.set[/EMAIL]_text('''Purge GRUB before reinstalling it''')
[EMAIL="SET@_label_separateboot.set"]SET@_label_separateboot.set[/EMAIL]_text('''Separate /boot partition:''')
[EMAIL="SET@_label_efi.set"]SET@_label_efi.set[/EMAIL]_text('''Separate /boot/efi partition:''')
[EMAIL="SET@_label_sepusr.set"]SET@_label_sepusr.set[/EMAIL]_text('''Separate /usr partition:''')
[EMAIL="SET@_label_place_alldisks.set"]SET@_label_place_alldisks.set[/EMAIL]_text('''Place GRUB in all disks (except USB disks without OS)''')
[EMAIL="SET@_label_place_grub.set"]SET@_label_place_grub.set[/EMAIL]_text('''Place GRUB into:''')
[debug]combobox_ostoboot_bydefault_fillin
[debug]Order Linux noorder bits
[debug]LABEL_PART_FOR_REINSTAL[1] sda5 \(Ubuntu 17.10\)
COMBO@@END@@_combobox_ostoboot_bydefault@@sda5 (Ubuntu 17.10)
COMBO@@END@@_combobox_ostoboot_bydefault@@Windows (via sda5 menu)
[EMAIL="SET@_combobox_ostoboot_bydefault.set"]SET@_combobox_ostoboot_bydefault.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_label_lastgrub.set"]SET@_label_lastgrub.set[/EMAIL]_text('''Upgrade GRUB to its most recent version''')
[EMAIL="SET@_label_legacy.set"]SET@_label_legacy.set[/EMAIL]_text('''GRUB Legacy''')
[EMAIL="SET@_label_blankextraspace.set"]SET@_label_blankextraspace.set[/EMAIL]_text('''Reset extra space after MBR (solves the [FlexNet] error)''')
[EMAIL="SET@_label_uncomment_gfxmode.set"]SET@_label_uncomment_gfxmode.set[/EMAIL]_text('''Uncomment GRUB_GFXMODE (solves the [no-signal / out-of-range] error)''')
[EMAIL="SET@_label_ata.set"]SET@_label_ata.set[/EMAIL]_text('''ATA disk support (solves the [out-of-disk] error)''')
[EMAIL="SET@_label_add_kernel_option.set"]SET@_label_add_kernel_option.set[/EMAIL]_text('''Add a kernel option:''')
COMBO@@END@@_combobox_add_kernel_option@@nomodeset
COMBO@@END@@_combobox_add_kernel_option@@acpi=off
COMBO@@END@@_combobox_add_kernel_option@@acpi_osi=
COMBO@@END@@_combobox_add_kernel_option@@edd=on
COMBO@@END@@_combobox_add_kernel_option@@i815modeset=1
COMBO@@END@@_combobox_add_kernel_option@@i915modeset=0
[email]COMBO@@END@@_combobox_add_kernel_option@@i915.modese[/email]t=0 xforcevesa
COMBO@@END@@_combobox_add_kernel_option@@noapic
COMBO@@END@@_combobox_add_kernel_option@@nodmraid
COMBO@@END@@_combobox_add_kernel_option@@nolapic
COMBO@@END@@_combobox_add_kernel_option@@nomodeset radeon mode=0
COMBO@@END@@_combobox_add_kernel_option@@nomodeset radeon mode=1
COMBO@@END@@_combobox_add_kernel_option@@rootdelay=90
COMBO@@END@@_combobox_add_kernel_option@@vga=771
COMBO@@END@@_combobox_add_kernel_option@@xforcevesa
[EMAIL="SET@_combobox_add_kernel_option.set"]SET@_combobox_add_kernel_option.set[/EMAIL]_active(0)
[EMAIL="SET@_combobox_add_kernel_option.set"]SET@_combobox_add_kernel_option.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_label_kernelpurge.set"]SET@_label_kernelpurge.set[/EMAIL]_text('''Purge kernels then reinstall last kernel''')
[EMAIL="SET@_label_open_etc_default_grub.set"]SET@_label_open_etc_default_grub.set[/EMAIL]_text('''Edit GRUB configuration file''')
[EMAIL="SET@_label_partition_booted_bymbr.set"]SET@_label_partition_booted_bymbr.set[/EMAIL]_text('''Partition booted by the MBR:''')
[EMAIL="SET@_about.set"]SET@_about.set[/EMAIL]_title('''About Boot Repair''')
[email]SET@_about.set_icon_from_file('''x-boot-repair.png[/email]''')
[EMAIL="SET@_label_translate.set"]SET@_label_translate.set[/EMAIL]_text('''Translate''')
[EMAIL="SET@_label_thanks.set"]SET@_label_thanks.set[/EMAIL]_text('''Credits''')
[EMAIL="SET@_label_gpl.set"]SET@_label_gpl.set[/EMAIL]_markup('''<small>GNU-GPL v3</small>''')
[EMAIL="SET@_label_copyright.set"]SET@_label_copyright.set[/EMAIL]_markup('''<small>(C) 2010-2017 Yann MRN</small>''')
[EMAIL="SET@_backupwindow.set"]SET@_backupwindow.set[/EMAIL]_title('''Boot Repair''')
[EMAIL="SET@_label_pleasechoosebackuprep.set"]SET@_label_pleasechoosebackuprep.set[/EMAIL]_text('''Please choose a folder to put the backup into.\nIt is recommended to choose a USB disk.''')
[EMAIL="SET@_label_backup_table.set"]SET@_label_backup_table.set[/EMAIL]_text('''Backup partition tables, bootsectors and logs''')
[EMAIL="SET@_label_winboot.set"]SET@_label_winboot.set[/EMAIL]_text('''Repair Windows boot files''')
[EMAIL="SET@_label_upload.set"]SET@_label_upload.set[/EMAIL]_text('''Upload the report to a pastebin''')
[EMAIL="SET@_label_upload1.set"]SET@_label_upload1.set[/EMAIL]_text('''Upload the report to a pastebin''')
[EMAIL="SET@_label_stats.set"]SET@_label_stats.set[/EMAIL]_text('''Participate to statistics of use''')
[EMAIL="SET@_label_internet.set"]SET@_label_internet.set[/EMAIL]_text('''Check internet connection''')
[EMAIL="SET@_label_internet1.set"]SET@_label_internet1.set[/EMAIL]_text('''Check internet connection''')
[EMAIL="SET@_button_recommendedrepair.set"]SET@_button_recommendedrepair.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_checkbutton_repairfilesystems.set"]SET@_checkbutton_repairfilesystems.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_wubi.set"]SET@_checkbutton_wubi.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_wubi.set"]SET@_checkbutton_wubi.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_checkbutton_pastebin.set"]SET@_checkbutton_pastebin.set[/EMAIL]_active(True)
[EMAIL="SET@_checkbutton_upload.set"]SET@_checkbutton_upload.set[/EMAIL]_active(True)
[debug]MAIN_MENU becomes : Recommended-Repair
[EMAIL="SET@_checkbutton_unhide_boot_menu.set"]SET@_checkbutton_unhide_boot_menu.set[/EMAIL]_active(True)
[debug]set_checkbutton_reinstall_grub
[EMAIL="SET@_tab_grub_location.set"]SET@_tab_grub_location.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_vbox_grub_location.show"]SET@_vbox_grub_location.show[/EMAIL]()
[EMAIL="SET@_tab_grub_options.set"]SET@_tab_grub_options.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_vbox_grub_options.show"]SET@_vbox_grub_options.show[/EMAIL]()
[EMAIL="SET@_tab_mbr_options.set"]SET@_tab_mbr_options.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_vbox_mbr_options.hide"]SET@_vbox_mbr_options.hide[/EMAIL]()
[EMAIL="SET@_checkbutton_restore_mbr.set"]SET@_checkbutton_restore_mbr.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_restore_bkp.hide"]SET@_checkbutton_restore_bkp.hide[/EMAIL]()
[EMAIL="SET@_checkbutton_create_bkp.hide"]SET@_checkbutton_create_bkp.hide[/EMAIL]()
[EMAIL="SET@_checkbutton_winefi_bkp.hide"]SET@_checkbutton_winefi_bkp.hide[/EMAIL]()
[EMAIL="SET@_button_mainapply.set"]SET@_button_mainapply.set[/EMAIL]_sensitive(False)
[debug]osbydefault_consequences sda5
[EMAIL="SET@_vbox_sepusr.hide"]SET@_vbox_sepusr.hide[/EMAIL]()
[EMAIL="SET@_combobox_sepusr.set"]SET@_combobox_sepusr.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_label_sepusr.set"]SET@_label_sepusr.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_checkbutton_sepusr.set"]SET@_checkbutton_sepusr.set[/EMAIL]_active(False)
[debug]combobox_separateboot_fillin
COMBO@@CLEAR@@_combobox_separateboot
COMBO@@END@@_combobox_separateboot@@sda1
[EMAIL="SET@_combobox_separateboot.set"]SET@_combobox_separateboot.set[/EMAIL]_active(0)
[EMAIL="SET@_combobox_separateboot.set"]SET@_combobox_separateboot.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_combobox_separateboot.set"]SET@_combobox_separateboot.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_vbox_separateboot.show"]SET@_vbox_separateboot.show[/EMAIL]()
[EMAIL="SET@_checkbutton_separateboot.set"]SET@_checkbutton_separateboot.set[/EMAIL]_active(False)
[EMAIL="SET@_combobox_separateboot.set"]SET@_combobox_separateboot.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_checkbutton_kernelpurge.set"]SET@_checkbutton_kernelpurge.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_kernelpurge.set"]SET@_checkbutton_kernelpurge.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_button_open_etc_default_grub.show"]SET@_button_open_etc_default_grub.show[/EMAIL]()
[EMAIL="SET@_checkbutton_purge_grub.set"]SET@_checkbutton_purge_grub.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_purge_grub.set"]SET@_checkbutton_purge_grub.set[/EMAIL]_sensitive(True)
[debug]combobox_efi_fillin sda5 , 
COMBO@@CLEAR@@_combobox_efi
[EMAIL="SET@_combobox_efi.set"]SET@_combobox_efi.set[/EMAIL]_active(0)
[EMAIL="SET@_combobox_efi.set"]SET@_combobox_efi.set[/EMAIL]_sensitive(True)
[debug]EFIFILEPRESENCE , QTY_SUREEFIPART 0
[EMAIL="SET@_checkbutton_signed.hide"]SET@_checkbutton_signed.hide[/EMAIL]()
[EMAIL="SET@_combobox_efi.set"]SET@_combobox_efi.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_vbox_place_or_force.show"]SET@_vbox_place_or_force.show[/EMAIL]()
[EMAIL="SET@_checkbutton_legacy.show"]SET@_checkbutton_legacy.show[/EMAIL]()
[EMAIL="SET@_checkbutton_legacy.set"]SET@_checkbutton_legacy.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_button_open_etc_default_grub.show"]SET@_button_open_etc_default_grub.show[/EMAIL]()
[EMAIL="SET@_checkbutton_purge_grub.set"]SET@_checkbutton_purge_grub.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_purge_grub.set"]SET@_checkbutton_purge_grub.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_checkbutton_lastgrub.hide"]SET@_checkbutton_lastgrub.hide[/EMAIL]()
[debug]LASTGRUB_ACTION becomes: 
[EMAIL="SET@_checkbutton_restore_bkp.hide"]SET@_checkbutton_restore_bkp.hide[/EMAIL]()
[EMAIL="SET@_checkbutton_create_bkp.hide"]SET@_checkbutton_create_bkp.hide[/EMAIL]()
[EMAIL="SET@_checkbutton_winefi_bkp.hide"]SET@_checkbutton_winefi_bkp.hide[/EMAIL]()
[EMAIL="SET@_checkbutton_efi.set"]SET@_checkbutton_efi.set[/EMAIL]_active(False)
[EMAIL="SET@_vbox_efi.hide"]SET@_vbox_efi.hide[/EMAIL]()
[EMAIL="SET@_button_open_etc_default_grub.show"]SET@_button_open_etc_default_grub.show[/EMAIL]()
[EMAIL="SET@_checkbutton_purge_grub.set"]SET@_checkbutton_purge_grub.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_purge_grub.set"]SET@_checkbutton_purge_grub.set[/EMAIL]_sensitive(True)
COMBO@@CLEAR@@_combobox_place_grub
COMBO@@END@@_combobox_place_grub@@sda
[EMAIL="SET@_combobox_place_grub.set"]SET@_combobox_place_grub.set[/EMAIL]_active(0)
[EMAIL="SET@_radiobutton_place_grub.set"]SET@_radiobutton_place_grub.set[/EMAIL]_active(True)
[debug]set_radiobutton_place_grub
[EMAIL="SET@_combobox_place_grub.set"]SET@_combobox_place_grub.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_label_force_grub.set"]SET@_label_force_grub.set[/EMAIL]_text('''Force GRUB into: sda5 (for chainloader)''')
[EMAIL="SET@_checkbutton_purge_grub.show"]SET@_checkbutton_purge_grub.show[/EMAIL]()
[EMAIL="SET@_checkbutton_legacy.set"]SET@_checkbutton_legacy.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_button_open_etc_default_grub.show"]SET@_button_open_etc_default_grub.show[/EMAIL]()
[EMAIL="SET@_checkbutton_purge_grub.set"]SET@_checkbutton_purge_grub.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_purge_grub.set"]SET@_checkbutton_purge_grub.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_checkbutton_lastgrub.hide"]SET@_checkbutton_lastgrub.hide[/EMAIL]()
[debug]LASTGRUB_ACTION becomes: 
[EMAIL="SET@_checkbutton_blankextraspace.set"]SET@_checkbutton_blankextraspace.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_checkbutton_blankextraspace.set"]SET@_checkbutton_blankextraspace.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_uncomment_gfxmode.set"]SET@_checkbutton_uncomment_gfxmode.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_ata.set"]SET@_checkbutton_ata.set[/EMAIL]_active(False)
[EMAIL="SET@_combobox_add_kernel_option.set"]SET@_combobox_add_kernel_option.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_checkbutton_add_kernel_option.set"]SET@_checkbutton_add_kernel_option.set[/EMAIL]_active(False)
[EMAIL="SET@_button_mainapply.set"]SET@_button_mainapply.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_combobox_ostoboot_bydefault.set"]SET@_combobox_ostoboot_bydefault.set[/EMAIL]_active(0)
[debug]MBR_ACTION is set : reinstall (NBOFDISKS is 1)
[EMAIL="SET@_checkbutton_reinstall_grub.set"]SET@_checkbutton_reinstall_grub.set[/EMAIL]_active(True)
[EMAIL="SET@_hbox_bootflag.set"]SET@_hbox_bootflag.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_combobox_bootflag.set"]SET@_combobox_bootflag.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_checkbutton_bootflag.set"]SET@_checkbutton_bootflag.set[/EMAIL]_active(False)
[EMAIL="SET@_vbox_winboot.set"]SET@_vbox_winboot.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_button_recommendedrepair.set"]SET@_button_recommendedrepair.set[/EMAIL]_sensitive(True)
[EMAIL="SET@pulsatewindow.hide"]SET@pulsatewindow.hide[/EMAIL]()
[EMAIL="SET@_mainwindow.show"]SET@_mainwindow.show[/EMAIL]()
/usr/share/boot-sav/gui-tab-other.sh: line 86:  3333 Terminated              while true; do
    echo 'SET@_progressbar1.pulse()'; sleep 0.2;
done
DEBUG=> in bash NOT GET _combobox_add_kernel_option nomodeset
[debug]CHOSEN_KERNEL_OPTION becomes : nomodeset
DEBUG=> in bash NOT GET _checkbutton_unhide_boot_menu True
[EMAIL="SET@_spinbutton_unhide_boot_menu.set"]SET@_spinbutton_unhide_boot_menu.set[/EMAIL]_sensitive(True)
[debug]UNHIDEBOOT_ACTION becomes : unhide-bootmenu-10s
DEBUG=> in bash NOT GET _combobox_separateboot sda1
[debug]RET_sepboot (BOOTPART_TO_USE) : sda1
DEBUG=> in bash NOT GET _combobox_place_grub sda
[debug]RETOURCOMBO_place_grub (NOFORCE_DISK) : sda
DEBUG=> in bash NOT GET _combobox_ostoboot_bydefault sda5 (Ubuntu 17.10)
[debug]RETOURCOMBO_ostoboot_bydefault : sda5 (Ubuntu 17.10)
[debug]sda5 \(Ubuntu 17.10\)
[debug]Windows \(via sda5 menu\)
[debug]
[debug]Warning: Duplicate _combobox_ostoboot_bydefault .
[debug]
DEBUG=> in bash NOT GET _checkbutton_reinstall_grub True
[debug]set_checkbutton_reinstall_grub
[EMAIL="SET@_tab_grub_location.set"]SET@_tab_grub_location.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_vbox_grub_location.show"]SET@_vbox_grub_location.show[/EMAIL]()
[EMAIL="SET@_tab_grub_options.set"]SET@_tab_grub_options.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_vbox_grub_options.show"]SET@_vbox_grub_options.show[/EMAIL]()
[EMAIL="SET@_tab_mbr_options.set"]SET@_tab_mbr_options.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_vbox_mbr_options.hide"]SET@_vbox_mbr_options.hide[/EMAIL]()
[EMAIL="SET@_checkbutton_restore_mbr.set"]SET@_checkbutton_restore_mbr.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_restore_bkp.hide"]SET@_checkbutton_restore_bkp.hide[/EMAIL]()
[EMAIL="SET@_checkbutton_create_bkp.hide"]SET@_checkbutton_create_bkp.hide[/EMAIL]()
[EMAIL="SET@_checkbutton_winefi_bkp.hide"]SET@_checkbutton_winefi_bkp.hide[/EMAIL]()
[EMAIL="SET@_button_mainapply.set"]SET@_button_mainapply.set[/EMAIL]_sensitive(False)
[debug]osbydefault_consequences sda5
[EMAIL="SET@_vbox_sepusr.hide"]SET@_vbox_sepusr.hide[/EMAIL]()
[EMAIL="SET@_combobox_sepusr.set"]SET@_combobox_sepusr.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_label_sepusr.set"]SET@_label_sepusr.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_checkbutton_sepusr.set"]SET@_checkbutton_sepusr.set[/EMAIL]_active(False)
[debug]combobox_separateboot_fillin
COMBO@@CLEAR@@_combobox_separateboot
COMBO@@END@@_combobox_separateboot@@sda1
[EMAIL="SET@_combobox_separateboot.set"]SET@_combobox_separateboot.set[/EMAIL]_active(0)
[EMAIL="SET@_combobox_separateboot.set"]SET@_combobox_separateboot.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_combobox_separateboot.set"]SET@_combobox_separateboot.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_vbox_separateboot.show"]SET@_vbox_separateboot.show[/EMAIL]()
[EMAIL="SET@_checkbutton_separateboot.set"]SET@_checkbutton_separateboot.set[/EMAIL]_active(False)
[EMAIL="SET@_combobox_separateboot.set"]SET@_combobox_separateboot.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_checkbutton_kernelpurge.set"]SET@_checkbutton_kernelpurge.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_kernelpurge.set"]SET@_checkbutton_kernelpurge.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_button_open_etc_default_grub.show"]SET@_button_open_etc_default_grub.show[/EMAIL]()
[EMAIL="SET@_checkbutton_purge_grub.set"]SET@_checkbutton_purge_grub.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_purge_grub.set"]SET@_checkbutton_purge_grub.set[/EMAIL]_sensitive(True)
[debug]combobox_efi_fillin sda5 , 
COMBO@@CLEAR@@_combobox_efi
[EMAIL="SET@_combobox_efi.set"]SET@_combobox_efi.set[/EMAIL]_active(0)
[EMAIL="SET@_combobox_efi.set"]SET@_combobox_efi.set[/EMAIL]_sensitive(True)
[debug]EFIFILEPRESENCE , QTY_SUREEFIPART 0
[EMAIL="SET@_checkbutton_signed.hide"]SET@_checkbutton_signed.hide[/EMAIL]()
[EMAIL="SET@_combobox_efi.set"]SET@_combobox_efi.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_vbox_place_or_force.show"]SET@_vbox_place_or_force.show[/EMAIL]()
[EMAIL="SET@_checkbutton_legacy.show"]SET@_checkbutton_legacy.show[/EMAIL]()
[EMAIL="SET@_checkbutton_legacy.set"]SET@_checkbutton_legacy.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_button_open_etc_default_grub.show"]SET@_button_open_etc_default_grub.show[/EMAIL]()
[EMAIL="SET@_checkbutton_purge_grub.set"]SET@_checkbutton_purge_grub.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_purge_grub.set"]SET@_checkbutton_purge_grub.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_checkbutton_lastgrub.hide"]SET@_checkbutton_lastgrub.hide[/EMAIL]()
[debug]LASTGRUB_ACTION becomes: 
[EMAIL="SET@_checkbutton_restore_bkp.hide"]SET@_checkbutton_restore_bkp.hide[/EMAIL]()
[EMAIL="SET@_checkbutton_create_bkp.hide"]SET@_checkbutton_create_bkp.hide[/EMAIL]()
[EMAIL="SET@_checkbutton_winefi_bkp.hide"]SET@_checkbutton_winefi_bkp.hide[/EMAIL]()
[EMAIL="SET@_checkbutton_efi.set"]SET@_checkbutton_efi.set[/EMAIL]_active(False)
[EMAIL="SET@_vbox_efi.hide"]SET@_vbox_efi.hide[/EMAIL]()
[EMAIL="SET@_button_open_etc_default_grub.show"]SET@_button_open_etc_default_grub.show[/EMAIL]()
[EMAIL="SET@_checkbutton_purge_grub.set"]SET@_checkbutton_purge_grub.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_purge_grub.set"]SET@_checkbutton_purge_grub.set[/EMAIL]_sensitive(True)
COMBO@@CLEAR@@_combobox_place_grub
COMBO@@END@@_combobox_place_grub@@sda
[EMAIL="SET@_combobox_place_grub.set"]SET@_combobox_place_grub.set[/EMAIL]_active(0)
[EMAIL="SET@_radiobutton_place_grub.set"]SET@_radiobutton_place_grub.set[/EMAIL]_active(True)
[debug]set_radiobutton_place_grub
[EMAIL="SET@_combobox_place_grub.set"]SET@_combobox_place_grub.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_label_force_grub.set"]SET@_label_force_grub.set[/EMAIL]_text('''Force GRUB into: sda5 (for chainloader)''')
[EMAIL="SET@_checkbutton_purge_grub.show"]SET@_checkbutton_purge_grub.show[/EMAIL]()
[EMAIL="SET@_checkbutton_legacy.set"]SET@_checkbutton_legacy.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_button_open_etc_default_grub.show"]SET@_button_open_etc_default_grub.show[/EMAIL]()
[EMAIL="SET@_checkbutton_purge_grub.set"]SET@_checkbutton_purge_grub.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_purge_grub.set"]SET@_checkbutton_purge_grub.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_checkbutton_lastgrub.hide"]SET@_checkbutton_lastgrub.hide[/EMAIL]()
[debug]LASTGRUB_ACTION becomes: 
[EMAIL="SET@_checkbutton_blankextraspace.set"]SET@_checkbutton_blankextraspace.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_checkbutton_blankextraspace.set"]SET@_checkbutton_blankextraspace.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_uncomment_gfxmode.set"]SET@_checkbutton_uncomment_gfxmode.set[/EMAIL]_active(False)
[EMAIL="SET@_checkbutton_ata.set"]SET@_checkbutton_ata.set[/EMAIL]_active(False)
[EMAIL="SET@_combobox_add_kernel_option.set"]SET@_combobox_add_kernel_option.set[/EMAIL]_sensitive(False)
[EMAIL="SET@_checkbutton_add_kernel_option.set"]SET@_checkbutton_add_kernel_option.set[/EMAIL]_active(False)
[EMAIL="SET@_button_mainapply.set"]SET@_button_mainapply.set[/EMAIL]_sensitive(True)
[EMAIL="SET@_combobox_ostoboot_bydefault.set"]SET@_combobox_ostoboot_bydefault.set[/EMAIL]_active(0)
[debug]MBR_ACTION is set : reinstall (NBOFDISKS is 1)
DEBUG=> in bash NOT GET _combobox_separateboot sda1
[debug]RET_sepboot (BOOTPART_TO_USE) : sda1
DEBUG=> in bash NOT GET _combobox_place_grub sda
[debug]RETOURCOMBO_place_grub (NOFORCE_DISK) : sda
DEBUG=> in bash NOT GET _button_justbootinfo clicked
[EMAIL="SET@_mainwindow.hide"]SET@_mainwindow.hide[/EMAIL]()
[EMAIL="SET@pulsatewindow.show"]SET@pulsatewindow.show[/EMAIL]()
[debug] debug_echo_important_variables
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[debug]MAIN_MENU becomes : Boot-Info
[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Create a BootInfo summary. This may require several minutes...''')


=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda5 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s      


=================== Final advice in case of suggested repair


The boot files of [Ubuntu 17.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))


=================== User settings
[debug] debug_echo_important_variables
The settings chosen by the user will not act on the boot.




[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Create a BootInfo summary. This may require several minutes...''')
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[debug]Unmount all blkid partitions except df ones
[debug]BLKID Mount point of sda2 is: /mnt/boot-sav/sda2
[debug]BLKID Mount point of sda3 is: /mnt/boot-sav/sda3
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[debug]BLKID Mount point of sda5 is: /mnt/boot-sav/sda5
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[debug]BLKID Mount point of sda1 is: /mnt/boot-sav/sda1
umount: /mnt/boot-sav/sda1: not mounted.
[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Create a BootInfo summary (bis). This may require several minutes...''')

Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]

[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
Identifying MBRs...
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
Searching sda2 for information... 
Searching sda3 for information... 
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
Searching sda4 for information... 
Searching sda5 for information... 
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
Searching sda6 for information... 
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()

Finished. The results are in the file "RESULTS.txt"
located in "/tmp/boot-repair-lecds/".

[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Create a BootInfo summary (bs-check). This may require several minutes...''')
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
cat: write error: Broken pipe
[EMAIL="SET@pulsatewindow.hide"]SET@pulsatewindow.hide[/EMAIL]()
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
/usr/share/boot-sav/gui-actions.sh: line 621: 10977 Terminated              while true; do
    echo 'SET@_progressbar1.pulse()'; sleep 0.2;
done
Upload the report to a pastebin ? yes
[EMAIL="SET@pulsatewindow.show"]SET@pulsatewindow.show[/EMAIL]()
[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Create a BootInfo summary (net-check). This may require several minutes...''')
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[debug]internet: connected
[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Create a BootInfo summary (url). This may require several minutes...''')
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[debug]Mount all blkid partitions except the ones already mounted and BIOS_Boot
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[debug]BLKID Mount point of sda2 is: /mnt/boot-sav/sda2
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[debug]BLKID Mount point of sda3 is: /mnt/boot-sav/sda3
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[debug]BLKID Mount point of sda5 is: /mnt/boot-sav/sda5
[debug]Mount path of sda5 is: /mnt/boot-sav/sda5
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/sda1 : Error code 12
mount -r /dev/sda1 /mnt/boot-sav/sda1
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/sda1 : Error code 12
[debug]BLKID Mount point of sda1 is: /mnt/boot-sav/sda1
[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Create a BootInfo summary (net-check). This may require several minutes...''')
[debug]internet: connected
[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Create a BootInfo summary (net-ok). This may require several minutes...''')
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Create a BootInfo summary (20). This may require several minutes...''')
[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Create a BootInfo summary (19). This may require several minutes...''')
[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Create a BootInfo summary (18). This may require several minutes...''')
[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Create a BootInfo summary (17). This may require several minutes...''')
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[EMAIL="SET@_label0.set"]SET@_label0.set[/EMAIL]_text('''Create a BootInfo summary. Please wait few seconds...''')
[debug]Logs saved into /mnt/boot-sav/sda5/var/log/boot-repair/20180204_141205
[debug]Unmount all blkid partitions except df ones
[debug]BLKID Mount point of sda2 is: /mnt/boot-sav/sda2
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[debug]BLKID Mount point of sda3 is: /mnt/boot-sav/sda3
[debug]BLKID Mount point of sda5 is: /mnt/boot-sav/sda5
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
[debug]BLKID Mount point of sda1 is: /mnt/boot-sav/sda1
umount: /mnt/boot-sav/sda1: not mounted.
[EMAIL="SET@pulsatewindow.hide"]SET@pulsatewindow.hide[/EMAIL]()
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
```

---

### Post by oldfred on 2018-02-04
Please use code tags on long text or terminal output. 
And easy to add code tags with forum's Advanced Editor and # icon.

Also when very long like the Boot-Repair summary often better to use a pastebin site and just post link.

Only really needed logs as you were saying Boot-Repair was failing and wanted to see where it stopped working. 
But once it ran report, there is little in logs that is helpful as they are just detailing each step to generate the output in report.

You have not been good about housecleaning kernels, so now grub menu is very long. It probably scrolls off bottom of screen (box) that boot entries are in. 
You may have a tiny arrow showing you have more entries. 
And Windows would be at bottom, but report does not show it being found?

What version of Windows?
If Windows 8 or 10 did you leave fast start up/hibernation on, or does Windows need chkdsk?
Grub only boots working Windows or Windows that is not hibernated. And Windows 10 on updates will turn fast start up back on.

You  have a newer Acer with UEFI, but both Windows & Ubuntu are installed in the now 35 year old BIOS/MBR configuration.
Most of the Acer with UEFI have needed "trust" settings to boot a new UEFI entry, but it should just boot in BIOS/Legacy/CSM mode if you choose hard drive.

UEFI makes it easy to directly boot Windows, so then you can repair it or turn fast start up back off, if grub does not boot Windows.
But with BIOS you have to temporarily restore the Windows boot loader, and see if f8 repair console lets you fix Windows or then in Windows turn off fast start up. Best to also have Windows repair flash drive whether UEFI or BIOS.

Report says Secure Boot may be on. It must be off to boot in BIOS boot mode. And best to always boot Ubuntu live installer/Boot-Repair in BIOS mode since you have converted your system to BIOS.
Run this in Ubuntu, if you can get to it.
sudo update-grub

Use gparted on Ubuntu live installer and move boot flag back to sda2, the Windows boot partition. Flag was moved to sda3 and boot files are now in sda3, so it may boot. Boot-Repair often copies Windows boot files from boot partition to Windows partition as many users do not even know Windows has a boot partition and delete it, deleting all ways to boot. Grub does not use boot flag, but looks for typical Windows boot files to know which partition to boot.

Then using Windows repair flash drive or perhaps Boot-Repair's advanced mode and choose Windows & MBR to temporarily restore the Windows boot to MBR. Boot Windows to confirm it works, make sure fast start up is off.
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 

      
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by eddugo on 2018-02-06
Just read your reply and wanted answer question re: Windows version.  It is 7 Home Premium.

Also, if I tick restore MBR, it will boot into Windows - no GRUB appears.  I did that, and then ran boot repair without ticking restore MBR and it went back to no boot.

---

### Post by oldfred on 2018-02-06
Use Boot-Repair's advanced mode and run the full uninstall/reinstall of grub. Also check install latest kernel.

May need to check options on more than one screen. Have not used it recently and these screens may not be current.
 [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

