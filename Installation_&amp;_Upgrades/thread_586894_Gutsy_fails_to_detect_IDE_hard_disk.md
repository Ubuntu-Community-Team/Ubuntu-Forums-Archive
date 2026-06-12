---
title: "Gutsy fails to detect IDE hard disk"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by mfajer on 2007-10-22
Hello all,

I recently attempted to upgrade from Feisty to Gutsy on both my desktop and laptop.  The laptop upgrade went smoothly (eliminating CD error) but the live CD boot on my desktop fails to detect my primary IDE hard disk.  The hard disk is an IDE WD1600 which worked perfectly fine since Warty.  I have a dual boot with Windows and can still boot fine under Windows and the Feisty live CD.

Any thought on how to proceed?

---

### Post by nicklikesfire on 2007-10-22
I'm having this problem as well. I'm going from dapper to gutsy,

My two SATA media drives show up, but my 40 gig IDE does not.

Also, what would be the best way to partition the 40 gig? I really only need to use it to store programs on, and necessary files, as I have the two larger HDs for media.

---

### Post by Wollongong on 2007-10-22
Same problem, also with Western Digital IDE disk, as reported yesterday
[http://ubuntuforums.org/showthread.php?t=585906](http://ubuntuforums.org/showthread.php?t=585906)
**Does everyone with this problem have a Western Digital disk?**

Regarding how to partition your 40GB disk:
 I would create 3 partitions of about 13GB each.
 Partition 1 to be the root partition "/"
 Partition 2 is for your home partition "/home" It makes backup easier if your home is separate, and it makes an upgrade easier - if you need to re-install the operating system in the root partition, you won't lose your personal files.
 Partition 3 is a spare area that you can use to try out the next release of Ubuntu (or any other distro) without losing your current one.

---

### Post by mfajer on 2007-10-22
Thanks Wollongong for pointing out the other thread.  Yes, my hard disk is indeed a Wester Digital IDE drive.  I have attached the output of both " lspci -vvn" and "dmesg" under both the Edgy LiveCD and the Gutsy LiveCD.  Comparing the dmesg output between the two version shows a lack of the ```
 Probing IDE interface ide0...
``` in the Gutsy boot.  Hope this helps someone diagnose the problem.

---

### Post by Wollongong on 2007-10-23
Perhaps more likely is that the problem is specific to the IDE interface chip.
The chip is Intel 82801EB in these 2 cases with Western Digital disk.

I don't know which driver is responsible. Certainly "piix" should appear in the lsmod - it is the PCI interface driver that supports this Intel southbridge chip.

Here is lsmod from system with 82801EB and Western Digital, running successfully Etch Debian:
Module                  Size  Used by
ipv6                  229184  10
i915                   18304  2
drm                    64276  3 i915
ppdev                   8484  0
lp                     10784  0
thermal                13288  0
fan                     4676  0
button                  6544  0
processor              23272  1 thermal
ac                      4836  0
battery                 9476  0
dm_snapshot            15584  0
dm_mirror              19092  0
dm_mod                 49204  2 dm_snapshot,dm_mirror
sbp2                   21092  0
scsi_mod              124684  1 sbp2
loop                   15496  0
eth1394                19556  0
tsdev                   7456  0
mousedev               10880  1
serio_raw               6916  0
psmouse                34952  0
e100                   33764  0
mii                     5280  1 e100
i2c_i801                8172  0
floppy                 54960  0
i2c_core               19840  1 i2c_i801
serial_core            19808  0
ohci1394               30384  0
ieee1394               87704  3 sbp2,eth1394,ohci1394
snd_intel8x0           30556  1
parport_pc             32368  1
parport                33288  3 ppdev,lp,parport_pc
snd_ac97_codec         83648  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            44576  0
snd_mixer_oss          15904  1 snd_pcm_oss
snd_pcm                78532  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              22244  1 snd_pcm
ehci_hcd               28520  0
snd                    48672  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9216  1 snd
uhci_hcd               28528  0
snd_page_alloc         10024  2 snd_intel8x0,snd_pcm
usbcore               114816  3 ehci_hcd,uhci_hcd
ide_cd                 35936  0
cdrom                  32304  1 ide_cd
hw_random               5592  0
shpchp                 39648  0
pci_hotplug            25020  1 shpchp
pcspkr                  3460  0
rtc                    13364  0
intel_agp              21436  1
agpgart                30696  3 drm,intel_agp
evdev                   8992  1
ext3                  118152  2
jbd                    51412  1 ext3
mbcache                 8292  1 ext3
ide_disk               15072  4
ide_generic             1344  0 [permanent]
trm290                  4452  0 [permanent]
cs5530                  5120  0 [permanent]
siimage                10912  0 [permanent]
it821x                  7748  0 [permanent]
alim15x3               11280  0 [permanent]
cs5535                  4192  0 [permanent]
serverworks             8264  0 [permanent]
hpt34x                  5248  0 [permanent]
triflex                 3744  0 [permanent]
ns87415                 4460  0 [permanent]
sc1200                  6656  0 [permanent]
atiixp                  5744  0 [permanent]
hpt366                 17024  0 [permanent]
sis5513                12204  0 [permanent]
cmd64x                 10236  0 [permanent]
rz1000                  2688  0 [permanent]
amd74xx                12924  0 [permanent]
via82cxxx               8164  0 [permanent]
generic                 4388  0 [permanent]
pdc202xx_new            7904  0 [permanent]
cy82c693                4356  0 [permanent]
pdc202xx_old            9600  0 [permanent]
slc90e66                5440  0 [permanent]
piix                    9444  0 [permanent]
aec62xx                 7456  0 [permanent]
cs5520                  4640  0 [permanent]
opti621                 4388  0 [permanent]
ide_core              115564  30 ide_cd,ide_disk,ide_generic,trm290,cs5530,siimage,it821x,alim15x3,cs5535,serverworks
,hpt34x,triflex,ns87415,sc1200,atiixp,hpt366,sis5513,cmd64x,rz1000,amd74xx
,via82cxxx,generic,pdc202xx_new,cy82c693,pdc202xx_old,slc90e66,piix,aec62xx
,cs5520,opti621

---

### Post by mfajer on 2007-10-23
I won't be able to check on this for the next few days since I've had to evacuate from the wildfires in Southern California.  I'll let you know what I get from lsmod when I get back.

---

### Post by Wollongong on 2007-10-25
This certainly looks like a (serious) bug :(

Looking through the known problem reports, I'd say it is this one:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/133666](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/133666)

It affects Intel motherboards. The problem is in the ata_piix driver module.
There is a bug fix in the kernel, but it is not ready for Gutsy Gibbon yet.

The only solution that I can see is to create your own kernel, or sit it out (on Ubuntu 7.04) until the update trickles down.

---

### Post by TexMex657 on 2007-10-27
How do you tell if the update has been released?  What should I be checking so that I know when to upgrade to Gutsy

---

### Post by EinreNB on 2007-10-27
I've just tried to install Gutsy on a brand new SATA HD  (WD3200AAKS) which was installed just for Ubuntu. The new HD Has been formatted in one partition using XP ( NTFS without DMA enabled). Gutsy did not recognize the HD, but Windows XP did. Since this is my very first attempt at using Ubuntu, I haven't a clue about what to do next. My first thought was that there was something wrong with my new HD - a faulty driver perhaps, or the not enabled DMA. I seems to work great in XP,though. A read of other posts, however, suggests that this may be a broader problem. Should I just put off installing Gutsy in my new drive until someone fixes whatever the problem is?

---

### Post by mfajer on 2007-10-28
Hey EinreNB,

It does look like the problem is broader, specifically a bug that affects specific motherboards.  I have reverted to Kubuntu 7.04 again, which is what you might want to try.  Good luck!

---

### Post by nicklikesfire on 2007-10-28
People are saying this is an intel problem, but I'm using an ASUS A8N-SLI SE MoBo.

Anyone know if there's been some headway in solving this issue? Is there anything I can do to help? I'm not a developer, but the fact that my PC won't recognize the HD might be useful in some way?

---

### Post by strider22 on 2007-10-29
ubuntu 7.10 will work from CD on my PC but will not install. It stops at detecting the ide drive - loading aec62xx. 

My drive per /proc (booted from the 7.10 CD) is a maxtor 6L160p0

The computer is an older pentium III 733mhz. To boot from the CD requires safe graphics mode.

------
further details from a second try. (this time I did not mount the hard drive before installing.)
Starting from a CD booted system, the partitioner works fine on the IDE drive. In fact the system appears to have installed except for this new driver.
I have a desktop that works. It just has the error message and is still running off the CD.
The newly installed drive /target appears to have most of the system installed.

Is there a control file that can be edited to force the correct IDE driver to be loaded. If yes how do I identify the correct driver used by the CD.

Also since I had to select the safe graphics mode, how do I specify that to the install. The install does not appear to have a safe graphics option.

---

### Post by Wollongong on 2007-10-29
Could everyone with this problem please advise:
 [LIST]
[*]Brand and Model number of motherboard. Please include the IDE controller chip type, if you know that information. (run 'lspci' using another linux and look for 'IDE')
[*]Brand, Capacity, Type (SATA or IDE/PATA) and Model Number of disk (run 'dmesg' using another linux and look for 'DISK')
[*]Is the disk already partitioned and formatted?
[/LIST]

This might help to narrow down the issue. 
We still don't know if it is disk or controller related.

Here is the information for one system where Ubuntu failed to detect IDE disks:

 [LIST]
[*]Intel D865 motherboard;  Intel 82801EB i/o controller
[*]Western Digital 160GB IDE disk, WD16000BB
[*]Disk is already formatted, with NTFS partition 1&2, ext3 partitions 5,6,7
[/LIST]

---

### Post by strider22 on 2007-10-30
Attached is the lspci report from a working Ubuntu running from the CD.

Please answer the question. Can I modify a control file to install the correct IDE driver during the install from this working CD?

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: ALi Corporation M1621 (rev 04)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] (rev c3)
00:0c.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0c.1 Communication controller: C-Media Electronics Inc CM8738 (rev 10)
00:0e.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 02)
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c2)
00:10.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV5 [Aladdin TNT2] (rev 20)
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 6
cpu MHz         : 733.404
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
bogomips        : 1468.06
clflush size    : 32

