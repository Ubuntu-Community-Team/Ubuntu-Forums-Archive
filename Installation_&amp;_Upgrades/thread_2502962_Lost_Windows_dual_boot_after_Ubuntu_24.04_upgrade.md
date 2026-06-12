---
title: "Lost Windows dual boot after Ubuntu 24.04 upgrade"
date: 2024-12-08
forum: Installation &amp; Upgrades
---

### Post by nitescan2 on 2024-12-08
Here are the results of boot-repair that I ran just a bit ago. I appreciate any help you can give me on this. I'm not that well versed on the root level of Linux & how things can get mucked up from just upgrading. I don't want to get to far out on my own here without somebody guiding me on how to proceed. Thank You. 


```
boot-repair-4ppa2081                                              [20241208_0704]

============================== Boot Info Summary ===============================


 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe


sda3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda4: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda6: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 24.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img




================================ 3 OS detected =================================


OS#1 (linux):   The OS now in use - Ubuntu 24.04.1 LTS on sda6
OS#2 (windows):   Windows 10 (boot) on sda1
OS#3 (windows):   Windows 10 or 11 on sda2


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: RV730 PRO [Radeon HD 4650] from Advanced Micro Devices, Inc. [AMD/ATI]
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.8.0-49-generic root=UUID=6dfe59ef-2f2d-4206-bf83-98bd7bc14a57 ro quiet splash vt.handoff=7
df -Th / : /dev/sda6      ext4  358G   23G  317G   7% /


===================================== UEFI =====================================


BIOS/UEFI firmware: WBIBX10J.86A.0319.2011.0223.2022(0.0) from Intel Corp.
This installed-session is in Legacy/BIOS/CSM mode (not in EFI mode).






============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda6    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
sda2    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda3    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda1    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far


Partitions info (2/3): _________________________________________________________


sda6    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot, ntfs


Partitions info (3/3): _________________________________________________________


sda6    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0xf03a5a86
     Boot     Start       End   Sectors   Size Id Type
sda1  *         2048    206847    204800   100M  7 HPFS/NTFS/exFAT
sda2          206848 203701000 203494153    97G  7 HPFS/NTFS/exFAT
sda3       203702272 204799999   1097728   536M 27 Hidden NTFS WinRE
sda4       204802046 976771071 771969026 368.1G  5 Extended
sda5       968407040 976771071   8364032     4G 82 Linux swap / Solaris
sda6       204802048 968407039 763604992 364.1G 83 Linux
Partition table entries are not in disk order.


parted -lm (filtered): _________________________________________________________


sda:500GB:scsi:512:512:msdos:ATA Samsung SSD 850:;
1:1049kB:106MB:105MB:ntfs::boot;
2:106MB:104GB:104GB:ntfs::;
3:104GB:105GB:562MB:ntfs::msftres;
4:105GB:500GB:395GB:::;
6:105GB:496GB:391GB:ext4::;
5:496GB:500GB:4282MB:linux-swap(v1)::swap;


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL           PARTLABEL
sda                                                                                                       
&#9500;&#9472;sda1 ntfs     22020C47020C2301                     f03a5a86-01                          System Reserved 
&#9500;&#9472;sda2 ntfs     62FC1A5CFC1A2B35                     f03a5a86-02                                          
&#9500;&#9472;sda3 ntfs     1C1AF9B61AF98CD0                     f03a5a86-03                                          
&#9500;&#9472;sda4                                               f03a5a86-04                                          
&#9500;&#9472;sda5 swap     0a277204-ff22-4b43-b315-ba339fabea89 f03a5a86-05                                          
&#9492;&#9472;sda6 ext4     6dfe59ef-2f2d-4206-bf83-98bd7bc14a57 f03a5a86-06                                          


Mount points (filtered): _______________________________________________________


                        Avail Use% Mounted on
/dev/sda1               70.3M  30% /mnt/boot-sav/sda1
/dev/sda2               22.4G  77% /mnt/boot-sav/sda2
/dev/sda3              108.3M  80% /mnt/boot-sav/sda3
/dev/sda6              316.3G   6% /


Mount options (filtered): ______________________________________________________


/dev/sda1              fuseblk         ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda2              fuseblk         ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda3              fuseblk         ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda6              ext4            rw,relatime,errors=remount-ro


====================== sda6/boot/grub/grub.cfg (filtered) ======================


Ubuntu   6dfe59ef-2f2d-4206-bf83-98bd7bc14a57
Windows 10 (on sda1)   22020C47020C2301
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###


========================== sda6/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=6dfe59ef-2f2d-4206-bf83-98bd7bc14a57 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0


======================= sda6/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


==================== sda6: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
 256.713973999 = 275.644530688  boot/grub/grub.cfg                             1
 287.844085693 = 309.070233600  boot/grub/i386-pc/core.img                     1
 161.139904022 = 173.022654464  boot/vmlinuz                                   2
 240.254070282 = 257.970843648  boot/vmlinuz-5.15.0-126-generic                2
 161.139904022 = 173.022654464  boot/vmlinuz-6.8.0-49-generic                  2
 240.254070282 = 257.970843648  boot/vmlinuz.old                               2
 198.907222748 = 213.575004160  boot/initrd.img                                6
 109.376651764 = 117.442285568  boot/initrd.img-5.15.0-126-generic             1
 198.907222748 = 213.575004160  boot/initrd.img-6.8.0-49-generic               6
 109.376651764 = 117.442285568  boot/initrd.img.old                            1


===================== sda6: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18133 Apr  4  2024 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4  2024 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4  2024 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4  2024 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4  2024 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4  2024 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Aug 21 13:39 35_fwupd
-rwxr-xr-x 1 root root   214 Feb  7  2019 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom






Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would reinstall the grub2 of
sda6 into the MBR of sda.
Grub-efi would not be selected by default because no ESP detected.
Additional repair would be performed: unhide-bootmenu-10s win-legacy-basic-fix
```

