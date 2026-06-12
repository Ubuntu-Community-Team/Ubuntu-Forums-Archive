---
title: "FakeRAID and GPT"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by lilithfr on 2009-12-31
Hello,

I have 2 FakeRAID, one using the standard MBR and one using the GPT.
For the MBR disks (nvidia_aafcgibg), I see the partition in the /dev/mapper but for the GPT disks (nvidia_efcdgcgc) I see nothing.

parted gives me the good partition on the GPT disks so I don't understand why I cannot have access to them.


```

$ ll /dev/mapper
total 0
crw-rw---- 1 root root  10, 60 2010-01-01 12:47 control
brw-rw---- 1 root disk 252,  1 2010-01-01 12:47 nvidia_aafcgibg
brw-rw---- 1 root disk 252,  2 2010-01-01 12:47 nvidia_aafcgibg1
brw-rw---- 1 root disk 252,  0 2010-01-01 12:47 nvidia_efcdgcgc

``````

$ sudo dmraid -r
/dev/sde: nvidia, "nvidia_efcdgcgc", mirror, ok, 2930277166 sectors, data@ 0
/dev/sdd: nvidia, "nvidia_efcdgcgc", mirror, ok, 2930277166 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_aafcgibg", mirror, ok, 976773166 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_aafcgibg", mirror, ok, 976773166 sectors, data@ 0

``````

$ sudo parted /dev/mapper/nvidia_efcdgcgc print
Model: Linux device-mapper (mirror) (dm)
Disk /dev/mapper/nvidia_efcdgcgc: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
 2      135MB   1500GB  1500GB  ntfs         Basic data partition

``````

$ sudo gptsync /dev/mapper/nvidia_efcdgcgc 

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             34       262177  MS Reserved
 2         264192   2930276351  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1           33  ee  EFI Protective
 2             34       262177  c0  Unknown
 3 *       264192   2930276351  07  NTFS/HPFS

Status: Analysis inconclusive, will not touch this disk.

```

---

### Post by lilithfr on 2010-01-01
Hi,