ubuntu@ubuntu:~$ cat /proc/ide/hda/model
Maxtor 6L160P0

ubuntu@ubuntu:~$ cat /proc/ide/hda/driver
ide-disk version 1.18

ubuntu@ubuntu:~$ cat /proc/ide/hda/geometry 
physical     17475/15/63
logical      19457/255/63

ubuntu@ubuntu:~$ sudo cat /proc/ide/hda/settings 
name                    value           min             max             mode
----                    -----           ---             ---             ----
acoustic                0               0               254             rw
address                 1               0               2               rw
bios_cyl                19457           0               65535           rw
bios_head               255             0               255             rw
bios_sect               63              0               63              rw
bswap                   0               0               1               r
current_speed           66              0               70              rw
failures                0               0               65535           rw
init_speed              66              0               70              rw
io_32bit                0               0               3               rw
keepsettings            0               0               1               rw
lun                     0               0               7               rw
max_failures            1               0               65535           rw
multcount               0               0               16              rw
nice1                   1               0               1               rw
nowerr                  0               0               1               rw
number                  0               0               3               rw
pio_mode                write-only      0               255             w
unmaskirq               0               0               1               rw
using_dma               0               0               1               rw
wcache                  1               0               1               rw
ubuntu@ubuntu:~$

---

### Post by strider22 on 2007-10-30
and lsmod

ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
aec62xx                 8084  1 [permanent]
usb_storage            73024  0 
libusual               18448  1 usb_storage
nls_utf8                3072  0 
ufs                    83332  0 
qnx4                   12292  0 
hfsplus                78084  0 
hfs                    49924  0 
minix                  32772  0 
ntfs                  108096  0 
msdos                  10752  0 
xfs                   575192  0 
reiserfs              248704  0 
jfs                   189412  0 
vfat                   14080  0 
fat                    54300  2 msdos,vfat
ext2                   67208  0 
ipv6                  273892  10 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
apm                    22616  2 
ppdev                  10244  0 
lp                     12580  0 
speedstep_lib           6404  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
snd_cmipci             37044  1 
gameport               16776  1 snd_cmipci
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_opl3_lib           11520  1 snd_cmipci
snd_hwdep              10244  1 snd_opl3_lib
snd_mpu401_uart         9600  1 snd_cmipci
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9228  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
snd                    54660  12 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             39012  2 
parport                37448  3 ppdev,lp,parport_pc
bcm43xx               127374  1 
ieee80211softmac       31360  1 bcm43xx
ieee80211              35656  2 bcm43xx,ieee80211softmac
psmouse                39952  0 
i2c_core               26112  0 
soundcore               8800  1 snd
ieee80211_crypt         7040  1 ieee80211
serio_raw               8068  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
ali_agp                 8192  1 
agpgart                35016  1 ali_agp
evdev                  11136  1 
squashfs               48132  1 
loop                   19076  2 
unionfs                77096  1 
nls_cp437               6784  1 
isofs                  36412  1 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  2 ext2,ext3
ide_cd                 32672  1 
cdrom                  37536  1 ide_cd
ide_disk               18560  3 
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  2 usb_storage,libata
floppy                 60004  0 
alim15x3               12556  0 [permanent]
ide_core              116804  5 aec62xx,usb_storage,ide_cd,ide_disk,alim15x3
sis900                 24960  0 
mii                     6528  1 sis900
ohci_hcd               22916  0 
usbcore               138632  4 usb_storage,libusual,ohci_hcd
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
ubuntu@ubuntu:~$

---

