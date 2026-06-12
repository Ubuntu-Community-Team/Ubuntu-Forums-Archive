---
title: "Ubuntu fresh install black screen on boot"
date: 2024-06-10
forum: Installation &amp; Upgrades
---

### Post by amazingmation92 on 2024-06-10
So today I decided to install Ubuntu because some software I need isn't on Debian. I download the iso (24.04 LTS) onto a Ventoy USB. I plug it into the computer and boot to it. I get to the menu where you can pick normal or other options. The first time I picked normal and it showed the Ubuntu logo and a loading thing after a second, but it then disappeared and the screen went black. The screen stopped receiving output. Eventually after like 30-60 seconds it made the chime that Ubuntu makes when the installer gui opens in the Ubuntu environment. I rebooted and eventually chose the safe graphics or something like that instead. I was able to boot and install Ubuntu (the screen resolution was messed up but I assume thats because of the safe graphics). I then reboot the system and go to boot in and the screen goes black and gives then gives no output. I troubleshooted for a couple of hours and tried lots of things. I sometimes can get it to boot into grub and one of the two times I got into grub I changed something according to a guide in where you click e in grub and I changed quiet splash to nomodeset or something like that. At this point I can't find anything else and don't know what to do. I have tried editing a few files on the installed system from the install usb. I have tried reinstalling the iso. I have tried reinstalling Ubuntu. I looked through the settings in the bios and nothing looked like it could help. I don't know what to do at this point.

System:
Product Name: HP Compaq 6200 Pro SFF PC
CPU: i5 2400
Ram: 8gb ddr3 1333MHz
1 tb hdd
System BIOS: JO1 v02.06
Integrated Graphics on cpu

I believe there is no safe boot on this system as it is too old. 

Before going to Ubuntu, I had Debian 12 running just fine on it. If you need more info about the system by me running commands or something I can a couple more times to boot into something to get more info.

---

### Post by yancek on 2024-06-11
>  I troubleshooted for a couple of hours and tried lots of things. 

If these 'things' didn't work, it would be best if you went through your notes and undid whatever it is you did.

>  you click e in grub and I changed quiet splash to nomodeset or something like that 

That method is a one time change for that single boot and will not work on the next boot.  You need to edit the proper grub file which is /etc/default/grub, explained at the link below.

[https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)

You might try downloading boot repair on the Ubuntu usb you used to install it.  Use the 2nd option described at the link below to Create BootInfo Summary and post the link you get when it finishes here for help.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by amazingmation92 on 2024-06-11
I tried changing the grub file like 10 times and each time got an error. The first erros where about it not being able to find /cow. I did all the chroot stuff and wasn't able to change it. But, the one time I was able to boot into Ubuntu, I changed it and rebooted and it still showed a black screen and no grub on boot. To undo all of the other things I did, I can try to reinstall Ubuntu again, but that didn't fix the issue the last time.

I will go ahead and try boot repair to see if that helps.

---

### Post by amazingmation92 on 2024-06-11
So, I just used boot repair and now I can actually get to grub. If I continue with the boot regularly, the screen goes black again and nothing is every shown. I would assume its a graphics issue/graphics driver issue, but I don't know how I would fix that. here are the pastebins from the boot repair:

[https://paste.ubuntu/com/p/R5ChWnCVCD](https://paste.ubuntu/com/p/R5ChWnCVCD)
[https://paste.ubuntu.com/p/JkSqf_qnTH](https://paste.ubuntu.com/p/JkSqf_qnTH) (the _ is either g or y because somehow i put the cursor over the code and dint realize)

Also, it does boot to Ubuntu with nomodeset, but as you said this isn't permanent. It would be quiet annoying to set this everytime and not have the correct aspect ratio.

---

### Post by jeremy31 on 2024-06-11
Can you post results from terminal for ```
sudo dmesg|grep -i amd
```

---

### Post by amazingmation92 on 2024-06-11
[    0.000000] Linux version 6.8.0-35-generic (buildd@lcy02-amd64-020) (x86_64-linux-gnu-gcc-13 (Ubuntu 13.2.0-23ubuntu4) 13.2.0, GNU ld (GNU Binutils for Ubuntu) 2.42) #35-Ubuntu SMP PREEMPT_DYNAMIC Mon May 20 15:51:52 UTC 2024 (Ubuntu 6.8.0-35.35-generic 6.8.4)
[    0.000000]   AMD AuthenticAMD
[    0.000000] RAMDISK: [mem 0xc4eb5000-0xc8bd9fff]

---

### Post by yancek on 2024-06-11
>  The first erros where about it not being able to find /cow

That message generally means you were using a 'live' system (DVD/USB) and were trying to make the change on the device (DVD/USB) which won't work as it is a read only filesystem.  The chroot method should work if done properly. 

Neither link you posted shows anything so run boot repair again with the Create BootInfo Summary option, do not make repairs, and carefully copy the actual link to post here.

Post information on your graphics card with either command below.

> lspci | grep VGA
sudo lshw -C video

---

### Post by amazingmation92 on 2024-06-11
I know that the /cow error was from the live usb but I couldnt get into the os at the time or grub so thats the only way to do it and doing chroot didnt work in any way because there were multiple other errors. I did do it once I got the os to load the first time but that didn't help at all.

boot repair new link: (expires 06/12/24)
[https://paste.ubuntu.com/p/d6brFggQYY/](https://paste.ubuntu.com/p/d6brFggQYY/)

[COLOR=#000000][I]lspci | grep VGA:
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

[/I][/COLOR][COLOR=#000000][I]sudo lshw -C video:
*-display UNCLAIMED
    description: VGA compatible controller
    product: 2nd Generation Core Processor Family Integrated Graphics
Controller
    vendor: Intel Corporation
    physical id: 2
    bus info: pci@0000:00:02.0Z
    version: 09
    width: 64 bits
    clock: 33MHz
    capabilities: msi pm vga_controller bus_master cap_list
    configuration: latency=0
    resources: memoryfe000000-fe3fffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff
*-graphics
    product: simpledrmdrmfb
    physical id: 2
    logical name: /dev/fb0
    capabilities: fb
    configuration: depth=32 resolution=800,600




from pastebin (in case it expires):

[/I][/COLOR]boot-repair-4ppa2075                                              [20240611_1928]


============================== Boot Info Summary ===============================


 => No boot loader is installed in the MBR of /dev/sda.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 24.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub




================================ 1 OS detected =================================


OS#1:   The OS now in use - Ubuntu 24.04 LTS on sda2


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: 2nd Generation Core Processor Family Integrated Graphics Controller simpledrmdrmfb from Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.8.0-35-generic root=UUID=01dfffbb-920a-4e51-a272-b8ce33ce5bee ro nomodeset vt.handoff=7
df -Th / : /dev/sda2      ext4  915G   11G  859G   2% /


===================================== UEFI =====================================


BIOS/UEFI firmware: J01 v02.06(2.6) from Hewlett-Packard
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot disabled - This system doesn't support Secure Boot.
BootCurrent: 0000
Timeout: 0 seconds
No BootOrder is set; firmware will attempt recovery
Boot0007* IBA GE Slot 00C8 v1372	BBS(Network,,0x0)AMBO
      dp: 05 01 09 00 06 00 00 00 00 / 7f ff 04 00
    data: 41 4d 42 4f




============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	no-wind,	2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda2	: is-os,	64, apt-get,	signed grub-efi ,	grub2,	grub-install,	grubenv-ok,	update-grub,	end-after-100GB
sda1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far


Partitions info (2/3): _________________________________________________________


sda2	: isnotESP,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot


Partitions info (3/3): _________________________________________________________


sda2	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda
sda1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: B4783C3A-0047-4487-AAEA-E295553301FB
       Start        End    Sectors   Size Type
sda1     2048    2203647    2201600     1G EFI System
sda2  2203648 1953521663 1951318016 930.5G Linux filesystem


parted -lm (filtered): _________________________________________________________


sda:1000GB:scsi:512:512:gpt:ATA ST31000528AS:;
1:1049kB:1128MB:1127MB:fat32::boot, esp;
2:1128MB:1000GB:999GB:ext4::;


blkid (filtered): ______________________________________________________________


NAME   FSTYPE UUID                                 PARTUUID                             LABEL PARTLABEL
sda                                                                                           
&#9500;&#9472;sda1 vfat   FD46-D5E1                            e83cdbe6-f77b-4e1f-8418-5a9b7cd45f22       
&#9492;&#9472;sda2 ext4   01dfffbb-920a-4e51-a272-b8ce33ce5bee 4e4816cf-a036-40eb-871e-d6ae650d5e27       
sdb                                                                                           
sdc                                                                                           
sdd                                                                                           
sde                                                                                           
sdf                                                                                           


Mount points (filtered): _______________________________________________________


                                Avail Use% Mounted on
/dev/sda2                      858.1G   1% /
efivarfs                        49.8K  14% /sys/firmware/efi/efivars


Mount options (filtered): ______________________________________________________


/dev/sda2                      ext4            rw,relatime


===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================


search.fs_uuid 01dfffbb-920a-4e51-a272-b8ce33ce5bee root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


====================== sda2/boot/grub/grub.cfg (filtered) ======================


Ubuntu   01dfffbb-920a-4e51-a272-b8ce33ce5bee
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###


========================== sda2/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/01dfffbb-920a-4e51-a272-b8ce33ce5bee / ext4 defaults 0 1
# /boot/efi was on /dev/sda1 during curtin installation
/swap.img	none	swap	sw	0	0
UUID=FD46-D5E1  /boot/efi       vfat    defaults      0       1


======================= sda2/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false


==================== sda2: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
 371.664089203 = 399.071277056  boot/grub/grub.cfg                             1
   4.760002136 = 5.111013376    boot/vmlinuz                                   1
   4.760002136 = 5.111013376    boot/vmlinuz-6.8.0-35-generic                  1
   4.760002136 = 5.111013376    boot/vmlinuz.old                               1
 372.001113892 = 399.433154560  boot/initrd.img                                1
 372.001113892 = 399.433154560  boot/initrd.img-6.8.0-35-generic               1
 372.001113892 = 399.433154560  boot/initrd.img.old                            1


===================== sda2: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18133 Apr  4 06:12 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4 06:12 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4 06:12 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4 06:12 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4 06:12 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4 06:12 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Apr  5 07:36 35_fwupd
-rwxr-xr-x 1 root root   214 Apr  4 06:12 40_custom
-rwxr-xr-x 1 root root   215 Apr  4 06:12 41_custom






Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda2,
using the following options:  sda1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups


Final advice in case of suggested repair: ______________________________________


Please do not forget to make your UEFI firmware boot on the The OS now in use - Ubuntu 24.04 LTS entry (sda1/efi/****/grub****.efi (**** will be updated in the final message) file) !

---

### Post by amazingmation92 on 2024-06-13
Just tried Oibaf drivers and that didn't help. Still no display output without nomodeset

---

