---
title: "Install Ubuntu on USB-Stick"
date: 2014-12-29
forum: Installation &amp; Upgrades
---

### Post by stephano2 on 2014-12-29
Hello together, 

i wan't to install Ubuntu 14.04 64bit to a stick, but it doesn't work. I do following steps: 

I format a 4GB-Installation-Stick in windows 8 with the Tool "Rufus" and select the Ubuntu_64bit.iso. And then put in a second 64GB-Stick to the same laptop. The 64GB Stickis my goal device for the installation. 

Then i follow these steps:
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

In Point B: I press F12 to boot in UEFI from the 4GB-Installation-Stick, then i go "Try Ubuntu". There i create with gparted a "GPT-partition-table" and create following partitions:

> dev/sdc1: 1MB FAT32 with FLAG: bios_grub (unformated is not possible. If a click to "Apply" then he automatically use the FileSystem FAT32 and add a red exclamation mark.)
dev/sdc2: 550MB FAT32 Label EFI with FLAG: boot, esp (without esp is not possible)
dev/sdc3 12GB EXT4 (later forroot partition /)
dev/sdc4 1GB linux-swap
dev/sdc5 46GB NTFS for Data (Flags: msftdata)


[LIST]
[*]Then I restart the notebook (DELL XPS 15) press again F12 to start the 4GB-Installation-Stick and enter "Install Ubuntu". 
[*]Then I follow the normal installation-steps. 
[*]I choose "Something else" in partition windows and select for root-partition /dev/sdc3 and for bootloader-installation /dev/sdc 
[*]I Select time zone, language, user name, computer name, password ant start the installation process. 
[/LIST]
 
After some minutes i get a error message in german, like:
The execution of "grub install /dev/sdc" is failed. This is a fatal error. 

What can couse this reaction? For information, the 64GB-Stick has not set the removable bit. It is a Sandisk Extreme

---

### Post by stephano2 on 2014-12-29
I get following output after fdisk -l

> 
...
Device     Start     End Sectors  Size Type
/dev/sdb1   2048 7884766 7882719  3.8G Microsoft basic data

Disk /dev/sdc: 59.6 GiB, 64023257088 bytes, 125045424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 5FC07A85-0773-41B3-8591-6AC112B1FBF4

Device        Start       End  Sectors  Size Type
/dev/sdc1      2048      4095     2048    1M BIOS boot
/dev/sdc2      4096   1130495  1126400  550M EFI System
/dev/sdc3   1130496  25706495 24576000 11.7G Linux filesystem
/dev/sdc4  25706496  27754495  2048000 1000M Linux swap
/dev/sdc5  27754496 125044735 97290240 46.4G Microsoft basic data

sudo parted -l | tail -n8

> Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2097kB  1049kB                        bios_grub
 2      2097kB  579MB   577MB   fat32                 boot, esp
 3      579MB   13.2GB  12.6GB  ext4
 4      13.2GB  14.2GB  1049MB  linux-swap(v1)
 5      14.2GB  64.0GB  49.8GB  ntfs                  msftdata


More Information: 
If i start the installation process ascome to the partition menü, I see the partitions like in the top of this posting. But befor of /dev/sdc1 i see: Free Space 1 MB. After this I see then Dev/sdc with 1MB für bios_grub.

---

### Post by nerdtron on 2014-12-29
> 

[LIST]
[*]Then I restart the notebook (DELL XPS 15) press again F12 to start the 4GB-Installation-Stick and enter "Install Ubuntu".
[*]Then I follow the normal installation-steps.
[*]**I choose "Something else" in partition windows and select for root-partition /dev/sdc3 and for bootloader-installation /dev/sdc**
[*]I Select time zone, language, user name, computer name, password ant start the installation process.
[/LIST]


I don't think just a root partition will be enough on a UEFI system, I think you still need to put a smal parition for the EFI system and install grub.

What you did is still correct though but not on a UEFI system, that should work on a BIOS computer.

---