### Post by strider22 on 2007-10-31
ubuntu@ubuntu:~$ sudo dmidecode
```

# dmidecode 2.9
SMBIOS 2.3 present.
23 structures occupying 1774 bytes.
Table at 0x000F04F0.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
        Vendor: American Megatrends Inc.        
        Version: 62710                           
        Release Date: 07/15/97                        
        Address: 0xF0000
        Runtime Size: 64 kB
        ROM Size: 256 kB
        Characteristics:
                PCI is supported
                PNP is supported
                APM is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                5.25"/360 KB floppy services are supported (int 13h)
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 KB floppy services are supported (int 13h)
                3.5"/2.88 MB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                LS-120 boot is supported
                ATAPI Zip drive boot is supported
                BIOS boot specification is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
        Manufacturer:                                 
        Product Name:                                 
        Version: 0000000                         
        Serial Number: 00000000                        
        UUID: Not Present
        Wake-up Type: Modem Ring

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
        Manufacturer: Acer Laboratories Inc.          
        Product Name: ALi 1631                        
        Version: 1.0                             
        Serial Number: 00000000                        

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
        Manufacturer: ALi String                      
        Type: Desktop
        Lock: Not Present
        Version: 1.0                             
        Serial Number: 0000000                         
        Asset Tag: 0123ABC                         
        Boot-up State: Unknown
        Power Supply State: Unknown
        Thermal State: Unknown
        Security Status: Unknown
        OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 32 bytes
Processor Information
        Socket Designation: Socket-370                      
        Type: Central Processor
        Family: Pentium III
        Manufacturer: INTEL                           
        ID: 86 06 00 00 55 00 00 00
        Signature: Type 0, Family 6, Model 8, Stepping 6
        Flags:
                FPU (Floating-point unit on-chip)
                DE (Debugging extension)
                TSC (Time stamp counter)
                PAE (Physical address extension)
        Version: Pentium III                     
        Voltage: 2.0 V
        External Clock: 133 MHz
        Max Speed: 800 MHz
        Current Speed: 733 MHz
        Status: Populated, Enabled
        Upgrade: Slot 1
        L1 Cache Handle: 0x0005
        L2 Cache Handle: 0x0006
        L3 Cache Handle: Not Provided

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L1 Cache                        
        Configuration: Enabled, Not Socketed, Level 1
        Operational Mode: Write Back
        Location: Internal
        Installed Size: 32 KB
        Maximum Size: 1024 KB
        Supported SRAM Types:
                Synchronous
        Installed SRAM Type: Synchronous
        Speed: Unknown
        Error Correction Type: None
        System Type: Unified
        Associativity: 4-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L2 Cache                        
        Configuration: Enabled, Not Socketed, Level 2
        Operational Mode: Write Back
        Location: Internal
        Installed Size: 256 KB
        Maximum Size: 2048 KB
        Supported SRAM Types:
                Synchronous
        Installed SRAM Type: Synchronous
        Speed: Unknown
        Error Correction Type: None
        System Type: Unified
        Associativity: 4-way Set-associative

Handle 0x0007, DMI type 5, 22 bytes
Memory Controller Information
        Error Detecting Method: 64-bit ECC
        Error Correcting Capabilities:
                Single-bit Error Correcting
        Supported Interleave: One-way Interleave
        Current Interleave: One-way Interleave
        Maximum Memory Module Size: 512 MB
        Maximum Total Memory Size: 1536 MB
        Supported Speeds:
                Unknown
        Supported Memory Types:
                FPM
                EDO
                Parity
                ECC
                DIMM
                SDRAM
        Memory Module Voltage: 3.3 V
        Associated Memory Slots: 3
                0x0008
                0x0009
                0x000A
        Enabled Error Correcting Capabilities:
                None

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: DIMM1                           
        Bank Connections: 0 1
        Current Speed: Unknown
        Type: DIMM SDRAM
        Installed Size: 128 MB (Double-bank Connection)
        Enabled Size: 128 MB (Double-bank Connection)
        Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: DIMM2                           
        Bank Connections: 2 3
        Current Speed: Unknown
        Type: DIMM SDRAM
        Installed Size: 128 MB (Double-bank Connection)
        Enabled Size: 128 MB (Double-bank Connection)
        Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: DIMM3                           
        Bank Connections: 4 5
        Current Speed: Unknown
        Type: Unknown
        Installed Size: Not Installed
        Enabled Size: Not Installed
        Error Status: OK

Handle 0x000B, DMI type 9, 13 bytes
System Slot Information
        Designation: PCI1                            
        Type: 32-bit PCI
        Current Usage: In Use
        Length: Long
        ID: 1
        Characteristics:
                3.3 V is provided
                Opening is shared
                PME signal is supported

Handle 0x000C, DMI type 9, 13 bytes
System Slot Information
        Designation: PCI2                            
        Type: 32-bit PCI
        Current Usage: Available
        Length: Long
        ID: 2
        Characteristics:
                3.3 V is provided
                Opening is shared
                PME signal is supported

Handle 0x000D, DMI type 9, 13 bytes
System Slot Information
        Designation: PCI3                            
        Type: 32-bit PCI
        Current Usage: Available
        Length: Long
        ID: 3
        Characteristics:
                3.3 V is provided
                Opening is shared
                PME signal is supported

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: COM Port                        
        Internal Connector Type: None
        External Reference Designator: Serial Port A                   
        External Connector Type: DB-9 male
        Port Type: Serial Port 16550A Compatible

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: LPT Port                        
        Internal Connector Type: None
        External Reference Designator: Parallel Port                   
        External Connector Type: DB-25 female
        Port Type: Parallel Port ECP/EPP

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: Keyboard                        
        Internal Connector Type: None
        External Reference Designator: Keyboard                        
        External Connector Type: PS/2
        Port Type: Keyboard Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: Mouse                           
        Internal Connector Type: None
        External Reference Designator: PS/2 Mouse                      
        External Connector Type: PS/2
        Port Type: Mouse Port

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: Floppy                          
        Internal Connector Type: On Board Floppy
        External Reference Designator: Floppy                          
        External Connector Type: None
        Port Type: None

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: Primary IDE                     
        Internal Connector Type: On Board IDE
        External Reference Designator: IDE-1                           
        External Connector Type: None
        Port Type: None

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: Secondary IDE                   
        Internal Connector Type: On Board IDE
        External Reference Designator: IDE-2                           
        External Connector Type: None
        Port Type: None

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: USB Port                        
        Internal Connector Type: None
        External Reference Designator: USB                             
        External Connector Type: Access Bus (USB)
        Port Type: USB

Handle 0x0016, DMI type 13, 22 bytes
BIOS Language Information
        Installable Languages: 1
                English                         
        Currently Installed Language: Not Specified

ubuntu@ubuntu:~$

```

---

### Post by Roger K4RS on 2007-10-31
I have had Feisty working well and recently upgraded to Gutsy using the Alternate Install CD.  After playing with the system a few days I decided to wipe the drive and perform a clean install of Gutsy.  That is when I discovered the installer could not locate my primary hard drive.

I am using an Asus P4S8X-X motherboard (SiS 5513 IDE Controller) and have tried several different hard drives (Maxtor, Quantum, Fuitsu and WD).   Drives attached to my add on IDE controller (Promise Ultra 100) are detected correctly.

Again, the upgrade worked correctly, it is only the installer that can not detect hard drives attached to the SiS 5513 controller.  Hopefully this info will help in resolving the problem...

---

### Post by strider22 on 2007-10-31
As you are saying the installer worked fine, that leads me to feel stronger that the problem is perhaps timing related and only in the install. I have said that I can boot the CD but I do that by playing around with the mouse when the boot appears to slow down at about 3/4 into the boot. I try to make the drive light come on. Then the boot continues and I am up an running off the CD.

From the dumps above it looks like I am running aec62xx from the CD so it may be able to run once installed. Trouble is the install does not complete. It stops at aec62xx. Is there some way I can kill that step, complete the install and then load aec62xx via the rescue option? That would then confirm whether the issue is only an install issue.

-----------------
Oh, dear. I just had a thought about low memory also causing this kind of problem, so I reread the release notes...

Wikipedia is a "little" out of date!
> 
  For the Desktop release, the "recommended minimum requirements" for good performance are:
    * 500 MHz x86 processor
    * 192 MB of system memory (RAM)


