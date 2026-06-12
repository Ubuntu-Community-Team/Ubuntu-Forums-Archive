---
title: "Not Recognizing Video Card and Sata Hard Drive on Ubuntu 9.10"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by rcaca0 on 2010-02-21
Hello Again,

I have been trying to install Ubuntu on my main computer for some time.  I think I have two problems: my hard drive and video card.  I started with Ubuntu 9.04 but got nowhere.  I am now trying Ubuntu 9.10 32 bit.  I can at least use the live cd if I put the video on safe mode.  

Just in case you are wondering, I have tried other distros: Fedora, OpenSUSE, Slitaz, Wolvix, etc.  Only Slitaz and Ubuntu 9.10 works on a live cd.  

Information on my computer:
OS: Trying to install Ubuntu 9.10 32bit
Motherboard: ASUS M3A78
CPU: AMD Phenom 9500 Quad Core
Video Card: Galaxy Geforce 9500 GT 1GB 128 bit DDR2 (Nvidia)
Hard Drive: Hitachi 1 TB Sata Drive 3 Gb/sec 7200 RPM
Ram: 4 GB (I think, its been awhile since I built this thing)
DVD Burner: LG


I think I have two problems: the Sata Hard Drive and the Video Card.  When I go to install it, I can get to the install menu but from there all I get is a blank screen.  I have tried to put the video in safe mode then install it but I get the same result: a blank screen.  

How do I know if Ubuntu recognize the Hard Drive and Video Card?  I tried the mount command to see what it sees but I didn't notice any Sata Drives. I was told that I may have to do something with the kernel so it will recognize my Hard Drive.  How would I do that?  

I don't know what my next steps should be for troubleshooting so any help will be appreciated.  I have been working on this for awhile now.  

On a side note, does it matter which Sata Plug the hard drive is on?  Right now I have it on the 1st one but I would like to move it to the second one because I want a dual boot system.  And yes I know I can use the same hard drive but I would like to keep them separated and use a switch to pick which OS system to use.  

While running on the Live Cd, Ubuntu seems to know about my video card and ask to install some drivers but then it asked to be rebooted and it came back up not recognizing anything; video card and hard drive that is.  

On the live cd I ran the following commands: lswh, lspci, mount, and df.  I am not too sure if they will show if the hard drive and the video card are working since I did them on the Live CD.  Also on the lspci command, I did this after Ubuntu loaded the driver for the card.  
[B][COLOR=Red]
Here is the output of the lswh command:[/COLOR][/B] 

ubuntu
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3276MiB
     *-cpu
          product: AMD Phenom(tm) 9500 Quad-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.2.2
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RX780/RX790 Chipset Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RD790 PCI to PCI bridge (external gfx0 port A)
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:d000(size=4096) memory:f8000000-fbefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G96 [GeForce 9500 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff(prefetchable) memory:f8000000-f9ffffff ioport:dc00(size=128) memory:fbe80000-fbefffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port C)
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:e000(size=4096) memory:fbf00000-fbffffff ioport:f6f00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:23:54:d7:0b:b1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.101 latency=0 multicast=yes
                resources: irq:27 ioport:e800(size=256) memory:fbfff000-fbffffff memory:f6ff0000-f6ffffff(prefetchable) memory:fbfc0000-fbfdffff(prefetchable)
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:c000(size=8) ioport:b000(size=4) ioport:a000(size=8) ioport:9000(size=4) ioport:8000(size=16) memory:f7fff800-f7fffbff
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f7ffe000-f7ffefff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f7ffd000-f7ffdfff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:f7fff000-f7fff0ff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f7ffc000-f7ffcfff
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f7ffb000-f7ffbfff
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:f7ffa800-f7ffa8ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:f7ff4000-f7ff7fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
        *-usb:6
             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f7ff9000-f7ff9fff
     *-pci:1
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz

**[COLOR=Red]Here is the output of the lspci command:[/COLOR]**

00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

**[COLOR=Red]Here is the output of the mount command:[/COLOR]**

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
[B][COLOR=Red]
Here is the output of the df command (I did this just in case I could not recognize the hard drive in the mount command):[/COLOR][/B]

Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   1677608    191828   1485780  12% /
udev                   1677608       244   1677364   1% /dev
/dev/sr0                706532    706532         0 100% /cdrom
/dev/loop0              684032    684032         0 100% /rofs
none                   1677608       136   1677472   1% /dev/shm
tmpfs                  1677608        68   1677540   1% /tmp
none                   1677608        88   1677520   1% /var/run
none                   1677608         0   1677608   0% /var/lock
none                   1677608         0   1677608   0% /lib/init/rw



