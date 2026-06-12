---
title: "Grub issue with RAID GPT after 12.04 basic apt-get upgrade"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by CJNZ2011 on 2013-01-06
Hi,

I have an Ubuntu server 12.04 in a remote location that I am not able to physically access.
The server is running two 2TB drives in RAID1.

I ran apt-get upgrade and the system updated.
Part of the update led to Grub2 being updated.

The system asks where I would like to install GRUB as part of that upgrade. 
Either: /dev/sda, /dev/sdb, /dev/dm-0, /dev/dm-2

If I select any or all of these it says:
Grub failed to install to the following devices.
Do you want to continue anyway?
Writing GRUB to boot device failed - continue? 
Yes No.

I selected No and then it looped through the above screens again.. and again.

Eventually after trying a bunch of things based on a few hours of Googling I selected Yes and the update finished.

Now based on info I got from various Google searches I think that the system will not boot. Though as I said above I can't do a test reboot as the computer is a remote location I cannot easily access.

Any ideas how to ensure that this is a working, bootable system?

Many thanks!
CJ

---

### Post by CJNZ2011 on 2013-01-06
Further to my previous post, everything was working fine and booting prior to the apt-get upgrade grub2 error.

This is a standard Ubuntu server 12.04 install.
When I installed it I had to install to /dev/mapper/blahblahvolume0 which required a little bit of Googling to find out how to do this. This may be why the upgrade didn't work?

---

### Post by darkod on 2013-01-07
The /dev/mapper/... device is usually a fakeraid device (raid without proper dedicated hardware controller).

On a server you would usually use either linux software raid, or proper hardwae raid. But in case of proper hardware raid the card does all the raid work, and to the OS the array is presented as a single disk, /dev/sda. I am not sure if some hardware controllers can show the device as /dev/mapper/... to the OS.

With /dev/mapper/... and the fakeraid, you need to install the grub2 to the MBR of the array device, /dev/mapper/blahblahvolume0 like you did before.

Again, on proper server raid you shouldn't even see /dev/mapper/... but if you do see it like that my assumption is you need to install grub2 to its MBR, like you did earlier.

---

### Post by darkod on 2013-01-07
PS. With the system running you can always install grub2 to any location like:
```
sudo grub-install /dev/mapper/blahblahvolume0
```

If you want to call up the text menu selecting the grub2 location, you should be able to do it with:
```
sudo dpkg-reconfigure grub-pc
```

Don't forget that in text menus you select with the Space bar.

---

### Post by CJNZ2011 on 2013-01-07
Thanks very much for your help!

> **darkod said:**
> PS. With the system running you can always install grub2 to any location like:
```
sudo grub-install /dev/mapper/blahblahvolume0
```


When I issue the command above I get this output - which is probably the reason why the upgrade didn't work:
#sudo grub-install /dev/mapper/isw_dheheghgfa_Volume0
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

> **darkod said:**
> If you want to call up the text menu selecting the grub2 location, you should be able to do it with:
```
sudo dpkg-reconfigure grub-pc
```


When I run this command I get the same things that happened after the apt-get upgrade: 

GRUB failed to install to the following devices:                                     
/dev/sda /dev/sdb /dev/dm-0 /dev/dm-2                                                
Do you want to continue anyway? If you do, your computer may not start up properly.  
Writing GRUB to boot device failed - continue?

There is no mention of /dev/mapper/anything

Cheers,
CJ

---

### Post by CJNZ2011 on 2013-01-07
Oh also, the motherboard had built in RAID. So the unit is not using a dedicated PCI RAID controller. Just the motherboard controller on a new Gigabyte MB.

Therefore fakeraid?

---

### Post by darkod on 2013-01-07
Yeap, fakeraid. That explains the /dev/mapper/...
Since this is a server which usually means single boot (there is not much point in dual boot servers), it would have been a much better solution to use linux (ubuntu) software raid, not the mobo raid.
The general opinion is that for single boot software raid is much better option. I would only use fakeraid if you need to dual boot with windows on the machine because windows can't understand linux software raid and can't work on it.

But your current issue is not the fakeraid. It's that you have gpt table on the raid device but you didn't create a small bios_grub partition.

