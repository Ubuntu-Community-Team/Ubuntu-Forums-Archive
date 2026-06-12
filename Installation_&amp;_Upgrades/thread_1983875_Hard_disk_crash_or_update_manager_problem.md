---
title: "Hard disk crash or update manager problem?"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by Ubu_Fester on 2012-05-20
Been using mythtv for couple years now.  Moved to 11.10 a few months ago.  

Last few weeks the ubuntu system monitor was showing normal stats, except system load averages appeared high (between 1.5 and 3.5).  A few days ago, I went through update manager and updated the 100+ updates.  I am now unable to boot my PC.  System boots to the GRUB screen (which I normally don't see).  

When booting OS via CD I am able to see all my partitions on both drives. I tried to run "Boot-Repair" but get errors (need to run a 64bit version, or ??).  

Is my hard drive toast?  Or did my OS update crash my boot drive?

System:  HTPC
mythbuntu 11.10 64bit  (mythtv .24?), 2GB memory, nvidia 210, 
HD:  Samsung 1TB (OS and multiple partitions) 
Seagate 2TB (mostly stored video)

From my Boot-Repair log, here is my system information:

[HTML]

                Boot Info Script 0.61-git      [12 April 2012]   ============================= Boot Info Summary: ===============================   => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.  => No boot loader is installed in the MBR of /dev/sdb.  sda1: __________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:      Operating System:  Ubuntu 11.10     Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img  sda2: __________________________________________________________________________      File system:       Extended Partition     Boot sector type:  -     Boot sector info:   sda5: __________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:   sda6: __________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:      Operating System:       Boot files:          sda3: __________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:      Operating System:       Boot files:          sda4: __________________________________________________________________________      File system:       vfat     Boot sector type:  -     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files:          sdb1: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7: NTFS     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files:          sdb2: __________________________________________________________________________      File system:       vfat     Boot sector type:  FAT32     Boot sector info:  According to the info in the boot sector, sdb2 starts                         at sector -864607846. But according to the info from                         fdisk, sdb2 starts at sector 3430359450.     Operating System:       Boot files:          ============================ Drive/Partition Info: =============================  Drive: sda _____________________________________________________________________  Disk /dev/sda: 1000.2 GB, 1000204886016 bytes 255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sda1    *             63   125,001,764   125,001,702  83 Linux /dev/sda2         554,692,444 1,953,520,064 1,398,827,621   5 Extended /dev/sda5       1,942,965,423 1,953,520,064    10,554,642  82 Linux swap / Solaris /dev/sda6         554,692,446 1,942,965,359 1,388,272,914  83 Linux /dev/sda3         125,001,765   320,320,034   195,318,270  83 Linux /dev/sda4         320,320,035   554,692,319   234,372,285  83 Linux   Drive: sdb _____________________________________________________________________  Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes 255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sdb1                  63 3,430,359,449 3,430,359,387   7 NTFS / exFAT / HPFS /dev/sdb2       3,430,359,450 3,907,028,991   476,669,542   b W95 FAT32   "blkid" output: ________________________________________________________________  Device           UUID                                   TYPE       LABEL  /dev/loop0                                              squashfs    /dev/sda1        a90a6001-8d87-4602-9e55-45b193b0ec50   ext4        /dev/sda3        2cb2e02a-bac8-42c2-b57f-25c0255e6480   ext4        /dev/sda4        02DA-5489                              vfat        /dev/sda5        9fa85721-2005-428f-8e5c-f369aea5bd57   swap        /dev/sda6        9f907db7-c6f3-4f01-bcbc-d992b0096088   ext4        /dev/sdb1        3BBFCCC014E3C8A8                       ntfs       video2 /dev/sdb2        1547-2B71                              vfat       backup  ================================ Mount points: =================================  Device           Mount_Point              Type       Options  /dev/loop0       /rofs                    squashfs   (ro,noatime) /dev/sr0         /cdrom                   iso9660    (ro,noatime)   =========================== sda1/boot/grub/grub.cfg: =========================== [edit:  deleted this section]  =============================== sda1/etc/fstab: ================================  -------------------------------------------------------------------------------- # /etc/fstab: static file system information. # # Use 'blkid' to print the universally unique identifier for a # device; this may be used with UUID= as a more robust way to name devices # that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sda1 during installation UUID=a90a6001-8d87-4602-9e55-45b193b0ec50 /               ext4    errors=remount-ro 0       1 # /home was on /dev/sda3 during installation UUID=2cb2e02a-bac8-42c2-b57f-25c0255e6480 /home           ext4    defaults        0       2 # /media/backup was on /dev/sdb2 during installation UUID=1547-2B71           /media/backup   vfat    utf8,umask=007,gid=46 0       1 # /media/video2 was on /dev/sdb1 during installation # ###UUID=3BBFCCC014E3C8A8    /media/video2   ntfs-3g defaults,nls=utf8,umask=007,gid=46 0       0 # ###UUID=3BBFCCC014E3C8A8    /media/video2   ntfs-3g auto,users,uid=1000,gid=1000,umask=007    0       0 #UUID=3BBFCCC014E3C8A8    /media/video2   ntfs-3g defaults,uid=1000,gid=117,umask=007    0       0 UUID=3BBFCCC014E3C8A8    /media/video2   ntfs-3g defaults,uid=117,gid=117,umask=007    0       0 # /music was on /dev/sda4 during installation UUID=02DA-5489           /music          vfat    utf8,umask=007,gid=46 0       1 # /video was on /dev/sda6 during installation UUID=9f907db7-c6f3-4f01-bcbc-d992b0096088 /video          ext4    defaults        0       2 # swap was on /dev/sda5 during installation UUID=9fa85721-2005-428f-8e5c-f369aea5bd57 none            swap    sw              0       0 --------------------------------------------------------------------------------  =================== sda1: Location of files loaded by Grub: ====================             GiB - GB             File                                 Fragment(s)     4.328341961 = 4.647521792    boot/grub/core.img                             1    0.138015270 = 0.148192768    boot/grub/grub.cfg                             1    6.732654095 = 7.229132288    boot/initrd.img-2.6.31-22-generic              1    1.101592541 = 1.182825984    boot/initrd.img-2.6.32-27-generic              2    4.627711773 = 4.968967680    boot/initrd.img-2.6.35-24-generic              2   10.912517071 = 11.717225984   boot/initrd.img-2.6.35-25-generic              2   15.971000195 = 17.148730880   boot/initrd.img-2.6.35-28-generic              2    5.127280712 = 5.505375744    boot/initrd.img-2.6.35-30-generic              4    5.222419262 = 5.607529984    boot/initrd.img-2.6.35-31-generic              2    2.484405041 = 2.667609600    boot/initrd.img-3.0.0-12-generic               2    2.812530041 = 3.019931136    boot/initrd.img-3.0.0-14-generic               2    8.505008221 = 9.132183040    boot/initrd.img-3.0.0-16-generic               2    8.055789471 = 8.649838080    boot/initrd.img-3.0.0-19-generic               3    1.253921032 = 1.346387456    boot/initrd.img-3.2.0-23-generic               1    1.510886669 = 1.622302208    boot/vmlinuz-2.6.31-22-generic                 1    1.827479839 = 1.962241536    boot/vmlinuz-2.6.32-27-generic                 1    1.655097485 = 1.777147392    boot/vmlinuz-2.6.35-24-generic                 1    1.698871136 = 1.824148992    boot/vmlinuz-2.6.35-25-generic                 1    1.591239452 = 1.708580352    boot/vmlinuz-2.6.35-28-generic                 1    5.035411358 = 5.406731776    boot/vmlinuz-2.6.35-30-generic                 2    5.218131542 = 5.602926080    boot/vmlinuz-2.6.35-31-generic                 1    1.168433666 = 1.254596096    boot/vmlinuz-3.0.0-12-generic                  1    1.957496166 = 2.101845504    boot/vmlinuz-3.0.0-14-generic                  1    7.254397869 = 7.789350400    boot/vmlinuz-3.0.0-16-generic                  1    7.395026684 = 7.940349440    boot/vmlinuz-3.0.0-19-generic                  1    7.395026684 = 7.940349440    vmlinuz                                        1    7.254397869 = 7.789350400    vmlinuz.old                                    1   ADDITIONAL INFORMATION : =================== log of boot-repair 2012-05-20__21h29 =================== boot-repair version : 3.18-0ppa16~oneiric boot-sav version : 3.18-0ppa50~oneiric glade2script version : 0.3.2.1-0ppa7~oneiric boot-repair is executed in live-session (Ubuntu 11.10 , oneiric , Ubuntu , i686)  =================== OSPROBER: /dev/sda1:Ubuntu 11.10 (11.10):Ubuntu:linux  =================== BLKID: /dev/loop0: TYPE="squashfs" /dev/sda1: UUID="a90a6001-8d87-4602-9e55-45b193b0ec50" TYPE="ext4" /dev/sda3: UUID="2cb2e02a-bac8-42c2-b57f-25c0255e6480" TYPE="ext4" /dev/sda4: UUID="02DA-5489" TYPE="vfat" /dev/sda5: UUID="9fa85721-2005-428f-8e5c-f369aea5bd57" TYPE="swap" /dev/sda6: UUID="9f907db7-c6f3-4f01-bcbc-d992b0096088" TYPE="ext4" /dev/sdb1: LABEL="video2" UUID="3BBFCCC014E3C8A8" TYPE="ntfs" /dev/sdb2: LABEL="backup" UUID="1547-2B71" TYPE="vfat"   1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.  Warning: extended partition does not start at a cylinder boundary. DOS and Linux will interpret the contents differently.   =================== /mnt/boot-sav/sda1/etc/default/grub :  # If you change this file, run 'update-grub' afterwards to update # /boot/grub/grub.cfg. # For full documentation of the options in this file, see: #   info -f grub -n 'Simple configuration'  GRUB_DEFAULT=0 GRUB_HIDDEN_TIMEOUT=0 GRUB_HIDDEN_TIMEOUT_QUIET=true GRUB_TIMEOUT=10 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" GRUB_CMDLINE_LINUX=""  # Uncomment to enable BadRAM filtering, modify to suit your needs # This works with Linux (no patch required) and with any kernel that obtains # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...) #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"  # Uncomment to disable graphical terminal (grub-pc only) #GRUB_TERMINAL=console  # The resolution used on graphical terminal # note that you can use only modes which your graphic card supports via VBE # you can see them in real GRUB with the command `vbeinfo' #GRUB_GFXMODE=640x480  # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux #GRUB_DISABLE_LINUX_UUID=true  # Uncomment to disable generation of recovery mode menu entries #GRUB_DISABLE_RECOVERY="true"  # Uncomment to get a beep at grub start #GRUB_INIT_TUNE="480 440 1"     =================== sda1/boot/grub/grubenv : /var/log/boot-sav/log/2012-05-20__21h29boot-repair32/sda1/grubenv     =================== PARTITIONS & DISKS: sda1    : sda,    not-sepboot,    grubenv-ng    grub2,    grub-pc,    update-grub,    64,    with-boot,    is-os,    not-on-gpt-disk,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    apt-get,    grub-install,    /mnt/boot-sav/sda1. sda3    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not-on-gpt-disk,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sda3. sda4    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not-on-gpt-disk,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sda4. sda6    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not-on-gpt-disk,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sda6. sdb1    : sdb,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not-on-gpt-disk,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sdb1. sdb2    : sdb,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not-on-gpt-disk,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    /mnt/boot-sav/sdb2.  sda    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     63 sectors * 512 bytes sdb    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     63 sectors * 512 bytes  =================== PARTED:  Model: ATA SAMSUNG HD103SI (scsi) Disk /dev/sda: 1000GB Sector size (logical/physical): 512B/512B Partition Table: msdos  Number  Start   End     Size    Type      File system     Flags 1      32.3kB  64.0GB  64.0GB  primary   ext4            boot 3      64.0GB  164GB   100GB   primary   ext4 4      164GB   284GB   120GB   primary   fat32 2      284GB   1000GB  716GB   extended 6      284GB   995GB   711GB   logical   ext4 5      995GB   1000GB  5404MB  logical   linux-swap(v1)   Model: ATA ST32000542AS (scsi) Disk /dev/sdb: 2000GB Sector size (logical/physical): 512B/512B Partition Table: msdos  Number  Start   End     Size    Type     File system  Flags 1      32.3kB  1756GB  1756GB  primary  ntfs 2      1756GB  2000GB  244GB   primary  fat32                                                                               Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.                                                                             Error: Can't have a partition outside the disk!   =================== MOUNT: /cow on / type overlayfs (rw) proc on /proc type proc (rw,noexec,nosuid,nodev) sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) fusectl on /sys/fs/fuse/connections type fusectl (rw) udev on /dev type devtmpfs (rw,mode=0755) devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) /dev/sr0 on /cdrom type iso9660 (ro,noatime) /dev/loop0 on /rofs type squashfs (ro,noatime) none on /sys/kernel/debug type debugfs (rw) none on /sys/kernel/security type securityfs (rw) tmpfs on /tmp type tmpfs (rw,nosuid,nodev) none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) none on /run/shm type tmpfs (rw,nosuid,nodev) binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu) /dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw) /dev/sda3 on /mnt/boot-sav/sda3 type ext4 (rw) /dev/sda4 on /mnt/boot-sav/sda4 type vfat (rw) /dev/sda6 on /mnt/boot-sav/sda6 type ext4 (rw) /dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) /dev/sdb2 on /mnt/boot-sav/sdb2 type vfat (rw)   /sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 size slaves stat subsystem trace uevent /sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent /sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent /dev:  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg log lp0 mapper mcelog mem net network_latency network_throughput null oldmem parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda3 sda4 sda5 sda6 sdb sdb1 sdb2 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 vga_arbiter zero /dev/mapper:  control  =================== DF:  Filesystem    Type    Size  Used Avail Use% Mounted on /cow     overlayfs   1007M  155M  853M  16% / udev      devtmpfs   1000M   12K 1000M   1% /dev tmpfs        tmpfs    403M  840K  402M   1% /run /dev/sr0   iso9660    696M  696M     0 100% /cdrom /dev/loop0 squashfs    668M  668M     0 100% /rofs tmpfs        tmpfs   1007M  668K 1007M   1% /tmp none         tmpfs    5.0M  4.0K  5.0M   1% /run/lock none         tmpfs   1007M  104K 1007M   1% /run/shm /dev/sda1     ext4     59G   17G   40G  29% /mnt/boot-sav/sda1 /dev/sda3     ext4     92G   70G   18G  81% /mnt/boot-sav/sda3 /dev/sda4     vfat    112G   19G   94G  17% /mnt/boot-sav/sda4 /dev/sda6     ext4    652G  436G  184G  71% /mnt/boot-sav/sda6 /dev/sdb1  fuseblk    1.6T  1.4T  207G  88% /mnt/boot-sav/sdb1 /dev/sdb2     vfat    228G  100G  128G  44% /mnt/boot-sav/sdb2  =================== FDISK:  Disk /dev/sda: 1000.2 GB, 1000204886016 bytes 255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x000002f9  Device Boot      Start         End      Blocks   Id  System /dev/sda1   *          63   125001764    62500851   83  Linux /dev/sda2       554692444  1953520064   699413810+   5  Extended /dev/sda3       125001765   320320034    97659135   83  Linux /dev/sda4       320320035   554692319   117186142+  83  Linux /dev/sda5      1942965423  1953520064     5277321   82  Linux swap / Solaris /dev/sda6       554692446  1942965359   694136457   83  Linux  Partition table entries are not in disk order  Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes 255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x000d5928  Device Boot      Start         End      Blocks   Id  System /dev/sdb1              63  3430359449  1715179693+   7  HPFS/NTFS/exFAT /dev/sdb2      3430359450  3907028991   238334771    b  W95 FAT32    =================== Default settings recommendedrepair This setting would reinstall the grub2 of sda1 into the MBRs of all disks (except USB without OS). Additional repair would be performed: unhide-bootmenu  =================== Settings chosen by the user customrepair This setting will restore a generic MBR (mbr) in sda, and make it boot on sda1. Additional repair will be performed: unhide-bootmenu   Unhide GRUB boot menu in sda1/etc/default/grub Will restore the MBR_TO_RESTORE : sda (mbr) into sda dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda 0+1 records in 0+1 records out parted /dev/sda set 1 boot on                                                                             Information: You may need to update /etc/fstab.  Unhide GRUB boot menu in sda1/boot/grub/grub.cfg Boot successfully repaired.  You can now reboot your computer.

[/HTML]

---

### Post by Ubu_Fester on 2012-05-20
Earlier post did not show the boot-repair findings in an easy to read format.  See
[http://paste.ubuntu.com/998078/](http://paste.ubuntu.com/998078/)

---

### Post by YannBuntu on 2012-05-21
Hello
your installed OS is 64bits, so you need to use Boot-Repair from a 64bits CD. 
For example: [Ubuntu Secure 64bits]("https://help.ubuntu.com/community/UbuntuSecureRemix?action=show&redirect=UbuntuSecuredRemix").

---

### Post by Ubu_Fester on 2012-05-21
Thanks for your response.

I actually started with the 64bit 12.04 CD.  I received a number of errors/issues and gave up.  I can get to the bootinfo, but can't run the tool.  [http://paste.ubuntu.com/998062/](http://paste.ubuntu.com/998062/)

I then went to an old 11.10 CD that was not 64bit.

Since my OS is 11.10, shouldn't I use a 64bit 11.10 CD, then download the boot-repair tool "on the fly"?

---

### Post by YannBuntu on 2012-05-21
I see no error in your log. Please could you run Boot-Repair, click "Advanced options", click the "Backup partition tables..." button, save the ZIP file somewhere, then attach this ZIP file to your message ?

> **Ubu_Fester said:**
> Since my OS is 11.10, shouldn't I use a 64bit 11.10 CD

Not necessary, you can use any version of Ubuntu.

---

### Post by Ubu_Fester on 2012-05-21
Thanks, I will perform those steps tonight when I get back to the pc.

So, sounds like I may be able to save the hard disk?  Or, is it too early to know for sure...

---

### Post by Ubu_Fester on 2012-05-21
Here is the zip file from the boot-repair utility:

I have multiple logs saved (user error), so believe you can ignore logs ids ...16 and ...49

Thanks for investigating!

---

### Post by YannBuntu on 2012-05-22
No error in the logs.
What do you observe exactly when you boot your PC ? do you see the GRUB menu ? if yes, have you tried the "Previous Linux versions" entries?
What do you observe when selecting the entries ?

---

### Post by Ubu_Fester on 2012-05-22
When I first started working on this problem, I was getting a grub menu with ~ 4 options.  
Now, when I reboot, I get the following:

```
Missing operating system.

Reboot and Select proper Boot device
or insert Boot Media in selected Boot device and press a key
```

---

### Post by YannBuntu on 2012-05-22
No more ideas. If i were you, i would simply burn a 12.04 CD and reinstall.
If boot still does not work, try with Ubuntu 10.04 (maybe the problem is due to a GRUB regression).

---

### Post by Ubu_Fester on 2012-05-22
Thanks.  A few more questions:

1) While I have been using Ubuntu CDs (11.10 and 12.04), my install is really mythbuntu.  I presume I can install 12.04 Mythbuntu instead of your suggestion?

2) Do I need GRUB working (installed) even though I am using only a single OS?

3) While I will perform a backup on key folders, the reinstall will only affect my "/" filesystem (sda1 partition), correct? 

4) Once I get this reinstalled, are there some recommended disk utilities to use to check my two hard drives?  Or should the HD checks be done BEFORE I reinstall.

---

### Post by Ubu_Fester on 2012-05-22
Oh, fyi, I'm really not on 10.10 (that's an old profile).

I'm using Mythbuntu 11.10.

---

### Post by YannBuntu on 2012-05-22
1) yes. All flavors (Myth*K*X*L*ubuntu) 12.04 use the same GRUB version.

2) Yes

3) It will keep your /home if you follow this tutorial: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

4) You can check your disks via the "Disk Utility" tool which is in Ubuntu live-CD.

---

### Post by Ubu_Fester on 2012-05-22
Thank you!!

---

