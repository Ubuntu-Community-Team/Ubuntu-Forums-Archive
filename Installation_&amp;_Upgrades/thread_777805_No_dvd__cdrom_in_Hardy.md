---
title: "No dvd / cdrom in Hardy"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by gwoodruff on 2008-05-01
Since I upgraded to Hardy (via update manager) I can no longer mount my dvd rw drive. I can boot into Gutsy and the device is listed and mounts fine ect. If I boot into Hardy no cdrom  drive is listed in /DEV folder. I have a Hardy alternate install disk that will boot and start the install process until it scans for a cdrom. Then it errors and cannot locate one (neither can I). i am starting to think this may be some kernal error as I see other posts but with no solution.

I have:

changed IDE cables
changed drives from CS to Master/Slave
made sure cdvd is first boot device

All with no success. I would appreciate any help offered!

Thanks, Gary

---

### Post by gwoodruff on 2008-05-01
Here is some data for those that would like to see:

MOUNT

[sudo] password for gary: 
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda5 on /home type ext3 (rw)
/dev/sda6 on /tmp type ext3 (rw)
/dev/sda7 on /usr type ext3 (rw)
/dev/sda8 on /var type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gary@Ath-64:~$ 

fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e3a08ffd-b0e0-434c-b0dc-b8875bb714f7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=2b95ec6e-ba65-4986-8ccf-6067ab77fb8d /home           ext3    defaults        0       2
# /dev/hda6
UUID=d160bd4d-5d57-4a14-8cf4-201104591f55 /tmp            ext3    defaults        0       2
# /dev/hda7
UUID=a763d82d-b1aa-4146-af21-5aad9b6f1786 /usr            ext3    defaults        0       2
# /dev/hda8
UUID=3b79fa72-086d-4464-b686-dcf843b14e5e /var            ext3    defaults        0       2
# /dev/hda9
UUID=5aa7b1d4-8577-42f4-ba76-84f0ecece3a6 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

MTAB

/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
/dev/sda5 /home ext3 rw 0 0
/dev/sda6 /tmp ext3 rw 0 0
/dev/sda7 /usr ext3 rw 0 0
/dev/sda8 /var ext3 rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0

LSHW