On gpt disks grub2 needs a small (only 1MiB) partition WITHOUT any filesystem, and which has the bios_grub flag set. This is because the gpt MBR is smaller than the msdos MBR and grub2 can't fit on it, so it needs the small partition to use as location for part of the files. You still install onto the MBR, grub2 will sort it out itself. You do NOT need to install it onto the small partition. The bios_grub flag shows grub2 where to keep its files.

Do you have maybe 1MiB on the array that you can use?

Can you post this:
```
sudo parted unit MiB print all
```

---

### Post by CJNZ2011 on 2013-01-07
Thanks! That explains it.

Error with this output:
# sudo parted unit MiB print all
Error: Could not stat device unit - No such file or directory.            
Retry/Cancel? C

So I tried:
#sudo parted /dev/sda unit MiB print all
Error: The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the disk is
smaller.  Fix, by moving the backup to the end (and removing the old backup)?
parted: invalid token: all
Fix/Ignore/Cancel? I                                                      
Warning: Not all of the space available to /dev/sda appears to be used, you can fix the GPT to use all of the space (an extra 6056 blocks) or
continue with the current setting? 
Fix/Ignore? I                                                             
Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sda: 1907729MiB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start       End         Size        File system     Name  Flags
 1      1.00MiB     95.0MiB     94.0MiB     fat32                 boot
 2      95.0MiB     1903739MiB  1903644MiB  ext4
 3      1903739MiB  1907726MiB  3987MiB     linux-swap(v1)


AND:
#sudo parted /dev/sdb unit MiB print all
Error: The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the disk is
smaller.  Fix, by moving the backup to the end (and removing the old backup)?
parted: invalid token: all
Fix/Ignore/Cancel? I                                                      
Warning: Not all of the space available to /dev/sdb appears to be used, you can fix the GPT to use all of the space (an extra 6056 blocks) or
continue with the current setting? 
Fix/Ignore? I                                                             
Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sdb: 1907729MiB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start       End         Size        File system     Name  Flags
 1      1.00MiB     95.0MiB     94.0MiB     fat32                 boot
 2      95.0MiB     1903739MiB  1903644MiB  ext4
 3      1903739MiB  1907726MiB  3987MiB     linux-swap(v1)

Is that enough information?

---

### Post by darkod on 2013-01-07
Not really. I don't know if you should worry about those errors or it's simply that it doesn't understand the raid array correctly.

The 'print all' option should have printed all devices, I was more interested in the raid device. Try this then:
```
sudo parted /dev/mapper/blahblahvolume0 unit MiB print
```

Lets see if that prints the mapper device which is the important one.

---

### Post by CJNZ2011 on 2013-01-07
Ok, sure here it is:

# sudo parted /dev/mapper/isw_dheheghgfa_Volume0 unit MiB print
Model: Linux device-mapper (mirror) (dm)
Disk /dev/mapper/isw_dheheghgfa_Volume0: 1907726MiB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start       End         Size        File system     Name  Flags
 1      1.00MiB     95.0MiB     94.0MiB     fat32                 boot
 2      95.0MiB     1903739MiB  1903644MiB  ext4
 3      1903739MiB  1907726MiB  3987MiB     linux-swap(v1)

---

### Post by darkod on 2013-01-08
OK, the good news is you have 94MiB before your ubuntu partition. You can clearly see that.
The bad news is that there is one fat32 partition taking that space.

In a linux only system, you don't need this fat32 partition and it seems it's not used. It's probably a leftover. Is it? And are you sure you are not using it and it can be deleted?

If it can be deleted, I would delete it and create the small 1MiB partition in that space. But I didn't install your server and I can't tell you 100% to delete it because I don't know if it's doing anything or not.

In case you do decide to delete this partition and make the small bios_grub, the procedure would be:
```
sudo parted /dev/mapper/blahblahvolume0
unit MiB
print
rm 1
mkpart GRUB 1 2
set 1 bios_grub on
quit
```

