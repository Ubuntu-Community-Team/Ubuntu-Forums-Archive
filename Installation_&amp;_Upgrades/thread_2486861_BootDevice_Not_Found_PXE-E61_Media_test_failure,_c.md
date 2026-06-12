---
title: "BootDevice Not Found PXE-E61: Media test failure, check cable Please disable BIOS-com"
date: 2023-05-14
forum: Installation &amp; Upgrades
---

### Post by agitationswapping on 2023-05-14
After giving up on setting up dual boot (the closest I got was both operating systems would boot but I had to enter the really long password I set up in Linux to get into Windows and Windows Update was hopelessly broken), I decided to just get a new hard drive and install what I thought would be the easiest Linux distribution. My laptop makes it super easy to physically swap hard drives so that was my plan to have each OS on a different drive.

I downloaded the Ubuntu 22.04 ISO onto a basically new USB thumb drive, swapped in the new hard drive, and went through the full installation process. Everything seemed to be going reasonably well until the screen came up where it said to disconnect the removable media and press Enter.

When I removed the USB and pressed enter, the following screen came up:

    ```
Intel(R) Boot Agent GE v1.5.50
Copyright (C) 1997-2013 Intel Corporation
    
Intel(R) Boot Agent PXE Base Code (PXE-2.1 build 092)
Copyright (C) 1997-2010, Intel Corporation
    
Initializing and establishing link...
```

About 5 seconds later, it changed to:

    ```
Intel(R) Boot Agent GE v1.5.50
Copyright (C) 1997-2013 Intel Corporation
    
Intel(R) Boot Agent PXE Base Code (PXE-2.1 build 092)
Copyright (C) 1997-2010, Intel Corporation

PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Intel Boot Agent.
```

And then after 3 or so more seconds:

    ```
BootDevice Not Found
    
Please install an operating system on your hard disk.
    
Hard Disk - (3F0)
    
F2 System Diagnostics
    
For more information, please visit: [www.hp.com\go\techcenter\startup]("http://www.hp.com\go\techcenter\startup")
```

When I go to do the standard Hard Drive tests, it says those are "NOT AVAILABLE". Now, this is a brand new hard drive, and while it's possible that there's a manufacturing defect, I'd be surprised such wouldn't come up in the whole installation process.

I can boot into Ubuntu using the USB thumb drive just fine, and it starts up off that thumb drive to "Try Ubuntu". From there, I can see the files on the hard drive and explore them, and so it does seem to be working. In addition, GParted seems to show the partitions all set up:

[https://i.stack.imgur.com/QsJzt.png](https://i.stack.imgur.com/QsJzt.png)


One other thing I've done is [tried the boot-repair tool installed via the terminal]("https://help.ubuntu.com/community/Boot-Repair"). It comes up with this error:
[IMG]https://i.stack.imgur.com/U2mYp.png[/IMG]


The text is as follows:> The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode. This will enable this feature.

I have no idea what it's trying to ask me to do. I fiddled around with many of the options in the BIOS menu I get to by pressing F10 immediately when the PC is starting up, but none of them seem to fix the problem. (On the other hand, they may have contributed to me losing everything I had open in Windows when I swapped back to the Windows hard drive with all the applications hibernated.)

I couldn't get the pastebin thing to work, but here is the raw text of the report that the boot repair tool generates:

    ```
boot-repair-4ppa2056                                              [20230514_0715]
    
============================== Boot Info Summary ===============================
    
 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 2048 
   of the same hard drive for core.img. core.img is at this location and 
   looks for (,gpt3)/boot/grub. It also embeds following components:
   
   modules
   ---------------------------------------------------------------------------
   fshelp ext2 part_gpt biosdisk
   ---------------------------------------------------------------------------
    
sda1: __________________________________________________________________________

   File system:       BIOS Boot partition
   Boot sector type:  Grub2's core.img
   Boot sector info: 
    
sda2: __________________________________________________________________________

   File system:       vfat
   Boot sector type:  FAT32
   Boot sector info:  No errors found in the Boot Parameter Block.
   Operating System:  
   Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                      /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                      /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg
sda3: __________________________________________________________________________
    
   File system:       ext4
   Boot sector type:  -
   Boot sector info: 
   Operating System:  Ubuntu 22.04.2 LTS
   Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                      /boot/grub/i386-pc/core.img
sdb: ___________________________________________________________________________
  
   File system:       iso9660
   Boot sector type:  Grub2 (v1.99-2.00)
   Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                      sdb and looks at sector 0 of the same hard drive for 
                      core.img, but core.img can not be found at this 
                      location.
   Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.
    
================================ 1 OS detected =================================
    
OS#1:   Ubuntu 22.04.2 LTS on sda3
    
================================ Host/Hardware =================================
    
CPU architecture: 64-bit
Video: GK107GLM [Quadro K1100M] 4th Gen Core Processor Integrated Graphics Controller from NVIDIA Corporation Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.2 LTS, jammy, x86_64)
  
===================================== UEFI =====================================
    
BIOS/UEFI firmware: L70 Ver. 01.10(1.10) from Hewlett-Packard
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).


a9c517741ac31962d7feb152948ad1ee   sda2/BOOT/fbx64.efi
a660182adef313615746a665966d2ccc   sda2/BOOT/mmx64.efi
5ddf997e8b025bfbc2009e85b32f60dc   sda2/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   sda2/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   sda2/ubuntu/shimx64.efi
64349b3622c65f495a99dbf6102496e3   sda2/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    hasBIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda3    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios

Partitions info (2/3): _________________________________________________________

sda2    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda3    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
Disk identifier: F39F0C60-4B2B-4D24-A4A5-A6972993BFCA
        Start        End    Sectors   Size Type
sda1     2048       4095       2048     1M BIOS boot
sda2     4096    1054719    1050624   513M EFI System
sda3  1054720 2000408575 1999353856 953.4G Linux filesystem
Disk sdb: 28.91 GiB, 31037849600 bytes, 60620800 sectors
Disk identifier: A0891D7E-B930-4513-94D9-F629DBD637B2
        Start      End  Sectors  Size Type
sdb1       64  9613459  9613396  4.6G Microsoft basic data
sdb2  9613460  9623527    10068  4.9M EFI System
sdb3  9623528  9624127      600  300K Microsoft basic data
sdb4  9625600 60620736 50995137 24.3G Linux filesystem

parted -lm (filtered): _________________________________________________________
 
sda:1024GB:scsi:512:512:gpt:ATA Patriot P210 102:;
1:1049kB:2097kB:1049kB:::bios_grub;
2:2097kB:540MB:538MB:fat32:EFI System Partition:boot, esp;
3:540MB:1024GB:1024GB:ext4::;
sdb:31.0GB:scsi:512:512:gpt:Lexar USB Flash Drive:;
1:32.8kB:4922MB:4922MB::ISO9660:hidden, msftdata;
2:4922MB:4927MB:5155kB::Appended2:boot, esp;
3:4927MB:4928MB:307kB::Gap1:hidden, msftdata;
4:4928MB:31.0GB:26.1GB:ext4::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                
&#9500;&#9472;sda1                                               9ecd8b89-a878-40c7-a82a-8352705315ea                          
&#9500;&#9472;sda2 vfat     5610-9E02                            c7f6faac-8109-4316-b54b-07abfed38800                          EFI System Partition
&#9492;&#9472;sda3 ext4     a138f88d-5722-4fd9-a791-4c83205edbe6 7a22b403-0191-4701-b295-db957648ae3b                          
sdb    iso9660  2023-02-23-04-13-44-00                                                    Ubuntu 22.04.2 LTS amd64 
&#9500;&#9472;sdb1 iso9660  2023-02-23-04-13-44-00               a0891d7e-b930-4513-94d8-f629dbd637b2 Ubuntu 22.04.2 LTS amd64 ISO9660
&#9500;&#9472;sdb2 vfat     F7DB-4D56                            a0891d7e-b930-4513-94db-f629dbd637b2 ESP                      Appended2
&#9500;&#9472;sdb3                                               a0891d7e-b930-4513-94da-f629dbd637b2                          Gap1
&#9492;&#9472;sdb4 ext4     9b6bac4e-b902-4ece-8b1d-70fa231cc82f f9917063-1451-7f4e-9ac5-d66bc8713fe0 writable                 

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/disk/by-label/writable[/install-logs-2023-05-14.1/crash]  22.5G   0% /var/crash
/dev/disk/by-label/writable[/install-logs-2023-05-14.1/log]    22.5G   0% /var/log
/dev/sda2                                                     505.9M   1% /mnt/boot-sav/sda2
/dev/sda3                                                     878.1G   1% /mnt/boot-sav/sda3
/dev/sdb1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________


===================== sda2/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid a138f88d-5722-4fd9-a791-4c83205edbe6 root hd0,gpt3 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda3/boot/grub/grub.cfg (filtered) ======================

Ubuntu   a138f88d-5722-4fd9-a791-4c83205edbe6
Ubuntu, with Linux 5.19.0-41-generic   a138f88d-5722-4fd9-a791-4c83205edbe6
Ubuntu, with Linux 5.19.0-32-generic   a138f88d-5722-4fd9-a791-4c83205edbe6
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda3/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=a138f88d-5722-4fd9-a791-4c83205edbe6 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=5610-9E02  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

======================= sda3/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

 ==================== sda3: Location of files loaded by Grub ====================
               GiB - GB             File                                 Fragment(s)
 512.448955536 = 550.237876224  boot/grub/grub.cfg                             1
 480.467124939 = 515.897647104  boot/grub/i386-pc/core.img                     1
  80.608036041 = 86.552219648   boot/vmlinuz                                   1
 713.737300873 = 766.369591296  boot/vmlinuz-5.19.0-32-generic                 2
  80.608036041 = 86.552219648   boot/vmlinuz-5.19.0-41-generic                 1
 713.737300873 = 766.369591296  boot/vmlinuz.old                               2
 128.600528717 = 138.083766272  boot/initrd.img                                1
 176.561367035 = 189.581324288  boot/initrd.img-5.19.0-32-generic              2
 128.600528717 = 138.083766272  boot/initrd.img-5.19.0-41-generic              1
 176.561367035 = 189.581324288  boot/initrd.img.old                            2

===================== sda3: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Dec  2 15:18 10_linux
-rwxr-xr-x 1 root root 43031 Dec  2 15:18 10_linux_zfs
-rwxr-xr-x 1 root root 14180 Dec  2 15:18 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec  2 15:18 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec  2 15:18 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Sep 20  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Dec  2 15:18 40_custom
-rwxr-xr-x 1 root root   215 Dec  2 15:18 41_custom


Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda3,
using the following options:  sda2/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Blockers in case of suggested repair: __________________________________________

  The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode. This will enable this feature.
    
Final advice in case of suggested repair: ______________________________________
    
Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.2 LTS entry (sda2/efi/****/grub****.efi (**** will be updated in the final message) file) !
The boot of your PC is in BIOS-compatibility/CSM/Legacy mode. You may want to retry after changing it to UEFI mode.
```

There's a bit more there but I'm still not sure exactly what it's asking me to do. My best guess is that I have to create a different bootable USB with the boot-repair in "UEFI" mode, and also change something in the BIOS, but I have no idea what. Has anyone encountered this before and what do I need to do - step by step?

---

### Post by jeremy31 on 2023-05-14
Try going into BIOS settings, System Config go to UEFI boot order, press enter select ubuntu, then press F10 twice, save settings and exit BIOS

---

### Post by agitationswapping on 2023-05-14
Okay here is what I see in the BIOS screen I can get to by pressing F10:
[img]https://i.imgur.com/KNxpYbi.jpg[/img]

There is nothing which says "System Config" that I can see.

In the "Advanced" tab I did find "Boot Options" and a "UEFI Boot Order" screen but it is greyed out.
[img]https://i.imgur.com/TY4N2SY.png[/img]
[img]https://i.imgur.com/RAmyC2v.png[/img]

If I select any of the two UEFI options (with or without CSM), then the computer will just restart repeatedly after briefly displaying text that says something similar to "SYSTEM RESET".

---

### Post by jeremy31 on 2023-05-14
Does it give any options if you choose "OS Boot Manager" under UEFI Boot Order?

---

### Post by agitationswapping on 2023-05-14
In the meantime, as a test, I installed Windows 10 and that is booting completely fine on the new hard drive.

In order to be able to change the UEFI Boot Order, I had to switch the Boot Mode. I switched to "UEFI Hybrid (With CSM)". Then I put "OS Boot Manager" on top.
[COLOR=unset][/COLOR][COLOR=unset][/COLOR][COLOR=unset][/COLOR][IMG]https://i.imgur.com/d8BjiR2.png[/IMG]
[IMG]https://i.imgur.com/HjwGaUG.png[/IMG]

Windows 10 continued to launch just fine with these settings.

Then I plugged back in the USB  for Ubuntu and used F9 repeatedly to  select to launch that USB and installed it, overwriting the Windows 10  installation. (Windows 10 no longer launched just fine with that setting.) As before, with OS Boot Manager I briefly see this text  which says "Reset System", followed by the system resetting.
[IMG]https://i.imgur.com/IutrTPE.png[/IMG]

The  system continues to start up and reset over and over again until I push  a key like F9 to select a different option. For example, if I select  "Notebook Hard Drive" I'm back to the "BootDevice Not Found" error as in  my original post.

None of the other options seem to help, unless I plug back in the Ubuntu USB stick. In which case I can "Try Ubuntu" just fine.

---

### Post by tea for one on 2023-05-15
Your boot-repair report in post 1 shows sda1 as a BIOS boot partition.
This means that you installed in old-fashioned Legacy mode.

Would you be prepared to start from scratch?
UEFI settings > UEFI Native (Without CSM)
Boot into a live session, open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```
Hopefully, you will see "UEFI mode" and then allow the installer to use default settings.

Edit: Even better if you create GPT (via Gparted) on your disk before starting the installation.

---

### Post by jeremy31 on 2023-05-15
> **tea for one said:**
> Your boot-repair report in post 1 shows sda1 as a BIOS boot partition.
This means that you installed in old-fashioned Legacy mode.

Would you be prepared to start from scratch?
UEFI settings > UEFI Native (Without CSM)
Boot into a live session, open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```
Hopefully, you will see "UEFI mode" and then allow the installer to use default settings.

Edit: Even better if you create GPT (via Gparted) on your disk before starting the installation.

I agree that this would be a good starting point

---

### Post by MAFoElffen on 2023-05-15
I recognize the screenshot as being of HP UEFI BIOS Settings.

As I remember oldfred, tea for one, and I ran into this with a user with and HP ZBook laptop last January... As far as I can remember, the only way you could disable SecureBoot was to set to UEFI Hybrid, without CSM, then burn the LiveUSB (with Rufus) as GPT, with only UEFI... But there were other specific BIOS options, that also had to be set, because just doing that UEFI Hybrid setting then caused a boot (error) loop...

But my memory on that is a little fuzzy at the moment. To confirm, I found that thread/post, and here was the post where the golden-secret key to the right combination of BIOS settings was found to be able to work:
[https://ubuntuforums.org/showthread.php?t=2482555&p=14125216#post14125216](https://ubuntuforums.org/showthread.php?t=2482555&p=14125216#post14125216)

I hope these specific UEFI settings in that post work for you...

---

### Post by tea for one on 2023-05-16
@MAFoElffen - Memory successfully jogged.

There are also some other UEFI setting, which may be relevant for the OP:-

Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot (It may prevent access to one-time boot menu via dedicated keys because the device boots too fast) 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500)
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module) or TPT (Trust Platform Technology)
Disable Optane memory and storage
Remove Optane drive and reset UEFI to default (with the suggested changes above)
[https://ubuntuforums.org/showthread.php?t=2471365](https://ubuntuforums.org/showthread.php?t=2471365)

---

### Post by agitationswapping on 2023-05-16
I have got it "working".

Ubuntu would only install in UEFI mode, no matter what options I selected. My Windows was/is definitely in CSM/Bios/Legacy.

Even though the BIOS was set to CSM/Legacy/Bios only, the installer put Ubuntu in UEFI mode. So when I pushed enter and removed the USB, the BIOS couldn't find it, because EFI support wasn't enabled in the BIOS at that time (and I didn't know what it was).

The other thing that may have helped was upgrading the BIOS. To do that, I downloaded the HP Support Assistant in Windows and set that up. The progress of upgrading the BIOS was fairly straightforward. It's not clear to me whether that helped or not, but the BIOS was out of date (version from 2014) and it certainly didn't hurt. I obviously can't easily downgrade the BIOS to test with.

I haven't managed to install Ubuntu in CSM/Bios/Legacy mode and I'm not really sure how I might do that. I don't think this is a reasonable expectation of a new user to learn all about UEFI mode and make BIOS changes to get their Ubuntu working. That took me hours to figure out.

At the moment, I set the BIOS to UEFI Hybrid with CSM support ("UEFI Hybrid (With CSM)" option). That means Windows starts just fine, but for Ubuntu I have to rapidly tap F9 and then go into an "EFI Boot Manager", then go through various menu options to select "ubuntu" and something like "grub32.efi". If I don't do that, then I get the endless "RESET SYSTEM" loop, or "3F0 No Bootable Drive" from the other options.

The other option is to switch the BIOS back and forth to UEFI every time. I don't think it's much easier, and I believe doing that is destroying my hibernation sessions in Windows. I'm not really prepared to reinstall Windows in UEFI mode.

Another unfortunate side effect - it seems like the computer time gets reset to UTC every single time, which I just observed even with UEFI hybrid with CSM support being left alone in the BIOS. Then I need to uncheck and recheck "Set time automatically" in Windows and it will go back to my local time. But at least it seems like if I leave the BIOS alone in hybrid mode, my Windows hibernation sessions haven't been destroyed (yet).

Unrelated issues - I can't get any hibernation to work in Ubuntu, and I managed to get the VPN to connect properly twice. The rest of the time, the VPN says it connected, but anyone I connect to says my IP address is just the normal one. (I will have to post about the VPN separately.)

---

### Post by oldfred on 2023-05-16
You typically cannot dual boot on same drive with UEFI & BIOS with Windows.
Windows requires boot flag on its boot partition. UEFI has boot,esp flags on the ESP. Only one boot flag per drive.
Grub may still boot a working Windows as it ignores boot flags & looks for boot files. But if Windows turns on fast start up or needs chkdsk then grub will not boot it.
Grub will not boot an install in different boot mode. Once you start booting in one mode UEFI or BIOS you cannot switch.

If boot flag moved back to Windows boot partition in BIOS mode, the UEFI boot entry may still work as it uses GUID of ESP once installed. But later I would expect issues.

Best to see details:
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB live installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by mIk3_08 on 2023-05-16
> **agitationswapping said:**
> I have got it "working".

If your query has been sorted then you can mark this thread as solve.
On how to mark this thread as solve,
Please Click the "Solve thread" link below.
> **agitationswapping said:**
> 
Unrelated issues - I can't get any hibernation to work in Ubuntu, and I  managed to get the VPN to connect properly twice. The rest of the time,  the VPN says it connected, but anyone I connect to says my IP address is  just the normal one. (I will have to post about the VPN  separately.)
It would be best if you will open another thread for this. Regards and cheers.

---

### Post by agitationswapping on 2023-06-04
Thanks everyone for the help. Yes, I got it to work but it's still not ideal because having to select in the boot menu quickly every time I start Ubuntu is annoying.

> **agitationswapping said:**
> I haven't managed to install Ubuntu in CSM/Bios/Legacy mode and I'm not really sure how I might do that.

> **oldfred said:**
> Grub will not boot an install in different boot mode. Once you start booting in one mode UEFI or BIOS you cannot switch.

If I understand, you are saying it's not possible to change an Ubuntu operating system installation from UEFI mode to Bios mode (or vice versa). Or is this about when the system (PC) first starts up after you've booted you can't go back and change modes?

Supposing that I wanted to start over and install Ubuntu in CSM/Bios/Legacy mode (same as Windows is presently), would that be possible? Or is Ubuntu restricted to only start in UEFI mode with no practical Bios/CSM/Legacy start option available? If no support for Bios/CSM/Legacy mode, why not? Is that unique to Ubuntu or also with other Linux distributions?

If Ubuntu does support a Bios/CSM/Legacy mode, is there any way to switch the Ubuntu from UEFI booting to Bios booting and still keep the files/setup intact? If not, then what makes this not practical?

Thanks again.

---

### Post by oldfred on 2023-06-04
You can convert an Ubuntu install relatively easily.
The only real difference is the version of grub2. BIOS uses grub-pc and UEFI uses grub-efi-amd64. A few settings are automatically changed with the change in grub install, like mount of ESP in fstab.

What you cannot do is once you start to boot is change boot mode and then grub can only boot other installs in same boot mode. UEFI/BIOS writes hardware configuration data onto drive for operating ssystem as part of UEFI pre-boot. UEFI fast boot skips that step and assumes no hardware change. But UEFI writes that data to drive differently and BIOS writes that data.

While from within Ubuntu you can reinstall grub, often easier with Boot-Repair.
How you boot live installer UEFI or BIOS is both how it repair or installs.
So boot Boot-Repair in BIOS mode, and choose advanced mode & total reinstall of grub.

---

### Post by agitationswapping on 2023-06-11
> **oldfred said:**
> You can convert an Ubuntu install relatively easily.

> **oldfred said:**
> While from within Ubuntu you can reinstall grub, often easier with Boot-Repair.
How you boot live installer UEFI or BIOS is both how it repair or installs.
So boot Boot-Repair in BIOS mode, and choose advanced mode & total reinstall of grub.

So I [found this guide here]("https://help.ubuntu.com/community/Grub2/Installing"):
> **Reinstalling GRUB 2 from a Working System**

[COLOR=#333333][FONT=Ubuntu]If Ubuntu is operating normally, boot into the working installation and run the following command from a terminal.[/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit][FONT=inherit]**X**[/FONT] is the [FONT=inherit]drive[/FONT] (letter) on which you want GRUB to write the boot information. Normally users should **not** include a partition number, which would produce an error message as the command would attempt to write the information to a partition.[/FONT]
sudo grub-install /dev/sdX  # Example: sudo grub-install /dev/sda
[/LIST]
[COLOR=#333333][FONT=Ubuntu]This will rewrite the MBR information to point to the current installation and rewrite some GRUB 2 files (which are already working). Since it isn't done during execution of the previous command, running sudo update-grub after the install will ensure GRUB 2's menu is up-to-date.[/FONT][/COLOR]
Is this the right kind of strategy and I just need to modify the command somehow to ensure it installs in BIOS mode?

```
sudo grub-install /dev/sdX # Example: sudo grub-install /dev/sda
```

When I tried to figure out what I need to do differently to make sure it installs in CSM/BIOS/Legacy mode I only found [a couple sources]("https://askubuntu.com/questions/1433692/how-to-boot-ubuntu-with-legacy-bios-and-gpt-without-to-need-grub-lilo-or-uefi") and none seemed helpful.

[This one]("https://help.ubuntu.com/community/Grub2/Installing") had some note but I'm not understanding it at the moment:> [COLOR=#333333][FONT=Ubuntu]If the BIOS is setup to boot the disk in [/FONT][/COLOR][Legacy/mbr mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")[COLOR=#333333][FONT=Ubuntu], installing GRUB2 on a GPT (GUID Partition Table) disk requires a dedicated BIOS boot partition with a recommended size of at least 1 MiB. This partition can be created via [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][GParted]("https://help.ubuntu.com/community/GParted")[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] or other partitioning tools, or via the command line. It must be identified with a [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]bios_grub[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] flag. The necessary GPT modules are automatically included during installation when GRUB 2 detects a GPT scheme.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]If you could help either give me something more step by step or point me in the direction of a better tutorial for what I'm trying to do (take my working UEFI Ubuntu installation and get a working CSM/Legacy/BIOS Ubuntu installation without losing any data) that would be really awesome.

Thanks so much![/FONT][/COLOR]

---

### Post by oldfred on 2023-06-12
if Windows is in BIOS mode, the drive has to be MBR(msdos).
And with MBR you do not need bios_grub partition.

Generally better to use gpt, but Windows requires MBR for BIOS installs.
And Windows requires gpt partitioning for UEFI installs.

Post link to summary report from Boot-Repair.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If booted in UEFI mode, just reinstalling grub will reinstall the UEFI version.

You can do this, but if any step fails, you will not be able to boot. So must have good backups & a repair Ubuntu live installer.
# purge old and reinstall new to sda (BIOS version)
Make sure repositories are updated
sudo apt update
sudo apt upgrade
sudo apt purge grub-efi-amd64 grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub
sudo update-initramfs -u -k

---

