---
title: "Failed to boot after power outage"
date: 2022-06-30
forum: Installation &amp; Upgrades
---

### Post by edie209 on 2022-06-30
I am new here so please be gentle as I am not sure of the protocols here.

I have this pastebin [https://pastebin.ubuntu.com/p/mTZnY3vsWG/](https://pastebin.ubuntu.com/p/mTZnY3vsWG/) and I presume that I ask here for help.  As long as I can save my data on my raid I will be happy.

Thanks in advance


```
[COLOR=#111111][FONT=monospace]boot-repair-4ppa200                                              [/FONT][/COLOR][COLOR=#666666][FONT=monospace][[/FONT][/COLOR][COLOR=#111111][FONT=monospace]20220629_1454[/FONT][/COLOR][COLOR=#666666][FONT=monospace]][/FONT][/COLOR]
[COLOR=#666666]==============================[/COLOR] Boot Info [COLOR=#B8860B]Summary[/COLOR] [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector [COLOR=#666666]2048[/COLOR] 
    of the same hard drive [COLOR=#AA22FF]**for**[/COLOR] core.img. core.img is at this location and 
    looks [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR]mduuid/6a791c8c0fe9764ed07b23aa7ccc3316,1[COLOR=#666666])[/COLOR]/boot/grub. It also 
    embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt diskfilter mdraid1x raid5rec biosdisk
    ---------------------------------------------------------------------------
 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdf and looks at sector [COLOR=#666666]1[/COLOR] of 
    the same hard drive [COLOR=#AA22FF]**for**[/COLOR] core.img. core.img is at this location and looks 
    [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR]hd0,msdos1[COLOR=#666666])[/COLOR]/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi

md0: ___________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 

sdb: ___________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdc: ___________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdd: ___________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sde: ___________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 


[COLOR=#666666]================================[/COLOR] [COLOR=#666666]0[/COLOR] OS [COLOR=#B8860B]detected[/COLOR] [COLOR=#666666]=================================[/COLOR]


[COLOR=#666666]================================[/COLOR] Host/Hardware [COLOR=#666666]=================================[/COLOR]

CPU architecture: [COLOR=#666666]64[/COLOR]-bit
Video: RS880 [COLOR=#666666][[/COLOR]Radeon HD [COLOR=#666666]4250[/COLOR][COLOR=#666666]][/COLOR] from Advanced Micro Devices, Inc. [COLOR=#666666][[/COLOR]AMD/ATI[COLOR=#666666]][/COLOR]
Live-session OS is Ubuntu [COLOR=#666666]64[/COLOR]-bit [COLOR=#666666]([/COLOR]Ubuntu [COLOR=#666666]22[/COLOR].04 LTS, jammy, x86_64[COLOR=#666666])[/COLOR]

[COLOR=#666666]=====================================[/COLOR] [COLOR=#B8860B]UEFI[/COLOR] [COLOR=#666666]=====================================[/COLOR]

BIOS/UEFI firmware: V4.6.5.1 R1.8.0 [COLOR=#AA22FF]**for**[/COLOR] D3090-A1x[COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR].8[COLOR=#666666])[/COLOR] from FUJITSU // American Megatrends Inc.
This live-session is in Legacy/BIOS/CSM mode [COLOR=#666666]([/COLOR]not in EFI mode[COLOR=#666666])[/COLOR].



[COLOR=#666666]=============================[/COLOR] Drive/Partition [COLOR=#B8860B]Info[/COLOR] [COLOR=#666666]=============================[/COLOR]

Disks info: ____________________________________________________________________

sdb    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    [COLOR=#666666]2048[/COLOR] sectors * [COLOR=#666666]512[/COLOR] bytes
sdc    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    [COLOR=#666666]2048[/COLOR] sectors * [COLOR=#666666]512[/COLOR] bytes
sdd    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    [COLOR=#666666]2048[/COLOR] sectors * [COLOR=#666666]512[/COLOR] bytes
sde    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    [COLOR=#666666]2048[/COLOR] sectors * [COLOR=#666666]512[/COLOR] bytes

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________


Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]2[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________


Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]3[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________


fdisk -l [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ___________________________________________________________

Disk sda: [COLOR=#666666]55[/COLOR].9 GiB, [COLOR=#666666]60022480896[/COLOR] bytes, [COLOR=#666666]117231408[/COLOR] sectors
Disk identifier: C6166894-94EA-474E-B7D6-C9D2BDCDE833
      Start   End Sectors Size Type
sda1   [COLOR=#666666]2048[/COLOR]  [COLOR=#666666]4095[/COLOR]    [COLOR=#666666]2048[/COLOR]   1M BIOS boot
Disk sdb: [COLOR=#666666]1[/COLOR].82 TiB, [COLOR=#666666]2000398934016[/COLOR] bytes, [COLOR=#666666]3907029168[/COLOR] sectors
Disk sdc: [COLOR=#666666]1[/COLOR].82 TiB, [COLOR=#666666]2000398934016[/COLOR] bytes, [COLOR=#666666]3907029168[/COLOR] sectors
Disk sdd: [COLOR=#666666]1[/COLOR].82 TiB, [COLOR=#666666]2000398934016[/COLOR] bytes, [COLOR=#666666]3907029168[/COLOR] sectors
Disk sde: [COLOR=#666666]1[/COLOR].82 TiB, [COLOR=#666666]2000398934016[/COLOR] bytes, [COLOR=#666666]3907029168[/COLOR] sectors
Disk sdf: [COLOR=#666666]14[/COLOR].88 GiB, [COLOR=#666666]15971909632[/COLOR] bytes, [COLOR=#666666]31195136[/COLOR] sectors
Disk identifier: 0x146975c6
      Boot Start      End  Sectors  Size Id Type
sdf1  *     [COLOR=#666666]2048[/COLOR] [COLOR=#666666]31195135[/COLOR] [COLOR=#666666]31193088[/COLOR] [COLOR=#666666]14[/COLOR].9G  c W95 FAT32 [COLOR=#666666]([/COLOR]LBA[COLOR=#666666])[/COLOR]

parted -lm [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: _________________________________________________________

sda:60.0GB:scsi:512:512:gpt:ATA KINGSTON SV300S3:;
[COLOR=#666666]1[/COLOR]:1049kB:2097kB:1049kB:::bios_grub;
sdb:2000GB:scsi:512:4096:unknown:ATA ST2000DM006-2DM1:;
sdc:2000GB:scsi:512:4096:unknown:ATA ST2000DM001-1ER1:;
sdd:2000GB:scsi:512:4096:unknown:ATA ST2000DM001-9YN1:;
sde:2000GB:scsi:512:4096:unknown:ATA ST2000DM001-9YN1:;
sdf:16.0GB:scsi:512:512:msdos:Kingston DT [COLOR=#666666]101[/COLOR] G2:;
[COLOR=#666666]1[/COLOR]:1049kB:16.0GB:16.0GB:fat32::boot, lba;

Free space >10MiB: ______________________________________________________________

sda: [COLOR=#666666]2[/COLOR].00MiB:57242MiB:57240MiB

blkid [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ______________________________________________________________

NAME   FSTYPE            UUID                                 PARTUUID                             LABEL           PARTLABEL
sda                                                                                                                
&#9492;&#9472;sda1                                                        68d66628-672e-4cdf-ada7-3e468f48123c                 
sdb    linux_raid_member 6a791c8c-0fe9-764e-d07b-23aa7ccc3316                                      ubuntu-server:0 
&#9492;&#9472;md0                                                                                                              
sdc    linux_raid_member 6a791c8c-0fe9-764e-d07b-23aa7ccc3316                                      ubuntu-server:0 
&#9492;&#9472;md0                                                                                                              
sdd    linux_raid_member 6a791c8c-0fe9-764e-d07b-23aa7ccc3316                                      ubuntu-server:0 
&#9492;&#9472;md0                                                                                                              
sde    linux_raid_member 6a791c8c-0fe9-764e-d07b-23aa7ccc3316                                      ubuntu-server:0 
&#9492;&#9472;md0                                                                                                              
sdf                                                                                                                
&#9492;&#9472;sdf1 vfat              [COLOR=#666666]5095[/COLOR]-256B                            146975c6-01                          UBUNTU 22_0     

Mount points [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: _______________________________________________________

                        Avail Use% Mounted on
/dev/sdf1               [COLOR=#666666]11[/COLOR].5G  [COLOR=#666666]23[/COLOR]% /cdrom

Mount options [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ______________________________________________________

/dev/sdf1              vfat            ro,noatime,fmask[COLOR=#666666]=[/COLOR][COLOR=#666666]0022[/COLOR],dmask[COLOR=#666666]=[/COLOR][COLOR=#666666]0022[/COLOR],codepage[COLOR=#666666]=[/COLOR][COLOR=#666666]437[/COLOR],iocharset[COLOR=#666666]=[/COLOR]iso8859-1,shortname[COLOR=#666666]=[/COLOR]mixed,errors[COLOR=#666666]=[/COLOR]remount-ro

[COLOR=#666666]======================[/COLOR] sdf1/boot/grub/grub.cfg [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]======================[/COLOR]

Try or Install Ubuntu
Ubuntu [COLOR=#666666]([/COLOR]safe graphics[COLOR=#666666])[/COLOR]
OEM install [COLOR=#666666]([/COLOR][COLOR=#AA22FF]**for**[/COLOR] manufacturers[COLOR=#666666])[/COLOR]
Boot from next volume
UEFI Firmware Settings
Test [COLOR=#B8860B]memory[/COLOR]

[COLOR=#666666]====================[/COLOR] sdf1: Location of files loaded by [COLOR=#B8860B]Grub[/COLOR] [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]
            ?? [COLOR=#666666]=[/COLOR] ??             boot/grub/grub.cfg                             [COLOR=#B8860B]1[/COLOR]

[COLOR=#666666]========================[/COLOR] Unknown MBRs/Boot Sectors/etc [COLOR=#666666]=========================[/COLOR]

Unknown BootLoader on [COLOR=#B8860B]md0[/COLOR]



[COLOR=#666666]=================================[/COLOR] User [COLOR=#B8860B]choice[/COLOR] [COLOR=#666666]==================================[/COLOR]

[COLOR=#666666][[/COLOR]dmraid[COLOR=#666666]][/COLOR] packages may interfere with MDraid. Do you want to remove them? [COLOR=#B8860B]yes[/COLOR]


[COLOR=#666666]===================[/COLOR] blkid [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] before raid [COLOR=#B8860B]activation[/COLOR] [COLOR=#666666]====================[/COLOR]

/dev/sdb: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"6a791c8c-0fe9-764e-d07b-23aa7ccc3316"[/COLOR] [COLOR=#B8860B]UUID_SUB[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"26a25efd-2eb7-d9a1-e310-d4c3662f3c88"[/COLOR] [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ubuntu-server:0"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"linux_raid_member"[/COLOR]
/dev/sdc: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"6a791c8c-0fe9-764e-d07b-23aa7ccc3316"[/COLOR] [COLOR=#B8860B]UUID_SUB[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"c33e2aa9-3105-85de-2751-ef43be92516e"[/COLOR] [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ubuntu-server:0"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"linux_raid_member"[/COLOR]
/dev/sdd: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"6a791c8c-0fe9-764e-d07b-23aa7ccc3316"[/COLOR] [COLOR=#B8860B]UUID_SUB[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"7c316348-1565-b64d-30c0-90f03d9ddd16"[/COLOR] [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ubuntu-server:0"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"linux_raid_member"[/COLOR]
/dev/sde: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"6a791c8c-0fe9-764e-d07b-23aa7ccc3316"[/COLOR] [COLOR=#B8860B]UUID_SUB[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"1502c82e-4085-6393-12d5-0adb7a52f7fd"[/COLOR] [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ubuntu-server:0"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"linux_raid_member"[/COLOR]
/dev/sdf1: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"UBUNTU 22_0"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"5095-256B"[/COLOR] [COLOR=#B8860B]BLOCK_SIZE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"512"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"vfat"[/COLOR] [COLOR=#B8860B]PARTUUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"146975c6-01"[/COLOR]
/dev/sda1: [COLOR=#B8860B]PARTUUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"68d66628-672e-4cdf-ada7-3e468f48123c"[/COLOR]


[COLOR=#666666]====================================[/COLOR] [COLOR=#B8860B]dmraid[/COLOR] [COLOR=#666666]====================================[/COLOR]

dmraid -si -c
no raid disks
No DMRAID disk.
apt-get remove -y dmraid
Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be REMOVED:
  dmraid
[COLOR=#666666]0[/COLOR] upgraded, [COLOR=#666666]0[/COLOR] newly installed, [COLOR=#666666]1[/COLOR] to remove and [COLOR=#666666]239[/COLOR] not upgraded.
After this operation, [COLOR=#666666]101[/COLOR] kB disk space will be freed.
[COLOR=#666666]([/COLOR]Reading database ... 
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]5[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]10[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]15[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]20[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]25[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]30[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]35[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]40[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]45[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]50[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]55[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]60[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]65[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]70[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]75[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]80[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]85[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]90[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]95[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]100[/COLOR]%
[COLOR=#666666]([/COLOR]Reading database ... [COLOR=#666666]207281[/COLOR] files and directories currently installed.[COLOR=#666666])[/COLOR]
Removing dmraid [COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR].0.0.rc16-10ubuntu2[COLOR=#666666])[/COLOR] ...
update-initramfs is disabled since running on read-only media
Processing triggers [COLOR=#AA22FF]**for**[/COLOR] man-db [COLOR=#666666]([/COLOR][COLOR=#666666]2[/COLOR].10.2-1[COLOR=#666666])[/COLOR] ...


[COLOR=#666666]====================================[/COLOR] [COLOR=#B8860B]mdadm[/COLOR] [COLOR=#666666]=====================================[/COLOR]
mdadm --assemble --scan

mdadm --detail --scan

Warning: no active raid [COLOR=#666666]([/COLOR]DMRAID nor MD_ARRAY[COLOR=#666666])[/COLOR].
No active RAID.


Suggested repair: ______________________________________________________________
 [COLOR=#111111][FONT=monospace]The default repair of the Boot-Repair utility would not act on the boot.[/FONT][/COLOR]
```

---

### Post by ActionParsnip on 2022-06-30
I suggest you boot to live CD / USB and run a full fsck on all internal partitions (that are Linux based). Make sure the file systems are healthy

---

### Post by edie209 on 2022-07-01
Thanks for the reply I have tried this twice now hence the delay in replying.

My boot disk is sda
                           sd1

I get a bad magic number you might try running e2fsck with an alternative superblock (well out of my comfort zone now) 

I run e2fsck -b 8193 /dev/sda   and get  the superblock could not be read or does not describe a valid  ext2/ext3/ext4 filesystem

If I was to reinstall the os on the boot drive could I re-attach the raid with the data is there anything I would need from the boot drive?

---

### Post by ActionParsnip on 2022-07-01
If the boot disks is efi based then just move on and fsck the rest

---

### Post by oldfred on 2022-07-01
Since you attached the link to Boot-Repair you did not need to post it.
And please use Code tags with text or terminal output.

The fsck or e2fsck commands are for ext4 or other ext formatted partitions. Other formats use different tools.
For the ESP, there is dosfsck which is for FAT32 formatted partition.

Normally you specify partitions like sda2 not drives like sda for fsck, but I do not know RAID nor if command is then different.
Are your drives not then partitioned?

You do have good backups?
RAID is for uptime, primary used with servers.

I do not know nor use RAID:
[https://www.smallnetbuilder.com/archives/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](https://www.smallnetbuilder.com/archives/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by edie209 on 2022-07-03
Thanks for your help but I was still unable to get anything to work someone suggested I look into my bios and the sata setting had changed I corrected this and it is now up and running.

---