### Post by stephano2 on 2014-12-29
Ok, I thougt the manual was also for BIOS and UEFI. And thought, normally it doesn't matter, if the host was a EFI System or not. Because, if I start from USB, then he load his unindependant his own bootloader. 

But mostly, my problem is, that i not even finish the instalaltion, because he cannot install grup.

---

### Post by oldfred on 2014-12-29
The bios_grub partition must be unformatted. Otherwise grub will give that error about not being able to install in BIOS boot mode.

I think unformatted is the very bottom choice of formats in gparted & you have to scroll down in the combo box of choices.

You parted list does make it look like it is unformatted?

Are you installing in BIOS or UEFI boot mode?
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by stephano2 on 2014-12-29
> **oldfred said:**
> 
I think unformatted is the very bottom choice of formats in gparted & you have to scroll down in the combo box of choices.

You parted list does make it look like it is unformatted?


Ok, I try it again. Problem was, that I create the first unformatted partition with gparted. To set the flag "bios_grub" I have to click "Apply". Then the menu-item "manage flags" are activated. But, after clicking to Apply he set automaticaly to FAT32. Afterwards I can not set again to "unformatted", only to "cleared" or something like that. Is it the same?

---

### Post by stephano2 on 2014-12-29
Ok, i get the "unformatted" partition. 

Instead of these steps:

> 1a. Make a 1 MiB partition without file system (unformatted) 
Apply
1b. Add the flag bios_grub. 
2a. Make a 250 MiB partition with FAT32 file system and the label EFI 
Apply
2b. Add the boot flag

I have to do following order:

> 1a. Make a 1 MiB partition without file system (unformatted) 
2a. Make a 250 MiB partition with FAT32 file system and the label EFI
Apply
3a. Add the flag bios_grub for 1a
3b. Add the boot flag 2a

then the first partition is "unknown", also unformatted. 

After Installation again, I get a new error message. In my translation like that:

"The package"grub-efi-amd64-signed" could not installed in /target/. Without GRUB-Bootloader the installed System will not boot.

---

### Post by oldfred on 2014-12-29
Now the error is from an UEFI install with secure boot on as that uses the signed versions. Not sure if you have efi partition why it would give an install error. You do not just label the partition efi but must set the efi flag. The actual code is a very long GUID and gparted uses the flag to assign the correct GUID. If you use gdisk the code is ef00 for the efi partition and ef02 for the bios_grub partition. 
 [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)