Those commands do:
Sets the units to MiB.
Prints the partition list. MAKE SURE the partition you want to delete is still number #1 otherwise adjust the next command!!!
Deletes partition #1 (the fat32 partition).
Makes new partition with label GRUB from 1st to 2nd MiB, which means 1MiB size.
Sets the bios_grub flag on it (in case the new partition is not number #1 any more you will have to adjust this command and use the correct number).

After that the repeat the grub2 install command to /dev/mapper/... and it should work fine.

I repeat, all of this is under the assumption that you don't need that fat32 partition. Having the server remotely without physical access makes things complicated if they get messed up.

---

### Post by CJNZ2011 on 2013-01-08
Thanks very much Darkod for the help!!

> **darkod said:**
> OK, the good news is you have 94MiB before your ubuntu partition. You can clearly see that.
The bad news is that there is one fat32 partition taking that space.

In a linux only system, you don't need this fat32 partition and it seems it's not used. It's probably a leftover. Is it? And are you sure you are not using it and it can be deleted?

I tried to do a standard install of Ubuntu server .. but I made a change during install based on a Google search to get raid working. So I guess I have a sort of hybrid system as a result.
The thing is that it booted fine prior to running apt-get upgrade.

Here is output from df -h:
Filesystem                            Size  Used Avail Use% Mounted on
/dev/mapper/isw_dheheghgfa_Volume0p2  1.8T   15G  1.7T   1% /
udev                                  1.9G  4.0K  1.9G   1% /dev
tmpfs                                 769M  368K  769M   1% /run
none                                  5.0M     0  5.0M   0% /run/lock
none                                  1.9G     0  1.9G   0% /run/shm
/dev/mapper/isw_dheheghgfa_Volume0p1   94M  1.0K   94M   1% /boot/efi

My only worry is that isw_dheheghgfa_Volume0p1 is the fat32 partition and is mounted.. but there is nothing in it. So I guess that means I can safely remove it?

---

### Post by darkod on 2013-01-08
Uhh, I can't really tell you for sure. I was afraid it will show up as efi partition. In EFI boot you need to have one small fat32 partition usually at the start of the disk. But in case you are using efi boot it should not be empty I guess.

I haven't worked with efi yet. If you are using efi boot chances are deleting the partition will mess up your system.

Can you post the content of your /boot/grub? While you are at it, post the content of /boot/efi too.
```
ls /boot/grub
ls /boot/efi
```

The grub packages for the legacy and efi boot are different. grub-pc is for legacy, grub-efi for efi boot. Checking which package you have installed might point which version of the boot you are running.

If I remember correctly the apt command to check for packages is like:
```
sudo apt-cache show <package_name>
```

It will show the latest version available in the repository and whether it's installed or not. You can make the check for both grub-pc and grub-efi.

---

### Post by CJNZ2011 on 2013-01-08
> **darkod said:**
> Can you post the content of your /boot/grub? While you are at it, post the content of /boot/efi too.
```
ls /boot/grub
ls /boot/efi
```


# ls -l /boot/grub/
total 4356
-rw-r--r-- 1 root root    7368 Jan  8 08:58 915resolution.mod
-rw-r--r-- 1 root root   10420 Jan  8 08:58 acpi.mod
-rw-r--r-- 1 root root    1848 Jan  8 08:58 adler32.mod
-rw-r--r-- 1 root root    4644 Jan  8 08:58 affs.mod
-rw-r--r-- 1 root root    5092 Jan  8 08:58 afs_be.mod
-rw-r--r-- 1 root root    4928 Jan  8 08:58 afs.mod
-rw-r--r-- 1 root root    1132 Jan  8 08:58 aout.mod
-rw-r--r-- 1 root root    8184 Jan  8 08:58 ata.mod
-rw-r--r-- 1 root root    2276 Jan  8 08:58 ata_pthru.mod
-rw-r--r-- 1 root root    4236 Jan  8 08:58 at_keyboard.mod
-rw-r--r-- 1 root root    5004 Jan  8 08:58 befs_be.mod
-rw-r--r-- 1 root root    4832 Jan  8 08:58 befs.mod
-rw-r--r-- 1 root root    4780 Jan  8 08:58 biosdisk.mod
-rw-r--r-- 1 root root    2560 Jan  8 08:58 bitmap.mod
-rw-r--r-- 1 root root    3084 Jan  8 08:58 bitmap_scale.mod
-rw-r--r-- 1 root root    2192 Jan  8 08:58 blocklist.mod
-rw-r--r-- 1 root root     512 Jan  8 08:58 boot.img
-rw-r--r-- 1 root root    2636 Jan  8 08:58 boot.mod
-rw-r--r-- 1 root root   27992 Jan  8 08:58 bsd.mod
-rw-r--r-- 1 root root   13588 Jan  8 08:58 btrfs.mod
-rw-r--r-- 1 root root    2032 Jan  8 08:58 bufio.mod
-rw-r--r-- 1 root root    2428 Jan  8 08:58 cat.mod
-rw-r--r-- 1 root root     512 Jan  8 08:58 cdboot.img
-rw-r--r-- 1 root root    2652 Jan  8 08:58 chain.mod
-rw-r--r-- 1 root root    1720 Jan  8 08:58 cmostest.mod
-rw-r--r-- 1 root root    2136 Jan  8 08:58 cmp.mod
-rw-r--r-- 1 root root    2830 Jan  8 08:58 command.lst
-rw-r--r-- 1 root root    2368 Jan  8 08:58 configfile.mod
-rw-r--r-- 1 root root   27010 Jan  8 08:58 core.img
-rw-r--r-- 1 root root    2940 Jan  8 08:58 cpio.mod
-rw-r--r-- 1 root root    1684 Jan  8 08:58 cpuid.mod
-rw-r--r-- 1 root root     842 Jan  8 08:58 crypto.lst
-rw-r--r-- 1 root root    4464 Jan  8 08:58 crypto.mod
-rw-r--r-- 1 root root    4212 Jan  8 08:58 cs5536.mod
-rw-r--r-- 1 root root    1952 Jan  8 08:58 datehook.mod
-rw-r--r-- 1 root root    2336 Jan  8 08:58 date.mod
-rw-r--r-- 1 root root    1353 Jan  8 08:58 datetime.mod
-rw-r--r-- 1 root root     149 Jan  7 12:14 device.map
-rw-r--r-- 1 root root     512 Jan  8 08:58 diskboot.img
-rw-r--r-- 1 root root    1968 Jan  8 08:58 dm_nv.mod
-rw-r--r-- 1 root root    5576 Jan  8 08:58 drivemap.mod
-rw-r--r-- 1 root root    2108 Jan  8 08:58 echo.mod
-rw-r--r-- 1 root root    7408 Jan  8 08:58 efiemu32.o
-rw-r--r-- 1 root root   11089 Jan  8 08:58 efiemu64.o
-rw-r--r-- 1 root root   24580 Jan  8 08:58 efiemu.mod
-rw-r--r-- 1 root root    4632 Jan  8 08:58 elf.mod
-rw-r--r-- 1 root root    1700 Jan  8 08:58 example_functional_test.mod
-rw-r--r-- 1 root root    5912 Jan  8 08:58 ext2.mod
-rw-r--r-- 1 root root    4572 Jan  8 08:58 extcmd.mod
-rw-r--r-- 1 root root    6112 Jan  8 08:58 fat.mod
-rw-r--r-- 1 root root   11976 Jan  8 08:58 font.mod
-rw-r--r-- 1 root root    2892 Jan  8 08:58 fshelp.mod
-rw-r--r-- 1 root root     149 Jan  8 08:58 fs.lst
-rw-r--r-- 1 root root    2556 Jan  8 08:58 functional_test.mod
-rw-r--r-- 1 root root     512 Jan  8 08:58 g2hdr.img
-rw-r--r-- 1 root root    1824 Jan  8 08:58 gcry_arcfour.mod
-rw-r--r-- 1 root root    8308 Jan  8 08:58 gcry_blowfish.mod
-rw-r--r-- 1 root root   34668 Jan  8 08:58 gcry_camellia.mod
-rw-r--r-- 1 root root   17412 Jan  8 08:58 gcry_cast5.mod
-rw-r--r-- 1 root root    3088 Jan  8 08:58 gcry_crc.mod
-rw-r--r-- 1 root root   19440 Jan  8 08:58 gcry_des.mod
-rw-r--r-- 1 root root    3304 Jan  8 08:58 gcry_md4.mod
-rw-r--r-- 1 root root    3988 Jan  8 08:58 gcry_md5.mod
-rw-r--r-- 1 root root    2632 Jan  8 08:58 gcry_rfc2268.mod
-rw-r--r-- 1 root root   19236 Jan  8 08:58 gcry_rijndael.mod
-rw-r--r-- 1 root root    8752 Jan  8 08:58 gcry_rmd160.mod
-rw-r--r-- 1 root root   16740 Jan  8 08:58 gcry_seed.mod
-rw-r--r-- 1 root root   18092 Jan  8 08:58 gcry_serpent.mod
-rw-r--r-- 1 root root    8856 Jan  8 08:58 gcry_sha1.mod
-rw-r--r-- 1 root root    3660 Jan  8 08:58 gcry_sha256.mod
-rw-r--r-- 1 root root    5868 Jan  8 08:58 gcry_sha512.mod
-rw-r--r-- 1 root root   11916 Jan  8 08:58 gcry_tiger.mod
-rw-r--r-- 1 root root   39688 Jan  8 08:58 gcry_twofish.mod
-rw-r--r-- 1 root root   24712 Jan  8 08:58 gcry_whirlpool.mod
-rw-r--r-- 1 root root    4012 Jan  8 08:58 gettext.mod
-rw-r--r-- 1 root root     699 Nov 29 11:00 gfxblacklist.txt
-rw-r--r-- 1 root root   32992 Jan  8 08:58 gfxmenu.mod
-rw-r--r-- 1 root root   11984 Jan  8 08:58 gfxterm.mod
-rw-r--r-- 1 root root    3780 Jan  8 08:58 gptsync.mod
-rw-r--r-- 1 root root   10240 Jan  8 08:58 grldr.img
-r--r--r-- 1 root root    7097 Jan  8 09:00 grub.cfg
-rw-r--r-- 1 root root    1024 Jan  7 11:24 grubenv
-rw-r--r-- 1 root root    8704 Jan  8 08:58 gzio.mod
-rw-r--r-- 1 root root    4076 Jan  8 08:58 halt.mod
-rw-r--r-- 1 root root    5136 Jan  8 08:58 hashsum.mod
-rw-r--r-- 1 root root    7404 Jan  8 08:58 hdparm.mod
-rw-r--r-- 1 root root    1292 Jan  8 08:58 hello.mod
-rw-r--r-- 1 root root    2548 Jan  8 08:58 help.mod
-rw-r--r-- 1 root root    3296 Jan  8 08:58 hexdump.mod
-rw-r--r-- 1 root root    6136 Jan  8 08:58 hfs.mod
-rw-r--r-- 1 root root    6024 Jan  8 08:58 hfsplus.mod
-rw-r--r-- 1 root root   38972 Jan  8 08:58 hwmatch.mod
-rw-r--r-- 1 root root    2928 Jan  8 08:58 iorw.mod
-rw-r--r-- 1 root root    6344 Jan  8 08:58 iso9660.mod
-rw-r--r-- 1 root root    6212 Jan  8 08:58 jfs.mod
-rw-r--r-- 1 root root    5908 Jan  8 08:58 jpeg.mod
-rw-r--r-- 1 root root   30168 Jan  8 08:58 kernel.img
-rw-r--r-- 1 root root    4588 Jan  8 08:58 keylayouts.mod
-rw-r--r-- 1 root root    2104 Jan  8 08:58 keystatus.mod
-rw-r--r-- 1 root root   27668 Jan  8 08:58 legacycfg.mod
-rw-r--r-- 1 root root    5768 Jan  8 08:58 linux16.mod
-rw-r--r-- 1 root root   10184 Jan  8 08:58 linux.mod
-rw-r--r-- 1 root root    1024 Jan  8 08:58 lnxboot.img
-rw-r--r-- 1 root root      87 Jan  8 08:58 load.cfg
-rw-r--r-- 1 root root    5756 Jan  8 08:58 loadenv.mod
drwxr-xr-x 2 root root    4096 Nov 29 11:33 locale
-rw-r--r-- 1 root root    2988 Jan  8 08:58 loopback.mod
-rw-r--r-- 1 root root    3716 Jan  8 08:58 lsacpi.mod
-rw-r--r-- 1 root root    2308 Jan  8 08:58 lsapm.mod
-rw-r--r-- 1 root root    1804 Jan  8 08:58 lsmmap.mod
-rw-r--r-- 1 root root    4436 Jan  8 08:58 ls.mod
-rw-r--r-- 1 root root    4968 Jan  8 08:58 lspci.mod
-rw-r--r-- 1 root root    7216 Jan  8 08:58 lvm.mod
-rw-r--r-- 1 root root    9084 Jan  8 08:58 lzopio.mod
-rw-r--r-- 1 root root    1976 Jan  8 08:58 mdraid09.mod
-rw-r--r-- 1 root root    2380 Jan  8 08:58 mdraid1x.mod
-rw-r--r-- 1 root root    2144 Jan  8 08:58 memdisk.mod
-rw-r--r-- 1 root root    2948 Jan  8 08:58 memrw.mod
-rw-r--r-- 1 root root    3528 Jan  8 08:58 minicmd.mod
-rw-r--r-- 1 root root    3880 Jan  8 08:58 minix2.mod
-rw-r--r-- 1 root root    3880 Jan  8 08:58 minix.mod
-rw-r--r-- 1 root root    9300 Jan  8 08:58 mmap.mod
-rw-r--r-- 1 root root    3292 Jan  8 08:58 moddep.lst
-rw-r--r-- 1 root root    2492 Jan  8 08:58 msdospart.mod
-rw-r--r-- 1 root root   12984 Jan  8 08:58 multiboot2.mod
-rw-r--r-- 1 root root   12292 Jan  8 08:58 multiboot.mod
-rw-r--r-- 1 root root    6716 Jan  8 08:58 nilfs2.mod
-rw-r--r-- 1 root root  106448 Jan  8 08:58 normal.mod
-rw-r--r-- 1 root root    3540 Jan  8 08:58 ntfscomp.mod
-rw-r--r-- 1 root root    9612 Jan  8 08:58 ntfs.mod
-rw-r--r-- 1 root root    2636 Jan  8 08:58 ntldr.mod
-rw-r--r-- 1 root root   10432 Jan  8 08:58 ohci.mod
-rw-r--r-- 1 root root    1772 Jan  8 08:58 part_acorn.mod
-rw-r--r-- 1 root root    1856 Jan  8 08:58 part_amiga.mod
-rw-r--r-- 1 root root    2192 Jan  8 08:58 part_apple.mod
-rw-r--r-- 1 root root    2860 Jan  8 08:58 part_bsd.mod
-rw-r--r-- 1 root root    2452 Jan  8 08:58 part_gpt.mod
-rw-r--r-- 1 root root      82 Jan  8 08:58 partmap.lst
-rw-r--r-- 1 root root    2388 Jan  8 08:58 part_msdos.mod
-rw-r--r-- 1 root root    1644 Jan  8 08:58 part_sun.mod
-rw-r--r-- 1 root root    1776 Jan  8 08:58 part_sunpc.mod
-rw-r--r-- 1 root root      17 Jan  8 08:58 parttool.lst
-rw-r--r-- 1 root root    4568 Jan  8 08:58 parttool.mod
-rw-r--r-- 1 root root    2052 Jan  8 08:58 password.mod
-rw-r--r-- 1 root root    2940 Jan  8 08:58 password_pbkdf2.mod
-rw-r--r-- 1 root root    1416 Jan  8 08:58 pbkdf2.mod
-rw-r--r-- 1 root root    1272 Jan  8 08:58 pci.mod
-rw-r--r-- 1 root root    2568 Jan  8 08:58 play.mod
-rw-r--r-- 1 root root    6620 Jan  8 08:58 png.mod
-rw-r--r-- 1 root root    2740 Jan  8 08:58 probe.mod
-rw-r--r-- 1 root root    1024 Jan  8 08:58 pxeboot.img
-rw-r--r-- 1 root root    1408 Jan  8 08:58 pxecmd.mod
-rw-r--r-- 1 root root    6160 Jan  8 08:58 pxe.mod
-rw-r--r-- 1 root root    1472 Jan  8 08:58 raid5rec.mod
-rw-r--r-- 1 root root    2876 Jan  8 08:58 raid6rec.mod
-rw-r--r-- 1 root root    6536 Jan  8 08:58 raid.mod
-rw-r--r-- 1 root root    1640 Jan  8 08:58 read.mod
-rw-r--r-- 1 root root    1200 Jan  8 08:58 reboot.mod
-rw-r--r-- 1 root root   41940 Jan  8 08:58 regexp.mod
-rw-r--r-- 1 root root    9544 Jan  8 08:58 reiserfs.mod
-rw-r--r-- 1 root root   14644 Jan  8 08:58 relocator.mod
-rw-r--r-- 1 root root    4028 Jan  8 08:58 scsi.mod
-rw-r--r-- 1 root root    2980 Jan  8 08:58 search_fs_file.mod
-rw-r--r-- 1 root root    3008 Jan  8 08:58 search_fs_uuid.mod
-rw-r--r-- 1 root root    2912 Jan  8 08:58 search_label.mod
-rw-r--r-- 1 root root    2628 Jan  8 08:58 search.mod
-rw-r--r-- 1 root root    7260 Jan  8 08:58 sendkey.mod
-rw-r--r-- 1 root root    7128 Jan  8 08:58 serial.mod
-rw-r--r-- 1 root root     706 Jan  8 08:58 setjmp.mod
-rw-r--r-- 1 root root    5512 Jan  8 08:58 setpci.mod
-rw-r--r-- 1 root root       0 Nov 29 11:41 setup_left_core_image_in_filesystem
-rw-r--r-- 1 root root    4052 Jan  8 08:58 sfs.mod
-rw-r--r-- 1 root root    2392 Jan  8 08:58 sleep.mod
-rw-r--r-- 1 root root    3972 Jan  8 08:58 squash4.mod
-rw-r--r-- 1 root root    2968 Jan  8 08:58 tar.mod
-rw-r--r-- 1 root root     132 Jan  8 08:58 terminal.lst
-rw-r--r-- 1 root root    3836 Jan  8 08:58 terminal.mod
-rw-r--r-- 1 root root   10296 Jan  8 08:58 terminfo.mod
-rw-r--r-- 1 root root    1508 Jan  8 08:58 test_blockarg.mod
-rw-r--r-- 1 root root    2816 Jan  8 08:58 testload.mod
-rw-r--r-- 1 root root    5100 Jan  8 08:58 test.mod
-rw-r--r-- 1 root root    2940 Jan  8 08:58 tga.mod
-rw-r--r-- 1 root root    1763 Jan  8 08:58 trig.mod
-rw-r--r-- 1 root root    1356 Jan  8 08:58 true.mod
-rw-r--r-- 1 root root    6572 Jan  8 08:58 udf.mod
-rw-r--r-- 1 root root    4740 Jan  8 08:58 ufs1.mod
-rw-r--r-- 1 root root    5052 Jan  8 08:58 ufs2.mod
-rw-r--r-- 1 root root    6004 Jan  8 08:58 uhci.mod
-rw-r--r-- 1 root root 2560080 Jan  8 09:00 unicode.pf2
-rw-r--r-- 1 root root    4300 Jan  8 08:58 usb_keyboard.mod
-rw-r--r-- 1 root root    9656 Jan  8 08:58 usb.mod
-rw-r--r-- 1 root root    5604 Jan  8 08:58 usbms.mod
-rw-r--r-- 1 root root    2048 Jan  8 08:58 usbserial_common.mod
-rw-r--r-- 1 root root    2452 Jan  8 08:58 usbserial_ftdi.mod
-rw-r--r-- 1 root root    2812 Jan  8 08:58 usbserial_pl2303.mod
-rw-r--r-- 1 root root    3756 Jan  8 08:58 usbtest.mod
-rw-r--r-- 1 root root    8840 Jan  8 08:58 vbe.mod
-rw-r--r-- 1 root root    4724 Jan  8 08:58 vga.mod
-rw-r--r-- 1 root root    2308 Jan  8 08:58 vga_text.mod
-rw-r--r-- 1 root root    5536 Jan  8 08:58 video_bochs.mod
-rw-r--r-- 1 root root    5860 Jan  8 08:58 video_cirrus.mod
-rw-r--r-- 1 root root   19164 Jan  8 08:58 video_fb.mod
-rw-r--r-- 1 root root    3748 Jan  8 08:58 videoinfo.mod
-rw-r--r-- 1 root root      33 Jan  8 08:58 video.lst
-rw-r--r-- 1 root root   10752 Jan  8 08:58 video.mod
-rw-r--r-- 1 root root    4268 Jan  8 08:58 videotest.mod
-rw-r--r-- 1 root root    6152 Jan  8 08:58 xfs.mod
-rw-r--r-- 1 root root   31736 Jan  8 08:58 xnu.mod
-rw-r--r-- 1 root root    2016 Jan  8 08:58 xnu_uuid.mod
-rw-r--r-- 1 root root   14468 Jan  8 08:58 xzio.mod
-rw-r--r-- 1 root root    6360 Jan  8 08:58 zfsinfo.mod
-rw-r--r-- 1 root root   33308 Jan  8 08:58 zfs.mod

# ls /boot/efi is empty

> **darkod said:**
> If I remember correctly the apt command to check for packages is like:
```
sudo apt-cache show <package_name>
```

It will show the latest version available in the repository and whether it's installed or not. You can make the check for both grub-pc and grub-efi.

# sudo apt-cache policy grub-pc
grub-pc:
  Installed: 1.99-21ubuntu3.7
  Candidate: 1.99-21ubuntu3.7
  Version table:
 *** 1.99-21ubuntu3.7 0
        500 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.99-21ubuntu3 0
        500 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise/main amd64 Packages

# sudo apt-cache policy grub-efi
grub-efi:
  Installed: (none)
  Candidate: 1.99-21ubuntu3.7
  Version table:
     1.99-21ubuntu3.7 0
        500 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise-updates/main amd64 Packages
     1.99-21ubuntu3 0
        500 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise/main amd64 Packages

# dpkg -l | grep grub
ii  grub-common             1.99-21ubuntu3.7    GRand Unified Bootloader (common files)
ii  grub-gfxpayload-lists   0.6                 GRUB gfxpayload blacklist
ii  grub-pc                 1.99-21ubuntu3.7    GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin             1.99-21ubuntu3.7    GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common            1.99-21ubuntu3.7    GRand Unified Bootloader (common files for version 2)

Looks pretty safe to remove that partition?

Thanks!

---

### Post by darkod on 2013-01-08
Yes, it does. You can use the procedure we outlined before, and make sure the partition is still #1 before deleting it with rm 1. It must be, but it never hurts to check.

Since it's mounted, you should unmount it first with:
sudo umount /boot/efi

After that do the procedure command by command and run the grub-install.

Ubuntu is usually very resilient. You can even completely remove grub and install it, and it will work. Unless you reboot before reinstalling grub of course. :) So I hope all of this goes well.