Release notes
> 
 The minimum memory requirement for Ubuntu 7.10 is 384MB of memory for desktop CDs, and 256MB for other installation methods. 
 (Note that some of your system's memory may be unavailable due to being used for the graphics card.)

 With only the minimum amount of memory available, the installation process will take longer than normal, but will complete successfully, 
 and the system will perform  adequately once installed. Low-memory systems may be able to use the desktop CD to install by adding
 the only-ubiquity boot option to run just the installer rather  than the whole desktop. 


I have 256MB (and 16meg is taken by the video.)
I also tried the boot option only-ubiquity which skips loading the desktop and goes straight into the install dialogs.
This also stopped on loading aec62xx at 90%

I'll go try xbuntu.

Xbuntu also fails at 120% complete on loading aec62xx

---

### Post by Im3m on 2007-11-01
Harddisc:           W1200EVS 120GB SATA
Motherboard:    M720S (clevo/SIS)
Controller:         SiS 180 SATA Control Chip sein
Processor:         Intel Core Dou T2450 @ 2GHz


hard disc is not found during installation of both drapper and feisty as well as kubuntu fedora opensuse and the new debian linux

---

### Post by stevie_velvet on 2007-11-01
Long shot Workarounds, 

If you have small hard drive, old systems, the chances are you won't have these options in your BIOS
 -enbale AHCPI*
 -enable IDE Block Mode

*May cause a blue screen in Windows XP & VISTA

The 2.6.23 Kernel is out, but I can't see a fix in the atapi driver forit..also there's no 2.6.23 *nix install OSs out yet to test\try

---

### Post by strider22 on 2007-11-01
I usually walk away from installs but the 120% got my interest. I watched the xbuntu install again through the whole thing. 

It threw an installer error installing mozilla-firefox-locale-en-gb at about 83%
then it continued.  (I forget if I clicked the OK or not) 

Although the top box comment still said it was installing language packs, the progress bar said it was about 115% and the bottom comment said it was configuring hardware.

Next it said it was detecting hardware on the top comment and then while at 120% with the bottom saying loading aec62xx it stopped progressing.

If I ignore the stopped progress box, I still have a working CD based system to use.

My big question is why does it configure hardware before it detects it?

---

### Post by mfajer on 2007-11-03
Here is my failed Gutsy system information:

The system is a IBM Thinkpad A50p (8194-CLU).
Motherboard: IBM 89P7942
IDE Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller
Harddisk: Western Digital, WDC WD1600JB-OOEVA0, ATA DISK drive

Disk already formatted with:
hda1: 74GB ntfs
hda2: 64GB ext3
hda3: 9.4GB ext3
hda4: 2GB swap

---

### Post by strider22 on 2007-11-03
I tried Xubuntu 6.06.1 and it also failed to install. I don't have any particulars other than on reboot after installing I got the grub 15 error. The hardware drivers failed when booting from the CD but it still ran from the CD.

I then tried Debian 40r1and I'm working in the first boot now. I haven't run the update wizard yet.
On rebooting the loading stops at  "Compaq touchscreen protocol" but after 2.5 minutes it continues and thus this first boot.

Below in the code box is the output of dmesg which gives some particulars about the IDE driver.
This isthe IDE part:
hda: max request size: 128KiB
hda: cannot use LBA48 DMA - PIO mode will be used for accessing sectors > 268435456
hda: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(66)
hda: cache flushes supported
 hda:hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
ide: failed opcode was: unknown
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
ide: failed opcode was: unknown
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
ide: failed opcode was: unknown
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
ide: failed opcode was: unknown
hdb: DMA disabled
ide0: reset: success
 hda1 hda2 < hda5 >
hdb: ATAPI 52X CD-ROM drive, 128kB Cache
Uniform CD-ROM driver Revision: 3.20
Attempting manual resume
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.


```

Linux version 2.6.18-5-686 (Debian 2.6.18.dfsg.1-13) (dannf@debian.org) (gcc version 4.1.2 20061115 (prerelease) (Debian 4.1.1-21)) #1 SMP Fri Jun 1 00:47:00 UTC 2007
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000000f000000 (usable)
 BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
0MB HIGHMEM available.
240MB LOWMEM available.
On node 0 totalpages: 61440
  DMA zone: 4096 pages, LIFO batch:0
  Normal zone: 57344 pages, LIFO batch:15
DMI 2.3 present.
ACPI: Unable to locate RSDP
Allocating PCI resources starting at 10000000 (gap: 0f000000:f0ff0000)
Detected 733.398 MHz processor.
Built 1 zonelists.  Total pages: 61440
Kernel command line: root=/dev/hda1 ro
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (011e9000)
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
PID hash table entries: 1024 (order: 10, 4096 bytes)
Console: colour VGA+ 80x25
Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Memory: 235708k/245760k available (1541k kernel code, 9572k reserved, 576k data, 196k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay using timer specific routine.. 1467.94 BogoMIPS (lpj=2935883)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Capability LSM initialized
Mount-cache hash table entries: 512
CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 256K
CPU serial number disabled.
CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
Compat vDSO mapped to ffffe000.
Checking 'hlt' instruction... OK.
SMP alternatives: switching to UP code
Freeing SMP alternatives: 12k freed
CPU0: Intel Pentium III (Coppermine) stepping 06
SMP motherboard not detected.
Local APIC not detected. Using dummy APIC emulation.
Brought up 1 CPUs
migration_cost=0
checking if image is initramfs... it is
Freeing initrd memory: 4776k freed
NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
PCI: Using configuration type 1
Setting up standard PCI resources
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI: disabled
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00f71a0
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x6064, dseg 0xf0000
PnPBIOS: 13 nodes reported by PnP BIOS; 13 recorded by driver
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
Boot video device is 0000:01:00.0
PCI: Using ALI IRQ Router
PCI: Using IRQ router ALI [10b9/1533] at 0000:00:07.0
PCI: Hardcoded IRQ 14 for device 0000:00:0f.0
PCI: Bridge: 0000:00:01.0
  IO window: b000-bfff
  MEM window: dde00000-dfefffff
  PREFETCH window: d1c00000-d5cfffff
PCI: Setting latency timer of device 0000:00:01.0 to 64
NET: Registered protocol family 2
IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
TCP established hash table entries: 8192 (order: 4, 65536 bytes)
TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
TCP: Hash tables configured (established 8192 bind 4096)
TCP reno registered
audit: initializing netlink socket (disabled)
audit(1194122567.780:1): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Initializing Cryptographic API
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)
Activating ISA DMA hang workarounds.
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
mice: PS/2 mouse device common for all mice
TCP bic registered
NET: Registered protocol family 1
NET: Registered protocol family 17
NET: Registered protocol family 8
NET: Registered protocol family 20
Using IPI No-Shortcut mode
Time: tsc clocksource has been installed.
Freeing unused kernel memory: 196k freed
input: AT Translated Set 2 keyboard as /class/input/input0
usbcore: registered new driver usbfs
usbcore: registered new driver hub
sis900.c: v1.08.10 Apr. 2 2006
PCI: setting IRQ 3 as level-triggered
PCI: Found IRQ 3 for device 0000:00:0e.0
0000:00:0e.0: SiS 900 Internal MII PHY transceiver found at address 1.
0000:00:0e.0: Using transceiver found at address 1 as default
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 3, 00:d0:09:81:43:a1.
ALI15X3: IDE controller at PCI slot 0000:00:0f.0
PCI: Hardcoded IRQ 14 for device 0000:00:0f.0
ALI15X3: chipset revision 194
ALI15X3: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
Probing IDE interface ide0...
hda: Maxtor 6L160P0, ATA DISK drive
hdb: CD-ROM 52X L, ATAPI CD/DVD-ROM drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
PCI: setting IRQ 10 as level-triggered
PCI: Found IRQ 10 for device 0000:00:02.0
ohci_hcd 0000:00:02.0: OHCI Host Controller
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
ohci_hcd 0000:00:02.0: irq 10, io mem 0xdffff000
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
hda: max request size: 128KiB
hda: cannot use LBA48 DMA - PIO mode will be used for accessing sectors > 268435456
hda: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(66)
hda: cache flushes supported
 hda:hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
ide: failed opcode was: unknown
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
ide: failed opcode was: unknown
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
ide: failed opcode was: unknown
hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
ide: failed opcode was: unknown
hdb: DMA disabled
ide0: reset: success
 hda1 hda2 < hda5 >
hdb: ATAPI 52X CD-ROM drive, 128kB Cache
Uniform CD-ROM driver Revision: 3.20
Attempting manual resume
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
logips2pp: Detected unknown logitech mouse model 89
input: PC Speaker as /class/input/input1
Linux agpgart interface v0.101 (c) Dave Jones
agpgart: Detected ALi M1631 chipset
agpgart: AGP aperture is 64M @ 0xd8000000
Real Time Clock Driver v1.12ac
ieee80211_crypt: registered algorithm 'NULL'
ieee80211: 802.11 data/management/control stack, git-1.1.13
ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Floppy drive(s): fd0 is 1.44M
input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
FDC 0 is a post-1991 82077
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
bcm43xx driver
PCI: setting IRQ 9 as level-triggered
PCI: Found IRQ 9 for device 0000:00:10.0
PCI: Sharing IRQ 9 with 0000:00:0c.1
bcm43xx: Could not determine Chip ID
BUG: unable to handle kernel NULL pointer dereference at virtual address 00000001
 printing eip:
cf9a081b
*pde = 00000000
Oops: 0000 [#1]
SMP
Modules linked in: bcm43xx firmware_class parport_pc parport floppy ieee80211softmac ieee80211 ieee80211_crypt snd rtc ali_agp agpgart pcspkr serio_raw psmouse shpchp pci_hotplug soundcore evdev ext3 jbd mbcache ide_cd cdrom ide_disk generic ohci_hcd alim15x3 ide_core sis900 mii usbcore processor
CPU:    0
EIP:    0060:[<cf9a081b>]    Not tainted VLI
EFLAGS: 00010246   (2.6.18-5-686 #1)
EIP is at bcm43xx_pctl_set_crystal+0x110/0x18e [bcm43xx]
eax: 00000000   ebx: 00000000   ecx: ce667d9c   edx: 00000200
esi: ce5e2da0   edi: 00000000   ebp: ffffffed   esp: ce667d9c
ds: 007b   es: 007b   ss: 0068
Process modprobe (pid: 1244, ti=ce666000 task=cebf6000 task.ti=ce666000)
Stack: 000000c0 00000000 000000ff cf9a8b8c ce5e2da0 00004710 cf992f68 c11c1800
       cefb7400 00000202 00000096 ffffffff 00000fff 00000001 ce667df8 c011624d
       00000000 00000003 ceb40574 00000000 ceb40574 00000000 00000001 ce667e1c
Call Trace:
 [<cf992f68>] bcm43xx_attach_board+0xea2/0xf0a [bcm43xx]
 [<c011624d>] __wake_up_common+0x2f/0x53
 [<c011669e>] __wake_up+0x2a/0x3d
 [<c012ac75>] __queue_work+0x3c/0x49
 [<c012accd>] queue_work+0x4b/0x50
 [<cf99449d>] bcm43xx_init_one+0x1f4/0x238 [bcm43xx]
 [<c0210c68>] __driver_attach+0x0/0x5d
 [<c01c19a8>] pci_device_probe+0x36/0x57
 [<c0210bc9>] driver_probe_device+0x42/0x8b
 [<c0210ca0>] __driver_attach+0x38/0x5d
 [<c02106ea>] bus_for_each_dev+0x33/0x55
 [<c0210b33>] driver_attach+0x11/0x13
 [<c0210c68>] __driver_attach+0x0/0x5d
 [<c0210403>] bus_add_driver+0x64/0xfd
 [<c01c1ae4>] __pci_register_driver+0x47/0x63
 [<c01358c1>] sys_init_module+0x16c3/0x1846
 [<c0161b4c>] cp_new_stat64+0xfd/0x10f
 [<c0102c11>] sysenter_past_esp+0x56/0x79
Code: 0c 8b 50 20 8b 40 10 51 b9 b4 00 00 00 e8 50 d9 81 f0 5e 85 c0 89 c3 75 77 b8 b8 ae 47 01 e8 2e a6 81 f0 eb 7b 8b 86 34 01 00 00 <80> 78 01 04 76 6f f6 86 98 00 00 00 20 75 66 ba 01 00 00 00 89
EIP: [<cf9a081b>] bcm43xx_pctl_set_crystal+0x110/0x18e [bcm43xx] SS:ESP 0068:ce667d9c
 <6>ts: Compaq touchscreen protocol output
Adding 698788k swap on /dev/hda5.  Priority:-1 extents:1 across:698788k
EXT3 FS on hda1, internal journal
loop: loaded (max 8 devices)
device-mapper: ioctl: 4.7.0-ioctl (2006-06-24) initialised: dm-devel@redhat.com
eth0: Media Link On 100mbps full-duplex
lp0: using parport0 (interrupt-driven).
ppdev: user-space parallel port driver
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
IPv6 over IPv4 tunneling driver
NET: Registered protocol family 5
Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
NFSD: starting 90-second grace period
eth0: no IPv6 routers present
lithium:/home/chris#

```

Also of note is the dump after;
  bcm43xx: Could not determine Chip ID
  BUG: unable to handle kernel NULL pointer dereference at virtual address 00000001

---

### Post by strider22 on 2007-11-03
There are 3 bug reports concerning aec62xx
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103755](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103755)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/69353](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/69353)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107740](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107740)

