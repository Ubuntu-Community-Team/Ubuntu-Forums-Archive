---
title: "Ubuntu 16.10 unable to find hard drives on new machine"
date: 2016-12-06
forum: Installation &amp; Upgrades
---

### Post by ravalox on 2016-12-06
Hey, I'm an owner of one of the new Alienware 17 R4's; got a pretty good deal on it- anyway I'm attempting to dual boot Ubuntu with it and it can't seem to find any of the hard drives on the machine.  I know this is possible on linux; there are people on the forums who have working arch linux installations who say all the hardware has drivers in linux.  Now I know Arch isn't Ubuntu but I thought I'd ask around for strategies to get these drives detected.  It currently can only detect the live USB stick I'm using.

```
I've taken an LSPCI:
00:00.0 Host bridge: Intel Corporation Skylake Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Skylake PCIe Controller (x16) (rev 07)
00:01.2 PCI bridge: Intel Corporation Skylake PCIe Controller (x4) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 RAID bus controller: Intel Corporation SATA Controller [RAID mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #1 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #5 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #6 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
01:00.0 VGA compatible controller: NVIDIA Corporation GP104M [GeForce GTX 1070] (rev a1)
3c:00.0 Ethernet controller: Qualcomm Atheros Killer E2400 Gigabit Ethernet Controller (rev 10)
3d:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)

and an lshw
ubuntu@ubuntu:~$ sudo lshw -class disk -class storage
  *-usb:0                  
       description: Mass storage device
       product: Flash Disk
       vendor: USB
       physical id: 1
       bus info: usb@1:1
       logical name: scsi4
       version: 11.00
       serial: FBF1101121409068
       capabilities: usb-2.00 scsi emulated scsi-host
       configuration: driver=usb-storage maxpower=500mA speed=480Mbit/s
     *-disk
          description: SCSI Disk
          product: Flash Disk
          vendor: USB
          physical id: 0.0.0
          bus info: scsi@4:0.0.0
          logical name: /dev/sda
          logical name: /cdrom
          version: 1100
          size: 1912MiB (2004MB)
          capabilities: removable
          configuration: logicalsectorsize=512 mount.fstype=iso9660 mount.options=ro,noatime sectorsize=512 state=mounted
        *-medium
             physical id: 0
             logical name: /dev/sda
             logical name: /cdrom
             size: 1912MiB (2004MB)
             capabilities: partitioned partitioned:dos
             configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=05e037df state=mounted
  *-storage
       description: RAID bus controller
       product: SATA Controller [RAID mode]
       vendor: Intel Corporation
       physical id: 17
       bus info: pci@0000:00:17.0
       version: 31
       width: 32 bits
       clock: 66MHz
       capabilities: storage msix pm bus_master cap_list
       configuration: driver=ahci latency=0
       resources: irq:16 memory:dd1a0000-dd1a7fff memory:dd1b9000-dd1b90ff ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:dd100000-dd17ffff
```

---

### Post by gordintoronto on 2016-12-07
How about in the file manager?  Hard drive partitions might appear as "518 GB Volume" or something along those lines.

When you boot Windows, are the hard drives identified as "dynamic disks"? Linux doesn't know how to deal with dynamic disks.

Your message suggests that you have multiple drives. What is the drive setup, with what partitions?

---

### Post by oldfred on 2016-12-08
Please use Code Tags with longer text or terminal output. Easy to add code tags with # icon in Forum's advanced editor.

You seem to be running RAID. The desktop installer does not yet fully support RAID installs. 
With 12.04 they had an alternative installer for RAID & LVM. They said eventually they would add it to the desktop installer and have added LVM, but not RAID.
You may be able to use server installer, and then install desktop of choice which would give you the same end install.

 Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[URL="http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr"]http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr
[/URL]
 Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers) 

[URL="http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr"]
[/URL]

---

### Post by ravalox on 2016-12-09
Wow, thanks this is good information; I have tried several different installers and none of them seem to be able to solve the problem completely; I tried ubuntu server but it didn't seem to be able to detect the drives. I tried Mint and strangely it could detect one of the drives but not both- the forum users indicated arch linux works so I'm trying to create a usb installer but it's kernel panicking when I start it so I'll have to look at how I'm booting that.  The network card works in ubuntu live, not in mint strangely.  This may be a situation where I have to accept windows for the time being.

---

