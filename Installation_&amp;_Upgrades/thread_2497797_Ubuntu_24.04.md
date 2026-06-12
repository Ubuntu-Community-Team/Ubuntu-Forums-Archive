---
title: "Ubuntu 24.04"
date: 2024-05-17
forum: Installation &amp; Upgrades
---

### Post by etcusr on 2024-05-17
I upgraded from Ubuntu 22.04 (Jammy Jellyfish) to the new 24.04 (Jammy Jellyfish) by wiping drive and installing version 24.04 (Jammy Jellyfish) from scratch. I am finding that 24.04 (Jammy Jellyfish) is very slow. After reboot the system is sluggish. When I click on any application such as terminal, or File Manager it take almost 10 seconds for the application to open before it can be used.

I'm considering going back to version 22.04 (Jammy Jellyfish) by wiping drive and reloading version 22.04.

It's takes hours to restore my backups and reinstall all applications, so I want to ask if anyone has experienced this performance issue before I go back to Ubuntu 22.04?

I'm hoping there's a solution.

Thanks in advance.

Regards

---

### Post by oldfred on 2024-05-17
If you have good backups, it should not take long to restore system.
I can reinstall in 10 minutes. I export list of installed apps & use that to restore them & rsync /home from backup into system.
Probably about an hour I can have a fully restore system.

What brand/model system? What video card/chip?
Have you updated UEFI & SSD (if you have SSD) firmware to latest available.
If you do not have SSD that is probably the best improvement you can make for speed.

How much RAM. If 4GB or less, a lighter weight flavor is suggested.

---

### Post by ian-weisser on 2024-05-17
22.04 is Jammy Jellyfish
24.04 is not.

There is also no supported upgrade path yet from 22.04 to 24.04.

So it's confusing to us. It's unclear what you actually did. Please update with accurate detail.

---

### Post by etcusr on 2024-05-17
Okay, sorry for cut and paste errors.  I upgraded from version 22.04 (Jammy Jellyfish) to latest version Ubuntu **24.04 LTS **[Noble Numbat by re-installing]("https://wiki.ubuntu.com/NobleNumbat").  The new version of Ubuntu **24.04 LTS **[Noble Numbat]("https://wiki.ubuntu.com/NobleNumbat") is performing badly where as Ubuntu **22.04.4 LTS**[Jammy Jellyfish]("https://wiki.ubuntu.com/JammyJellyfish") performs great.

ALL I did was install Ubuntu **24.04 LTS **[Noble Numbat]("https://wiki.ubuntu.com/NobleNumbat"), there was NO Upgrade. If you actually read my post you will discover that I wiped the drive and re-installed with Ubuntu **24.04 LTS **[Noble Numbat]("https://wiki.ubuntu.com/NobleNumbat").


I have HP Zbook G3, 32GB RAM, 2TB Nvme SSD. Performance is not an issue with old Ubuntu 22.04 (Jammy Jellyfish). **You seem to criticize rather than help. It's better to provide constructive advice than to criticize.  Restrain from sharing your criticism as it does not help, or don't reply at all.**

---

### Post by etcusr on 2024-05-17
Thanks for your reply. My data backup is 400GB of compressed data so it takes about several hours to perform the restore. I've been using duplicity to backup the data for several years. However, here are the answers to your questions:
What brand/model system: HP Zbook G3 Workstation Laptop
RAM: 32 GB
Storage: Samsung 2TB NVMe M.2 SSD 
Video: NVIDIA Corporation GM107GLM [Quadro M1000M]

UEFI Version. Running dmidecode I got the following:
BIOS Information
    Vendor: HP
    Version: N81 Ver. 01.53
    Release Date: 04/29/2021
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 16 MB
    Characteristics:
        PCI is supported
        PC Card (PCMCIA) is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        Smart battery is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 1.53
    Firmware Revision: 16.117

