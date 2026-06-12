---
title: "[SOLVED] My computer freezes when I use a USB drive boot and I can't reinstall Ubuntu"
date: 2021-09-14
forum: Installation &amp; Upgrades
---

### Post by thealpman on 2021-09-14
Hello,
After a worsening freezing problem ([https://ubuntuforums.org/showthread.php?t=2466904](https://ubuntuforums.org/showthread.php?t=2466904)), I decided to reinstall Ubuntu from a USB drive.
I tried with Ubuntu 21.04, my screen froze after error messages at the beginning.
[[IMG]https://i.ibb.co/jzHGCDd/IMG-20210913-190732.jpg[/IMG]]("https://ibb.co/jzHGCDd") [URL="https://ibb.co/mD3xRXh"][IMG]https://i.ibb.co/mD3xRXh/IMG-20210913-190847.jpg[/IMG]

[/URL]
I also tried with Ubuntu Mate 20.04.3 and Ubuntu 20.04.3, it froze again with slightly different error messages at the beginning.
 [URL="https://ibb.co/hZSJzbY"][IMG]https://i.ibb.co/hZSJzbY/IMG-20210913-200747.jpg[/IMG]


 [/URL]Can it be a hardware problem ? Is it useful to reset/upgrade the BIOS ? How can I do it ?

Thank you for your help.

(My config : PCspecialist Initia Series (~Clevo NL51LU) Intel i5-1035G1, 2x8GB Corsair 2133MHz SODIMM DDR4, Integrated Intel® HD Graphics, 1TB SEAGATE BARRACUDA 120 2.5" SSD)

---

### Post by tea for one on 2021-09-14
There are various things to try, here my suggestions:-

Power off and use the dedicated key to access the UEFI firmware.

Reset the UEFI/BIOS to default
Disable Secure Boot
Disable Fast Boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Disable TPM

Remake your bootable thumb drive (use [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb))
Try all your USB ports
Change the thumb drive

---

### Post by MAFoElffen on 2021-09-14
I looked at your linked post... And the problems were on Kernel 5.4, DRM, hardware related missing filetypes and folders. I can see that you are UEFI BIOS, and Intel CPU/APU using the i915 graphics driver in the Kernel..

What Computer is this and is there UEFI firmware updates available for it?

Next, after you update the firmware... My recommendation for installation would be, for the types of errors you are getting, to install 20.04.3... But when booting the USB, quickly arrow down to the lower Grub Menu selection of installing straight to a HWE version, which will better support the hardware... and the HWE Kernel version range will be that of 21.04. That is better for Intel CPU and the integrated Intel Graphics of.

---

### Post by thealpman on 2021-09-15
Hello,

Thank you for your answers.

I have a new problem : sometimes, the computer doesn't even start, I cannot press F2 to access UEFI !

 @tea for one : It finally started and I tried the configuration of UEFI.
Reset the UEFI/BIOS to default : done
Disable Secure Boot : not found
Disable Fast Boot : done
Disable Legacy mode : not found
Check that Legacy USB Support is enabled : not found
Disable TPM : done

Another problem : the computer completely froze during this operation. What can make this happen at this stage ? Could that be a hardware problem ?

@MAFoElffen : the problems started with the 5.8 kernel, so I downgraded it to 5.4 but the problems came back.
I have a Clevo NL51LU.
When I look at the firmware update ([https://www.clevo.com.tw/EN/E-SERVICES/download/ftpOut.asp?Lmodel=NLxxLU_LU1&ltype=9&submit=+GO+](https://www.clevo.com.tw/EN/E-SERVICES/download/ftpOut.asp?Lmodel=NLxxLU_LU1&ltype=9&submit=+GO+)), I found files for Windows only. How can I update the firmware on Ubuntu anyway ?

Thank you !

---

### Post by tea for one on 2021-09-15
> **thealpman said:**
> Disable Secure Boot : not found!
Secure boot [COLOR="#0000FF"]must[/COLOR] be somewhere in your UEFI set-up.
Do you have a security tab?
> **thealpman said:**
> I have a new problem : sometimes, the computer doesn't even start, I cannot press F2 to access UEFI !
That looks ominous - power or battery possibly?
> **thealpman said:**
> Another problem : the computer completely froze during this operation. What can make this happen at this stage ? Could that be a hardware problem ?
If the laptop froze while you were configuring the UEFI set-up, I would have a word with the supplier.

These additional problems are pointing to hardware failure rather than Ubuntu software difficulties.
Is the device still under warranty?

---

### Post by MAFoElffen on 2021-09-16
Tea for One is right... This device is having problems even with just running on it's own UEFI firmware. What is strange is that Vendor says that it does not have any BIOS updates, but then doesn't even have the original BIOS there for download.

*** Take note of this "Tea For One":
Depending on it's age, or the company's hardware compliance to SMBIOS standards (could be brand new and fall into that category)... It may not have Secure Boot there at all as a setting. Just because it is UEFI, does not mean it has that. I ran into an old Lenovo (yes main brand) last night that was UEFI "only". It did not have any setting for "Secure Boot." Nor did it have any setting to boot into Legacy Boot mode. It could only boot as UEFI.

If you are using a Ubuntu 20.04LTS Desktop LiveCD... Does it, at any time boot and run on "Try"? If not, and not run stably, then it would be a waste of time thinking anything would be better trying to install it on it right? The question would be, if you boot from a 20.04 Server LiveCD, see if that boots... if it does, at the first panel, arrow up until the help button hightlights, then press <enter>... You will be at a Console prompt where you can diagnose the machine.

Tell us if either of those work...

But before youi try any of those, since a notebook or laptop... take off the back memory cover and ensure the memory dimm's are seated well. It is a portable/mobile device.

---

### Post by thealpman on 2021-09-17
Thank you for your answers.

I agree that freezing in the BIOS setup might point to a hardware problem. Yes, the computer is recent and under warranty, I will call the supplier. But since I bought it without OS and installed Ubuntu myself, I'm afraid he might not be too concerned.

I will look again for secure boot.

I already tried live USB start and diagnoses, no problems were found. But I can try again.

And when I have time I can try a installation of 20.04.3 HWE.

I'll let you know, thanks again

---

### Post by MAFoElffen on 2021-09-17
If you are going to boot on any Ubuntu ISO, please use "Try" and see if if starts to the desktop. If so, then open a terminal an type this
```

mokutil --sb-state

```
if it is not on the LiveCD you booted from install it then type the command above.

The output from that will tell me whether the BIOS if confirmed as UEFI, if it has a Secure Boot setting or not, and if it does have that setting, what that setting is set at.

Then run the system-info script in my signature line, from the UbuntuForums GitHub, which will tell us about your hardware and what the system settings are set at. That will give us a better picture of what is going on and what we are recommending solutions for.

---

### Post by thealpman on 2021-10-20
Hello,
Thank you for your answers.
I tried to boot on a USB drive and tru 20.04.3, 18.04.6 and 21.10, it freezes all the time with the same kind of error in my first message.
I ran your commands :
```
jr@jr-ubuntu:~$ mokutil --sb-state
SecureBoot disabled
Platform is in Setup Mode
jr@jr-ubuntu:~$
```

And I ran your script. Below is the result.

Thanks again for your help.

```
Starting the Ubuntu Forums 'system-info' Report: 2021-10-20  13:22:48 CEST (+0200)
    Part of the Ama-gi Project
    Version: 01.00-01, Script Date: 2021.09.30

---------------------------------------------------------------
Main Complaint: The computer freezes
Problem Description:  No action is possible
---------- General computer specs:

  --- Computer/CPU Information --- 
*-Cpu
    Description: CPU
    Product: Intel(R) Core(TM) i5-1035G1 CPU @ 1.00GHz
    Vendor: Intel Corp.
    Physical id: 4
    Bus info: cpu@0
    Version: Intel(R) Core(TM) i5-1035G1 CPU @ 1.00GHz
    Serial: [REMOVED]
    Slot: U3E1
    Size: 2556MHz
    Capacity: 4005MHz
    Width: 64 bits
    Clock: 100MHz
    Capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 
        apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse 
        sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art 
        arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid 
        aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est 
        tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe 
        popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 
        3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp 
        ibrs_enhanced tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase 
        tsc_adjust bmi1 avx2 smep bmi2 erms invpcid avx512f avx512dq rdseed 
        adx smap avx512ifma clflushopt intel_pt avx512cd sha_ni avx512bw 
        avx512vl xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp 
        hwp_notify hwp_act_window hwp_epp hwp_pkg_req avx512vbmi umip pku 
        ospke avx512_vbmi2 gfni vaes vpclmulqdq avx512_vnni avx512_bitalg 
        avx512_vpopcntdq rdpid md_clear flush_l1d arch_capabilities cpufreq
    Configuration: cores=4 enabledcores=4 threads=8

computer
    Description: Notebook
    Product: NL4x_NL5xLU (Not Applicable)
    Vendor: PC Specialist LTD
    Version: Not Applicable
    Serial: [REMOVED]
    Width: 64 bits
    Capabilities: smbios-3.2.0 dmi-3.2.0 smp vsyscall32
    Configuration:
        boot=normal
        chassis=notebook
        family=Not Applicable
        sku=Not Applicable
        uuid=[REMOVED]

------------------ SMBIOS Information
Bios Vendor:         INSYDE Corp.
Bios Version:        1.07.02TPCS
Board Vendor:        CLEVO
Board Name:          NL4x_NL5xLU
Board Version:       Not Applicable                  
Board Serial:        Not Applicable                  
Board Asset Tag:     Tag 12345

Current boot mode:   UEFI Firmware mode
SecureBoot disabled
Platform is in Setup Mode


---------- Memory Information:
              total        used        free      shared  buff/cache   available
Mem:           15Gi       3.9Gi       211Mi       813Mi        11Gi        10Gi
Swap:         975Mi        18Mi       957Mi

---------- IP Adress Information:
  --- IP Adress Information --- 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
2: enp1s0f1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]
4: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 100
    inet [REMOVED]
    inet6 [REMOVED]

  --- Internet Connection Status --- 
Connected to Internet with DNS

  --- Network Device Status Summary ---  
These Network Devices are up:
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
4: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 100

  --- Hostname ---  
The 'Hostname' of the computer system is: jr-ubuntu


---------- File system specs from 'df -h':
Filesystem                Type      Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu-root ext4      914G  507G  361G  59% /
/dev/sda2                 ext4      705M  317M  338M  49% /boot
/dev/sda1                 vfat      511M   12M  500M   3% /boot/efi
/dev/sdb2                 fuseblk   3.7T  2.0T  1.7T  54% /media/jr/SEAGATE1

---------- Disk/Partition Information From 'fdisk':

Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: Seagate BarraCud
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 7B54DB80-E057-4BC8-A1ED-2A038B7C67E1

Device       Start        End    Sectors   Size Type
/dev/sda1     2048    1050623    1048576   512M EFI System
/dev/sda2  1050624    2549759    1499136   732M Linux filesystem
/dev/sda3  2549760 1953523711 1950973952 930.3G Linux filesystem

Disk /dev/mapper/sda3_crypt: 930.29 GiB, 998881886208 bytes, 1950941184 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/mapper/vgubuntu-root: 929.33 GiB, 997854281728 bytes, 1948934144 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/mapper/vgubuntu-swap_1: 976 MiB, 1023410176 bytes, 1998848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sdb: 3.65 TiB, 4000787029504 bytes, 7814037167 sectors
Disk model: Expansion       
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 167E2CB9-DB1A-43F7-8085-428B3EE41C18

Device      Start        End    Sectors  Size Type
/dev/sdb2  264192 7814035455 7813771264  3.7T Microsoft basic data

---------- Disk/Partition Information From 'lsblk':
NAME                    SIZE FSTYPE      LABEL   MOUNTPOINT                   MODEL
sda                   931.5G                                                  Seagate_BarraCuda_120_SSD_ZA1000CM10003
|-sda1                  512M vfat                /boot/efi                    
|-sda2                  732M ext4                /boot                        
`-sda3                930.3G crypto_LUKS                                      
  `-sda3_crypt        930.3G LVM2_member                                      
    |-vgubuntu-root   929.3G ext4                /                            
    `-vgubuntu-swap_1   976M swap                [SWAP]                       
sdb                     3.7T                                                  Expansion
`-sdb2                  3.7T exfat       SEAGATE /media/jr/SEAGATE1           
   ------- 'lsblk' information continued ...
NAME                  HOTPLUG PARTUUID                             UUID
sda                         0                                      
|-sda1                      0 8b707bbf-3b95-4063-9fa5-5ba1872a6120 81D5-B24C
|-sda2                      0 a321ab1f-3908-40cd-b39d-eaab618025e3 d207a405-4bb3-47c2-93b0-39db6e7b9040
`-sda3                      0 ed8c4037-28f9-4d17-9801-006c63b2c069 7d607e2e-e7f2-4574-9617-4787fc4db75c
  `-sda3_crypt              0                                      4U70Cz-eIIx-KZI6-TDrh-yFai-0jUf-YblxQA
    |-vgubuntu-root         0                                      75eb9f2f-bfa3-4d45-887e-d18658dfee50
    `-vgubuntu-swap_1       0                                      30473dfe-10d6-4e85-97b7-9b6448d0e636
sdb                         1                                      
`-sdb2                      1 c7af46cd-f663-4c8a-9032-7e5541cef07f 4DF6-100F

---------- Mount Details of '/etc/fstab':
/dev/mapper/vgubuntu-root /               ext4    errors=remount-ro 0       1
UUID=d207a405-4bb3-47c2-93b0-39db6e7b9040 /boot           ext4    defaults        0       2
/dev/mapper/vgubuntu-swap_1 none            swap    sw              0       0
UUID=81D5-B24C  /boot/efi       vfat    defaults      0       1

---------- Current Mount Details of 'mount':
/dev/fuse on /run/user/1000/doc type fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/mapper/vgubuntu-root on / type ext4 (rw,relatime,errors=remount-ro)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda2 on /boot type ext4 (rw,relatime)
/dev/sdb2 on /media/jr/SEAGATE1 type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)

---------- USB Information:
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
    |__ Port 1: Dev 2, If 0, Class=Mass Storage, Driver=uas, 5000M
        ID 0bc2:231a Seagate RSS LLC Expansion Portable
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/12p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 7: Dev 2, If 0, Class=Video, Driver=uvcvideo, 480M
        ID 5986:9102 Acer, Inc 
    |__ Port 7: Dev 2, If 1, Class=Video, Driver=uvcvideo, 480M
        ID 5986:9102 Acer, Inc 
    |__ Port 10: Dev 3, If 0, Class=Wireless, Driver=btusb, 12M
        ID 8087:0029 Intel Corp. 
    |__ Port 10: Dev 3, If 1, Class=Wireless, Driver=btusb, 12M
        ID 8087:0029 Intel Corp. 
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/1p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub

---------- Video Details from 'lshw':

  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: 
           irq:130 
           memory:80000000-80ffffff 
           memory:70000000-7fffffff 
           ioport:4000(size=64) 
           memory:c0000-dffff

   --- Graphics Environment Continued ----
The Current Configured Destop is: ubuntu:GNOME 
The Current Desktop Session is: ubuntu 
The Current Session Type is: x11 
The Current Display Manager is: gdm3
The Current Desktop Theme: 'Yaru-Deepblue'
The Current Virtual TTYs being used are:
    TTY#    Used By
    tty2    gdm-x-session
    tty2    Xorg
    tty2    gnome-session-b

---------- Repository Information:

Sources List:
deb http://fr.archive.ubuntu.com/ubuntu/ focal main restricted
deb http://fr.archive.ubuntu.com/ubuntu/ focal-updates main restricted
deb http://fr.archive.ubuntu.com/ubuntu/ focal universe
deb http://fr.archive.ubuntu.com/ubuntu/ focal-updates universe
deb http://fr.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://fr.archive.ubuntu.com/ubuntu/ focal-updates multiverse
deb http://fr.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse

Sources List from SourcesD:
/etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-focal.list:
deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal main
/etc/apt/sources.list.d/morphis-ubuntu-anbox-support-focal.list.save:
File had no entries.
/etc/apt/sources.list.d/teams.list:
deb [arch=amd64] https://packages.microsoft.com/repos/ms-teams stable main
/etc/apt/sources.list.d/signal-xenial.list:
deb [arch=amd64 signed-by=/usr/share/keyrings/signal-desktop-keyring.gpg] https://updates.signal.org/desktop/apt xenial main
/etc/apt/sources.list.d/signal-xenial.list.save:
deb [arch=amd64 signed-by=/usr/share/keyrings/signal-desktop-keyring.gpg] https://updates.signal.org/desktop/apt xenial main
/etc/apt/sources.list.d/skype-stable.list.save:
deb [arch=amd64] https://repo.skype.com/deb stable main
/etc/apt/sources.list.d/teamviewer.list:
deb https://linux.teamviewer.com/deb stable main
/etc/apt/sources.list.d/alex-p-ubuntu-aegisub-focal.list.save:
deb http://ppa.launchpad.net/alex-p/aegisub/ubuntu focal main
/etc/apt/sources.list.d/brave-browser-release.list.save:
deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main
/etc/apt/sources.list.d/libreoffice-ubuntu-ppa-focal.list.save:
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu focal main
/etc/apt/sources.list.d/nordvpn.list:
deb https://repo.nordvpn.com/deb/nordvpn/debian stable main
/etc/apt/sources.list.d/libreoffice-ubuntu-ppa-focal.list:
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu focal main
/etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-focal.list.save:
deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal main
/etc/apt/sources.list.d/teams.list.save:
deb [arch=amd64] https://packages.microsoft.com/repos/ms-teams stable main
/etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-focal.list.save:
File had no entries.
/etc/apt/sources.list.d/brave-browser-release.list:
deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main
/etc/apt/sources.list.d/morphis-ubuntu-anbox-support-focal.list:
File had no entries.
/etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-focal.list:
File had no entries.
/etc/apt/sources.list.d/nordvpn.list.save:
deb https://repo.nordvpn.com/deb/nordvpn/debian stable main
/etc/apt/sources.list.d/alex-p-ubuntu-aegisub-focal.list:
deb http://ppa.launchpad.net/alex-p/aegisub/ubuntu focal main
/etc/apt/sources.list.d/mkusb-ubuntu-unstable-focal.list:
deb http://ppa.launchpad.net/mkusb/unstable/ubuntu focal main
/etc/apt/sources.list.d/teamviewer.list.save:
deb https://linux.teamviewer.com/deb stable main
/etc/apt/sources.list.d/skype-stable.list:
deb [arch=amd64] https://repo.skype.com/deb stable main

---------- Other Details:
The current kernel version is:       5.4.0-88-generic 
The current release description is:  Ubuntu 20.04.3 LTS 
Original Installation Date:          2021-04-08+13:24:09 
Original Installation Media: Ubuntu 20.04.2.0 LTS "Focal Fossa" - Release amd64 (20210209.1)


These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference:
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.11.0.38.42
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.4.0.26.32

   --- HWE Package Status:
HWE package linux-generic-hwe-20.04 was not detected. Please check 
kernel version to verify range

   --- Certified Hardware Platform Status: (By the Ubuntu Wiki Standards)
Ubuntu Certified Hardware Platform. Safe to install 
the Hardware Enablement Stack (HWE).

Currently logged in User(s):
NAME     LINE         TIME         COMMENT
jr       :0           Oct 20 12:09 (:0)

The User running this script was: jr
uid=1000(jr)
gid=1000(jr)
groups=1000(jr),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),
120(lpadmin),131(lxd),132(sambashare),998(nordvpn)

*** End Of Report ***
```

---

### Post by ActionParsnip on 2021-10-20
Are you connecting the drive to a USB hub? If so then try connecting directly to the system's USB ports. Is it the same? Is it the same in USB 2 and USB 3 ports?

---

### Post by thealpman on 2021-10-20
I don't use any USB hub.
I have a USB2 and a USB3 port. My trials with the different versions were probably random on these 2 ports...

---

### Post by thealpman on 2021-11-18
Hello,

I sent the computer back to the manufacturer, they changed the SSD and motherboard and extensively tested with Windows and say there is no more problems now. They say the UEFI is up to date
As tea For One siggested, I reset the UEFI/BIOS to default, disabled Secure Boot, disabled Fast Boot, disabled TPM (but couldn't disable Legacy mode : not found)

But I still have the same problems ! Freezing during USB boot with 20.04.3 and 21.10 after ~30s (unless safe recovery mode).
I remade the USB boots, change the USB drive and  the USB port.

I still get these error messages :
```
[     2.272550] tpm tpm0: [Firmware Bug]/ TPM interrupt not working, polling instead
[     3.534459] platform idma64.0: failed to claim resource 0: [mem 0x00000800-0x000000fff]
[     3.535612] platform i2c_designware.0: failed to claim resource 0: [mem 0x00000000-0x000001ff]
[     3.554632] platform idma64.0: failed to claim resource 0: [mem 0x00000800-0x000000fff]]
[     3.556919] platform i2c_designware.0: failed to claim resource 0: [mem 0x00000000-0x000001ff
```

And these ones when I quit after trying USB boot + recovery mode :
```
[   415.399628] ACPI BIOS Error (bug): Could not resolve symbol [\_S8.PCI0.LPC8.EC._Q61.P80H], AE_NOT_FOUND (20201113-psargs-330)
[   415.402897] ACPI Error: Aborting method \_S8.PCI0.LPC8.EC._Q61 due to previous error (AE_NOT_FOUND) (20201113-psparse-529)
```
But I read these last ones may not be too serious ?

Thank you for your help

---

### Post by MAFoElffen on 2021-11-18
So I researched the error messages and thoughts on what they meant... They are very "varied".

Most say it's some kind of firmware conflict.

Recommends to try varied from (test each one at a time):

In the UEFI BIOS firmware settings, disable the TPM, diable SecureBoot, disable quiet boot (so that instead of any logo, it shows the POST messages)... Try to toggle ACPI off/on. Try disabling/toggling USB3.x support.

In the grub boot line, change/set as "nosplash --verbose video=vesafb:nomtr,ypan,invers noapic"... This will disable the splash, turn on verbose messaging, give a video helper until XServer starts... and turn off the apic (which sometime causes freezing when there is a firmware problem and device address / irq conflicts... which would cause a not able to claim a resource error... because it was already busy by something else.)

If that does not work then "nosplash --verbose text"... Which will turn off the splash, turn on verbose boot messaging, and boot to a text console... to see if the freezing occurs without the XServer and graphics layer present... If this still occurs on just the kernel... then we know it is not the graphics layer... We can try to compartmentalize where and when the error occurs.

---

### Post by tea for one on 2021-11-18
Info from post no.9
```
/dev/sdb2 fuseblk   3.7T  2.0T  1.7T  54% /media/jr/SEAGATE1
/dev/sdb2  264192 7814035455 7813771264  3.7T Microsoft basic data
```
Do you still have this drive accessible when you try to boot a live session?
Can you remove this device and try again?

---

### Post by thealpman on 2021-11-20
Hello,

Thank you for your answers.

@tea for one
Yes, there was an external 2.5 hard drive. I get the same results when I try without, unfortunately this will probably not explains my problems...

@MAFoElffen
I tried with the "nosplash --verbose video=vesafb:nomtr,ypan,invers noapic" options, the screen froze all the same
I also tried with the "nosplash --verbose text" options, it froze also. I did not see changes apart from many information during the boot, what do you mean by "boot to a text console" ?

I tried also to boot on :
- 22.04 : it freezes instantly
- 20.04 (and not 20.04.3), it freezes
- 18.04 (not 18.04.6), it works, no freezing so far, but also no wifi and no bluetooth... and new error messages :
```
[ time ] hw perf events fixed 4 > max(3), clipping!
[ time ] Couldn't get size: 0x800000000000000e
[ time ] MODSIGN: Couldn't get UEFI db list
[ time ] Couldn't get size: 0x800000000000000e
[ time ] sd 1:0:0:0: [sdb] No Caching mode page found
[ time ] sd 1:0:0:0: [sdb] Assuming drive cache: write through
```

Does his help ?

---

### Post by tea for one on 2021-11-20
More than two months since this thread started and little progress has been made.
Nevertheless, there must be a solution somewhere?............... ](*,) or :-k

Here are a couple of daft suggestions;-

Remove (or de-activate/isolate) your internal and external disks - boot your USB?
Beg, borrow, steal a USB DVD drive, burn your ISO to a DVD and boot?

Any luck?

---

### Post by MAFoElffen on 2021-11-21
I have another suggestion: Report it as a bug to Launchpad.

This is a problem with your specific combination of hardware, not just for you, and not just this Linux Distribution. I keep seeing threads on this, with this specific hardware, with these specific error messages, trying to resolve this in forums or other places... It seems to go away (temporarily), before it identifies what the error actually is. This needs to be escalated, and it is time to call it. It needs to be analyzed by looking at the system logs and back traces on the specific errors.

These errors on this specific hardware seem to fall in and out of being corrected with different Linux Kernels, but is really never identified what the specific problem is/was... Honestly, I don't see where they have specifically nailed down where and what the problem really is. After you post the bug there, please post it here, so I can follow it, not just to keep up with it, but to also post to support what we have had you do, and the results of that. 

Like I said... There were many varied thoughts of what it might be from, or what helps it... But nothing I found really locked done what specifically causes this problem with this specific hardware.

You are not alone. I care that this issue is resolved for you. That helps us all, and Ubuntu as a whole, that things like this are resolved. I think that this is the next logical step with this.

---

### Post by thealpman on 2021-11-21
Hello tea for one and MaFoElffen,

Thanks again for your precious help.

@tea for one : I don't know how to deactivate my internal SSD before launching a USB live session, is there a way to do it from the UEFI ? Little chance I can get my hands on an external DVD drive...

@ MaFoElffen, I declared the bug to Launchpad : [https://bugs.launchpad.net/launchpad/+bug/1951733](https://bugs.launchpad.net/launchpad/+bug/1951733). I hope it can work fast, I'm considering selling this one and buying another (much more expensive) computer with Ubuntu preinstalled. I was really hoping to get rid of Windows, not so easy so far :(...

I hope we can get to the bottom of this one day !

---

### Post by ActionParsnip on 2021-11-21
Make sure that you have the latest BIOS. It may be an issue which is resolved in the newer version

---

### Post by MAFoElffen on 2021-11-21
@ActionParsnip...

It is still on warranty... His computer Vendor told him they didn't have any BIOS Firmware upgrade to it. Additionally, the Vendor had him ship it back, supposedly test it intensively (With Windows) and said they couldn't find anything wrong with it.

I would say, yes hopefully fast, so that he can try to get his money back on it before that warranty expires, so that if this cannot, that he can use that to get something that can run Ubuntu on.

EDIT: Or maybe they have another Model that will(?)

I know with Dell, HP and Lenovo, form having to do FRU Warranty Service calls... They are bigger and more mainstream. If there are 3 services call in a short amount of time, then it goes to Depot. If it still has a problem, whether in Depot or afterwards, then then talk to the customer about another device or a refund.

I subscribed and added some comments.

---

### Post by tea for one on 2021-11-21
> **thealpman said:**
> I don't know how to deactivate my internal SSD before launching a USB live session, is there a way to do it from the UEFI ? 

Yes, there is a way but it completely depends on the facilities provided by the vendor's UEFI firmware.
I'm lucky because my UEFI firmware allows me to turn on/off almost everything (screenshot attached)

Also, you have filed your bug report against Launchpad itself which is probably not the correct target.
I'm not sure exactly where you should file it to generate an adequate response - possibly [https://launchpad.net/ubuntu-cdimage](https://launchpad.net/ubuntu-cdimage)

---

### Post by MAFoElffen on 2021-11-21
Yes. I saw that... And asked those there if they could move it somewhere where it will get the correct attention. 

It needs to be filed against "something". I'm not quite sure if that something would be possibly against package linux-firmware as a guess(?)

---

### Post by MAFoElffen on 2021-11-21
While that is in play at Launchpad... I have some other things for you to try.

For kernel boot options, please try these (one at a time):
```

nomodeset
i915.modeset=0

```
Those would turn the KMS graphics helpers off in the kernel.

The third thing is what I tried to have you try with the last boot parameter, from a previous post, that sometimes will not work from a desktop LiveCD... with the " text " boot parameter... To try to get it to boot without the graphics layer, to see if it boots and stays stable with a Linux Kernel, without graphics. 

This is where I wish my Ama-Gi Project was closer to be running as a LiveCD (even in an Alpha stage). That is meant to boot as an Ubuntu Text Console Live Image, with the Linux Graphics layer available to run on-demand. It is meant to be a Support LiveCD to diagnose things like this. It is based on Ubuntu Server...

Which most people do not realize that the Ubuntu Server LiveCD, is a LiveCD... And runs a "Live" Linux Console Image. 

That is my third idea... Boot an Ubuntu Server 20.04.03 LiveCD, and when it get just past the keyboard/Language Selection, use the upper right Menu Option to get to Console Command prompt and test if it runs as stable, without freezing. If so, then we could start diagnosing things from that live environment.

---

### Post by thealpman on 2021-11-23
Hello,

Thanks for your answers.

I thought I had declared this bug in the Ubuntu section, not the Launchpad...

I tried what you suggested :
- nomodeset : it feels the same as "safe graphics" : it works, but the display is very slow, almost impossible to work like that...
- same with i915.modeset=0

i also tried what I found here : [https://forums.linuxmint.com/viewtopic.php?t=308570](https://forums.linuxmint.com/viewtopic.php?t=308570) :
- sudo apt-get install xserver-xorg-video-intel : I already have the newest version
- put "i915.alpha_support=1" as kernel parameter, doesn't help
- I tried to put this in a /etc/X11/xorg.conf file
```

Section "Device"
Identifier "Device0"
Driver "intel"
EndSection
```

Is it of any help ?

---

### Post by MAFoElffen on 2021-11-23
LOL. Well, that Xorg Intel driver was needed before Ubuntu 16.04. It still works, but...

Intel, about 16.04 open sourced their own video drivers and maintain them themselves. The i915 driver (Intel) is now directly inside the kernel. Intel submits their opensource video drivers directly to kernel.org so that can happen upstream there. 

How do I know this? Laughing more: embarrassed.....Have you read the "Graphics Resolution: Sticky in my signature line? I am the author... I have been supporting the Linux Graphics layer and XServer for a long time... Because I have been exposed to a lot of things for a lot of years. (Hint: I started supporting XServer on Mainframes and terminals.). 

In diagnostics of a Linux System, the first stage is the boot loader stage: to see if Grub is actually booting a kernel image. UEFI is also in this first stage. Next, during the boot process, is does the kernel boot successfully? If so, then you have the stage where the Linux Graphics Layer comes up... Each of these stages has many pieces that fit together. A "blank screen" can mean many things... in any of those stages. That is why I came up with a methodology to diagnose these kinds of things...

The graphics Layer gets helpers or things that affect it from all 3 stages... That is why it is important to identify which stage the problem is coming from.

What I keep asking, and wondering, so that we can cross things off our lit, is if it can run a current kernel, and be stable, before it tries to load any graphics layer pieces?

One thing that may help now... Is that you "are" using XServer "now" right?

Please try to boot once. Then go to pastebin.ubuntu.com and paste in one boot cycle's worth of your system log at /var/log/syslog...

Then in a post, post your last failed /var/log/Xorg.0.log... Wrapped within [noparse]```
 output_here 
```[/noparse] Tags.

---

### Post by thealpman on 2021-11-24
Hello,

Thanks for the info, to be honest, I hadn't quite read your post, it's above my skills...

Here is the relevant part of my /var/log/syslog file : [https://pastebin.ubuntu.com/p/YW2YxgrXK7/](https://pastebin.ubuntu.com/p/YW2YxgrXK7/)
As for the /var/log/Xorg.0.log file, it is not created during a normal boot, only during a safe graphics boot. Seems strange... Would it be of any help ?

I've created a thread here : [https://www.linux.org/threads/my-computer-freezes-when-i-use-a-usb-drive-boot-and-i-cant-reinstall-ubuntu.37745/](https://www.linux.org/threads/my-computer-freezes-when-i-use-a-usb-drive-boot-and-i-cant-reinstall-ubuntu.37745/)
Following their suggestion, I successfully installed Manjaro and MX ! Does it help ?

And here : [https://forums.linuxmint.com/viewtopic.php?f=46&t=361559&p=2099394#p2099394](https://forums.linuxmint.com/viewtopic.php?f=46&t=361559&p=2099394#p2099394), they suggested that I don't have the most up-to-date version of the UEFI, how could I upgrade it (all I find is these Windows-related files : [https://www.clevo.com.tw/EN/E-SERVICES/download/ftpOut.asp?Lmodel=NLxxLU_LU1&ltype=9&submit=+GO+](https://www.clevo.com.tw/EN/E-SERVICES/download/ftpOut.asp?Lmodel=NLxxLU_LU1&ltype=9&submit=+GO+)) ?

---

### Post by MAFoElffen on 2021-11-26
Your vendor said they have no BIOS update for your BIOS... We went over that.

I started analyzing your syslog... It boots fine. It boots the kernel and and starts XServer sussessfully. The problem looks like it starts to oocur further up in the Graphics Layer in the gnome-sessions DE. It looks like here is where your crash started:
```

Nov 24 13:49:39 jr systemd[1287]: Started Accessibility services bus.
Nov 24 13:49:39 jr gnome-session[1500]: gnome-session-check-accelerated: GL Helper exited with code 512
Nov 24 13:49:39 jr gnome-session[1548]: libEGL warning: DRI2: failed to authenticate
Nov 24 13:49:39 jr gnome-session[1500]: gnome-session-check-accelerated: GLES Helper exited with code 512
Nov 24 13:49:39 jr systemd[1287]: gnome-session-x11@ubuntu.target: Requested dependency OnFailure=gnome-session-failed.target ignored (target units cannot fail).
Nov 24 13:49:39 jr systemd[1287]: gnome-session.target: Requested dependency OnFailure=gnome-session-failed.target ignored (target units cannot fail).
Nov 24 13:49:39 jr systemd[1287]: gnome-session@gnome-initial-setup.target: Requested dependency OnFailure=gnome-session-failed.target ignored (target units cannot fail).
Nov 24 13:49:39 jr systemd[1287]: gnome-session-pre.target: Requested dependency OnFailure=gnome-session-shutdown.target ignored (target units cannot fail).
Nov 24 13:49:39 jr systemd[1287]: gnome-session-initialized.target: Requested dependency OnFailure=gnome-session-shutdown.target ignored (target units cannot fail).
Nov 24 13:49:39 jr systemd[1287]: gnome-session@gnome-login.target: Requested dependency OnFailure=gnome-session-failed.target ignored (target units cannot fail).
Nov 24 13:49:39 jr systemd[1287]: gnome-session-x11.target: Requested dependency OnFailure=gnome-session-failed.target ignored (target units cannot fail).
Nov 24 13:49:39 jr systemd[1287]: gnome-session@ubuntu.target: Requested dependency OnFailure=gnome-session-failed.target ignored (target units cannot fail).
Nov 24 13:49:39 jr systemd[1287]: gnome-session-failed.target: Requested dependency OnFailure=gnome-session-shutdown.target ignored (target units cannot fail).
Nov 24 13:49:39 jr systemd[1287]: Created slice gnome\x2dsession\x2dmanager.slice.
Nov 24 13:49:39 jr systemd[1287]: Started Path trigger for Avahi .local domain notifications.
Nov 24 13:49:39 jr systemd[1287]: Started Path trigger for Apport crash notifications.
Nov 24 13:49:39 jr systemd[1287]: Started Path trigger for new release of Ubuntu notifications.
Nov 24 13:49:39 jr systemd[1287]: Condition check resulted in GNOME Initial Setup Copy Worker being skipped.

```

You should refile your bug at launchpad against package "gnome-sessions", most likely with a title of "gnome-session-check-accelerated: GL Helper exited with code 512". Copy that snip into your bug report... Then link your pastebin of your syslog.

Following that intiial error, it then gets gnome-shell errors on authentications, where it fails and goes downhill from there... Just search on "gnome-shell'. For example:
```

Nov 24 13:49:39 jr gnome-shell[1592]: Impossible to set scaling on crtc 1312 to 1,000000, error id 2
Nov 24 13:49:39 jr gnome-shell[1592]: Window manager warning: Scalig CRTC 1312 at 1,000000 failed
Nov 24 13:49:40 jr gnome-shell[1592]: Some code accessed the property 'CredentialManager' on the module 'credentialManager'. That property was defined with 'let' or 'const' inside the module. This was previously supported, but is not correct according to the ES6 standard. Any symbols to be exported from a module must be defined with 'var'. The property access will work as previously for the time being, but please fix your code anyway.
Nov 24 13:49:40 jr gnome-shell[1592]: Unset XDG_SESSION_ID, getCurrentSessionProxy() called outside a user session. Asking logind directly.
Nov 24 13:49:40 jr gnome-shell[1592]: Will monitor session 1

```
On the display of, there is also another problem related to this error:
```

unable to get EDID for xrandr-default: unable to get EDID for output

```
What are you using for it's display? I can see above that, in the start XServer and the writing of It's log, that it successfully set the mode as 1920x1024. Is that an okay mode for your Display? If so, then that can be ignored...

---

### Post by thealpman on 2021-12-23
Hello,

The problem is finally solved by a change of RAM!
Apparently Corsair RAM (I had 2x 8GB DDR4) sometimes causes problems with Linux (when everything works fine with Windows).
It was changed by a company specialized in Linux which uses Crucial or Kingston.

As a reminder, I had found a workaround to launch a video in loop in VLC, strangely, it avoided the freezing.

And also Manjaro and MX seemed to be working fine.

Thanks to all for your help.

---