---

### Post by grahammechanical on 2024-12-08
Can you still boot in to Microsoft Windows? If so make sure that Fast Startup is turned off. Then boot into Ubuntu and run

```
sudo update-grub
```

Watch the printout. Is Windows detected?

Regards

---

### Post by oldfred on 2024-12-08
How old is computer hardware?
Microsoft required vendors to install Windows in UEFI boot mode to gpt partitioned drives since 2012.
You have BIOS boot with very old MBR(msdos) partitioning. Often used with Windows 7.
But systems before 2012 are typically not spec 'd high enough for Ubuntu, so a lightweight flavor is better.

I use Kubuntu for both old & new systems, but it is more middle-weight.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

If dual booting with old BIOS on one drive, you only have one MBR for booting. So you always need both a Windows repair/recovery drive & Ubuntu live installer to make repairs & reinstall boot loader to MBR.

With UEFI all boot loaders exist in one ESP - efi system partition and all systems can be directly booted from UEFI boot menu. Or relatively easy to switch boot from one system to another.

But with BIOS you have to have correct boot loader in MBR. Grub will boot Windows as long as Windows has no issue, no fast startup and no bitlocker.
Since Windows turns fast startup/hibernation back on with update or NTFS may need chkdsk or defrag, you then cannot boot Windows from grub. You have to restore Windows or a Windows type BIOS boot loader & fix Windows. Then restore grub to dual boot again.

If newer system, better to plan conversion to UEFI/gpt, but changing a drive from MBR to gpt totally erases a drive or good backups required.

---

### Post by nitescan2 on 2024-12-08
> **grahammechanical said:**
> Can you still boot in to Microsoft Windows? If so make sure that Fast Startup is turned off. Then boot into Ubuntu and run

```
sudo update-grub
```

Watch the printout. Is Windows detected?

Regards