thanks,
R

---

### Post by darkod on 2010-02-21
Don't worry about the video right now, just run in safe graphics. Any drivers you install in the live desktop are lost after reboot. Once you have it installed on the hdd you'll install drivers and they'll stay there of course.

About the HDD. When you say you got a blank screen, you mean in step 4 in the installer it doesn't show you any hdd to install onto? And in the info about your computer you wrote one hdd but then you are asking about plugging it in 1st or 2nd connector and dual boot. How many hdds do you have?

In the live desktop, if you open Gparted (System-Administration) can you see the hdds?

---

### Post by rcaca0 on 2010-02-21
When I go to install on my Hard Drive I will see a blinking Ubuntu logo then it will go to a blank screen with the underscore on the top left of the screen.  After a while the screen will just go blank.  I am not too sure what you mean by step 4.  I am just going by the screen where you get to pick your options: Work with Ubuntu without install, Check hard drive, install, etc (<-- I don't have these in order).  Also is there a way to see what is going on in the background?  I thought I could press  ALT F2 and the screen will show me whats going on.  
 
As for my hard drives I have two 1 TB Hitachis on this computer.  It really is not a true dual boot since I turn on (using a switch) the power to only one Hard Drive at a time, so the computer only knows of one.  For this test I have the switch deactivated a just have the Hard Drive plugged into the Sata Port and Power it up.  The other hard drive is completely unplugged.  In other words it is set up as a normal computer.  Once I have everything installed and running I would like to go ahead and activate the switch so I can choose between Hard drive.  Thats why I was asking if it matters if I use another Sata Port besides 1.  Sorry for the confusion.  
 
Where is the Gparted program?  I am looking under System --> Administration and I don't see anything called Gparted.  (I'm at work so I am looking at another system with Ubuntu 9.04 on it)  I even opened the Synapic Package Manager and I don't see anything like that.  I'll double check this when I get home.  If I am looking in the wrong place let me know.  
 
Thanks again for your help,
R

---

### Post by oldfred on 2010-02-21
Gparted is not in the installed version as you cannot edit mounted partitions. We often download it (synaptic)  anyway to review partitions and possibly edit unmounted other drives. It is installed in almost all liveCD's.

SATA ports should not matter. One advantage of Grub is it lets you select which drive/partition to boot so you do not have to do drive switching. I still like to have each drive be able to boot on its own as a backup in case of issues on a drive.

Have you installed and it is not working or is it that you cannot see the installer?

---

### Post by rcaca0 on 2010-02-21
I found the Gparted. On the Live CD it is where darkod mentioned it would be. When I ran it I could see the hard drive. 
 
 
It clearly shows a device on /dev/sda1. File system; ntfs Size 931.5 GiB Used 3.92 GiB Unused 927.58 GiB Flags: boot.... then under status it shows the status of "Not Mounted". 
 
I tried the mount command by typing mount /dev/sda1 but it gave a reply of cant find /dev/sda1 in /etc/fstab or /etc/mtab. What does this mean? It knows it is there but for some reason I cannot mount it. 
 
On the dual hard drives, don't worry about it for now.  I have disabled the other drive (aka I disconnected it). So it is set up like a regular computer.  Sorry for the confusion.  As for the install and is it working, I can get it started but I don't think it is going anywhere.  I just end up at a blank screen.  I think it is not working because it does not recongize my hard drive.  Do you know of a way to see what is going on in the background?  I think I need to press alt F2 or Cltrl F2 but neither one works.  
 
 
Thanks again for your help, 
 
R

---

### Post by oldfred on 2010-02-22
When you say it is working but a blank screen, do you get a grub menu. If you only have Ubuntu you may have to hold down the shift key to know if you are past the menu. I would try booting the recovery mode if you do get the menu. If you do not get a menu and it is still a boot issue and not now the video issue then run the script in Darko's signature. Script will not help if booting is ok but it is now a video issue.

---

### Post by rcaca0 on 2010-02-22
I have two issues: the video card and my hard drive.  The video card I think I found a work around.  I just put it in Safe Mode (F4) for the video on the Install Menu.  At that point I can then work from the Live CD.  
 
