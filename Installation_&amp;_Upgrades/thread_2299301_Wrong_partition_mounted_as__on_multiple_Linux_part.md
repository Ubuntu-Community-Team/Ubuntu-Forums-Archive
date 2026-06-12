---
title: "Wrong partition mounted as / on multiple Linux partitions disk"
date: 2015-10-17
forum: Installation &amp; Upgrades
---

### Post by deepakdeshp on 2015-10-17
Hello,
I have multiple Linux distros and WIndows installed in EFI mode. But when I boot from sda13 sda12 or sda10 , sda13 is getting mounted as /. I had tried Cloneziall restore on sda13. Also had copied the partition sda13 to sda10 and sda10 using gparted. I was getting same UUID for sda10 sda12 and sda13.  How do I get sda12 to mount as / when I boot sda12 from GRUB?


[LIST]
[*]I generated new UUIDs for sda10 and sda12 with uuidgen.
I assigned the uuids to sda10 and sda12 with command tune2fs /dev/sda12 -U (newly generated UUID for sda12. 
I edited fstab in sda12 and changed the UUID for /
[/LIST]
```
$blkid -o full -s UUID

/dev/sda1: UUID="825E58295E5817ED" 
/dev/sda2: UUID="3446-8563" 
/dev/sda4: UUID="C8CA93C9CA93B264" 
/dev/sda5: UUID="442863B02863A022" 
/dev/sda6: UUID="9C2858B52858905E" 
/dev/sda8: UUID="103cbf83-409c-43a6-8e92-1cb7e49ee29a" 
/dev/sda9: UUID="a382f57f-6887-4124-b6b4-20a9f4a6255a" 
/dev/sda10: UUID="afc80bf2-4b55-4455-acae-bd4711ea8c3b" 
/dev/sda11: UUID="9c996a65-a267-40ae-96f3-78dee1af3643" 
/dev/sda12: UUID="709441e6-eae8-4243-a4c0-981629fec9ae" 
/dev/sda13: UUID="378069b3-76f5-41ba-bea2-ff986413e8e3" 
/dev/sdb1: UUID="FC19-830E"

update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.2.0-040200-generic
Found initrd image: /boot/initrd.img-4.2.0-040200-generic
  No volume groups found
Found Linux Mint 17.2 Rafaela (17.2) on /dev/sda10
Found Ubuntu 14.04.3 LTS (14.04) on /dev/sda11
Found Linux Mint 17.2 Rafaela (17.2) on /dev/sda12
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Found Kali GNU/Linux 2.0 (2.0) on /dev/sda9
Adding boot menu entry for EFI firmware configuration
done

#mount /dev/sda12 /mnt
 # cat /mnt/etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
#UUID=378069b3-76f5-41ba-bea2-ff986413e8e3 /               ext4    errors=remount-ro 0       1
UUID=709441e6-eae8-4243-a4c0-981629fec9ae /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
#UUID=3446-8563  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda8 during installation
UUID=426b29fc-870b-4230-b20e-a4f321207152 none            swap    sw              0       0
UUID=3446-8563   /boot/efi   vfat   defaults   0   1
```

---

### Post by sudodus on 2015-10-17
You seem to have the correct UUID for the root partition, but there is no partition with the UUID for swap in fstab.

You need to change the swap UUID too, or if you prefer, change the entry in fstab to match the UUID of the swap partition. I cannot see which is the swap partition, or even if there is one. It was /dev/sda8 when the fstab file was created, but it could have changed, so please check, for example with the following command

```
sudo blkid|grep swap
```

---

### Post by oldfred on 2015-10-17
With gpt you are not supposed to copy partitions, better to create new partition and copy data, and update fstab and grub with new UUID. Or just do another install, and copy /home, list of apps to reinstall and maybe some settings from /etc. If reasonably high speed Internet a new install can be quicker than all the changes required copying an install.

Gpt(GUID) also has internal GUIDs that must not be duplicated just like UUIDs cannot be duplicated.

---

### Post by deepakdeshp on 2015-10-17
> **sudodus said:**
> You seem to have the correct UUID for the root partition, but there is no partition with the UUID for swap in fstab.

You need to change the swap UUID too, or if you prefer, change the entry in fstab to match the UUID of the swap partition. I cannot see which is the swap partition, or even if there is one. It was /dev/sda8 when the fstab file was created, but it could have changed, so please check, for example with the following command

```
sudo blkid|grep swap
```

Thank you. The swap problem is fixed now** .I had created new partitions . That may be the reason the sda08 and possibly sda10 and sda12 UUID changed**. There was no swap as seen by the free command below . I changed the UUID of swap to the sda08 current UUID in  fstab. After swapon -a command swap was effective. 

In my first post  I have tried to fix the issue with generating new  UUID for sda10 and sda12. I changed the fstab entry to reflect the new UUIDs for sda10 and sda12. I am either missing something or  there is some error. The result is that , booting from sda10,sda12 and sda13 all cause sda13 mounted at /.  I have spent considerable time on this issue but without any success
```
#sudo blkid|grep swap/dev/sda8: UUID="103cbf83-409c-43a6-8e92-1cb7e49ee29a" TYPE="swap" 


#free
             total       used       free     shared    buffers     cached
Mem:       3475124    3207460     267664      90056      85100    1062540
-/+ buffers/cache:    2059820    1415304
Swap:            0          0          0
uma-HP-Notebook ~ # swapon -a
uma-HP-Notebook ~ # free
             total       used       free     shared    buffers     cached
Mem:       3475124    3208880     266244      90056      85152    1063116
-/+ buffers/cache:    2060612    1414512
Swap:      5226492          0    5226492
```

---

### Post by deepakdeshp on 2015-10-17
When I boot from sda12 sda13 is mounted as / . There is different software installed in the Mint 17 in sda12. Can I use the software in sda12 if I chroot to sda12? Similarly can I upgrade packages in sda12 after chroot to sda12?

---

### Post by sudodus on 2015-10-17
I can't see what is wrong now, but I have confidence that oldfred can help you :-)

Maybe you can use [Boot Repair](https://help.ubuntu.com/community/Boot-Repair) to ***write a BootInfo summary*** and paste the link it in a reply. Do not let it repair now. Wait for a reply from here.

---

### Post by deepakdeshp on 2015-10-17
The boot-info is run and available at [http://paste2.org/VUGVmmBv](http://paste2.org/VUGVmmBv)   :D

---

### Post by sudodus on 2015-10-17
```
sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 17.2 Rafaela 
    [COLOR="#FF0000"]Boot files:     [/COLOR]   

sda13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 17.2 Rafaela 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

```

The first 'heads up' I find is, that no boot files are found in /dev/sda12 (in contrast to /dev/sda13)

---

### Post by sudodus on 2015-10-17
```
=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to sign-grub fix customized files) and reinstall the grub-efi-amd64-signed of sda13, using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file  restore-efi-backups


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda (500GB) disk!

The boot files of [The OS now in use - Linux Mint 17.2 Rafaela] are far from the start of the disk.
Your BIOS may not detect them. You may want to retry after creating a /boot partition
(EXT4, >200MB, start of the disk). This can be performed via tools such as gParted.
Then select this partition via the [Separate /boot partition:] option of [Boot Repair].
(https://help.ubuntu.com/community/BootPartition)

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\...\grub*.efi

```

Have a look at this 'automatic analysis' by Boot Repair while waiting for a comment from oldfred.

---

### Post by deepakdeshp on 2015-10-17
> **sudodus said:**
> ```
sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 17.2 Rafaela 
    [COLOR=#FF0000]Boot files:     [/COLOR]   

sda13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 17.2 Rafaela 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

```

The first 'heads up' I find is, that no boot files are found in /dev/sda12 (in contrast to /dev/sda13)

Grub has detected Mint 17.2 in sda12.

```
sudo mount /dev/sda12 /mnt[sudo] password for uma: 
uma@uma-HP-Notebook / $ ls -l /mnt/boot
total 39012
-rw-r--r-- 1 root root  1283944 Aug 31 01:10 abi-4.2.0-040200-generic
-rw-r--r-- 1 root root   183782 Aug 31 01:10 config-4.2.0-040200-generic
drwxr-xr-x 2 root root     4096 Aug  9 17:14 efi
drwxr-xr-x 6 root root     4096 Sep 19 13:37 grub
-rw-r--r-- 1 root root 27505066 Sep 23 02:06 initrd.img-4.2.0-040200-generic
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3731831 Aug 31 01:10 System.map-4.2.0-040200-generic
-rw------- 1 root root  6681680 Aug 31 01:10 vmlinuz-4.2.0-040200-generic



```

---

### Post by oldfred on 2015-10-17
Did you leave Windows hibernated?
> Failed to mount '/dev/sda4': Operation not permitted

 	The NTFS partition is in an unsafe state. Please resume and shutdown
 	Windows fully (no hibernation or fast restarting), or mount the volume
 	read-only with the 'ro' mount option.
 	mount -t ntfs-3g -o remove_hiberfile /dev/sda4 /mnt/boot-sav/sda4
Boot Windows directly from UEFI and turn off fast startup or its always on hibernation.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

If you copied partitions you may have duplicate GUID which also is not allowed, but I only know how to see one at a time. Perhaps gdisk's verify will show issues?

sudo gdisk /dev/sda
You will get into advanced mode,
Use v to verify, i to list details of one partition(compare GUID with GUID of one you copied) and q to exit.
       
 [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

Ubuntu only boots from one entry in UEFI. Boot-Repairs summary report does not show the grub.cfg in /EFI/ubuntu. Post that, it should be a 3 line configfile entry to the UUID that you boot, so we know which partition's grub.cfg is the one used.

Why the copies of the same system? I install multiple versions of Ubuntu but not exactly the same anyway?

---

### Post by deepakdeshp on 2015-10-17
Windows did not shut down cleanly which would have caused the problem. There is no problem with Windows as such. Should I reboot Windows cleanly and again run boot-repair?

```
sudo gdisk /dev/sda[sudo] password for uma: 
GPT fdisk (gdisk) version 0.8.8


Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present


Found valid GPT with protective MBR; using GPT.


Command (? for help): v


No problems found. 103340013 free sectors (49.3 GiB) available in 4
segments, the largest of which is 61440000 (29.3 GiB) in size.
Command (? for help): i
Partition number (1-13): 13
Partition GUID code: 0FC63DAF-8483-4772-8E79-3D69D8477DE4 (Linux filesystem)
Partition unique GUID: 865E0BAF-C04E-480C-A5BD-999B8EAFEBD5
First sector: 361596928 (at 172.4 GiB)
Last sector: 443516927 (at 211.5 GiB)
Partition size: 81920000 sectors (39.1 GiB)
Attribute flags: 0000000000000000
Partition name: ''


Command (? for help): i 12
Partition number (1-13): 12
Partition GUID code: 0FC63DAF-8483-4772-8E79-3D69D8477DE4 (Linux filesystem)
Partition unique GUID: CBBC761C-7D9A-4771-941D-3BCB9A652DB1
First sector: 571676672 (at 272.6 GiB)
Last sector: 676124671 (at 322.4 GiB)
Partition size: 104448000 sectors (49.8 GiB)
Attribute flags: 0000000000000000
Partition name: ''


Command (? for help): i
Partition number (1-13): 10
Partition GUID code: 0FC63DAF-8483-4772-8E79-3D69D8477DE4 (Linux filesystem)
Partition unique GUID: 49752AE2-AB54-4228-8420-1472EDFB7B69
First sector: 443516928 (at 211.5 GiB)
Last sector: 571676671 (at 272.6 GiB)
Partition size: 128159744 sectors (61.1 GiB)
Attribute flags: 0000000000000000
Partition name: ''




```

[COLOR=#ff0000]GUID code of all the 3 partitions sda10 sda12 and sda13 are same[/COLOR]. All are Linux Mint / partitions.
sda13 Mint is the first entry in my grub booting menu. So will this be the partition from which grub.cfg is being used?

I am using 3 copies of Mint to ensure that when I try out things with one partition and if something goes wrong, I will use the other good partition rather than try to recover from the error.
Is there a better way to do it? One way I know is backup the partition using Clonezilla

---

### Post by LostFarmer on 2015-10-17
from your boor-repair:

```
menuentry "Linux Mint 17.2 Cinnamon 64-bit" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-378069b3-76f5-41ba-bea2-ff986413e8e3' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt10'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  [COLOR=#ff0000]378069b3-76f5-41ba-bea2-ff986413e8e3[/COLOR]
    else
      search --no-floppy --fs-uuid --set=root [COLOR=#ff0000]378069b3-76f5-41ba-bea2-ff986413e8e3[/COLOR]
    fi
    linux    /boot/vmlinuz-4.2.0-040200-generic.old root=UUID=[COLOR=#ff0000]378069b3-76f5-41ba-bea2-ff986413e8e3[/COLOR] ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.2.0-040200-generic
}

menuentry "Linux Mint 17.2 Rafaela (17.2) (on /dev/sda12)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-378069b3-76f5-41ba-bea2-ff986413e8e3' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt12 --hint-efi=hd0,gpt12 --hint-baremetal=ahci0,gpt12  [COLOR=#ff0000]378069b3-76f5-41ba-bea2-ff986413e8e3[/COLOR]
    else
      search --no-floppy --fs-uuid --set=root [COLOR=#ff0000]378069b3-76f5-41ba-bea2-ff986413e8e3[/COLOR]
    fi
    linux /boot/vmlinuz-4.2.0-040200-generic root=UUID=[COLOR=#ff0000]378069b3-76f5-41ba-bea2-ff986413e8e3[/COLOR] ro quiet splash $vt_handoff
    initrd /boot/initrd.img-4.2.0-040200-generic
}
```

The uuid's for the above entries are that of sda13.  
You must once again rerun "update-grub" from the linux in control of the boot process.

If you are not sure which linux is in charge of the boot process , look at "/boot/efi/EFI/ubuntu/grub.cfg" and check what uuid is listed for controlling linux.

---

### Post by oldfred on 2015-10-17
The unique GUID are different. The GUID is the type of partion which as a data partition will be the same.
       [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

I have just installed a second or third time. It is pretty quick to install again.

---

### Post by deepakdeshp on 2015-10-17
I will run update-grub from all my Linux partitions

> **LostFarmer said:**
> from your boor-repair:

```
menuentry "Linux Mint 17.2 Cinnamon 64-bit" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-378069b3-76f5-41ba-bea2-ff986413e8e3' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt10'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  [COLOR=#ff0000]378069b3-76f5-41ba-bea2-ff986413e8e3[/COLOR]
    else
      search --no-floppy --fs-uuid --set=root [COLOR=#ff0000]378069b3-76f5-41ba-bea2-ff986413e8e3[/COLOR]
    fi
    linux    /boot/vmlinuz-4.2.0-040200-generic.old root=UUID=[COLOR=#ff0000]378069b3-76f5-41ba-bea2-ff986413e8e3[/COLOR] ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.2.0-040200-generic
}

menuentry "Linux Mint 17.2 Rafaela (17.2) (on /dev/sda12)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-378069b3-76f5-41ba-bea2-ff986413e8e3' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt12 --hint-efi=hd0,gpt12 --hint-baremetal=ahci0,gpt12  [COLOR=#ff0000]378069b3-76f5-41ba-bea2-ff986413e8e3[/COLOR]
    else
      search --no-floppy --fs-uuid --set=root [COLOR=#ff0000]378069b3-76f5-41ba-bea2-ff986413e8e3[/COLOR]
    fi
    linux /boot/vmlinuz-4.2.0-040200-generic root=UUID=[COLOR=#ff0000]378069b3-76f5-41ba-bea2-ff986413e8e3[/COLOR] ro quiet splash $vt_handoff
    initrd /boot/initrd.img-4.2.0-040200-generic
}
```

The uuid's for the above entries are that of sda13.  
You must once again rerun "update-grub" from the linux in control of the boot process.

If you are not sure which linux is in charge of the boot process , look at "/boot/efi/EFI/ubuntu/grub.cfg" and check what uuid is listed for controlling linux.

I ran update-grub after booting from sda10,sda12 and sda13(ran the command 3 times). After this the boot-repair is available at [http://paste2.org/Xy23L9BV.Butt](http://paste2.org/Xy23L9BV.Butt) there is no change as shown in code below. sda10 again shows UUID for sda13.



```

[LIST=|INDENT=1]
[*][FONT=inherit][COLOR=#408080][FONT=inherit]*### BEGIN /etc/grub.d/30_os-prober ###*[/FONT][/COLOR][/FONT]

[*][FONT=inherit]menuentry [COLOR=#BA2121][FONT=inherit]'Linux Mint 17.2 Rafaela (17.2) (on /dev/sda10)'[/FONT][/COLOR] --class gnu-linux --class gnu --class os [COLOR=#19177C][FONT=inherit]$menuentry_id_option[/FONT][/COLOR] [COLOR=#BA2121][FONT=inherit]'osprober-gnulinux-simple-378069b3-76f5-41ba-bea2-ff986413e8e3'[/FONT][/COLOR] [COLOR=#666666][FONT=inherit]{[/FONT][/COLOR][/FONT]

[*][FONT=inherit]	insmod part_gpt[/FONT]

[*][FONT=inherit]	insmod ext2[/FONT]

[*][FONT=inherit]	[COLOR=#008000][FONT=inherit]set [/FONT][/COLOR][COLOR=#19177C][FONT=inherit]root[/FONT][/COLOR][COLOR=#666666][FONT=inherit]=[/FONT][/COLOR][COLOR=#BA2121][FONT=inherit]'hd0,gpt10'[/FONT][/COLOR][/FONT]

[*][FONT=inherit]	[COLOR=#008000][FONT=inherit]**if**[/FONT][/COLOR] [COLOR=#666666][FONT=inherit][[/FONT][/COLOR] x[COLOR=#19177C][FONT=inherit]$feature_platform_search_hint[/FONT][/COLOR] [COLOR=#666666][FONT=inherit]=[/FONT][/COLOR] xy [COLOR=#666666][FONT=inherit]][/FONT][/COLOR][FONT=inherit];[/FONT] [COLOR=#008000][FONT=inherit]**then**[/FONT][/COLOR][/FONT]

[*][FONT=inherit]	  search --no-floppy --fs-uuid --set[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]root --hint-bios[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]hd0,gpt10 --hint-efi[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]hd0,gpt10 --hint-baremetal[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]ahci0,gpt10  378069b3-76f5-41ba-bea2-ff986413e8e3[/FONT]

[*][FONT=inherit]	[COLOR=#008000][FONT=inherit]**else**[/FONT][/COLOR][/FONT]

[*][FONT=inherit]	  search --no-floppy --fs-uuid --set[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]root 378069b3-76f5-41ba-bea2-ff986413e8e3[/FONT]

[*][FONT=inherit]	[COLOR=#008000][FONT=inherit]**fi**[/FONT][/COLOR][/FONT]

[*][FONT=inherit]	linux /boot/vmlinuz-4.2.0-040200-generic [COLOR=#19177C][FONT=inherit]root[/FONT][/COLOR][COLOR=#666666][FONT=inherit]=[/FONT][/COLOR][COLOR=#19177C][FONT=inherit]UUID[/FONT][/COLOR][COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]378069b3-76f5-41ba-bea2-ff986413e8e3 ro quiet splash [COLOR=#19177C][FONT=inherit]$vt_handoff[/FONT][/COLOR][/FONT]

[*][FONT=inherit]	initrd /boot/initrd.img-4.2.0-040200-generic[/FONT]

[*][FONT=inherit][COLOR=#666666][FONT=inherit]}[/FONT][/COLOR][/FONT]

[*][FONT=inherit]submenu [COLOR=#BA2121][FONT=inherit]'Advanced options for Linux Mint 17.2 Rafaela (17.2) (on /dev/sda10)'[/FONT][/COLOR] [COLOR=#19177C][FONT=inherit]$menuentry_id_option[/FONT][/COLOR] [COLOR=#BA2121][FONT=inherit]'osprober-gnulinux-advanced-378069b3-76f5-41ba-bea2-ff986413e8e3'[/FONT][/COLOR] [COLOR=#666666][FONT=inherit]{[/FONT][/COLOR][/FONT]

[*][FONT=inherit]	menuentry [COLOR=#BA2121][FONT=inherit]'Linux Mint 17.2 Cinnamon 64-bit (on /dev/sda10)'[/FONT][/COLOR] --class gnu-linux --class gnu --class os [COLOR=#19177C][FONT=inherit]$menuentry_id_option[/FONT][/COLOR] [COLOR=#BA2121][FONT=inherit]'osprober-gnulinux-/boot/vmlinuz-4.2.0-040200-generic--378069b3-76f5-41ba-bea2-ff986413e8e3'[/FONT][/COLOR] [COLOR=#666666][FONT=inherit]{[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		insmod part_gpt[/FONT]

[*][FONT=inherit]		insmod ext2[/FONT]

[*][FONT=inherit]		[COLOR=#008000][FONT=inherit]set [/FONT][/COLOR][COLOR=#19177C][FONT=inherit]root[/FONT][/COLOR][COLOR=#666666][FONT=inherit]=[/FONT][/COLOR][COLOR=#BA2121][FONT=inherit]'hd0,gpt10'[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		[COLOR=#008000][FONT=inherit]**if**[/FONT][/COLOR] [COLOR=#666666][FONT=inherit][[/FONT][/COLOR] x[COLOR=#19177C][FONT=inherit]$feature_platform_search_hint[/FONT][/COLOR] [COLOR=#666666][FONT=inherit]=[/FONT][/COLOR] xy [COLOR=#666666][FONT=inherit]][/FONT][/COLOR][FONT=inherit];[/FONT] [COLOR=#008000][FONT=inherit]**then**[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		  search --no-floppy --fs-uuid --set[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]root --hint-bios[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]hd0,gpt10 --hint-efi[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]hd0,gpt10 --hint-baremetal[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]ahci0,gpt10  378069b3-76f5-41ba-bea2-ff986413e8e3[/FONT]

[*][FONT=inherit]		[COLOR=#008000][FONT=inherit]**else**[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		  search --no-floppy --fs-uuid --set[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]root 378069b3-76f5-41ba-bea2-ff986413e8e3[/FONT]

[*][FONT=inherit]		[COLOR=#008000][FONT=inherit]**fi**[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		linux /boot/vmlinuz-4.2.0-040200-generic [COLOR=#19177C][FONT=inherit]root[/FONT][/COLOR][COLOR=#666666][FONT=inherit]=[/FONT][/COLOR][COLOR=#19177C][FONT=inherit]UUID[/FONT][/COLOR][COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]378069b3-76f5-41ba-bea2-ff986413e8e3 ro quiet splash [COLOR=#19177C][FONT=inherit]$vt_handoff[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		initrd /boot/initrd.img-4.2.0-040200-generic[/FONT]

[*][FONT=inherit]	[COLOR=#666666][FONT=inherit]}[/FONT][/COLOR][/FONT]

[*][FONT=inherit]	menuentry [COLOR=#BA2121][FONT=inherit]'Linux Mint 17.2 Cinnamon 64-bit, with Linux 4.2.0-040200-generic (on /dev/sda10)'[/FONT][/COLOR] --class gnu-linux --class gnu --class os [COLOR=#19177C][FONT=inherit]$menuentry_id_option[/FONT][/COLOR] [COLOR=#BA2121][FONT=inherit]'osprober-gnulinux-/boot/vmlinuz-4.2.0-040200-generic--378069b3-76f5-41ba-bea2-ff986413e8e3'[/FONT][/COLOR] [COLOR=#666666][FONT=inherit]{[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		insmod part_gpt[/FONT]

[*][FONT=inherit]		insmod ext2[/FONT]

[*][FONT=inherit]		[COLOR=#008000][FONT=inherit]set [/FONT][/COLOR][COLOR=#19177C][FONT=inherit]root[/FONT][/COLOR][COLOR=#666666][FONT=inherit]=[/FONT][/COLOR][COLOR=#BA2121][FONT=inherit]'hd0,gpt10'[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		[COLOR=#008000][FONT=inherit]**if**[/FONT][/COLOR] [COLOR=#666666][FONT=inherit][[/FONT][/COLOR] x[COLOR=#19177C][FONT=inherit]$feature_platform_search_hint[/FONT][/COLOR] [COLOR=#666666][FONT=inherit]=[/FONT][/COLOR] xy [COLOR=#666666][FONT=inherit]][/FONT][/COLOR][FONT=inherit];[/FONT] [COLOR=#008000][FONT=inherit]**then**[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		  search --no-floppy --fs-uuid --set[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]root --hint-bios[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]hd0,gpt10 --hint-efi[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]hd0,gpt10 --hint-baremetal[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]ahci0,gpt10  378069b3-76f5-41ba-bea2-ff986413e8e3[/FONT]

[*][FONT=inherit]		[COLOR=#008000][FONT=inherit]**else**[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		  search --no-floppy --fs-uuid --set[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]root 378069b3-76f5-41ba-bea2-ff986413e8e3[/FONT]

[*][FONT=inherit]		[COLOR=#008000][FONT=inherit]**fi**[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		linux /boot/vmlinuz-4.2.0-040200-generic [COLOR=#19177C][FONT=inherit]root[/FONT][/COLOR][COLOR=#666666][FONT=inherit]=[/FONT][/COLOR][COLOR=#19177C][FONT=inherit]UUID[/FONT][/COLOR][COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]378069b3-76f5-41ba-bea2-ff986413e8e3 ro quiet splash [COLOR=#19177C][FONT=inherit]$vt_handoff[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		initrd /boot/initrd.img-4.2.0-040200-generic[/FONT]

[*][FONT=inherit]	[COLOR=#666666][FONT=inherit]}[/FONT][/COLOR][/FONT]

[*][FONT=inherit]	menuentry [COLOR=#BA2121][FONT=inherit]'Linux Mint 17.2 Cinnamon 64-bit, with Linux 4.2.0-040200-generic (recovery mode) (on /dev/sda10)'[/FONT][/COLOR] --class gnu-linux --class gnu --class os [COLOR=#19177C][FONT=inherit]$menuentry_id_option[/FONT][/COLOR] [COLOR=#BA2121][FONT=inherit]'osprober-gnulinux-/boot/vmlinuz-4.2.0-040200-generic-root=UUID=378069b3-76f5-41ba-bea2-ff986413e8e3 ro recovery nomodeset-378069b3-76f5-41ba-bea2-ff986413e8e3'[/FONT][/COLOR] [COLOR=#666666][FONT=inherit]{[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		insmod part_gpt[/FONT]

[*][FONT=inherit]		insmod ext2[/FONT]

[*][FONT=inherit]		[COLOR=#008000][FONT=inherit]set [/FONT][/COLOR][COLOR=#19177C][FONT=inherit]root[/FONT][/COLOR][COLOR=#666666][FONT=inherit]=[/FONT][/COLOR][COLOR=#BA2121][FONT=inherit]'hd0,gpt10'[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		[COLOR=#008000][FONT=inherit]**if**[/FONT][/COLOR] [COLOR=#666666][FONT=inherit][[/FONT][/COLOR] x[COLOR=#19177C][FONT=inherit]$feature_platform_search_hint[/FONT][/COLOR] [COLOR=#666666][FONT=inherit]=[/FONT][/COLOR] xy [COLOR=#666666][FONT=inherit]][/FONT][/COLOR][FONT=inherit];[/FONT] [COLOR=#008000][FONT=inherit]**then**[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		  search --no-floppy --fs-uuid --set[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]root --hint-bios[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]hd0,gpt10 --hint-efi[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]hd0,gpt10 --hint-baremetal[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]ahci0,gpt10  378069b3-76f5-41ba-bea2-ff986413e8e3[/FONT]

[*][FONT=inherit]		[COLOR=#008000][FONT=inherit]**else**[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		  search --no-floppy --fs-uuid --set[COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]root 378069b3-76f5-41ba-bea2-ff986413e8e3[/FONT]

[*][FONT=inherit]		[COLOR=#008000][FONT=inherit]**fi**[/FONT][/COLOR][/FONT]

[*][FONT=inherit]		linux /boot/vmlinuz-4.2.0-040200-generic [COLOR=#19177C][FONT=inherit]root[/FONT][/COLOR][COLOR=#666666][FONT=inherit]=[/FONT][/COLOR][COLOR=#19177C][FONT=inherit]UUID[/FONT][/COLOR][COLOR=#666666][FONT=inherit]=[/FONT][/COLOR]378069b3-76f5-41ba-bea2-ff986413e8e3 ro recovery nomodeset[/FONT]

[*][FONT=inherit]		initrd /boot/initrd.img-4.2.0-040200-generic[/FONT]

[*][FONT=inherit]	[COLOR=#666666][FONT=inherit]}[/FONT][/COLOR][/FONT]

[*][FONT=inherit][COLOR=#666666][FONT=inherit]}[/FONT][/COLOR][/FONT]
[/LIST]

```

> **oldfred said:**
> The unique GUID are different. The GUID is the type of partion which as a data partition will be the same.
       [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

I have just installed a second or third time. It is pretty quick to install again.

How do I install it again?

---

### Post by oldfred on 2015-10-18
I prefer to partition in advance with gparted.
And then just use Something else to choose the new partition as / (root). It will auto find swap.
If multiple installs and you want to share or get to same data in each install best to have a shared data partition which you can mount in each install.

       UEFI install,windows 8 with Something Else screen shots
[URL="http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html"]http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html
[/URL]
 Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

The small /EFI/ubuntu/grub.cfg will be overwritten with new install. So you can restore original from backup or if same version of grub, the only change is the UUID & partition number in the grub configfile which you can manually edit.

       
 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

    


[URL="http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html"]
[/URL]

---

### Post by deepakdeshp on 2015-10-18
> **oldfred said:**
> I prefer to partition in advance with gparted.
And then just use Something else to choose the new partition as / (root). It will auto find swap.
If multiple installs and you want to share or get to same data in each install best to have a shared data partition which you can mount in each install.


Thanks a lot .:D There is lot of useful information in the post. I dont have any data on any of the partitions. .  I just have various applications installed like I have virtual Box on which Ubuntu server runs.
Moodle, Drupal, running on server Al fresco , Eclipse etc installed on Mint and so on.

The main problem of mounting the correct partition as / , when I boot from different partitions is something for which I dont have any clue. I do not know how to proceed also .I had stated it in my first post. I am able to boot from all grub partitions as such but there is a / partition mismatch when I boot.

---

### Post by LostFarmer on 2015-10-18
looking at your last boot-repair:  out of the 5 grub.cfg 's only the one on sda10 is correct. All the others are wrong and will cause the problem you have.  You MUST run update-grub on the linux in control of the boot.  The linux in control will be the first boot menu entire.  

If that happens to be ubuntu on sda11, it looks like there is a added problem.  Its /ect/fstab list /home on a partition that is not in the system.  If ubuntu is the controlling linux and it is not bootable, I need to know.  (can copy /boot/grub/grub.cfg from sda10 to sda11) or (edit /boot/efi/EFI/ubuntu/grub.cfg so it points to sda10)

Running 'update-grub' on any other linux partition does not help.

---

### Post by oldfred on 2015-10-18
In post #15, you posted the grub.cfg from /EFI/ubuntu.
But it says sda10, but UUID is from sda13. You need to fix that so you know which partition you really are booting from. Grub primarily uses UUID, so default boot probably is sda13.

Which install is your main working install?
 You should update the /EFI/ubuntu/grub.cfg with the correct partition & UUID that you want to boot by default. And then boot the first entry in grub menu.

---

### Post by deepakdeshp on 2015-10-19
> **oldfred said:**
> In post #15, you posted the grub.cfg from /EFI/ubuntu.
But it says sda10, but UUID is from sda13. You need to fix that so you know which partition you really are booting from. Grub primarily uses UUID, so default boot probably is sda13.

Which install is your main working install?
 You should update the /EFI/ubuntu/grub.cfg with the correct partition & UUID that you want to boot by default. And then boot the first entry in grub menu.

Looks like sda13 is in control of the boot process as shown by below code. There is no /EFI/ubuntu/grub.cfg file . It is at another location and does not have entry for sda10.Please   below. All the code is from sda13a mounted as /

Looks like I need to change  /boot/grub/grub.cfg** ,, **But wont it be generated when I executed update-grub from sda13**?** I already did that.[B]Which file should I change ?
[/B]```

find . -name grub.cfg 
./media/uma/FC19-830E/EFI/boot/grub.cfg
./media/uma/FC19-830E/boot/grub/grub.cfg
./boot/grub/grub.cfg
./boot/efi/EFI/ubuntu/grub.cfg
./etc/grub.d/backup/boot_grub/grub.cfg
./usr/share/doc/grub-common/examples/grub.cfg
uma-HP-Notebook / # pwd
/
uma-HP-Notebook / # cat ./boot/efi/EFI/ubuntu/grub.cfg
search.fs_uuid 378069b3-76f5-41ba-bea2-ff986413e8e3 root hd0,gpt13 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
uma-HP-Notebook / # ^Cname grub.cfg 
uma-HP-Notebook / # more /etc/vfstab
/etc/vfstab: No such file or directory
uma-HP-Notebook / # more /etc/fstab
# /etc/fstab: static file system information.
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=378069b3-76f5-41ba-bea2-ff986413e8e3 /               ext4    errors=remount
-ro 0       1
# /boot/efi was on /dev/sda2 during installation
#UUID=3446-8563  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda8 during installation
UUID=103cbf83-409c-43a6-8e92-1cb7e49ee29a none            swap    sw            
  0       0
UUID=3446-8563    /boot/efi    vfat    defaults    0    1



```

---

### Post by oldfred on 2015-10-19
Your ESP has this: /EFI/ubuntu/grub.cfg
But when you boot it is mounted at /boot/efi
Your find command did find it:
./boot/efi/EFI/ubuntu/grub.cfg

If you are in another install that is not UEFI or your live installer then it will be where ever you mount it or Nautilus auto mounts it.

---

### Post by deepakdeshp on 2015-10-19
> **oldfred said:**
> Your ESP has this: /EFI/ubuntu/grub.cfg
But when you boot it is mounted at /boot/efi
Your find command did find it:
./boot/efi/EFI/ubuntu/grub.cfg

If you are in another install that is not UEFI or your live installer then it will be where ever you mount it or Nautilus auto mounts it.

**The problem is fixed now**. Thank you very much .:p . sda2 gets mounted on /boot/efi. /boot/efi/EFI/ubuntu/grub.cfg on sda13 has /boot/grub/grub.cfg as listed as the config file. I changed the /boot/grub/grub.cfg file to reflect the correct UUIDs for sda10 and sda12 for kernel 4.2.0.2. Earlier for Kernel 4.2.0.2 , sda10 and sda12 the UUID entries were for sda13. The diff is attached in code section. I have also attached both the original grub.cfg and edited files with this post.
When I ran update-grub after booting from sda13, it should have generated the correct  /boot/grub/grub.cfg. It was really painful editing the grub.cfg file manually. I had also installed new Kernel 4.2.0.2 on sda13 and removed the old kernel . This was because my AMD laptop graphics was not working properly. 
```
diff /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.old214c214< afc80bf2-4b55-4455-acae-bd4711ea8c3b
---
> 
222c222
<     insmod ext
---
>     insmod ext2
229c229
<     linux /boot/vmlinuz-4.2.0-040200-generic.old root=UUID=afc80bf2-4b55-4455-acae-bd4711ea8c3b ro quiet splash $vt_handoff
---
>     linux /boot/vmlinuz-4.2.0-040200-generic.old root=UUID=378069b3-76f5-41ba-bea2-ff986413e8e3 ro quiet splash $vt_handoff
242c242
<         linux /boot/vmlinuz-4.2.0-040200-generic.old root=UUID=afc80bf2-4b55-4455-acae-bd4711ea8c3b ro quiet splash $vt_handoff
---
>         linux /boot/vmlinuz-4.2.0-040200-generic.old root=UUID=378069b3-76f5-41ba-bea2-ff986413e8e3 ro quiet splash $vt_handoff
254c254
<         linux /boot/vmlinuz-4.2.0-040200-generic.old root=UUID=afc80bf2-4b55-4455-acae-bd4711ea8c3b ro quiet splash $vt_handoff
---
>         linux /boot/vmlinuz-4.2.0-040200-generic.old root=UUID=378069b3-76f5-41ba-bea2-ff986413e8e3 ro quiet splash $vt_handoff
266c266
<         linux /boot/vmlinuz-4.2.0-040200-generic.old root=UUID=afc80bf2-4b55-4455-acae-bd4711ea8c3b ro recovery nomodeset
---
>         linux /boot/vmlinuz-4.2.0-040200-generic.old root=UUID=378069b3-76f5-41ba-bea2-ff986413e8e3 ro recovery nomodeset
279c279
<     linux /boot/vmlinuz-4.2.0-040200-generic root=UUID= 709441e6-eae8-4243-a4c0-981629fec9aero quiet splash $vt_handoff
---
>     linux /boot/vmlinuz-4.2.0-040200-generic root=UUID=378069b3-76f5-41ba-bea2-ff986413e8e3 ro quiet splash $vt_handoff
292c292
<         linux /boot/vmlinuz-4.2.0-040200-generic root=UUID=709441e6-eae8-4243-a4c0-981629fec9ae ro quiet splash $vt_handoff
---
>         linux /boot/vmlinuz-4.2.0-040200-generic root=UUID=378069b3-76f5-41ba-bea2-ff986413e8e3 ro quiet splash $vt_handoff
304c304
<         linux /boot/vmlinuz-4.2.0-040200-generic root=UUID=709441e6-eae8-4243-a4c0-981629fec9ae ro quiet splash $vt_handoff
---
>         linux /boot/vmlinuz-4.2.0-040200-generic root=UUID=378069b3-76f5-41ba-bea2-ff986413e8e3 ro quiet splash $vt_handoff
316c316
<         linux /boot/vmlinuz-4.2.0-040200-generic root=UUID=709441e6-eae8-4243-a4c0-981629fec9ae ro recovery nomodeset
---
>         linux /boot/vmlinuz-4.2.0-040200-generic root=UUID=378069b3-76f5-41ba-bea2-ff986413e8e3 ro recovery nomodeset
uma@uma-HP-Notebook /boot/grub $ blkid |grep sda13
/dev/sda13: UUID="378069b3-76f5-41ba-bea2-ff986413e8e3" TYPE="ext4" 
uma@uma-HP-Notebook /boot/grub $ blkid |grep sda10
/dev/sda10: UUID="afc80bf2-4b55-4455-acae-bd4711ea8c3b" TYPE="ext4" 
uma@uma-HP-Notebook /boot/grub $ blkid |grep sda12
/dev/sda12: UUID="709441e6-eae8-4243-a4c0-981629fec9ae" TYPE="ext4" 
uma@uma-HP-Notebook /boot/grub $ 



```
[COLOR=#ff0000]Summary[/COLOR] Installing new kernel and copying partition sda13 to sda10 and sda12 using gparted must have created the problem. What I dont understand is why running update-grub from sda13 did not fix the problem

[COLOR=#ff0000]Workaround[/COLOR] I edited the /boot/efi/EFI/ubuntu/grub.cfg file to change UUID entries for Kernel 4.2.0.2. In the attachment they are renamed as .txt files because .cfg files can not be attached.

---

### Post by oldfred on 2015-10-19
Your /boot/efi/EFI/ubuntu should only be the 3 line configfile entry. As in post #15.

Only the grub.cfg in /boot will be updated automatically.

But often with many installs better to take manual control. Only let system auto update current working install and manually create in 40_custom entries to boot your other installs.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

    
It can be as simple as this:

 gksudo gedit /etc/grub.d/40_custom
```
menuentry "Install on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}



```

---

### Post by deepakdeshp on 2015-10-19
Thank you all and esp oldfred for all your valuable support.:p

---