1st- Thanks so much for helping. No, I cannot boot into windows. I do not get any choices now since the upgrade(yesterday). I was getting a choice for Ubuntu or Windows but, not now. In fact I just get a black screen for seems like maybe 30 secs to a min, then Ubuntu starts. Here is a screen shot of grub update run. I believe the "found memtest86+64 image: /boot/memtest85+64.bin is where I usually boot into. I was running Ubuntu 20.04 before this upgrade without any problems what-so-ever, very solid.

---

### Post by nitescan2 on 2024-12-08
> **oldfred said:**
> How old is computer hardware?
Microsoft required vendors to install Windows in UEFI boot mode to gpt partitioned drives since 2012.
You have BIOS boot with very old MBR(msdos) partitioning. Often used with Windows 7.
But systems before 2012 are typically not spec 'd high enough for Ubuntu, so a lightweight flavor is better.

I use Kubuntu for both old & new systems, but it is more middle-weight.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

If dual booting with old BIOS on one drive, you only have one MBR for booting. So you always need both a Windows repair/recovery drive & Ubuntu live installer to make repairs & reinstall boot loader to MBR.

With UEFI all boot loaders exist in one ESP - efi system partition and all systems can be directly booted from UEFI boot menu. Or relatively easy to switch boot from one system to another.

But with BIOS you have to have correct boot loader in MBR. Grub will boot Windows as long as Windows has no issue, no fast startup and no bitlocker.
Since Windows turns fast startup/hibernation back on with update or NTFS may need chkdsk or defrag, you then cannot boot Windows from grub. You have to restore Windows or a Windows type BIOS boot loader & fix Windows. Then restore grub to dual boot again.

If newer system, better to plan conversion to UEFI/gpt, but changing a drive from MBR to gpt totally erases a drive or good backups required.
 


1st- Thank you for helping out, very much appreciated.
I'm guessing my hardware is probably older, I will try to pinpoint an exact year cuz my brain is certainly older & CRS- with that I will do some digging. I don't believe Windows 7 was on this computer, I want to say 10 was a clean install, then Ubuntu 12 or maybe even older. Certainly don't remember having to go change the UEFI option in bios- but it's probably always been enabled, so there's that. I have one SSD installed dual booting with that.

---

### Post by yancek on 2024-12-08
Check the /etc/default/grub file to see if it has the line:  GRUB_DISABLE_OS_PROBER=false  to that file.  If it there and has a # at the beginning of the line, delete the # so that script is run.  If that line is there, it is some other problem.  If the line does not exist and you add it to the file (you need to be root/use sudo to edit the file), you will need to run sudo update-grub to add windows to the menu.  Did you check the /boot/grub/grub.cfg file to see if there is an entry for windows?  If not, do that.

The first partition on that drives shows as ntfs and shows as the boot drive which is the way windows 7 was installed.

---

### Post by nitescan2 on 2024-12-08
> **yancek said:**
> Check the /etc/default/grub file to see if it has the line:  GRUB_DISABLE_OS_PROBER=false  to that file.  If it there and has a # at the beginning of the line, delete the # so that script is run.  If that line is there, it is some other problem.  If the line does not exist and you add it to the file (you need to be root/use sudo to edit the file), you will need to run sudo update-grub to add windows to the menu.  Did you check the /boot/grub/grub.cfg file to see if there is an entry for windows?  If not, do that.

The first partition on that drives shows as ntfs and shows as the boot drive which is the way windows 7 was installed.


TY yancek, see attached- this is what's in my grub. I have thought all along I would have to edit & enable the prober as per the instructions. I'm just taking it kinda slow as I really don't want to cause any more problems than I already have. Just making sure as I go.

---

### Post by nitescan2 on 2024-12-09
This morning I enabled the GRUB_DISABLE_OS_PROBER=false line, did the update. Rebooted, same thing- Went into the grub.cfg file..... it's gonna be a minute for me to cipher all of that, I'm old- I did see where windows 10 entry is listed in that cfg file, also where os_prober begins & what it lists. Like I said it'll be a minute for ciphering what it all means. 
Just thought I would report this update. 
If I can do anything else please direct me!
Regards