Like I said, the system runs great on Ubuntu 22.04, I just wanted to upgrade to the latest version Ubuntu 24.04 LTS  Noble Numbat... Is anyone else having the same performance problem with Ubuntu 24.04 LTS  Noble Numbat?

---

### Post by etcusr on 2024-05-17
Thanks for your reply. My data backup is 400GB of compressed data so it takes about several hours to perform the restore. I've been using duplicity to backup the data for several years. However, here are the answers to your questions:
What brand/model system: HP Zbook G3 Workstation Laptop
RAM: 32 GB
Storage: Samsung 2TB NVMe M.2 SSD 
Video: NVIDIA Corporation GM107GLM [Quadro M1000M]

UEFI Version. Running dmidecode I got the following:
BIOS Information
    Vendor: HP
    Version: N81 Ver. 01.53
    Release Date: 04/29/2021
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 16 MB
    Characteristics:
        PCI is supported
        PC Card (PCMCIA) is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        Smart battery is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 1.53
    Firmware Revision: 16.117

Like I said, the system runs great on Ubuntu 22.04, I just wanted to upgrade to the latest version Ubuntu 24.04 LTS  Noble Numbat... Is anyone else having the same performance problem with Ubuntu 24.04 LTS  Noble Numbat?

Thanks again!

---

### Post by etcusr on 2024-05-18
I'm not the only one that sees a performance problem in Ubuntu 24.04. I found another post with same problem: [https://ubuntuforums.org/showthread.php?t=2494238](https://ubuntuforums.org/showthread.php?t=2494238)

I will be wiping the drive and re-install the older 22.04 LTS. The new Ubuntu 24.04 needs some time to mature.

---

### Post by TenPlus1 on 2024-05-18
I would recommend Kubuntu 24.04 over the main gnome version, it runs a whole lot better on my system and can be easily configured to look and feel similar.

---

### Post by oldfred on 2024-05-18
Did you install nVidia driver with new install?
#What is installed
dkms status

#To see video:
lspci -k | grep -EA3 'VGA|3D|Display'
lspci -vnn | grep VGA -A 12

With those specs you should be able to run Ubuntu, but I also just happen to prefer Kubuntu as it works on both my old & new systems.

Have you updated UEFI & SSD firmware?

boot speed can be improved, but I do not think these settings help on other speed issues.
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2496312&p=14183456#post14183456](https://ubuntuforums.org/showthread.php?t=2496312&p=14183456#post14183456)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) &

---

### Post by MAFoElffen on 2024-05-18
+1 with oldfred

I was a tester for DEV-Noble.

