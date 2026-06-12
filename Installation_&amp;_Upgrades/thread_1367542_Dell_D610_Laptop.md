---
title: "Dell D610 Laptop"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by kerryedwards on 2009-12-29
Greetings
I just received a Dell latitude D610 laptop as a gift. It had windows xp pro installed and it was working as good as could be expected using windows. 

Last night I attempted to install Ubuntu 4.10 in this computer. I used the whole disk and removed windows.

After installation and at first boot up(operating system did not start up) I received the following message:

error: no such device: 9964c975-1765-46d2-bd8f-e5bace0488d0

I really need this laptop for my small business.

Can someone please help me get my computer up and running? Please note that I am  not well versed in computer things but I learn fast.

Thank You very much for any help.

---

### Post by phillw on 2009-12-29
Hi & welcome to the forums.

A quick question ... what version of ubuntu did you install ?

Regards,

Phill.

---

### Post by kerryedwards on 2009-12-29
Hi Phil,
I installed Ubuntu 4.10 karmic koala (32 bit). 

Thanks

---

### Post by recluce on 2009-12-29
> **kerryedwards said:**
> Hi Phil,
I installed Ubuntu 4.10 karmic koala (32 bit). 

Thanks

4.10 = Warty Warthog

Karmic Koala = 9.10

Still doesn't make sense....

---

### Post by kerryedwards on 2009-12-29
Sorry!

I installed Karmic Koala 9.10

---

### Post by presence1960 on 2009-12-29
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by kerryedwards on 2009-12-30
Hi presence1960, 

I just tried to get the info text and I got the following:

bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory

Thanks

---

### Post by Bartender on 2009-12-30
I think you have to download his script first.

You may want to try installing 9.04 instead.  I did an experiment with an external drive the other day.  The details aren't important, suffice to say the exact same experiment done with 9.04 worked.  When I tried it in 9.10, I got a similar error message.  The long alphanumeric code you see is some sort of identification assigned to the disk.

---

### Post by moody_mark on 2009-12-30
I was running Ubuntu on a Dell 610 for ages. I can tell you that everything worked just fine so I dont think you'll have any compatibility issues. Im guessing here but Id say something went wrong with the install, perhaps you didnt finish the install?

One thing to try which will be very quick, boot the PC with the CD in the drive, hit F12 and boot from the CD, choose "try ubuntu without installing" when it boots to the desktop can you see your hard disc under "Places --> Computer"? If not then maybe something hardware wise has gone wrong and it actually cant find the drive.

The output of "sudo lshw" shows the hardware on your machine, posting that here might help too.

---

### Post by kerryedwards on 2009-12-30
Hi Moodey Mark

here is the info that might help.

ubuntu@ubuntu:~$ sudo 1shw
sudo: 1shw: command not found
ubuntu@ubuntu:~$ sudo lshw
ubuntu                    
    description: Portable Computer
    product: Latitude D610
    vendor: Dell Inc.
    serial: 7GNGM81
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-4700-104E-8047-B7C04F4D3831
  *-core
       description: Motherboard
       product: 0U8082
       vendor: Dell Inc.
       physical id: 0
       serial: .7GNGM81.CN4864359H0118.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A06 (10/02/2005)
          size: 64KiB
          capacity: 512KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.86GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.13.8
          slot: Microprocessor
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 768MiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: CE00000000000000
             physical id: 0
             serial: 500579D4
             slot: DIMM_A
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: C100000000000000
             physical id: 1
             serial: 020D7726
             slot: DIMM_B
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:dff00000-dff7ffff ioport:ec38(size=8) memory:c0000000-cfffffff(prefetchable) memory:dfec0000-dfefffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:dff80000-dfffffff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 memory:dfd00000-dfdfffff
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:14:22:b4:dd:7a
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5751-v3.29a ip=192.168.1.103 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:16 memory:dfdf0000-dfdfffff
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:bf80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:bf60(size=32)
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:bf40(size=32)
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:bf20(size=32)
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:ffa80800-ffa80bff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:dfc00000-dfcfffff memory:30000000-33ffffff(prefetchable)
           *-pcmcia
                description: CardBus bridge
                product: PCI6515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:19 memory:dfc00000-dfc00fff ioport:1400(size=256) ioport:1800(size=256) memory:30000000-33ffffff(prefetchable) memory:34000000-37ffffff
           *-communication UNCLAIMED
                description: Communication controller
                product: PCI6515 SmartCard Controller
                vendor: Texas Instruments
                physical id: 1.5
                bus info: pci@0000:03:01.5
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
                resources: memory:dfcfd000-dfcfdfff memory:dfcfe000-dfcfefff
           *-network
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:03:03.0
                logical name: eth1
                version: 05
                serial: 00:16:6f:ca:78:a4
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
                resources: irq:17 memory:dfcff000-dfcfffff
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:16 ioport:ed00(size=256) ioport:ec40(size=64) memory:dfebfe00-dfebffff memory:dfebfd00-dfebfdff
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16)
           *-disk
                description: ATA Disk
                product: HTS548040M9AT00
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MG2O
                serial: MRL202L2HDU07G
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=69205244
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: 9964c975-1765-46d2-bd8f-e5bace0488d0
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2009-12-28 23:00:47 filesystem=ext4 lastmountpoint=/target&#65533;S&#65533;&#65533;+&#65533;&#65533;0&#65533;&#65533;=Z&#65533;^&#65533;&#65533;iW&#65533;&#1557;h&#65533;&#65533;&#65533;&#65533;&#65533;h&#65533;+&#65533;&#65533;&#65533;^&#65533;&#65533;^&#65533;&#65533;&#65533;Y&#65533;&#65533;+&#65533; modified=2009-12-28 23:38:47 mounted=2009-12-28 23:38:47 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1608MiB
                   capacity: 1608MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1608MiB
                      capabilities: nofs
              *-volume:2 UNCLAIMED
                   description: Empty partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   capacity: 25MiB
                   capabilities: primary nofs
           *-cdrom
                description: DVD reader
                product: RW/DVD GCC-4241N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: A100
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
  *-battery
       product: DELL C260352
       vendor: Sony
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 48000mWh
       configuration: voltage=11.1V