---

### Post by yancek on 2024-12-09
Your windows entry should look like the example below.  sda1 is 100MB and is shown as Reserved and sda3 is 536MB which is too small to hold the windows OS but sda2 is 97GB which would be the main windows partition.  I don't know what purpose sda2 has.  In post 4, you show an image which lists windows on sda1.  With Windows 7, that would likely have been a boot partition but it is shown as Reserved in boot repair but it has some windows boot files shown in boot repair. 

> menuentry "Windows 10" {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos2)'
chainloader +1
} 

If you have an entry similar to the above and it shows (hd0,msdos1), try changing that to (hd0,msdos2).
Another thing to check is to use gparted from Ubuntu and highlight sda2, right lick on it in the main window and click on manage flags, check if the box to the left of boot is checked.  Do the same with sda1 to see which is set to boot/active.  This is needed on windows for the partition with the boot files but is not used with Linux systems.

---

### Post by nitescan2 on 2024-12-09
OK, will do- it does in fact show set root='(hd0,msdos1)' - I will make the modification & report back.

---

### Post by nitescan2 on 2024-12-09
Just checked in gparted, dev/sda1 flag is checked for boot, dev/sda2 flag is unchecked for boot. Should I check the boot flage for sda2?

---

### Post by yancek on 2024-12-09
Put the boot flag on sda2 from gparted.  I would suggest you make notes of the changes you are making in case it does not work.  The boot flag on sda1 would be expected with an old windows 7 install which used a separate boot partition.  Do you know if this computer was originally windows 7 and was updated to 10?

If this change fails make not of any warning/error messages you get.  If you have a proper Grub entry and booting windows fails, it is likely that windows boot files are corrupt and you cannot fix that from Linux.

---

### Post by nitescan2 on 2024-12-09
Yes sir, I believe it was originally win7, upgraded along the way. Plus 1 on the paper trail. I gotta run right now, but when I have time later to spend on it- I will make the appropriate changes & log everything. Thanks a million!!

---

### Post by nitescan2 on 2024-12-10
OK, here's the latest(might be lengthy read, but very-very simple solution). Back in reply #4 I stated I do not get any choices when my machine starts up, whereas I always got a choice before the upgrade. Well I couldn't get over the fact my console was not reporting anything during the boot process after the hand-off from the bios. I never lost sight of this fact- I didn't mention it again or bring it to the front again, I just went after the fact that windows wasn't booting or giving me the option of booting, maybe I didn't word it correctly. But, this morning I made up my mind to see if even the correct grub was in fact loading. Back in the day.... way, way back you could test your config file just by directing it to display a simply "hello". This is what I went for this morning- I wanted to see the grub post up on the monitor. It was right in plain sight- even back in post #7 attachment- Timeout style=hidden. You guessed it.... changed that to menu & voila- I get to choose to boot into Win-Blows. It went right into windows after I chose- so I'm pretty well fixed now & didn't change a thing except 1 word. 
Thank You yancek for sticking with me & helping, I do appreciate it very much!
I belong to a lot of forums & read a ton, only when I'm truly stuck will I seek help, likewise- I will not reply to somebody "if" I cannot 100% give good advice, I don't/will not post to receive any kind of recognition for it. I had visions of Ubuntu relegating to the Apple I-Phone days when Apple sent an update & rendered my phone un-usable( 2 times now), 1st time they paid a healthy fine for it, this 2nd time was with Iphone7, working perfectly- get coverage even in sparse areas, then one day you would call, I can hear you but you can't hear me...... absolutely no fix what-so-ever. You'll have to purchase a new phone- I did, Iphone 13- it's the absolute worst, especially in sparse areas where ol 7 worked. It cost me 400 dollars for a new windshield the last time I was in Texas. Thanks for all the help- if there's something more with/about this upgrade I should perform, please let me know. 
Regards

---