---

### Post by CJNZ2011 on 2013-01-08
Awesome! Thanks again!
Done and it worked.

One more question, do I need to run:
sudo dpkg-reconfigure grub-pc

I did this to test if it would work should this problem happen again.
It still only presented me with the choices as per before:
[ ] /dev/sda (2000398 MB; ST2000DM001-1CH164)
[ ] /dev/sdb (2000398 MB; ST2000DM001-1CH164)
[ ] /dev/dm-0 (2000395 MB; isw_dheheghgfa_Volume0)
[ ] /dev/dm-2 (1996115 MB; isw_dheheghgfa_Volume0)

Obviously, same error that led me to this problem initially as there is no /dev/mapper/blahblahvolume0 listed.

Is it fine to just install it as per:
sudo grub-install /dev/mapper/blahblahvolume0
Does that also manage the config which I guess is what dpkg-reconfigure grub-pc is doing?

---

### Post by darkod on 2013-01-08
Hmm, I usually don't see /dev/dm-X devices, but I guess it might be short for /dev/mapper/... Something like dm = device mapper.

If you look at the dm-0 and dm-2 options, later it actually says the array device, blahblah_Volume0.

I am only confused why there are two, one sligthly smaller.

I would leave it as it is, I think it's configured good. If you want to, use parted again to display the /dev/mapper/... device again but this time with unit MB and compare it's total size (the device, not the partitions on it) with the MB size the dpkg-reconfigure is giving you for the dm-0 and dm-2 devices. If it matches to one of them, select it and save the changes.

---

### Post by CJNZ2011 on 2013-01-08
Great! Thanks again for the HUGE help!

---