Doug S did some very detailed analysis and benchmarks on the new kernel and the Ubuntu Base. 
RE: 
[https://ubuntuforums.org/showthread.php?t=2494238](https://ubuntuforums.org/showthread.php?t=2494238)
[https://discourse.ubuntu.com/t/24-04-considerably-slower-than-20-04-or-22-04-for-some-high-system-percentage-usage-cases/41987/28](https://discourse.ubuntu.com/t/24-04-considerably-slower-than-20-04-or-22-04-for-some-high-system-percentage-usage-cases/41987/28)

You can see that I helped him collect benchmarks and stat's on those tests on my Workstation. Note that was on Kernel 6.7. There is some personal background info I will not share, of the why this was important to both of us. Doug S, to me, is an unsung hero who tests each proposed kernel, and how it runs with Ubuntu. He deserves more credit than he gets. 

There was a regression issue that affected 6.8 performance that was fixed in 1/2024.
RE: 
[https://www.phoronix.com/news/Torvalds-Perf-Regression-Fix](https://www.phoronix.com/news/Torvalds-Perf-Regression-Fix)
[https://www.phoronix.com/news/Linux-6.8-Regression-Fix](https://www.phoronix.com/news/Linux-6.8-Regression-Fix)

Since then... I'm not sure. I don't see an issue on my workstation, but it is Intel i9-13900K, with 32 cores & 128GB RAM.

After the release of 22.04, it was found that there was a mistakenly hard-coded limit of 8-cores, that was buried there for over 20 years, that was corrected in the scheduler code:
RE:
[https://thehftguy.com/2023/11/14/the-linux-kernel-has-been-accidentally-hardcoded-to-a-maximum-of-8-cores-for-nearly-20-years/](https://thehftguy.com/2023/11/14/the-linux-kernel-has-been-accidentally-hardcoded-to-a-maximum-of-8-cores-for-nearly-20-years/)

That has since been corrected, so kernels since then *should* be using more available resources.

If you really want to help with correcting this, be active in the solution and file a bug report on it. (Repeated for emphasis: ) *"Be an active participant in the solution."*  That is how things get corrected, and helps "all Users" of Ubuntu, not just yourself. That is just the right thing to do.

Even though I do DEV Testing in the DEV Cycles, for my daily drivers and servers, I use LTS versions, and wait until the .1 point release to upgrade the releases of them. Things have been worked out by then.

---

### Post by etcusr on 2024-05-18
univ@etcmon-HP-ZBook-15-G3:~$ lspci -k | grep -EA3 'VGA|3D|Display'
01:00.0 VGA compatible controller: NVIDIA Corporation GM107GLM [Quadro M1000M] (rev a2)
    Subsystem: Hewlett-Packard Company GM107GLM [Quadro M1000M]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
univ@etcmon-HP-ZBook-15-G3:~$ lspci -vnn | grep VGA -A 12
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107GLM [Quadro M1000M] [10de:13b1] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company GM107GLM [Quadro M1000M] [103c:810a]
    Flags: bus master, fast devsel, latency 0, IRQ 161, IOMMU group 1
    Memory at e3000000 (32-bit, non-prefetchable) [size=16M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    Memory at b0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 3000 [size=128]
    Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

01:00.1 Audio device [0403]: NVIDIA Corporation GM107 High Definition Audio Controller [GeForce 940MX] [10de:0fbc] (rev a1)

** THERE'S the output. AND, I do see the NVIDIA Driver installed (Using NVIDA driver metapackage from nvidia-driver-535(proprietary, tested) under Software & Updates Additional Drivers.**

I have not made any changes to UEFI or SSD firmware. **I'm pondering if I should just limp along with 24.04 until at least the next .1 release before deciding to go back to 22.04**

Regarding your question on UEFI. I'm unable to **find** the version or figure out if I even need to upgrade it. Here's what I found on UEFI.
univ@etcmon-HP-ZBook-15-G3:~$ sudo ls -l /sys/firmware/efi/
total 0
-r--r--r--  1 root root 4096 May 18 20:47 config_table
drwxr-xr-x  2 root root    0 May 18 20:10 efivars
drwxr-xr-x  3 root root    0 May 18 20:11 esrt
-r--r--r--  1 root root 4096 May 18 20:11 fw_platform_size
-r--r--r--  1 root root 4096 May 18 20:47 fw_vendor
drwxr-xr-x  2 root root    0 May 18 20:47 mok-variables
-r--r--r--  1 root root 4096 May 18 20:47 runtime
drwxr-xr-x 11 root root    0 May 18 20:47 runtime-map
-r--------  1 root root 4096 May 18 20:47 systab

univ@etcmon-HP-ZBook-15-G3:~$ sudo efibootmgr
BootCurrent: 000B
Timeout: 0 seconds
BootOrder: 000B,0012,0010,000D,000A,000C,000E,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000F
Boot0000  Startup Menu    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)0000000049535048
Boot0001  System Information    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)f1000000000049535048
Boot0002  Bios Setup    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)100f0000000049535048
Boot0003  3rd Party Option ROM Management    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)f3000000000049535048
Boot0004  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)f2000000000049535048
Boot0005  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)01f20000000049535048
Boot0006  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)02f20000000049535048
Boot0007  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)03f20000000049535048
Boot0008  Boot Menu    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)f9000000000049535048
Boot0009  HP Recovery    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)110f0000000049535048
Boot000A  USB:      BBS(65535,,0x0)/PciRoot(0x0)/Pci(0x14,0x0)ffff0b80000049535048
Boot000B* Ubuntu    HD(2,GPT,8fa4375e-3633-4de2-83c5-6b035bb9f7b8,0xe1800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot000C* Samsung SSD 970 EVO Plus 2TB-S6S2NS0T314722N:     BBS(HD,Samsung SSD 970 EVO Plus 2TB-S6S2NS0T314722N: ,0x400)/PciRoot(0x0)/Pci(0x1b,0x0)/Pci(0x0,0x0)/NVMe(0x1,00-25-38-53-21-42-44-7C)01001000000049535048
Boot000D* Seagate BUP Slim RD NA9EKPLK    PciRoot(0x0)/Pci(0x1c,0x4)/Pci(0x0,0x0)/Pci(0x2,0x0)/Pci(0x0,0x0)/USB(3,0)/USB(1,0)4eac0881119f594d850ee21a522c59b21000000049535048
Boot000E* Intel Corporation: IBA CL Slot 00FE v0112    BBS(Network,Intel Corporation: IBA CL Slot 00FE v0112,0x0)/PciRoot(0x0)/Pci(0x1f,0x6)15001000000049535048
Boot000F  Network Boot    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)120f0000000049535048
Boot0010  USB:      PciRoot(0x0)/Pci(0x14,0x0)4eac0881119f594d850ee21a522c59b20b80000049535048
Boot0011* Windows Boot Manager    HD(2,GPT,8fa4375e-3633-4de2-83c5-6b035bb9f7b8,0xe1800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)
Boot0012* Windows Boot Manager    HD(2,GPT,8fa4375e-3633-4de2-83c5-6b035bb9f7b8,0xe1800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000061000100000010000000040000007fff04001400000049535048


**Notice** I have a dual boot system with Ubuntu and Windows. This is the reason a wipe and re-install is a hassle. I have to re-install both operating systems. And, the data for both operating systems.

Thanks for your help.

---

### Post by etcusr on 2024-05-18
I agree that "If you really want to help with correcting this, be active in the solution and file a bug report on it". Personally, my family duties, full time work duties, and completing online master's degree in Cybersecurity is overwhelming. Possibly when I have less on my plate I could actually participate in testing, it seems like a rewarding tasks.  Thanks for the information you provided.

Best Regards.

---

### Post by MAFoElffen on 2024-05-18
I meant as reporting it as a bug report. That is less of a commitment, but really helps. We are all volunteers here. We can explain how to do something and suggest work-arounds we know of, but... If it isn't in a bug report, then it is not going to get changed in the CODE. Launchpad is where that happens.

A sideline issue... Please, when posting commands and/or raw output, please post them within CODE Tags (refer to the link in my signature line on how to do that) . #1= It's a Forum Policy, in the Posting Guidelines (refer to the link in my signature line.) #2 are the reasons why. It's hard to read, and it sometimes does strange things to the Forums software.

---

### Post by ingosteinke on 2024-10-11
Similar problems several months later: 24.04 upgrade feels more like downgrade than an upgrade. I had hoped to solve my networking problems with the upgrade, but they were unrelated. Now I have some larger fonts and new icons, an unnecessary configuration error due to unsupported pulseaudio, and many applications take much longer to open or don't open at all anymore, like clicking a link in Thunderbird email that is supposed to open a page in the default browser.

I booted a Mint 20 Live System from a USB stick to check my network hardware, and I have to say that I'd rather go back to Mint 20 than stay with Ubuntu 24.

Sorry to complain, but really what's the point of breaking changes? We use long term support (LTS) versions for a reason.

---