---

### Post by dawynn on 2007-11-06
Here's my details:

00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0) (prog-if 80 [Master])
	Subsystem: Silicon Integrated Systems [SiS] SiS5513 EIDE Controller (A,B step)
	Flags: bus master, fast devsel, latency 128
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ff00 [size=16]

[   17.905066] Probing IDE interface ide0...
[   18.319735] hda: Maxtor 6L120P0, ATA DISK drive
[   18.991334] Probing IDE interface ide1...
[   19.855123] hdc: DVDRW IDE 16X, ATAPI CD/DVD-ROM drive
[   20.638789] hdd: DVDROM 10X, ATAPI CD/DVD-ROM drive

The hard drive has a number of partitions.  The partitioning scheme was not changed at all for Gutsy.  It was working fine for Feisty:

1) vfat 4.760 MB
(not sure where 2 - 4 went)
5) vfat 9.529 MB
6) vfat 9.529 MB
7) vfat 9.529 MB
8) vfat 19.068 MB
9) vfat 19.068 MB
10) swap (256 MB, I believe)
11) ext3 /home 7.042 MB
12) ext3 /usr/local 9.389 MB
13) ext3 / (Gutsy root) 9.389 MB
14) ext3 (Feisty root) 9.389 MB
15) ext3 /boot 88 MB
16) ext3 (reserved for other root) rest of drive (about 10 MB)

Note: I was able to get Gutsy up and running by adding ide-generic and ide-disk to my /etc/initramfs-tools/modules file.  Its up, its running, but DMA does not work on either of my CD / DVD drives because of ide-generic.

---

### Post by dawynn on 2007-11-07
The more I look at this, the more I become convinced that, at least in my case, its a problem of not identifying the correct IDE driver.  ide-generic works -- somewhat.  But ide-generic breaks DMA, so its not the best solution.  I can use DMA in feisty, so I assume that, somewhere, there is a module for my ide device driver.

But that's where the problem comes in.  I've tried some searches on the web.  Evidently, I'm not specifying the right search criteria.

Can someone identify a link that provides guidance in determining the best module for a given IDE driver?  As you can see from my previous post, I have a SiS 5513 EIDE controller.  What kernel module does that translate to?  For the sake of helping everyone, please point to a guide that would provide guidance for many (if not all) IDE drivers.

Cheers!

---

### Post by dawynn on 2007-11-11
Perhaps this has something to do with the SiS 5513 issues:
From /boot/config-2.6.20-16-generic (feisty)
CONFIG_BLK_DEV_SIS5513=m