As for the hard drive the menu that I am talking about is the install menu.  I will click on the Install Ubuntu and it will eventually lead me to a blank screen.  On this hard drive there is another OS on it.  I installed the "other" OS on it to verify that the hard drive was working.  Otherwise it is completely blank.  I have no plans on using this "other" OS just wanted to test.  On my test computer I did not have any issues installing the Ubuntu OS on a hard drive with a previous OS on it.  I want this hard drive to only have Ubuntu on it. The biggest difference between the two computers is that this computer uses Sata Hard Drives.   
 
To make sure I am reading write, when I get home I am going to try to reinstall and press and hold the Shift key to see if I can see what is going on in the background while I am installing.  
 
Thanks again for all of your help, 
R

---

### Post by darkod on 2010-02-22
> **rcaca0 said:**
> I have two issues: the video card and my hard drive.  The video card I think I found a work around.  I just put it in Safe Mode (F4) for the video on the Install Menu.  At that point I can then work from the Live CD.  
 
As for the hard drive the menu that I am talking about is the install menu.  I will click on the Install Ubuntu and it will eventually lead me to a blank screen.  On this hard drive there is another OS on it.  I installed the "other" OS on it to verify that the hard drive was working.  Otherwise it is completely blank.  I have no plans on using this "other" OS just wanted to test.  On my test computer I did not have any issues installing the Ubuntu OS on a hard drive with a previous OS on it.  I want this hard drive to only have Ubuntu on it. The biggest difference between the two computers is that this computer uses Sata Hard Drives.   
 
To make sure I am reading write, when I get home I am going to try to reinstall and press and hold the Shift key to see if I can see what is going on in the background while I am installing.  
 
Thanks again for all of your help, 
R

OK, that's progress. I'm not sure directly selecting Install Ubuntu uses safe mode too, so you might try the following:
Use safe mode again and load the live desktop. Once it finishes loading, there should be Install icon on the desktop. Start the installer from there.
If all is fine it should show you your hdd and since you want ubuntu as only OS in step 4 of the installer just select Erase and use whole disk option. Note that after the install finished and you reboot you might not be able to boot OK until you sort out a video driver.
If I'm correct, you don't have any hdd issue, but the issue is only related to the video card. Lets see by doing the above.

---

### Post by styxone on 2010-02-22
hi guys i got a problem, i got an ext hard driver and when i try to clic on, i got this.

 iError mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0xc54cc946  size: 1024  usa_ofs: 32816  usa_count: 32770: Invalid argument
Record 6 has no FILE magic (0xc54cc946)
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.t 

i need help please

---

### Post by darkod on 2010-02-22
> **styxone said:**
> hi guys i got a problem, i got an ext hard driver and when i try to clic on, i got this.

 iError mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0xc54cc946  size: 1024  usa_ofs: 32816  usa_count: 32770: Invalid argument
Record 6 has no FILE magic (0xc54cc946)
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.t 

i need help please

Please don't hijack the OP thread! Did you try connecting the hdd to a windows computer and running the

chkdsk /f F: (use the letter of the drive)

as suggested by that message?

---

### Post by rcaca0 on 2010-02-22
I think I tried to install before from the Live CD before but I don't remember (too many computers).  I'll go ahead and try it when I get home and let you know what I get.  
 
I do have a few more questions.  Why when I ran the Gparted it showed the hard drive as not being mounted but when I tried to mount it, it gave me an error of not being able to find my hard drive?  Why does my hard drive need to be in the /etc/stab and/or the /etc/mtab?  
 
Thanks again for all your help.  
 
R

---

### Post by rcaca0 on 2010-02-22
Okay I cannot explain this but I now have Ubuntu 9.10 installed on my main computer.  On top of that I also have the video card working for both monitors.  

This afternoon I went to install Ubuntu just like I have in the past to see if I can see what I going on in the background.  I set the video to safe mode (F4) on the installation menu.  I then went to install the OS system.  This time for what ever reason it worked.  The only thing I can think that I did differently is that I had it in safe mode.  I am pretty sure I tried this before but maybe for some reason it slipped my mind.  

I am going to wait awhile then I am going to attempt to put my computer the way I want it to be which will mean that I will need to install the 64 bit version of Ubuntu.  I think I will wait until the next version comes out so I can play around with this one.  Besides I still have to get my media center working.  : )

I want to thank all of the people that helped me out with this.  It was a great help.  

Thanks again,
R

---

### Post by darkod on 2010-02-22
:p

---