ath-64                    
    description: Desktop Computer
    product: A13G
    vendor: PCCHIPS
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=0
  *-core
       description: Motherboard
       product: A13G
       vendor: PCCHIPS
       physical id: 0
       slot: &#65533;&#65533;
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (05/10/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3500+
          slot: Socket M2
          size: 2200MHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up rep_good pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: d
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: f
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cpu:1 DISABLED
          description: CPU
          vendor: Unknown
          physical id: 6
          bus info: cpu@1
          version: AMD Athlon(tm) 64 Processor 3500+
          slot: Socket M2
          size: 2211MHz
          capacity: 3GHz
          clock: 201MHz
        *-cache:0
             description: L1 cache
             physical id: e
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 10
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 2GiB
             width: 64 bits
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:06.0
          logical name: scsi0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-disk
             description: ATA Disk
             product: ST3120814A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: 5LSCA7JL
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=08020802
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                logical name: /dev/.static/dev
                version: 1.0
                serial: e3a08ffd-b0e0-434c-b0dc-b8875bb714f7
                size: 956MiB
                capacity: 956MiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2008-04-28 15:42:49 filesystem=ext3 modified=2008-05-01 15:45:01 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-05-01 15:38:13 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 110GiB
                capacity: 110GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /home
                   capacity: 88GiB
                   configuration: mount.fstype=ext3 mount.options=rw,relatime,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /tmp
                   capacity: 6675MiB
                   configuration: mount.fstype=ext3 mount.options=rw,relatime,data=ordered state=mounted
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   logical name: /usr
                   capacity: 9538MiB
                   configuration: mount.fstype=ext3 mount.options=rw,relatime,data=ordered state=mounted
              *-logicalvolume:3
                   description: Linux filesystem partition
                   physical id: 8
                   logical name: /dev/sda8
                   logical name: /var
                   capacity: 4957MiB
                   configuration: mount.fstype=ext3 mount.options=rw,relatime,data=ordered state=mounted
              *-logicalvolume:4
                   description: Linux swap / Solaris partition
                   physical id: 9
                   logical name: /dev/sda9
                   capacity: 1239MiB
                   capabilities: nofs
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1b:b9:96:fd:53
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.254.5 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: GeForce 6100 nForce 405
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list
          configuration: driver=nvidia latency=0 module=nvidia
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp

---

### Post by gwoodruff on 2008-05-02
bump - need help please - anyone?

---

### Post by Pumalite on 2008-05-02
I think that /media should be hanging from hda1:
'/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0'

---

### Post by odin79 on 2008-05-02
You are not alone, it seems like a lot of ppl are having this problem. IMHO I think it is a problem with Hardy.

---

### Post by gwoodruff on 2008-05-02
I think the fstab file is correct as I can still boot into Gutsy and this is the same fstab file used there. I have no problems with the this drive in Gutsy (shows up, mounts, ect), only when booted into Hardy is it missing. I will post a bug in launchpad

---

### Post by Pumalite on 2008-05-02
If you have both OS's and Gutsy owns the boot loader, then check the Hardy fstab and make sure the UUID's are OK.

---

### Post by gwoodruff on 2008-05-02
Pumalite - My fstab is posted above. I am not aware of different fstab files for the different releases. I am also confused as optical drives do not have uuid's in fstab (that I have seen).

Thanks, Gary

---

### Post by Pumalite on 2008-05-02
You have to make sure that blkid (in Terminal), fstab and menu.lst UUID's coincide, to boot Hardy.

---

### Post by gwoodruff on 2008-05-03
Pumalite, I am having trouble with my dvd drive when I boot to Hardy only. There is no UUID for optical drives in fstab. If you read all of my posts before offering advice your input may have more value.

---

### Post by pcmantinker on 2008-05-03
I have gotten my cd/dvd-rw drive and cd-rom drive mounting properly. It's weird because I have to start Hardy with a CD/DVD in one of my drives. I guess Hardy automatically mounts the media if it's present in the drive. Why doesn't it do that to begin with? :P Here is what I have for fstab:
```

/dev/cdrom0 /media/cdrom0 auto ro,noauto,user,exec 0 0
/dev/cdrom1 /media/cdrom1 auto ro,noauto,user,exec 0 0

```
I'm assuming that code will work for as many CD/DVD drives you have in your system. Just increment the cdrom number with each line, starting with 0. I haven't tried booting without a CD in the drive yet, but I will let you know if that works as well.

---

### Post by publicidadno on 2008-05-04
Maybe, try this:

```
gksudo gedit /etc/fstab
```

Replace:

/dev/cdrom0 /media/cdrom0 auto ro,noauto,user,exec 0 0
/dev/cdrom1 /media/cdrom1 auto ro,noauto,user,exec 0 0

By:

/dev/scd0 /media/cdrom0 auto ro,noauto,user,exec 0 0
/dev/scd1 /media/cdrom1 auto ro,noauto,user,exec 0 0

```
mount -a 
```

Regards

---

### Post by gwoodruff on 2008-05-04
I will give that a try Monday when I get to work. I am willing to try all but I do not believe the problem lies with fstab as Gutsy uses same fstab file and I can mount ect cd drive when booted into Gutsy. My guess is it's a problem with a different file or a kernel compatibility issue with my hardware. 

cdrom line from fstab being used by Gutsy and Hardy

/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

I have tried hdb as my hard drive partitions are listed as hda1-hda9 with the same result.
 Hard drive and dvd burner are on same IDE cable (tried new cable also)
Tried CS and M/S jumper settings on drives

Can someone confirm for me that if the optical drive does not show up in lshw no terminal command will mount it, or will the correct command make the device show up on the output of lshw?

One thing I love about Ubuntu is the level of support you get on these forums. While not everyone is an expert (nor am I) they are all trying to help one another. It's a wonderful thing. I have never found this available for any windows release from 3.10 to Vista. The Microsoft support channel was the best there is, and that's not saying much. The only way to add insult to that injury is when you have to pay for the product and then are extorted to pay more for support to solve a flaw in their product.



Thanks, Gary

---

### Post by gwoodruff on 2008-05-05
Bump- HELP.

I have tried changing the device to scd0 and scd1 in fstab (per above) with no success. The drive is ide and I believe this is to load a scuzzy drive? I have reverted back to:

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

as this works in Gutsy.

HELP PLEASE

---

### Post by cub on 2008-05-05
> **pcmantinker said:**
> I have gotten my cd/dvd-rw drive and cd-rom drive mounting properly. It's weird because I have to start Hardy with a CD/DVD in one of my drives. I guess Hardy automatically mounts the media if it's present in the drive.
That worked on my laptop as well. At least a workaround until the real issue is solved.

---

### Post by gwoodruff on 2008-05-06
Bump - I am still looking for a solution for this problem. I am seeing more and more people reporting similar problems with their optical drives. I have multiple PC's running Hardy and only one is unable to locate the dvd drive. I believe this error his hardware specific.

---

### Post by trebor7_1 on 2008-05-06
> **gwoodruff said:**
> Bump - I am still looking for a solution for this problem. I am seeing more and more people reporting similar problems with their optical drives. I have multiple PC's running Hardy and only one is unable to locate the dvd drive. I believe this error his hardware specific.

I have a similar problem all was well with 7.10 now although a DVD will mount ok it fails to play back. Also fails trying to burn an ISO image. I upgraded from 7.10 via the network but when I tried a clean install (onto a spare drive) I got the error 5 problem and could not load via CD. Had to burn the iso onto a DVD at min speed, that then loaded ok. However just got a great system that will not do anything with the DVD drive. Spent hours looking for fixes, no joy. Just going back to 7.10 now to make sure I was not dreaming everything was good then. If it is then maybe 8.10 will be next!

---

### Post by Pumalite on 2008-05-06
Sometimes the issue is resolved making the CD Drive 2nd Master. Depending on BIOS, sometimes AHCI does the trick, other times: Auto.

---

### Post by bml137 on 2008-05-06
> **gwoodruff said:**
> Bump- HELP.

I have tried changing the device to scd0 and scd1 in fstab (per above) with no success. The drive is ide and I believe this is to load a scuzzy drive? I have reverted back to:

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

as this works in Gutsy.

HELP PLEASE

I don't understand what is going on with Linux these days (I have been using it for almost 10 years now).  For some reason, IDEs are now SCSIs.  Maybe it is just Ubuntu though.  The UUID thing doesn't make sense either, as now we mount specific hard drives instead of their logical location.

That said, you CD drive is likely scdX now (where X is a number).  I have an IDE hd, IDE dvdrw, and SATA hd.

In Gutsy they were /dev/hda, /dev/hdc, and /dev/sda.
In Hardy they are /dev/sda, /dev/scd0, and /dev/sdb.

sda and sdb are random as to which points to which physical HD.  I have udev rules to make /dev/hda and /dev/sata so things make sense.

Do an "ls -l /dev/sc*" to see if you have scd0.  If you do, "ls -l /dev/cd" and you'll see it symbolically linked to scd0.

---

### Post by Pumalite on 2008-05-06
[http://i158.photobucket.com/albums/t82/Pumalite/Screenshot-1.png](http://i158.photobucket.com/albums/t82/Pumalite/Screenshot-1.png)

---

### Post by gwoodruff on 2008-05-07
I tried changing the fstab to scd0 with no success. I have two other pc's running Hardy besides the one with the dvd problem. Both of these pc's fstab files use hdc for the optical dives. This problem is going on since the Hardy upgrade was released with no solution. I also have lockup issues with any browser (FF, SM, Opera) I have tried in Hardy. I may have to revert back to Gutsy and scrap Hardy as it is not proving to be a reliable or stable release for me. I do not like going backwards and would prefer to forge ahead and make this work -- HELP

---

### Post by Therion on 2008-05-07
Don't know if it will help, but see my post:  [http://ubuntuforums.org/showthread.php?t=785417](http://ubuntuforums.org/showthread.php?t=785417)

---

### Post by gwoodruff on 2008-05-07
Already changed the drive cables and currently have 40/80. My problem is a little different as I NEVER see my drive in HARDY. I am going to try a older cdrom (not dvd) and see what happens. IMHO Hardy was NOT ready for release.

---

### Post by trebor7_1 on 2008-05-07
> **gwoodruff said:**
> Already changed the drive cables and currently have 40/80. My problem is a little different as I NEVER see my drive in HARDY. I am going to try a older cdrom (not dvd) and see what happens. IMHO Hardy was NOT ready for release.

Have to agree with you there gwoodruff. Finally got 7.10 on a spare drive and my dvd drive is perfect. Might play spot the difference but not sure I have the skills or patience

---

### Post by gwoodruff on 2008-05-07
The problem is hardware specific. I put in an old cdrw drive and it was present and mountable. I thought OK maybe there was some corruption because of the upgrade process. I did a clean install with a Hardy AMD64 alt cd. I had to restart the install 3 different times as it hung up at random points during installation (all 3 different - wtf?).  The  process completed and everything seems fine with the cdrw. I reinstalled the dvd rw and no optical drives can be found once again. I have not tracked down the manufacturer as it is not clearly labeled on the drive.

---

### Post by cybergalvez on 2008-05-07
> **bml137 said:**
> I don't understand what is going on with Linux these days (I have been using it for almost 10 years now).  For some reason, IDEs are now SCSIs.  Maybe it is just Ubuntu though.  The UUID thing doesn't make sense either, as now we mount specific hard drives instead of their logical location.

That said, you CD drive is likely scdX now (where X is a number).  I have an IDE hd, IDE dvdrw, and SATA hd.

In Gutsy they were /dev/hda, /dev/hdc, and /dev/sda.
In Hardy they are /dev/sda, /dev/scd0, and /dev/sdb.

sda and sdb are random as to which points to which physical HD.  I have udev rules to make /dev/hda and /dev/sata so things make sense.

Do an "ls -l /dev/sc*" to see if you have scd0.  If you do, "ls -l /dev/cd" and you'll see it symbolically linked to scd0.

you can also do "sudo lshw | less" to see how your hardware is actually listed, thats how I found mine
Jose

---

### Post by cub on 2008-05-09
> **gwoodruff said:**
> The problem is hardware specific.
I agree. I have the same problem on a HP nx9010 laptop and there's not really a good way to change cables or the drive like suggested in other threads.

---

### Post by gwoodruff on 2008-05-09
I am convinced this is a hardware compatibility issue. I have two other pc's running Hardy both with DVDRW drives that work properly. I cannot make the 3rd DVDRW drive show up. I will replace this drive. I am aslo starting a new post asking users to furnich thier model/make of dvdrw that is working or not. Maybe we can track down the issue.

---