ubuntu@ubuntu:~$

---

### Post by presence1960 on 2009-12-30
kerry we need the info from the script output. Click on the _Boot Info Script_ link in my signature. Download it & then move it to the desktop. Then run that command from terminal please. Post the contents of the RESULTS.txt file generated by the script.

[B]when posting large amount of text to the forum highlight the text then click the # sign on the top toolbar (see pic @ bottom - note my pointer. That is the # sign. This will prevent that text from taking up mega space on the page). It works like this:
[/B]
```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb
 => Lilo is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda7 and 
                       looks at sector 46409591 on boot drive #2 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/grub.conf.
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f07bc0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   123,234,614   123,234,552   5 Extended
/dev/sda5                 126     8,385,929     8,385,804  82 Linux swap / Solaris
/dev/sda6           8,385,993    46,138,679    37,752,687  83 Linux
/dev/sda7          46,138,743    88,084,394    41,945,652  83 Linux
/dev/sda2         203,896,980   976,768,064   772,871,085  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b4c62

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02020202

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   104,856,254   104,856,192   7 HPFS/NTFS
/dev/sdc2         104,856,255   230,693,399   125,837,145   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: LABEL="backup" UUID="b37b51c7-cc17-4401-a66c-4d43193d508a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="63538de2-1cc9-4451-ab42-5f8712695c89" TYPE="swap" 
/dev/sda6: LABEL="karmic" UUID="e0b415e6-168b-49e7-b62b-0fc42c83a6d7" TYPE="ext4" 
/dev/sda7: LABEL="Sabayon_5.0" UUID="b9e8a529-266d-4dd2-b892-914893cee3a2" TYPE="ext4" 
/dev/sdb1: LABEL="data" UUID="8f5b8ecd-2930-46a1-8256-88235c860965" TYPE="ext3" 
/dev/sdc1: UUID="5B8A70BC5646AB94" LABEL="xp" TYPE="ntfs" 
/dev/sdc2: UUID="42D35EE6525751C9" LABEL="win_data" TYPE="ntfs" 
/dev/ramzswap0: TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/raz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=raz)
/dev/sdb1 on /media/data type ext3 (rw,nosuid,nodev,uhelper=devkit)


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set b9e8a529-266d-4dd2-b892-914893cee3a2
	linux /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sdb7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sdb5 real_resume=/dev/sdb5
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
}
menuentry "Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (safe mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set b9e8a529-266d-4dd2-b892-914893cee3a2
	linux /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sdb7 dolvm init=/linuxrc console=tty1 resume=swap:/dev/sdb5 real_resume=/dev/sdb5 gentoo=nox gentoo=nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 5b8a70bc5646ab94
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


   4.2GB: boot/grub/grub.cfg
   4.2GB: boot/initrd.img-2.6.31-16-generic
   4.2GB: boot/initrd.img-2.6.31-17-generic
   4.2GB: boot/vmlinuz-2.6.31-16-generic
   4.2GB: boot/vmlinuz-2.6.31-17-generic
   4.2GB: initrd.img
   4.2GB: initrd.img.old
   4.2GB: vmlinuz
   4.2GB: vmlinuz.old

========================== sda7/boot/grub/grub.conf: ==========================

# grub.conf generated by the Sabayon Linux Installer
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd1,6)
#          kernel /boot/kernel-genkernel real_root=/dev/sdb7
#          initrd /boot/initramfs-genkernel
### AUTOMAGIC BOOT DEVICE DETECTION -- DO NOT REMOVE ###
#boot=sdb7
### AUTOMAGIC BOOT DEVICE DETECTION END ###
default=0
timeout=5
splashimage=(hd1,6)/boot/grub/splash.xpm.gz


title Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon)
	root (hd1,6)
	kernel /boot/kernel-genkernel-x86_64-2.6.31-sabayon  root=/dev/ram0 ramdisk=8192 real_root=/dev/sdb7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sdb5 real_resume=/dev/sdb5
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
	savedefault


title Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (safe mode)
	root (hd1,6)
	kernel /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sdb7 dolvm init=/linuxrc console=tty1 resume=swap:/dev/sdb5 real_resume=/dev/sdb5 gentoo=nox gentoo=nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
	savedefault


title Other Operating System - Microsoft Windows
	rootnoverify (hd2,0)
	chainloader +1
	savedefault

=============================== sda7/etc/fstab: ===============================

/dev/sdb7               /                       ext4    user_xattr,noatime 1 1
/dev/shm                /dev/shm                tmpfs   defaults        0 0
/dev/sdb5               swap                    swap    defaults        0 0

=================== sda7: Location of files loaded by Grub: ===================


  23.6GB: boot/grub/grub.conf
  23.6GB: boot/grub/menu.lst
  23.6GB: boot/grub/stage2

================================ sdc1/boot.ini: ================================

[Boot Loader]

timeout=15

Default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[Operating Systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="USB Repair NOT to Start Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  0a 00 01 0f 00 65 5d 04  a0 32 00 00 00 00 03 03  |.....e]..2......|
00000010  00 62 61 00 00 00 00 00  00 00 04 32 00 61 61 01  |.ba........2.aa.|
00000020  0c 00 00 00 00 00 05 33  00 64 64 00 00 00 00 00  |.......3.dd.....|
00000030  00 00 07 0f 00 52 3c ee  0a 97 0a 00 00 00 09 32  |.....R<........2|
00000040  00 5f 5f 40 11 00 00 00  00 00 0a 13 00 64 64 00  |.__@.........dd.|
00000050  00 00 00 00 00 00 0c 32  00 62 62 34 0a 00 00 00  |.......2.bb4....|
00000060  00 00 bb 32 00 64 64 00  00 00 00 00 00 00 bd 3a  |...2.dd........:|
00000070  00 64 64 00 00 00 00 00  00 00 be 22 00 47 39 1d  |.dd........".G9.|
00000080  00 1d 1d 00 00 00 c2 22  00 1d 2b 1d 00 00 00 12  |......."..+.....|
00000090  00 00 c3 1a 00 76 39 35  d3 d2 0b 00 00 00 c5 12  |.....v95........|
000000a0  00 64 64 00 00 00 00 00  00 00 c6 10 00 64 64 00  |.dd..........dd.|
000000b0  00 00 00 00 00 00 c7 3e  00 c8 c8 00 00 00 00 00  |.......>........|
000000c0  00 00 c8 00 00 64 fd 00  00 00 00 00 00 00 ca 32  |.....d.........2|
000000d0  00 64 fd 00 00 00 00 00  00 00 00 00 00 00 00 00  |.d..............|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 82 00 ae 01 00 5b  |...............[|
00000170  03 00 01 00 01 40 02 00  00 00 00 00 00 00 00 00  |.....@..........|
00000180  00 00 00 00 00 00 03 02  03 03 03 03 03 03 03 00  |................|
00000190  00 00 00 00 00 00 00 01  d9 53 13 16 00 00 00 00  |.........S......|
000001a0  01 00 af 1a 29 85 e3 01  00 00 00 00 00 00 00 00  |....)...........|
000001b0  00 00 00 00 d9 53 13 16  62 4c 0b 00 00 00 00 01  |.....S..bL......|
000001c0  01 00 83 fe ff ff 3f 00  00 00 42 45 1c 1d 00 00  |......?...BE....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by kerryedwards on 2009-12-30
Hi Everyone,

I reinstalled ubuntu, this time 9.04 as Bartender suggested, and now my computer boots right up and I am updating as we speak. 

Thanks everyone for taking time to help me.

---

