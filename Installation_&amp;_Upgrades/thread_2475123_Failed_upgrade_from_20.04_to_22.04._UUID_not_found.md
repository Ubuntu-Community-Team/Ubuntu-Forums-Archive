---
title: "Failed upgrade from 20.04 to 22.04. UUID not found."
date: 2022-05-17
forum: Installation &amp; Upgrades
---

### Post by stev on 2022-05-17
I tried an automatic upgrade from Ubuntu 20.04 to 22.04 and received an error on reboot that the UUID was not found. blkid displayed that they were, indeed, different. Because of the error, I am dropped into a shell and I can't figure out how to edit the fstab file from the shell to change the UUID to the correct value. Can anyone point me in the right direction?
Thanks,
Steve

---

### Post by Bashing-om on 2022-05-17
stev; Hello and Welcome to the Forum :D

Like anything else - making this edit is simple - once you have done it a few times.
Basically; one just mounts the target partition in a made up mount point, open a text editor (with root privileges)  and edit that /etc/fstab file to the desired value.

To help us assist you please post back -between code tags - from the liveUSB (installer in the "try ubuntu" mode) the out puts of terminal commands (ctl+alt+T to activate a terminal):
```

sudo fdisk -lu
sudo blkid
echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

These so we know what editor is available to you and the target to direct you you to.

[INDENT]easy as falling out of bed wide awake
[/INDENT]

---

### Post by stev on 2022-05-18
```

ubuntu@ubuntu:~$ sudo fdisk -lu
Disk /dev/loop0: 2.33 GiB, 2502324224 bytes, 4887352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 61.89 MiB, 64901120 bytes, 126760 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 248.76 MiB, 260841472 bytes, 509456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 155.63 MiB, 163188736 bytes, 318728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 45.86 MiB, 48087040 bytes, 93920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 43.63 MiB, 45748224 bytes, 89352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 284 KiB, 290816 bytes, 568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
GPT PMBR size mismatch (976767239 != 976773167) will be corrected by write.
The backup GPT table is not on the end of the device.


Disk /dev/sda: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: ST500DM002-1BD14
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 153B8960-3551-4F98-96D0-81B79F1766E8

Device       Start       End   Sectors   Size Type
/dev/sda1     2048      4095      2048     1M BIOS boot
/dev/sda2     4096   1054719   1050624   513M EFI System
/dev/sda3  1054720 976767206 975712487 465.3G Linux filesystem
GPT PMBR size mismatch (976767239 != 976773167) will be corrected by write.
The backup GPT table is not on the end of the device.


Disk /dev/sdb: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: ST500DM002-1BD14
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 153B8960-3551-4F98-96D0-81B79F1766E8

Device       Start       End   Sectors   Size Type
/dev/sdb1     2048      4095      2048     1M BIOS boot
/dev/sdb2     4096   1054719   1050624   513M EFI System
/dev/sdb3  1054720 976767206 975712487 465.3G Linux filesystem


Disk /dev/mapper/isw_ebjgdefagi_Volume1: 465.76 GiB, 500104826880 bytes, 976767240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 153B8960-3551-4F98-96D0-81B79F1766E8

Device                                     Start       End   Sectors   Size Type
/dev/mapper/isw_ebjgdefagi_Volume1-part1    2048      4095      2048     1M BIOS boot
/dev/mapper/isw_ebjgdefagi_Volume1-part2    4096   1054719   1050624   513M EFI System
/dev/mapper/isw_ebjgdefagi_Volume1-part3 1054720 976767206 975712487 465.3G Linux filesystem


Disk /dev/sdg: 14.45 GiB, 15510536192 bytes, 30294016 sectors
Disk model: USB 2.0 FD      
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A09DB2B8-B5F6-43AE-AFB3-91E0A90189A1

Device       Start      End  Sectors  Size Type
/dev/sdg1       64  7129427  7129364  3.4G Microsoft basic data
/dev/sdg2  7129428  7137923     8496  4.1M EFI System
/dev/sdg3  7137924  7138523      600  300K Microsoft basic data
/dev/sdg4  7139328 30293952 23154625   11G Linux filesystem


Disk /dev/loop8: 81.26 MiB, 85209088 bytes, 166424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo blkid
/dev/sda: TYPE="isw_raid_member"
/dev/sdb: TYPE="isw_raid_member"
/dev/sdg1: BLOCK_SIZE="2048" UUID="2022-04-19-10-23-19-00" LABEL="Ubuntu 22.04 LTS amd64" TYPE="iso9660" PARTLABEL="ISO9660" PARTUUID="a09db2b8-b5f6-43ae-afb2-91e0a90189a1"
/dev/loop1: TYPE="squashfs"
/dev/loop8: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/sdg3: PARTLABEL="Gap1" PARTUUID="a09db2b8-b5f6-43ae-afb0-91e0a90189a1"
/dev/sdg4: LABEL="writable" UUID="53209734-4bd5-4f2c-bb93-0c33e362a907" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="e34a7033-7b5c-cb42-b024-01fde314a6a8"
/dev/sdg2: SEC_TYPE="msdos" LABEL_FATBOOT="ESP" LABEL="ESP" UUID="8D6C-A9F8" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="Appended2" PARTUUID="a09db2b8-b5f6-43ae-afb1-91e0a90189a1"
/dev/loop0: TYPE="squashfs"
/dev/mapper/isw_ebjgdefagi_Volume1: PTUUID="153b8960-3551-4f98-96d0-81b79f1766e8" PTTYPE="gpt"
/dev/loop7: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
ubuntu@ubuntu:~$ 


ubuntu@ubuntu:~$ echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
ubuntu   ubuntu:GNOME
ubuntu@ubuntu


```

Thanks!

---

### Post by Bashing-om on 2022-05-18
stev; Ouch on me :(

I have no experience with LVM/encryption - I can not further aid you. Others here who do hopefully will chime in and guide.

I do see too:
> 
GPT PMBR size mismatch (976767239 != 976773167) will be corrected by write.
[color=red]The backup GPT table is not on the end of the device[/color].

that might possibly be of great concern - but again I do not know!

[INDENT][INDENT]a know-it-all I am not
[/INDENT][/INDENT]

---

### Post by stev on 2022-05-18
Thanks for the replies. I appreciate the help.

---

### Post by TheFu on 2022-05-18
That doesn't look like LVM or encryption to me.  Don't know what it is.
LVM+ LUKS encryption looks like this:

```
$ lsblk (with lots of options in an alias that I've posted 50 times to these forums)
NAME                  SIZE TYPE  FSTYPE      MOUNTPOINT
sda                 465.8G disk            
&#9500;&#9472;sda1                512M part  vfat        /boot/efi
&#9500;&#9472;sda2                732M part  ext2        /boot
&#9492;&#9472;sda3              464.6G part  crypto_LUKS 
  &#9492;&#9472;sda3_crypt      464.6G crypt LVM2_member 
    &#9500;&#9472;vg00-root        25G lvm   ext4        /
    &#9500;&#9472;vg00-swap_1     4.5G lvm   swap        [SWAP]
    &#9500;&#9472;vg00-home--lv    75G lvm   ext4        /home
    &#9492;&#9472;vg00-stuff      100G lvm   ext4        /stuff

```

Seeing the /etc/fstab file posted could answer that question.

---