I reply to give information to everybody
The issue is in the dmraid source themself, the binary handles only MBR :(.
I created a new version of dmraid based on the libparted to handle the different partitions and disks.

I attached the patch I made for dmraid.

bye
-- 
Edit: I add missing files

---

### Post by megamandos on 2010-06-20
I know this may be a bit of necro posting, but how do i apply this patch? does anyone know? I thought maybe i would just replace the corresponding files in the dmraid source, but they dont exist...

---

### Post by megamandos on 2010-06-20
ok, so I figured out what that stuff meant and made the changes outlined in that file (patch_dmraid-1.0.0.rc16.txt), and i did "./configure" and that worked i guess... so I did "make" next. And that didnt work so well, appearently './lib/activate/activate.c' is all messed up? Anywho, here is my make output:

```
make -C include
make[1]: Entering directory `/root/1.0.0.rc16/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/1.0.0.rc16/include'
make -C lib
make[1]: Entering directory `/root/1.0.0.rc16/lib'
gcc -MM -MF activate/activate.d -I. -I../include -I../lib -O2 -DDMRAID_NATIVE_LOG -DHAVE_GETOPTLONG -fPIC -Wall -Wundef -Wcast-align -Wwrite-strings -Winline -DDMRAID_TEST -DDMRAID_AUTOREGISTER -O2 -D_LARGEFILE64_SOURCE activate/activate.c; \
    gcc -c -I. -I../include -I../lib -O2 -DDMRAID_NATIVE_LOG -DHAVE_GETOPTLONG -fPIC -Wall -Wundef -Wcast-align -Wwrite-strings -Winline -DDMRAID_TEST -DDMRAID_AUTOREGISTER -O2 -D_LARGEFILE64_SOURCE activate/activate.c -o activate/activate.o
gcc -MM -MF activate/devmapper.d -I. -I../include -I../lib -O2 -DDMRAID_NATIVE_LOG -DHAVE_GETOPTLONG -fPIC -Wall -Wundef -Wcast-align -Wwrite-strings -Winline -DDMRAID_TEST -DDMRAID_AUTOREGISTER -O2 -D_LARGEFILE64_SOURCE activate/devmapper.c; \
    gcc -c -I. -I../include -I../lib -O2 -DDMRAID_NATIVE_LOG -DHAVE_GETOPTLONG -fPIC -Wall -Wundef -Wcast-align -Wwrite-strings -Winline -DDMRAID_TEST -DDMRAID_AUTOREGISTER -O2 -D_LARGEFILE64_SOURCE activate/devmapper.c -o activate/devmapper.o
activate/devmapper.c:15:26: error: libdevmapper.h: No such file or directory
activate/devmapper.c: In function &#8216;mkdm_path&#8217;:
activate/devmapper.c:34: warning: implicit declaration of function &#8216;dm_dir&#8217;
activate/devmapper.c:34: warning: initialization makes pointer from integer without a cast
activate/devmapper.c: In function &#8216;_init_dm&#8217;:
activate/devmapper.c:55: warning: implicit declaration of function &#8216;dm_log_init&#8217;
activate/devmapper.c: At top level:
activate/devmapper.c:60: warning: &#8216;struct dm_task&#8217; declared inside parameter list
activate/devmapper.c:60: warning: its scope is only this definition or declaration, which is probably not what you want
activate/devmapper.c: In function &#8216;_exit_dm&#8217;:
activate/devmapper.c:63: warning: implicit declaration of function &#8216;dm_task_destroy&#8217;
activate/devmapper.c:65: warning: implicit declaration of function &#8216;dm_lib_release&#8217;
activate/devmapper.c:66: warning: implicit declaration of function &#8216;dm_lib_exit&#8217;
activate/devmapper.c: In function &#8216;get_target_list&#8217;:
activate/devmapper.c:79: warning: implicit declaration of function &#8216;dm_task_create&#8217;
activate/devmapper.c:79: error: &#8216;DM_DEVICE_LIST_VERSIONS&#8217; undeclared (first use in this function)
activate/devmapper.c:79: error: (Each undeclared identifier is reported only once
activate/devmapper.c:79: error: for each function it appears in.)
activate/devmapper.c:80: warning: implicit declaration of function &#8216;dm_task_run&#8217;
activate/devmapper.c:80: warning: implicit declaration of function &#8216;dm_task_get_versions&#8217;
activate/devmapper.c: In function &#8216;valid_ttype&#8217;:
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: warning: left-hand operand of comma expression has no effect
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: warning: left-hand operand of comma expression has no effect
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:104: error: dereferencing pointer to incomplete type
activate/devmapper.c: At top level:
activate/devmapper.c:117: warning: &#8216;struct dm_task&#8217; declared inside parameter list
activate/devmapper.c: In function &#8216;handle_table&#8217;:
activate/devmapper.c:141: warning: implicit declaration of function &#8216;dm_task_add_target&#8217;
activate/devmapper.c: At top level:
activate/devmapper.c:151: warning: &#8216;struct dm_task&#8217; declared inside parameter list
activate/devmapper.c: In function &#8216;parse_table&#8217;:
activate/devmapper.c:153: warning: passing argument 2 of &#8216;handle_table&#8217; from incompatible pointer type
activate/devmapper.c:116: note: expected &#8216;struct dm_task *&#8217; but argument is of type &#8216;struct dm_task *&#8217;
activate/devmapper.c: In function &#8216;run_task&#8217;:
activate/devmapper.c:194: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:194: warning: implicit declaration of function &#8216;dm_task_set_name&#8217;
activate/devmapper.c:196: warning: passing argument 2 of &#8216;parse_table&#8217; from incompatible pointer type
activate/devmapper.c:151: note: expected &#8216;struct dm_task *&#8217; but argument is of type &#8216;struct dm_task *&#8217;
activate/devmapper.c:199: error: &#8216;DM_DEVICE_CREATE&#8217; undeclared (first use in this function)
activate/devmapper.c:201: warning: implicit declaration of function &#8216;dm_task_set_uuid&#8217;
activate/devmapper.c:206: warning: passing argument 1 of &#8216;_exit_dm&#8217; from incompatible pointer type
activate/devmapper.c:60: note: expected &#8216;struct dm_task *&#8217; but argument is of type &#8216;struct dm_task *&#8217;
activate/devmapper.c: In function &#8216;dm_create&#8217;:
activate/devmapper.c:217: error: &#8216;DM_DEVICE_CREATE&#8217; undeclared (first use in this function)
activate/devmapper.c: In function &#8216;dm_suspend&#8217;:
activate/devmapper.c:234: error: &#8216;DM_DEVICE_SUSPEND&#8217; undeclared (first use in this function)
activate/devmapper.c: In function &#8216;dm_resume&#8217;:
activate/devmapper.c:242: error: &#8216;DM_DEVICE_RESUME&#8217; undeclared (first use in this function)
activate/devmapper.c: In function &#8216;dm_reload&#8217;:
activate/devmapper.c:252: error: &#8216;DM_DEVICE_RELOAD&#8217; undeclared (first use in this function)
activate/devmapper.c: In function &#8216;dm_remove&#8217;:
activate/devmapper.c:269: error: &#8216;DM_DEVICE_REMOVE&#8217; undeclared (first use in this function)
activate/devmapper.c: In function &#8216;dm_status&#8217;:
activate/devmapper.c:279: error: storage size of &#8216;info&#8217; isn&#8217;t known
activate/devmapper.c:284: error: &#8216;DM_DEVICE_STATUS&#8217; undeclared (first use in this function)
activate/devmapper.c:286: warning: implicit declaration of function &#8216;dm_task_get_info&#8217;
activate/devmapper.c:287: warning: passing argument 1 of &#8216;_exit_dm&#8217; from incompatible pointer type
activate/devmapper.c:60: note: expected &#8216;struct dm_task *&#8217; but argument is of type &#8216;struct dm_task *&#8217;
activate/devmapper.c:279: warning: unused variable &#8216;info&#8217;
activate/devmapper.c: In function &#8216;dm_version&#8217;:
activate/devmapper.c:303: error: &#8216;DM_DEVICE_VERSION&#8217; undeclared (first use in this function)
activate/devmapper.c:305: warning: implicit declaration of function &#8216;dm_task_get_driver_version&#8217;
activate/devmapper.c:306: warning: passing argument 1 of &#8216;_exit_dm&#8217; from incompatible pointer type
activate/devmapper.c:60: note: expected &#8216;struct dm_task *&#8217; but argument is of type &#8216;struct dm_task *&#8217;
make[1]: *** [activate/devmapper.o] Error 1
make[1]: Leaving directory `/root/1.0.0.rc16/lib'
make: *** [lib] Error 2
```

---

### Post by el_nihilo on 2010-08-11
While a dmraid patch to support GPT would be good, a much easier way is to install kpartx (from [multipath-tools]("http://ftp.de.debian.org/debian/pool/main/m/multipath-tools/multipath-tools_0.4.8.orig.tar.gz") - might be available on Ubuntu by default, but I compiled it from source as I'm not actually using an Ubuntu distro) and then run the following to create the missing /dev/mapper partitions (if your fakeRAID nVIDIA raw disk is called /dev/mapper/nvidia_abcdefgh):
```
kpartx -a -v /dev/mapper/nvidia_abcdefgh
```You should then end up with /dev/mapper/nvidia_abcdefgh1, /dev/mapper/nvidia_abcdefgh2, etc. and be able to mount them at last.

---

### Post by blausand on 2010-11-07
I am desperately trying to solve the very same problem.
My System is a **Guru Storm i7** Laptop with two identical HDs á 500GB.
I have setup a _mirror of 120GB_ and _striped the rest to ~720GB_
I setup partitions using the **UbuntuStudio 64 10.10 alternate CD**,
[LIST]
[*]65GB for Windows7
[*]1MB for a bios_grub type and
[*]42GB ext4 for the Linux /
[*]The Swap is on the Stripe.
[/LIST]
Windows put it's EFI Partition on the stripe during the installation and skipped setting up the other 100MB as expected, populating only the ~65GB as the C: drive.
AFTERWARDS i setup Ubuntu itself into the dedicated partitions.

I tried that about **10 times** for both systems now, with and without installing a GrUB.

I burnt three types of Boot Disks including the UBCD 5.0.3,
tried to fix the GRUB2 in many ways.

In most cases, Windows was able to repair its own bootmanager. In most cases, i could get a malconfigured grub starting that does not find the right GPT-Partition for root, reporting:
```
ALERT! /dev/disks/by-uuid/[the wrong UUID] does not exist. 
```

[FONT="Courier New"]dmraid -r[/FONT] lists both disks as [FONT="Courier New"]isw_xxxxx GROUP, ok[/FONT], but no Partitions.

Using Ubuntu's System Repair, i see the /dev/mapper/, but if i run parted, i get:
```
(parted) print
Error: Invalid argument during seek for read in /dev/sda
Ignore
Error: The backup GPT table is corrupt, but the primary appears ok, so that will be used
OK
You found a bug in GNU Parted! ... Don't Panic! ...
Assertion (last_usable <= disk->dev->lengtzh) at
../../../libparted/lables/gpt.c:934 in function _parse_header() failed.
```

I managed chrooting into my System only once from a shell in the live Linux "Parted Magic" once like described [here]("http://wiki.ubuntuusers.de/chroot/Live-CD"), but couldn't [FONT="Courier New"]apt-get install kpartx[/FONT]. The whole System had no idea about the RAID anyway. No [FONT="Courier New"]/dev/dm*[/FONT], no [FONT="Courier New"]/dev/mapper[/FONT], just sda and sdb.
Therefore, following the GrUB reinstallation described [here]("http://wiki.ubuntuusers.de/GRUB_2/Installation#GRUB-2-mittels-Live-CD-auf-einem-System-aktualisieren"), run well but couldn't help at all.
From within the initramfs, i cannot use parted or many other tools.

Also, i can't find the gpt.mod anywhere to put it in my [FONT="Courier New"]/boot/grub/[/FONT]
This is one of the most promising next step i'd like to try. Can anybody tell how?

The BIOS has a switch for trial of "legacy boot" or EFI only.
If i use EFI only, i can only get into the GrUB by adding Ubuntu to the Windows-Bootmanager using the EasyBCD-Tool.

Thanks for any expert suggestions! I think this combination of RAID, GPT, DualBoot with Windows7, dealing with it's super penetrant EFI installation and the murksy GRUB2 is getting quite popular now.

---

### Post by dino99 on 2010-11-07
look at synaptic: 
- gptsync
**** An MBR partition table is required to use legacy bootloaders (lilo, grub) on
EFI-based (Extensible Firmware Interface) machines like the Intel-based Macs.
gptsync is usually used in combination with the rEFIt boot menu on such
machines. ****

---

### Post by srs5694 on 2010-11-07
Personally, I recommend using a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which is what gptsync creates, only as a very last most desperate measure. Hybrid MBRs are flaky, unreliable, and downright dangerous. At least one version of gptsync has a bug that creates a totally invalid hybrid MBR in at least some situations, although I've not investigated this in detail to know the precise versions or trigger conditions for this bug. In the interests of honest disclosure, my own [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) had a similar bug for a couple of versions. (The Apple subforums here see a post about this bug in gptsync every couple of days, on average, although I think the last such post was at least a week ago.) Sorry if I sound strident about this; as the developer of GPT fdisk (gdisk), I keep a close eye on developments related to GPT, and the list of problems related to hybrid MBRs just keeps growing, with more and more outlandish problems cropping up all the time. Hybrid MBRs are an ugly hack and whoever invented them is a menace who should be barred from ever using a computer in the future. (I exaggerate my opinion only slightly.)

OK, rant aside, I have several suggestions for blausand, some of which are mutually exclusive:


[list]
[*]You could try removing the grub-pc package and installing grub-efi-amd64 in its place. This should install the EFI-based version of GRUB rather than the BIOS-based version of GRUB. In principle, this should work better if you're using your firmware's EFI mode to boot, and obviate any need for a hybrid MBR. I can't promise how well it will work in practice, though. It (or, rather, grub-efi-ia32, which is what I need) seems to work on my Mac Mini 1,1, but I haven't yet worked out all the kinks.
[*]You could use another boot loader, such as rEFIt or ELILO, instead of or in addition to GRUB (either grub-pc or grub-efi). I've not tried ELILO, but rEFIt works tolerably on my Mac Mini. I'm not positive, but I think rEFIt relies on either GRUB or ELILO to work, though; AFAIK, it can't load a Linux kernel directly.
[*]You could try GPT fdisk (gdisk) for GPT manipulations rather than GParted. I recommend getting the latest version from [its Sourceforge download page](http://sourceforge.net/projects/gptfdisk/files/) rather than using the version available via APT; the version Ubuntu supplies is woefully out of date. Using GPT fdisk won't solve your booting problems, but it may enable you to see and manipulate your partition table even if GParted is being uncooperative.
[*]Moving to more radical changes, you could consider disabling the motherboard's software RAID. This would probably require you to re-install Windows, but there do seem to be an awful lot of problems related to motherboard-based software RAID. If you're mainly interested in RAID features in Linux, the Linux RAID solutions might be more reliable (although I've seen reports of problems with Linux's software RAID and GPT, so tread cautiously). For striping, Linux's LVM is another option, and one I personally favor over RAID, since it's much more flexible. LVM won't do mirroring, though.
[*]Another more radical solution is to switch from EFI to BIOS mode. Windows will then refuse to boot from EFI, so you'll probably have to switch from GPT to MBR partitions and re-install Windows. Be careful if you make this change, though; you don't want to leave some GPT data behind. I recommend using the "z" option on the gdisk experts' menu to wipe the old GPT data, or using the "g" option on the recovery & transformation menu to convert from GPT to MBR without trashing your partitions; some tools don't do a complete job of GPT-to-MBR conversion, which causes problems down the line when other tools (including GParted) get confused by the conflicting data.
[*]If you seriously need RAID, I recommend buying a true hardware RAID controller rather than rely on software RAID. Such a controller should present your disks as regular Linux disk devices (/dev/sda, etc.), but those devices will link to pre-RAIDed setups, thus reducing the odds of driver/RAID subsystem weirdness. Performance is likely to be better, too. Again, though, going this route will most likely require a complete re-installation of everything.
[/list]

---

### Post by blausand on 2010-11-07
Many thanks for the quick reply! I apreciate people a lot who care about sober implementations like [srs5694]("http://ubuntuforums.org/member.php?u=1032238") does! Keep your attitude up - may the force be with you a hundred and twenty years!

I am dealing with RAID systems since my very first post-ATARI computer (2001). Installing a developer's highly custom configured production environment, which is going to be modified and updated every day, on a non-redundant hardware is like building your house at the foot of a volcano.
Which is why i am so very happy to have two HDs in my Laptop. 

Said this, i liked your first suggestion best and started  looking around for possibilities of post-install the efi-capability and stumbled upon 
[COLOR="Navy"]grub-rescue-efi-amd64_1.98+20100804-5ubuntu3_amd64.deb[/COLOR]
When looking into my DVD image (if it was already included) i realized something that can hardly be explained. I mean, i really care like for checking MD5-sums before burning and so on. But seemingly, i have really managed to download a i386-iso, verifying the MD5, burning, and then celebratively labelling the disc "[COLOR="Navy"]UbuntuStudio 10.10 alternate 64bit[/COLOR]"...

Well, i am just reinstalling the whole bunch. I started erasing the Firmware-RAID and setting up a new one...

---

### Post by blausand on 2010-11-08
I really thought GUIDs were a brilliant idea for partitioning. However, in combination with my motherboard RAID and the BIOS successor EFI it was just evil. 
Here's what happened after 10 days of riddling and veeeeery painful nights of reinstalling the RAID and both operating systems:
[COLOR="Gray"][Just for the bots: My Goal was setting up RAID mirror AND stripe AND Dual boot UbuntuStudio 10.10 x86-64 / Windows7 x86-64 on Clevo W870CU based Laptop, in my case Guru Storm i7][/COLOR]

It turned out that using the motherboard RAID and writing GUID partition tables (GPT) into the resulting volumes via the UbuntuStudio installer DVD was kind of **nesting GPT**, neck-braking the GRUB2. [COLOR="DarkRed"]@srs5694[/COLOR][COLOR="Gray"]: I really tried *anything* a thousand times to get chrooted into the Ubuntu installation and implant that grub-efi-amd64, but i had no chance. apt-install was never installing anything, more like queueing or so. And i couldn't get into the system, because i couldn't map the partitions on the mirror volume from those stupid shells. I'll never install from an alternative ISO anymore; i recommend burning live-CDs and synapticking that ubuntustudio packages.[/COLOR]

Apart from that, using EFI boot, Ubuntu and Windows battled about different ways to write partition tables and so both were in perpetual conflict.
So, in short, it turned out to be possible to boot in both systems only by doing something i hate: Enabling legacy boot mode in the Firmware (fka BIOS). **Windows7 refuses to accept msdos partition tables (those using an MBR), when booting via EFI, but it is calm when EFI is bypassed and the RAID volumes contain good old msdos partition tables.**

[SIZE="4"]Here's a step-by-step guid to accomplish the two systems, both booting from the RAID0 (mirror) volume:[/SIZE]

[COLOR="Plum"]**OK, LETZTER INSTALLATIONSVORGANG! JETZT ALLES ANDERS:**[/COLOR]

[LIST]
[*]_setup a mirror **and** a stripe volume_ in the motherboards RAID-menu. [COLOR="DimGray"]I highly recommend this to combine safety for your systems **and** performance for your redundant media (VJing :) ) To be honest, however, performance test boosts of any software RAID1 *erunt demonstrandum*.[/COLOR]
[*]_setup partitions_ with any Ubuntu DVD capable of prompting you about the SATA_RAID devices and loading [FONT="Courier New"]dmraid-udev[/FONT] automatically.
[*]make sure NOT to choose the [FONT="Courier New"]gpt[/FONT] format, but [FONT="Courier New"]msdos[/FONT] !!!
For me, i choose
[LIST][FONT="Courier New"][*]-500MB ext4 = /boot
[*]  24GB ext4 = /
[*]  80GB FAT32= don't mount
[*]   2GB ext4 = reserved
[*]12.6GB swap on the stripe volume[/FONT][/LIST]
[*]turn off EFI in BIOS ([FONT="Courier New"]Legacy BIOS boot> enable[/FONT])
[*]kill the prepared FAT32 partition with Windows7 DVD and let it resetup the resulting free space automatically.
[*]_install Windows7_ right there.
[*]_install UbuntuStudio 10.10 in EXPERT MODE_
[*]select the package [FONT="Courier New"]partman-udeb[/FONT] and later, choose to setup partitions manually. **Only** assign the existing partitions for installation.
[*]At this point, i choose to _continue *without* installing a bootloader (GRUB)_. [COLOR="DarkRed"]**This might be crucial!**[/COLOR]
[COLOR="Gray"]The installaer told me i'd have to manually start linux with /vmlinuz on /dev/mapper/isw_didhdhcfhg_System2 root=/dev/mapper/isw_didhdhcfhg_System2. I didn't care a lot, i'm gonna install grub2 lateron.[/COLOR]
[/LIST]
[COLOR="Plum"]** 23:50 Montag, 8. November 2010 !! GESCHAFFT !! UbuntuStudio bootet endlich!**[/COLOR]
Now this is how i got the grub installed on the other device so that both bootloaders are present and don't eat each other up:
[LIST]
[*]once again _boot from the Ubuntu DVD_
[*]_go through the setup **completely**_, this time **network is important**.
[*]_start a recovery console_ with root on your target (dm-2 in this scenario). [COLOR="DimGray"]I got some errors in the first place, but after detecting drives and going through the pratition dialog once more it worked. It was useful to check /dev/dm* in parallel consoles (try [FONT="Courier New"][alt]-[F2][/FONT]) hereby.[/COLOR] Now, i guess the dialog performs the process commonly known as *chrooting *into the target system.
[*]Here's what i _told the shell_:
```
#bash
#mount /dev/dm-1 /boot
#apt-get install grub2
[COLOR="DimGray"] // that succeeded for me without complaints.[/COLOR]
#grub-install --root-directory=/ /dev/dm-5  
[COLOR="DimGray"] // that corresponds to the stripe VOLUME isw_xxxx_Data, 
 // not a particular partition.
 // That way, the bootloader of Windows is untouched, 
 // and the one of Ubuntu is on the stripe volume.[/COLOR]
#update-grub
#exit
#exit

```
[*]_reboot system_
[*]as long as the windows boot manager can't boot into Ubuntu (first attempts with easyBCD failed. Haha, there's no BCD anymore...) i _put the stripe-Volume in front_ of the mirror-Volume _in the firmware's boot order_, thus landing in the GRUB2.[/LIST]

Hell Yeah, that was a ride, folks. I hope anybody can make use of those personal experiences. And i hope, more than that, one day the **coexistence of operating systems** is not **pure war on user's sanity** anymore.

So long, hang loose. *And get that damn stuff up and running!*

---

### Post by frillip on 2011-06-02
> **el_nihilo said:**
> While a dmraid patch to support GPT would be good, a much easier way is to install kpartx (from [multipath-tools]("http://ftp.de.debian.org/debian/pool/main/m/multipath-tools/multipath-tools_0.4.8.orig.tar.gz") - might be available on Ubuntu by default, but I compiled it from source as I'm not actually using an Ubuntu distro) and then run the following to create the missing /dev/mapper partitions (if your fakeRAID nVIDIA raw disk is called /dev/mapper/nvidia_abcdefgh):
```
kpartx -a -v /dev/mapper/nvidia_abcdefgh
```You should then end up with /dev/mapper/nvidia_abcdefgh1, /dev/mapper/nvidia_abcdefgh2, etc. and be able to mount them at last.

Thanks el_nihilo, worked perfectly.

---