Post link to summary report.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by sudodus on 2014-12-30
I wrote the wiki page [https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

It worked for me in two different computers, but I am not sure it will work with all versions of UEFI. Anyway, you can try with ***Boot-Repair*** (booted from another drive than the one you want to create) at least twice according to the instruction steps K, L, M.

After that is working you can continue with the instruction steps N, ...

-o-

But I have not been able to make this system stable enough to survive certain updates as described [here]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Not_stable_enough_to_survive_certain_updates").

---

### Post by stephano2 on 2014-12-30
@oldfred

enclosed, you can find the report in the attachment


@sudodus
is the installation of the grub one of the last steps during the installation-process? Because Step "J" is not finished. I can try to run boot-repair, but i dont find the option to select the boot-repair of the boot (Stick) and not the boot from the internal HDD of the notebook

---

### Post by sudodus on 2014-12-30
You must get boot-repair separately (either get a dedicated boot-repair iso file or install it to a persistent USB install drive). See this link

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2014-12-30
You have Windows on a gpt partition sda drive, so it only boots in UEFI mode, but somehow installed a Windows boot loader into the gpt protective MBR on sda. That is not a problem, but never will be used.

You have no grub boot files in MBR of sdc for BIOS boot or in efi partition on sdc.

Boot-Repair is suggesting to turn off secure boot and that usually is a good idea. While Ubuntu will boot with secure boot on, not sure about installing grub to sdc with it on.

Boot-Repair says it wants the default install of grub for sdc3 into the efi partition on sda, you do not want that. You should be able to select advanced mode and choose the system in sdc3, Ubuntu and choose to install to sdc drive. It in UEFI mode then it will install grub to efi partition, if in BIOS mode it will install grub to MBR.

I put a second install of Ubuntu on my sdb drive in UEFI mode and was pretty sure I selected grub to install to sdb. But it overwrote the grub in my efi partition on sda. So I just copied that to sdb, and booted  my install in sda and reinstalled grub to sda in UEFI boot mode.

 Or good idea to backup efi partition before any install.

---

### Post by stephano2 on 2014-12-30
Hello together, 

enclosed my status after boot-repair. I install and run boot-repair in "Try Ubuntu", without the other options of the manual after step "M".


[LIST=1]
[*]Now, if the stick is connected and i start the notebook, i get automatically GRUB, where I can choose Ubuntu, windows-bootloader or something other options. Both OS are loading sucessfully. 
[*]If the stick is connected and i press F12 o get the UEFI Options, I can choose "Ubuntu". If i press to ubuntu, then I get the message "Invalid signature detected. Check secure boot policy in setup. If I press enter, i get the same options like point 1 and can start ubuntu or windows or other options. 
[*]If the stick is disconnected I get a bash console (Minimal BASH-like line editin is supported[..]) 
[*]I connect to USB to a "Microsoft Surface3 Pro" and start from USB. I get the same message like point 2. If I press enter, then Windows is starting 
[/LIST]

Now, i have two questions:


[LIST=1]
[*]Is it not possible, that the internal EFI partition from the notebook not changed. I mean, the EFI partition is in the original stare, before i install Ubuntu. That means, windows start normally. Only, if i press F12, or start from USB, then the GRUB bootloader starts 
[*]Is it possible to get a signated OS, that i can start this stick also from other notebooks? Otherwise i have to change the bios/efi setup ==> deactivate secure boot, and this is not good in foreign notebooks. 
[/LIST]

Here the Report after boot-repair:
[http://paste.ubuntu.com/9645428](http://paste.ubuntu.com/9645428)

Best Regards

---

### Post by oldfred on 2014-12-30
It looks like you left Windows in fast boot or always on hibernated as the os-prober was not able to mount and see your Windows install.

Ubuntu uses the Microsoft signing key, and will boot with secure boot on with many systems. Often better just to turn secure boot off.
But many vendors also are modifying UEFI to only boot a Windows entry as the use the description field in UEFI to check if it says Windows. I thought Dell was one that still would boot an Ubuntu entry.

       Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

For those systems we have many work arounds and best will depend on system and configuration. Most like to rename bootx64.efi and make it really be grub or shim. Then you can boot a hard drive entry (that seems to be allowed) from UEFI menu. Some with only Ubuntu just rename grub or shim entry to read Windows. Some use rEFInd which seems to work.

Work arounds:
      
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by sudodus on 2014-12-30
> **stephano2 said:**
> 
Now, i have two questions:


[LIST=1]
[*]Is it not possible, that the internal EFI partition from the notebook not changed. I mean, the EFI partition is in the original stare, before i install Ubuntu. That means, windows start normally. Only, if i press F12, or start from USB, then the GRUB bootloader starts 
[*]Is it possible to get a signated OS, that i can start this stick also from other notebooks? Otherwise i have to change the bios/efi setup ==> deactivate secure boot, and this is not good in foreign notebooks. 
[/LIST]

Here the Report after boot-repair:
[http://paste.ubuntu.com/9645428](http://paste.ubuntu.com/9645428)

Best Regards

I think both of us should reply.

1. It should be possible to boot from the pendrive in a way independent of all other drives in the computer.

2. The system provided by the current Ubuntu desktop 64-bit iso files contains a signed OS, which should satisfy the UEFI system. The idea is to make a portable system, that works in many computers and in BIOS and UEFI.

-o-

Did you try to download the compressed image file and to install it directly to the big USB pendrive using mkusb according to this link?

[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Installation_from_a_compressed_image_file-1](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Installation_from_a_compressed_image_file-1)

---

### Post by stephano2 on 2015-01-02
Hello together, 

I install again Windows 8 to get the factory settings in all partitions, including EFI. So theinternal SDA of the notebook is not changed. Now, If you put the 64GB-Stick (with installed Ubuntu on it) to the notebook and press F12 while startup, to select the USB, I don't get a selection with USB. That emans, on the 64GB-Stick is nothing regarding boot or grub.

If I put the 4GB-Stickwith LiveUSB, I can start the LiveUSB, after pressing F12 on startup. 


@oldfred
Do I understand it rightly regarding the workaround on [http://ubuntuforums.org/showthread.php?t=2234019:](http://ubuntuforums.org/showthread.php?t=2234019:)
I have to adapt the EFI partition on the 64GB-Stick (sdc) and not the local or internal hard disc (sda) on the notebook?

@sudodus
> Did you try to download the compressed image file and to install it  directly to the big USB pendrive using mkusb according to this link?

[https://help.ubuntu.com/community/In...d_image_file-1]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Installation_from_a_compressed_image_file-1")
I will try it tommorow. But I think, if you copy the image to the stick, the partitions will be overwritten


Appendix
Yesterday (before I install Windows 8) I start the notebook without stick and get (as described before) the grub bash console (Minimal BASH-like line editin is supported[..]) and forget the notebook open. After some minutes I fan of the notebook working extremly and the notebook was very hot. Should the console not normally takes big perfomance?

---

### Post by sudodus on 2015-01-02
Yes, the previous partitions will be overwritten. But a new bootloader and new partitions will come from the compressed image in the file (and be expanded and written to the stick). It will restore an exact copy of a system, that I am able to run in two computers in both UEFI and BIOS mode (both modes in both computers).

You can use the manual [mkUSB-quick-start-manual.pdf]("http://phillw.net/isos/linux-tools/mkusb/mkUSB-quick-start-manual.pdf")  for the installation, and [GrowIt.pdf]("http://phillw.net/isos/linux-tools/9w/GrowIt.pdf") to move the swap and to 'grow' the root partition according to this link (if you want to use more than 7.8 GB). Do not move the small partitions in the beginning of the drive!

---

### Post by stephano2 on 2015-01-03
Okey, thanks, i will try it. 


separate from mkusb, I have the open point to oldfred, where i have to adapt the efi file. In in internal storage or directly in the sdc?
Before I try mkusb, i look to the 64GB-Stick. First unmount dev/sda1 (EFI from internal storage). On the stick the folder /boot/efi/ is empty. Therefore, I think, it is not possible so start from the 64GB-Stick, after pressing F12 on startup. He don't list the 64GB-Stick, only the other 4GB LiveUSB or InstallationUSB. 


That means, its normaly make no sense to rename something else in /dev/sda1 like "https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Installation_from_a_compressed_image_file-1" or missunderstand I something?


Edit 14:43:
Now i start with LiveUSB boot-repair and change in advanced the setting, to install "GRUB" to dev/sdc. I hope, maybe the stick is bootable independant

---

### Post by stephano2 on 2015-01-03
Now, I start boot repair and change some setting in "advanced". I mark, to install grub on "/dev/sdc" and deactivate to reinstall kernel. 

Now if I startup the notebook and press to F12, I cannot the 64GB-Stick, but, after deactivate "Secure boot", I can se "USB Storage Device" under Legacy Options. If I chose now "USB Storage Device", I get a slow loaded Grub, where i can choose ubuntu. While startup of ubuntu, i get the message. that the device /boot is not prepared or cannot find. With "S" i can skip mounting or with "M" i can manually restore. 

If I press to "S" ubuntu starts normally. 

I think he install grub to "/dev/sdc3" instead of "/dev/sdc" or "/dev/sdc1". See [http://paste.ubuntu.com/9666044/](http://paste.ubuntu.com/9666044/)

On the other notebook (or tablet - microsoft surface 3), i get the same message: ""Invalid signature detected. Check secure boot policy in setup". I try to deactivate secure boot on microsoft surface

---

### Post by oldfred on 2015-01-03
You seem to have some sort of error with sdc5?

When you reboot, the boot drive is always hd0, but when you installed it was hd2. I was never able to get flash drives to boot until I changed hdX to hd0. But the search line is supposed to override incorrect drive numbers as it is using UUID.
If you are able to boot run sudo update-grub and it should reset everything automatically in grub.
 
```
 set root='[COLOR=#ff0000]hd2,gpt3[/COLOR]'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt3 --hint-efi=[COLOR=#ff0000]hd2,gpt3[/COLOR] --hint-baremetal=[COLOR=#ff0000]ahci2,gpt3[/COLOR]  d3957a75-2e34-4d3c-bd53-0925632f037e
else
  search --no-floppy --fs-uuid --set=root d3957a75-2e34-4d3c-bd53-0925632f037e


```

You have the sdc configured as BIOS boot. It will not boot with secure boot on.

Your fstab has this incorrect entry, best to just delete it. You do not have a /boot (the efi is not a /boot partition). 

```
UUID=530b8a5a-17d3-4028-96fb-a26f66718b2b	/boot	/dev/sdc1: PARTUUID=	defaults	0	2
```

---

### Post by stephano2 on 2015-01-03
Thank you together very much. 

> You seem to have some sort of error with sdc5?
SDC5 is the residual free space on the 64GB-Stick für Data. I will format it later in NTFS. 

> If you are able to boot run sudo update-grub and it should reset everything automatically in grub.
Oki, i will run "sudo update-grub"


> You have the sdc configured as BIOS boot. It will not boot with secure boot on.
I can try to install also EFI with boot-repair on the stick to /dev/sdc, if possible. But, if i remember rightly, I can only select /dev/sda.
How is a LiveUSB createdt or how is the structure? I think, the LiveUSB ist configured very well. You can put the stick and press F12, then you can see the LiveUSB on the boot-options and can select and start the LiveUSB very easily.


> Your fstab has this incorrect entry, best to just delete it. You do not have a /boot (the efi is not a /boot partition).
Thanks, i will delete it. But normally I configured with gpartedt /dev/sdc1 as /boot. 

> Number  Start   End     Size    File system     Name  Flags
1      1049kB  2097kB  1049kB                        bios_grub
2      2097kB  264MB   262MB   fat32                 boot, esp
3      264MB   12.8GB  12.6GB  ext4
4      12.8GB  13.9GB  1049MB  linux-swap(v1)
5      13.9GB  64.0GB  50.1GB                        msftdata


But as Logfile it seems that grub was in sdc3, instead of sdc1. 
> 
=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.

sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda2.

sda4	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda4.

sdc2	: sdc,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdc2.

sdc3	: sdc,	not-sepboot,	grubenv-ok	grub2,	signed grub-efi ,	update-grub,	64,	no-kernel,	is-os,	not--efi--part,	fstab-has-goodBOOT,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdc3.

sdc1	: sdc,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdc1.

sdc5	: sdc,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdc5.


sda	: GPT,	no-BIOS_boot,	has-correctEFI, 	not-usb,	has-os,	2048 sectors * 512 bytes

sdc	: GPT,	BIOS_boot,	has-no-EFIpart, 	usb-disk,	has-os,	2048 sectors * 512 bytes


---

### Post by oldfred on 2015-01-03
Grub is actually in a lot of places. 

With BIOS the boot loader is in the MBR, but the MBR is so tiny it has  core.img in the sectors after the MBR. But grub.cfg is in /boot/grub, grub's configuration settings are in /etc/default/grub, and grub's scripts are in /etc/grub.d. 

With UEFI the boot loader is in the /EFI/ubuntu folder, there is no core.img and everything else is in same place.

---