From /boot/config-2.6.22-14-generic (gutsy)
# CONFIG_BLK_DEV_SIS5513 is not set

For some reason, the Gutsy kernels have been compiled without SiS 5513 as even a module.  Can someone explain why?  If there's something wrong with the module, let's fix it.  But, I'm guessing completely cancelling the module is not the right thing to do.

(No, I have not yet tried rolling my own kernel)

Cheers!

---

### Post by rupierto on 2007-11-12
Similar problem?

[http://ubuntuforums.org/showthread.php?t=594180](http://ubuntuforums.org/showthread.php?t=594180)

---

### Post by strider22 on 2007-11-12
I don't think so. The following thread is talking about NTFS partitions rather than IDE or controler issues. I don't see the connection to this thread although until we know the answer won't know if they are connected. 

> Similar problem?

[http://ubuntuforums.org/showthread.php?t=594180](http://ubuntuforums.org/showthread.php?t=594180)

I'd be more willing to postulate that my problem might be related to broadcom network controllers.

---

### Post by strider22 on 2007-11-17
Based on my suspicion about broadcom, I went out and spent $20 for a new wireless PCI card and put the broadcom into storage.

I installed xubuntu 7.10 with no complaints at all. I've upgraded and rebooted and everything is fine. 

I'd say this IDE problem is really a broadcom problem.

---

### Post by barbaar on 2007-11-19
> **strider22 said:**
> Based on my suspicion about broadcom, I went out and spent $20 for a new wireless PCI card and put the broadcom into storage.

I installed xubuntu 7.10 with no complaints at all. I've upgraded and rebooted and everything is fine. 

I'd say this IDE problem is really a broadcom problem.
I don't think so. I have the same problem with gutsy x64_86

lspci:
```

root@ubuntu:/target/lib/modules/2.6.22-14-generic/kernel/drivers/scsi# lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
04:00.0 SCSI storage controller: HighPoint Technologies, Inc. RocketRAID 2310 4 Port SATA-II Controller (rev 02)
05:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
root@ubuntu:/target/lib/modules/2.6.22-14-generic/kernel/drivers/scsi#                
```

As you see, I have an Highpoint Rocketraid 2310 RAID-controller. Attached are two Seagates in RAID0. I downloaded the sourcecode for the kmods and compiled them. I think the Rocketraid has something to do with this..

Mobo: Asus a8n5x
No ATA disks connected, 1x cd-burner, 1x dvd-rom (both ata) and one dvd-burner (sata)

---

### Post by barbaar on 2007-11-19
Oh, lswh output:
```

root@ubuntu:/target/boot# lshw
ubuntu
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=D8753BDC-847A-DA11-9873-DE396216B970
  *-core
       description: Motherboard
       product: A8N5X
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.XX
       serial: 123456789000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS A8N5X ACPI BIOS Revision 1003 (06/01/2006)
          size: 128KB
          capacity: 448KB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          slot: Socket 939
          size: 2200MHz
          capacity: 3700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni lahf_lm cmp_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: b
             slot: L1 Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: d
             slot: L2 Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous internal write-back unified
     *-cpu:1
          description: CPU
          vendor: AMD
          physical id: 5
          bus info: cpu@1
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          slot: Socket 939
          size: 2200MHz
          capacity: 3700MHz
          clock: 200MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: L1 Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: e
             slot: L2 Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 3f
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             width: 64 bits
        *-bank:2
             description: DIMM 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 512MB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-multimedia
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3 module=amd74xx
        *-ide
             description: IDE Channel 1
             physical id: 1
             bus info: ide@1
             logical name: ide1
             clock: 66MHz
           *-cdrom:0
                description: CD-R/CD-RW writer
                product: LITE-ON LTR-12102B
                physical id: 0
                bus info: ide@1.0
                logical name: /dev/hdc
                version: NS1I
                capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                configuration: status=open
           *-cdrom:1
                description: DVD reader
                product: LITEON DVD-ROM LTD163
                physical id: 1
                bus info: ide@1.1
                logical name: /dev/hdd
                version: GDHF
                capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                configuration: mode=udma2 status=ready
              *-disc
                   physical id: 0
                   logical name: /dev/hdd
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 6
             bus info: pci@0000:05:06.0
             logical name: eth1
             version: 10
             serial: 00:40:f4:2e:41:38
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a3
          serial: 00:18:f3:02:71:d6
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=192.168.0.50 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-scsi
             description: SCSI storage controller
             product: RocketRAID 2310 4 Port SATA-II Controller
             vendor: HighPoint Technologies, Inc.
             physical id: 0
             bus info: pci@0000:04:00.0
             logical name: scsi8
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: scsi pm msi pciexpress bus_master cap_list scsi-host
             configuration: driver=rr2310_00 latency=0
           *-disk
                description: SCSI Disk
                product: DISK_8_0
                vendor: HPT
                physical id: 0.0.0
                bus info: scsi@8:0.0.0
                logical name: /dev/sda
                version: 4.00
                size: 148GB
                capabilities: partitioned partitioned:dos
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@8:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 94MB
                   capabilities: primary
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@8:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 972MB
                   capabilities: primary
              *-volume:2
                   description: Linux swap / Solaris partition
                   physical id: 3
                   bus info: scsi@8:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 1953MB
                   capabilities: primary nofs
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@8:0.0.0,4
                   logical name: /dev/sda4
                   size: 145GB
                   capacity: 145GB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 4769MB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 4769MB
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 136GB
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-display
             description: VGA compatible controller
             product: G70 [GeForce 7600 GT]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:01:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga bus_master cap_list
             configuration: latency=0
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp

```

Funny thing is.. I cannot create a new initrd by hand:
```
mkinitramfs -o /target/boot/initrd.img-2.6.22-14-generic 2.6.22-14-generic
```
This never finifshed, and the actual image is also 0 bytes. Maybe this has something to do with this?

Oh, and for some reason, I cannot edit my post :(

---

### Post by LarryT54 on 2007-11-20
I also have the same problem since upgrading from Feisty to Gutsy.  Feisty was working great and the upgrade appeared to run successfully, but I could not boot with the new 2.6.22-14-386 kernel.  

Pressing Ctrl-Alt-F1 revealed this error message:    ata1: SRST failed (errno = -16)  

The new kernel simply cannot recognize my hard disk.  Booting from the installation CD gives the same result - Gutsy loads but cannot recognize the hard disk.  It was already partitioned for a dual-boot system with Windows 2000 and Feisty Fawn.

Here are my system specs:

Asus motherboard  -  P4P800S-X
Chipset  -  82801EB/ER (ICH5/ICH5R)
Hard Disk  -  Western Digital WD1200JB-00GVA0

After a lot of time spent trying to make it work, I was relieved to learn that a bug has been identified for this Intel chipset.  

I really like using Ubuntu and will be checking frequently to see when a fix becomes available.

Many thanks, 
LarryT54

---

### Post by klhouse on 2007-11-23
I am a new linux user and I too have been getting the "disk drive not detected"  error during installation.            In another thread [http://ubuntuforums.org/showthread.php?t=617929]("http://ubuntuforums.org/showthread.php?t=617929")
 ChrisBieda  suggested changing the jumper on the Western Digital drive from Master to Single. I did this and it has solved the problem on my system.  Thanks ChrisBieda!

---

### Post by dawynn on 2007-12-01
I can't vouch for everyone here, but I will point out that for mfajer, even though his system indicated that his IDE controller was an INTEL 82801EB/ER, look at his lsmod report from etch.  It includes the SiS 5513 module -- a module that was present up through Feisty, but suddenly cancelled in Gutsy.  Note that this module was not cancelled by the Linux kernel folks, just disabled by the Ubuntu kernel folks.

I own a computer with an actual SiS 5513 IDE controller.  And I can vouch personally for the fact that the mere task of renabling this module in the kernel turns my computer from an unbootable machine into a working Gutsy machine.  Its a one-line code fix in the .config file that I'm trying to convince the kernel folks to make.  Initial reaction shows that this may not happen for Gutsy.

Cheers!

---

### Post by mfajer on 2007-12-05
> **klhouse said:**
> I am a new linux user and I too have been getting the "disk drive not detected"  error during installation.            In another thread [http://ubuntuforums.org/showthread.php?t=617929]("http://ubuntuforums.org/showthread.php?t=617929")
 ChrisBieda  suggested changing the jumper on the Western Digital drive from Master to Single. I did this and it has solved the problem on my system.  Thanks ChrisBieda!

That did the trick, thanks klhouse!!!

---

### Post by Lucifiel on 2007-12-07
I've the same problem with the latest version of Linux Mint: Daryna which is based on Ubuntu. Mint will not load past the "booting" screen if my IDE hdd is connected. 

Hmmm... I wonder if this issue will be fixed, come the next version of Ubuntu. If not, oh well.

Edit: I've looked at the recommended solution. Mmm... my hard disk is already set to Single(no jumper needed) 'cos there's only 1 Ide slot.

---

### Post by dawynn on 2007-12-19
As I was reviewing some bugs this morning, something finally caught my eye.  Please see bug 152820.

The original contributor of this bug indicated that he had problems with booting after doing an upgrade, but a fresh install fixed everything.  As indicated, there is something that does not get fixed by just doing an upgrade. Further, its indicated that the problem is likely in the /etc/fstab file.  This was confirmed just last week by the Ubuntu kernel folks.  When booting, there's some expectation to see certain drives under /dev/sda instead of /dev/hda.

I tested this.  I first went into /etc/fstab and changed every instance of /dev/hd* to /dev/sd*.  The computer now went further in the boot sequence, but stopped later prior to completing the boot process.  I then went back in and changed my /etc/fstab setup so only the '/' (root) partition specified /dev/sda* -- the others needed to be set to /dev/hda*.  This makes for a weird setup in /etc/fstab, but the point is -- it works.

So, now I can boot into Gutsy using the official Ubuntu kernel, instead of my own compile.  Someone more familiar with the complete specifics on the ata / pata changes for the Gutsy kernel needs to update the upgrade documentation with information about how to correct this issue for those that are upgrading instead of performing a fresh install.

Cheers!

---

### Post by rhempel on 2007-12-19
I've been seeing this error in my dmesg too. I am using an older Asus P4C800 motherboard and a newer Samsung HD300LD ATA drive as the slave drive.

My dmesg was showing the old Seagate 120G drive as the primary and properly configured for UDMA100.

The Samsung drive comes factory configured for UDMA133.

On a whim, I booted an Ultimate Boot CD and ran HDIAG from Samsung for drive diagnostics. I forced the drive to only report UDMA 100 (which is the highest supported by my BIOS) and voila, the drive is now recognized!

I wonder if some of the issues with additional drives on this thread have to do with UDMA incompatibility between what the drive reports it can do, what Ubuntu asks it to do, and what the drive controller chipset can actually do... :-)

Ralph

---

### Post by tuproxy on 2007-12-19
So has anyone been able to get their drives to work?  I had 5 WD 160GB IDE drives running in a RAID 0 array on 6.10.  How can a new distro go backwards in operability.?.  These are the reasons that i have not switched to Linux yet.  
:confused:

---

### Post by mfajer on 2007-12-20
[QUOTE=tuproxy]So has anyone been able to get their drives to work? How can a new distro go backwards in operability.?.  These are the reasons that i have not switched to Linux yet.  [/QUOTE]

My system became fully operational under Gutsy after I placed my hard disk alone on the primary IDE cable and removed the jumper on the drive to force it to SINGLE mode.  As to the operability, this problem seems fairly isolated (just look at the number of responses) and steps backwards occur all to frequently in all operating systems... human nature!  :-)

---

### Post by sebastion on 2007-12-27
Hi guys,

same error except I can't even boot to Ubuntu from the live CD. The error reports:

ata6: SRST Failed (errno=-16)

and this keeps repeating endlessly. And every time it is a different ata (ata6, ata8, ata1 or so).
This only occurs with Ubuntu Feisty 7.10 the 64 bit version. The 32 bit version works fine. I can't even boot to the live CD to install it. 

Anyone knows the answer?! Thx

---

### Post by killasooty on 2008-01-09
Hi ... I've been browsing threads like this one because I keep seeing DMA timeout errors reported on my son's system (an old HP Presario - Bios date was 1999) - every hard drive I  have fitted in it reports DMA errors like the ones in this thread - including CD drives.

prompted by the comment "*As to the operability, this problem seems fairly isolated (just look at the number of responses)*" I thought I'd mention that these messages look "normal" to me   :-)

I have installed Kubuntu & Ubuntu (all Gutsy) more times than I can count in the last month - & had a lot of system crashes (or desktop crashes?)  - these same disks perform without complaint when running windoze 

I also have a Kubuntu installation on my pc - which generally runs fine, but it sometimes logs DMA errrors as well - but only sometimes. 

These systems run, but I imagine they would run faster if the system supported DMA transfers.   The extract from dmesg below was taken from my running system just a minute ago - full of badness it seems, but my system is running. 

(also - being a noob with nearly 3 weeks of kubuntu under my belt now, I don't understand the significance of these logs yet - so any explanation would be gratefully received   :-)

Should I be concerned by any of this ????

```

[   22.072000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   22.072000] PCI: setting IRQ 11 as level-triggered
[   22.072000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   22.072000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   22.192000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/wireless/at76/at76c503.c: Atmel at76c50x USB Wireless LAN Driver 0.14beta1 loading
[   22.496000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/wireless/at76/at76c503.c: firmware version 0.100.5 #78 (fcs_len 4)
[   22.500000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/wireless/at76/at76c503.c: device's MAC 00:30:bd:63:d7:9d, regulatory domain ETSI (Europe - (Spain+France) (id 48)
[   22.500000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/wireless/at76/at76c503.c: registered wlan0
[   22.500000] usbcore: registered new interface driver at76_usb
[   22.948000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   22.948000] PCI: setting IRQ 10 as level-triggered
[   22.948000] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   22.948000] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   23.812000] lp0: using parport0 (interrupt-driven).
[   23.916000] Adding 1510068k swap on /dev/hdc5.  Priority:-1 extents:1 across:1510068k
[   24.464000] EXT3 FS on hdc1, internal journal
[   27.764000] No dock devices found.
[   27.988000] input: Power Button (FF) as /class/input/input4
[   27.988000] ACPI: Power Button (FF) [PWRF]
[   28.016000] input: Power Button (CM) as /class/input/input5
[   28.016000] ACPI: Power Button (CM) [PWRB]
[   28.496000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/wireless/at76/at76c503.c: 2522: assertion dev->istate == INIT failed
[   30.216000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/wireless/at76/at76c503.c: 1784: assertion dev->curr_bss == NULL failed
[   30.976000] ppdev: user-space parallel port driver
[   32.004000] audit(1199900603.951:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4725 profile="/usr/sbin/cupsd"
[   32.376000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   32.376000] apm: overridden by ACPI.
[   34.096000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: removed
[   34.704000] audit(1199900605.475:4):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=4796 profile="/usr/sbin/cupsd"
[   34.764000] audit(1199900605.475:5):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=4799 profile="/usr/sbin/cupsd"
[   34.984000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   34.984000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   34.984000] ide: failed opcode was: unknown
[   35.052000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   35.052000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   35.052000] ide: failed opcode was: unknown
[   35.512000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   35.512000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   35.512000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   38.460000] Failure registering capabilities with primary security module.
[   38.924000] Bluetooth: Core ver 2.11
[   38.924000] NET: Registered protocol family 31
[   38.924000] Bluetooth: HCI device and connection manager initialized
[   38.924000] Bluetooth: HCI socket layer initialized
[   39.100000] Bluetooth: L2CAP ver 2.8
[   39.100000] Bluetooth: L2CAP socket layer initialized
[   39.160000] Bluetooth: RFCOMM socket layer initialized
[   39.160000] Bluetooth: RFCOMM TTY layer initialized
[   39.160000] Bluetooth: RFCOMM ver 1.8
[   60.768000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   60.768000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   60.768000] ide: failed opcode was: unknown
[   60.844000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   60.844000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   60.844000] ide: failed opcode was: unknown
[   60.920000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   60.920000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   60.920000] ide: failed opcode was: unknown
[   61.000000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   61.000000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   61.000000] ide: failed opcode was: unknown
[   61.000000] hdd: DMA disabled
[   61.048000] ide1: reset: success
[  119.060000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  119.060000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[  119.060000] ide: failed opcode was: unknown
[  119.148000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  119.148000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[  119.148000] ide: failed opcode was: unknown
[  119.236000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  119.236000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[  119.236000] ide: failed opcode was: unknown
[  119.324000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  119.324000] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[  119.324000] ide: failed opcode was: unknown
[  119.372000] ide1: reset: success
[  220.808000] audit(1199900791.486:6):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=6403 profile="/usr/sbin/cupsd"
[  220.912000] audit(1199900791.486:7):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=6406 profile="/usr/sbin/cupsd"

```

---

### Post by Cdr_RF on 2008-01-12
Feisty & Gutsy live CDs mount 30GB Maxtor hard drive, but neither will mount 80GB Western Digital.  Hard drives (HDDs) are connected one at a time to the end (Master) plug of a 80-wire cable to the Primary IDE socket on an AOpen AX6B mainboard [Sandra: Chipset 1, Model: Intel Corporation 82443BX/ZX 440BX/ZX CPU to PCI Bridge (AGP Implemented), Intel 82371AB/EB PCI Bus Master IDE Controller].  CPU is PIII at 733MHz with Front Side Bus Speed = 133MHz.  (I know Sandra says FSB 100MHz max, but 133 is available in BIOS).  BIOS is the most recent available from AOpen (April 27, 2000, R2.35) and is set to auto-detect (Type & Mode = Auto) all IDE devices.  IDE cable Slave plugs are not connected to devices.  Motherboard does not have a SCSI socket and no SCSI adapter card is installed.  Feisty & Gutsy both mount a USB flash drive regardless of whether I'm using the 30GB or the 80GB HDD.  CD-RW connected to Secondary Master IDE.

30GB Maxtor DiamondMax Plus 8 6E030L0 [LBA 60058656] partitioned FAT32 C, D, E, F, G with the following sizes per Win95B System Resource Report (SRR):

       C:  Fixed Disk                   5924396K Total  3863796K Free [Win95B]
           739 Cylinders   255 Heads
           0 Bytes/Sector   63 Sectors/Track [<- SRR doesn't report correct Bytes/Sector]

       D:  Fixed Disk                   1392168K Total  933660K Free [smallest]
           174 Cylinders   255 Heads
           
       G:  Fixed Disk                   8361516K Total  746076K Free [largest]
           1043 Cylinders   255 Heads
           

80GB Western Digital [WD800JB-00ETA0, LBA 156301488, no jumper = Master or Single] also partitioned FAT32 C, D, E, F, G with the following sizes per Win98SE System Resource Report:

       C:  Fixed Disk                   7800336K Total  6147956K Free [Win98SE]
           973 Cylinders   255 Heads
           512 Bytes/Sector   63 Sectors/Track

       D:  Fixed Disk                   1956060K Total  1219784K Free [smallest]
           244 Cylinders   255 Heads
           
       G:  Fixed Disk                   24021456K Total  11855472K Free [largest]
           2992 Cylinders   255 Heads


Re: Gutsy (Ubuntu ver 7.10) with 80GB WD HDD:

No HDD icon visible on Desktop.  Only the following icons visible when Places > Computer: Floppy, CD-RW, USB Flash Drive, and Filessystem.

When System > Preferences > Hardware Information > Device Manager > Devices > SCSI Device > WDC WD800JB-00ET > 6 Volumes.  Volume information from Advanced Tabs: part1, part2, part5, part6, part7, and part8

Selected information from Device Manager's Advanced Tab, for the HDD as a whole:

block.device = /dev/sda
block.storage_device = /org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD800JB_00ETA0_WD_[I've deleted the HDD serial number]
storage.removable = false
storage.removable.media_size = 80026361856 (0x12a1f16000)

(I do not know now to expeditiously capture all of Device Manager's Advanced Tab parameters for a particular HDD partition, for example, other than via screen captures.  I tried Gutsy's Help with the search phrase 'Device Manager' [and other phrases] in an attempt to discover how to do this.)

Re: Knoppix v 4.02 (Linux Kernel 2.6.12) and v 5.0 (Kernel 2.6.17) with 80GB WD HDD:

Computer boots up with the following HDD mountable partitions (and other devices) on the Desktop: hda1, hda5, hda6, hda7, and hda8

---

### Post by Lord_Vader on 2008-01-13
> **mfajer said:**
> That did the trick, thanks klhouse!!!


Me too. :-)

---

### Post by barbex on 2008-01-18
I'd like to say a "me too" here regarding Gutsy and IDE HDD detection.

I was unable to install Gutsy on my Laptop with a SIS650 Chipset (my Thread is [Installation hangs on trm290 IDE chipset support (Feisty and Gutsy)]("http://ubuntuforums.org/showthread.php?t=620087"))

I'm quite sad about that.

---

### Post by joebob213 on 2008-06-30
Sorry to bump an old thread.

New guy here trying to install ubuntu for the first time!  

I am getting the SRST failed (errno=-16) message every time I try to install ubuntu.  A jumper on a Western Digital drive is not my problem.  I have two seagate drives and the only jumper on them is to force them to run at 1.5 gigs a second rather than 3 gigs.  

I just installed one of the drives today.  I am fed up with Windows and wanted to try something new but the frustration is about to change my mind!  

First I tried to install it on the same drive as my windows XP but gave up even after reading all the solutions I could find for the same problem.  I went out and bought a brand new hard drive that is now formatted and ready for data.  I've tried installing ubuntu with both drives hooked up and with each one seperate...  no luck.

Any suggestions?

---

### Post by barbex on 2008-07-01
Are you installing Hardy or Gutsy?

I was quite successful with Hardy, the install worked right away. If you are installing the most recent Ubuntu Hardy then you should probably start a new thread as this one is for Gutsy and some people might not look at it because of that.

By the way, I found some suggestions:
[http://ubuntuforums.org/showthread.php?t=637776](http://ubuntuforums.org/showthread.php?t=637776)
I know you said you had no jumper but if it is an IDE drive, you have jumpers to set the master-slave-order. I have had computers where I needed to set the drive to master and others set to single for the system to work at all. You can also try cable-select.

Have you ever set the jumper for single drive? Because there seems to be a known problem: [http://fixunix.com/ubuntu/397814-can-t-install-ubuntu-8-04-lts.html](http://fixunix.com/ubuntu/397814-can-t-install-ubuntu-8-04-lts.html)

There is a bug open, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706) you might want to watch that one too.

Good luck!

---

