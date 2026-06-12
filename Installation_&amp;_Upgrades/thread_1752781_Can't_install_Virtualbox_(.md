---
title: "Can't install Virtualbox :("
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by rockinruler on 2011-05-08
Hi,

I just installed Ubuntu 10.04 on my laptop the other day, and I'm trying to install the latest release of Virtualbox. I downloaded the .deb file and when I try to install it, it gives me an error which says :

```

Error: Dependency is not satisfiable: libpython2.7 (>= 2.7)

```

I also installed libpython3.1 from Synaptic package manager, since it is >2.7, but still it doesn't work.

Can anyone help me please?
I have a very time consuming assignment that needs to be done by coming Saturday for which I need to use windows server 2k3. :(

---

### Post by Toz on 2011-05-08
You should probably use the virtualbox repositories to install. Follow the instructions at: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) starting from the "Debian based linux distrubtions" section. Basically:

1. add to /etc/apt/sources.list:```
deb http://download.virtualbox.org/virtualbox/debian lucid contrib non-free
```

2. install the public key:```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

3. prepare and install:```
sudo apt-get update
sudo apt-get install virtualbox-4.0
```

This will also give you the added benefit of automatic updating through apt (Update Manager).

---

### Post by rockinruler on 2011-05-08
Toz, thank you very much, it worked :-)
I'd downloaded the .deb file from Virtualbox's site itself.  I just checked I'd downloaded the version for Natty instead.

Also I'm having another issue. When I launch two different guests (XP and Server2k3) inside virtualbox, both of them freeze and then shutdown and virtualbox shows me 'Aborted'.
This never happened when I used to run the same OSes in Windows 7 before.

Is this thing common with Linux, or is there a fix to it?

---

### Post by An Sanct on 2011-05-08
That is not common and should be considered "faulty" operation. Did you leave enough ram for the host machine? Maybe something is shared (and shouldn't be) or misconfigured.

Aborted means a crash of the guest OS - a blue screen of death, if you will.

---

### Post by tgm4883 on 2011-05-08
> **An Sanct said:**
> That is not common and should be considered "faulty" operation. Did you leave enough ram for the host machine? Maybe something is shared (and shouldn't be) or misconfigured.

Aborted means a crash of the guest OS - a blue screen of death, if you will.

No, aborted means a crash of the guest machine, not the guest OS. IE, the host machine running virtualbox couldn't handle something correctly. A crash of the guest OS (ie a BSOD), would show a BSOD in the running VM.

---

### Post by rockinruler on 2011-05-08
I have 4GB of ram on my laptop, and I assigned 1gb to each of the two virtual OSes.

---

### Post by An Sanct on 2011-05-08
Are they sharing something? I haven't ran two ms virtual machines yet, but I would guess, that they cannot handle something like sharing a sound card or pass-through optical drive.

Thats just a guess tho, try to disable sound, maybe it will help.

PS... okay, I messed up with the Abort thing :) to me its the same, the machine crashes. :)

---

### Post by DrNemo on 2011-05-08
Hi,
I had virtualbox running fine under 10.04, then updated to 11.04, and it doesn't work. I found a link for the donwload, but how do I actually update my vbox for 11.04?

Thanks, merci
Nemo

---

### Post by Toz on 2011-05-08
> **rockinruler said:**
> 
Also I'm having another issue. When I launch two different guests (XP and Server2k3) inside virtualbox, both of them freeze and then shutdown and virtualbox shows me 'Aborted'.
This never happened when I used to run the same OSes in Windows 7 before.

Is this thing common with Linux, or is there a fix to it?

In your home directory, there should be a folder called "VirtualBox VMs". In that folder is a corresponding folder for each vm. With each vms folder is a Logs folder. And in this folder, is a log file. Post back the contents of one of the log files for one of the vms that crashed.

---

### Post by Toz on 2011-05-08
> **DrNemo said:**
> Hi,
I had virtualbox running fine under 10.04, then updated to 11.04, and it doesn't work. I found a link for the donwload, but how do I actually update my vbox for 11.04?

Thanks, merci
Nemo

I would suggest that you create a new thread for this issue so that we don't get confused. When you create this new thread, also include some further info, specifically:
- how did you install it under 10.04
- what exactly is not running? Is it the VirtualBox application or a VM
- run "VirtualBox" from the command line and post back the responses.

---

### Post by rockinruler on 2011-05-09
Hi Toz,
I couldn't find the directories you talked about.
However, I found two log files in this location
Home folder --> .VirtualBox-->Machine-->Servers-->VBox.log and VBox.log.1

Here are the contents of the first file :

```

00:00:00.362 VirtualBox 3.2.12 r68302 linux.x86 (Nov 30 2010 14:58:00) release log
00:00:00.362 Log opened 2011-05-08T13:22:59.546885000Z
00:00:00.362 OS Product: Linux
00:00:00.362 OS Release: 2.6.32-24-generic
00:00:00.362 OS Version: #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010
00:00:00.362 DMI Product Name: Aspire 5742
00:00:00.362 DMI Product Version: V1.05
00:00:00.363 Host RAM: 2320MB RAM, available: 1032MB
00:00:00.363 Executable: /usr/lib/virtualbox/VirtualBox
00:00:00.363 Process ID: 7269
00:00:00.363 Package type: LINUX_32BITS_UBUNTU_10_04
00:00:00.425 SUP: Opened VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xfe2d7020.
00:00:00.480 File system of '/media/Windows/Users/Amit/.VirtualBox/HardDisks/WinServer.vdi' is unknown
00:00:00.504 VBoxSharedClipboard mode: Bidirectional
00:00:00.505 ************************* CFGM dump *************************
00:00:00.505 [/] (level 0)
00:00:00.505   CSAMEnabled     <integer> = 0x0000000000000001 (1)
00:00:00.505   EnablePAE       <integer> = 0x0000000000000000 (0)
00:00:00.505   HwVirtExtForced <integer> = 0x0000000000000000 (0)
00:00:00.505   MemBalloonSize  <integer> = 0x0000000000000000 (0)
00:00:00.505   Name            <string>  = "Server" (cb=7)
00:00:00.505   NumCPUs         <integer> = 0x0000000000000001 (1)
00:00:00.505   PATMEnabled     <integer> = 0x0000000000000001 (1)
00:00:00.505   PageFusion      <integer> = 0x0000000000000000 (0)
00:00:00.505   RamHoleSize     <integer> = 0x0000000020000000 (536870912)
00:00:00.505   RamSize         <integer> = 0x0000000040000000 (1073741824)
00:00:00.505   RawR0Enabled    <integer> = 0x0000000000000001 (1)
00:00:00.505   RawR3Enabled    <integer> = 0x0000000000000001 (1)
00:00:00.505   SyntheticCpu    <integer> = 0x0000000000000000 (0)
00:00:00.505   TimerMillies    <integer> = 0x000000000000000a (10)
00:00:00.505   UUID            <bytes>   = "9b 23 9d 70 14 c1 7f 4a 93 b5 e6 a2 e5 25 2e 87" (cb=16)
00:00:00.505 
00:00:00.505 [/CPUM/] (level 1)
00:00:00.505 
00:00:00.505 [/Devices/] (level 1)
00:00:00.505 
00:00:00.505 [/Devices/8237A/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/8237A/0/] (level 3)
00:00:00.505   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/Devices/AudioSniffer/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/AudioSniffer/0/] (level 3)
00:00:00.505 
00:00:00.505 [/Devices/AudioSniffer/0/Config/] (level 4)
00:00:00.505 
00:00:00.505 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:00.505   Driver <string>  = "MainAudioSniffer" (cb=17)
00:00:00.505 
00:00:00.505 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
00:00:00.505   Object <integer> = 0x0000000008d16ae8 (147942120)
00:00:00.505 
00:00:00.505 [/Devices/VMMDev/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/VMMDev/0/] (level 3)
00:00:00.505   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:00.505   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.505   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/Devices/VMMDev/0/Config/] (level 4)
00:00:00.505 
00:00:00.505 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:00.505   Driver <string>  = "HGCM" (cb=5)
00:00:00.505 
00:00:00.505 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:00.505   Object <integer> = 0x0000000008edc2a0 (149799584)
00:00:00.505 
00:00:00.505 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:00.505   Driver <string>  = "MainStatus" (cb=11)
00:00:00.505 
00:00:00.505 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:00.505   First   <integer> = 0x0000000000000000 (0)
00:00:00.505   Last    <integer> = 0x0000000000000000 (0)
00:00:00.505   papLeds <integer> = 0x0000000008e5b20c (149271052)
00:00:00.505 
00:00:00.505 [/Devices/acpi/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/acpi/0/] (level 3)
00:00:00.505   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:00.505   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.505   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/Devices/acpi/0/Config/] (level 4)
00:00:00.505   CpuHotPlug  <integer> = 0x0000000000000000 (0)
00:00:00.505   FdcEnabled  <integer> = 0x0000000000000000 (0)
00:00:00.505   HpetEnabled <integer> = 0x0000000000000000 (0)
00:00:00.505   IOAPIC      <integer> = 0x0000000000000000 (0)
00:00:00.505   NumCPUs     <integer> = 0x0000000000000001 (1)
00:00:00.505   RamHoleSize <integer> = 0x0000000020000000 (536870912)
00:00:00.505   RamSize     <integer> = 0x0000000040000000 (1073741824)
00:00:00.505   ShowCpu     <integer> = 0x0000000000000000 (0)
00:00:00.505   ShowRtc     <integer> = 0x0000000000000000 (0)
00:00:00.505   SmcEnabled  <integer> = 0x0000000000000000 (0)
00:00:00.505 
00:00:00.505 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:00.505   Driver <string>  = "ACPIHost" (cb=9)
00:00:00.505 
00:00:00.505 [/Devices/acpi/0/LUN#0/Config/] (level 5)
00:00:00.505 
00:00:00.505 [/Devices/apic/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/apic/0/] (level 3)
00:00:00.505   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/Devices/apic/0/Config/] (level 4)
00:00:00.505   IOAPIC  <integer> = 0x0000000000000000 (0)
00:00:00.505   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/Devices/e1000/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/i8254/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/i8254/0/] (level 3)
00:00:00.505 
00:00:00.505 [/Devices/i8254/0/Config/] (level 4)
00:00:00.505 
00:00:00.505 [/Devices/i8259/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/i8259/0/] (level 3)
00:00:00.505   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/Devices/i8259/0/Config/] (level 4)
00:00:00.505 
00:00:00.505 [/Devices/ichac97/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/ichac97/0/] (level 3)
00:00:00.505   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
00:00:00.505   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.505   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/Devices/ichac97/0/Config/] (level 4)
00:00:00.505 
00:00:00.505 [/Devices/ichac97/0/LUN#0/] (level 4)
00:00:00.505   Driver <string>  = "AUDIO" (cb=6)
00:00:00.505 
00:00:00.505 [/Devices/ichac97/0/LUN#0/Config/] (level 5)
00:00:00.505   AudioDriver <string>  = "pulse" (cb=6)
00:00:00.505   StreamName  <string>  = "Server" (cb=7)
00:00:00.505 
00:00:00.505 [/Devices/mc146818/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/mc146818/0/] (level 3)
00:00:00.505 
00:00:00.505 [/Devices/mc146818/0/Config/] (level 4)
00:00:00.505   UseUTC <integer> = 0x0000000000000000 (0)
00:00:00.505 
00:00:00.505 [/Devices/parallel/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/pcarch/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/pcarch/0/] (level 3)
00:00:00.505   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/Devices/pcarch/0/Config/] (level 4)
00:00:00.505 
00:00:00.505 [/Devices/pcbios/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/pcbios/0/] (level 3)
00:00:00.505   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/Devices/pcbios/0/Config/] (level 4)
00:00:00.505   BootDevice0    <string>  = "FLOPPY" (cb=7)
00:00:00.505   BootDevice1    <string>  = "DVD" (cb=4)
00:00:00.505   BootDevice2    <string>  = "IDE" (cb=4)
00:00:00.505   BootDevice3    <string>  = "NONE" (cb=5)
00:00:00.505   FloppyDevice   <string>  = "i82078" (cb=7)
00:00:00.505   HardDiskDevice <string>  = "piix3ide" (cb=9)
00:00:00.505   IOAPIC         <integer> = 0x0000000000000000 (0)
00:00:00.505   NumCPUs        <integer> = 0x0000000000000001 (1)
00:00:00.505   PXEDebug       <integer> = 0x0000000000000000 (0)
00:00:00.505   RamHoleSize    <integer> = 0x0000000020000000 (536870912)
00:00:00.505   RamSize        <integer> = 0x0000000040000000 (1073741824)
00:00:00.505   UUID           <bytes>   = "9b 23 9d 70 14 c1 7f 4a 93 b5 e6 a2 e5 25 2e 87" (cb=16)
00:00:00.505 
00:00:00.505 [/Devices/pcbios/0/Config/NetBoot/] (level 5)
00:00:00.505 
00:00:00.505 [/Devices/pcbios/0/Config/NetBoot/0/] (level 6)
00:00:00.505   NIC           <integer> = 0x0000000000000000 (0)
00:00:00.505   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:00.505   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.505 
00:00:00.505 [/Devices/pci/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/pci/0/] (level 3)
00:00:00.505   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/Devices/pci/0/Config/] (level 4)
00:00:00.505   IOAPIC <integer> = 0x0000000000000000 (0)
00:00:00.505 
00:00:00.505 [/Devices/pckbd/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/pckbd/0/] (level 3)
00:00:00.505   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/Devices/pckbd/0/Config/] (level 4)
00:00:00.505 
00:00:00.505 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:00.505   Driver <string>  = "KeyboardQueue" (cb=14)
00:00:00.505 
00:00:00.505 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:00.505   Driver <string>  = "MainKeyboard" (cb=13)
00:00:00.505 
00:00:00.505 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:00.505   Object <integer> = 0x0000000008e5b4e0 (149271776)
00:00:00.505 
00:00:00.505 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:00.505   QueueSize <integer> = 0x0000000000000040 (64)
00:00:00.505 
00:00:00.505 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:00.505   Driver <string>  = "MouseQueue" (cb=11)
00:00:00.505 
00:00:00.505 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:00.505   Driver <string>  = "MainMouse" (cb=10)
00:00:00.505 
00:00:00.505 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:00.505   Object <integer> = 0x0000000008e5b588 (149271944)
00:00:00.505 
00:00:00.505 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:00.505   QueueSize <integer> = 0x0000000000000080 (128)
00:00:00.505 
00:00:00.505 [/Devices/pcnet/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/pcnet/0/] (level 3)
00:00:00.505   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:00.505   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.505   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/Devices/pcnet/0/Config/] (level 4)
00:00:00.505   Am79C973       <integer> = 0x0000000000000001 (1)
00:00:00.505   CableConnected <integer> = 0x0000000000000001 (1)
00:00:00.505   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:00.505   MAC            <bytes>   = "08 00 27 c1 a4 ea" (cb=6)
00:00:00.505 
00:00:00.505 [/Devices/pcnet/0/LUN#0/] (level 4)
00:00:00.505   Driver <string>  = "NAT" (cb=4)
00:00:00.505 
00:00:00.505 [/Devices/pcnet/0/LUN#0/Config/] (level 5)
00:00:00.505   AliasMode       <integer> = 0x0000000000000000 (0)
00:00:00.505   BootFile        <string>  = "Server.pxe" (cb=11)
00:00:00.505   DNSProxy        <integer> = 0x0000000000000000 (0)
00:00:00.505   Network         <string>  = "10.0.2.0/24" (cb=12)
00:00:00.505   PassDomain      <integer> = 0x0000000000000001 (1)
00:00:00.505   TFTPPrefix      <string>  = "/home/amit/.VirtualBox/TFTP" (cb=28)
00:00:00.505   UseHostResolver <integer> = 0x0000000000000000 (0)
00:00:00.505 
00:00:00.505 [/Devices/pcnet/0/LUN#999/] (level 4)
00:00:00.505   Driver <string>  = "MainStatus" (cb=11)
00:00:00.505 
00:00:00.505 [/Devices/pcnet/0/LUN#999/Config/] (level 5)
00:00:00.505   papLeds <integer> = 0x0000000008e5b1ec (149271020)
00:00:00.505 
00:00:00.505 [/Devices/piix3ide/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/piix3ide/0/] (level 3)
00:00:00.505   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:00.505   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:00.505   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/Devices/piix3ide/0/Config/] (level 4)
00:00:00.505   Type <string>  = "PIIX4" (cb=6)
00:00:00.505 
00:00:00.505 [/Devices/piix3ide/0/LUN#0/] (level 4)
00:00:00.505   Driver <string>  = "Block" (cb=6)
00:00:00.505 
00:00:00.505 [/Devices/piix3ide/0/LUN#0/AttachedDriver/] (level 5)
00:00:00.505   Driver <string>  = "VD" (cb=3)
00:00:00.505 
00:00:00.505 [/Devices/piix3ide/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:00.505   Format <string>  = "VDI" (cb=4)
00:00:00.505   Path   <string>  = "/media/Windows/Users/Amit/.VirtualBox/HardDisks/WinServer.vdi" (cb=62)
00:00:00.505 
00:00:00.505 [/Devices/piix3ide/0/LUN#0/Config/] (level 5)
00:00:00.505   Mountable <integer> = 0x0000000000000000 (0)
00:00:00.505   Type      <string>  = "HardDisk" (cb=9)
00:00:00.505 
00:00:00.505 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:00.505   Driver <string>  = "Block" (cb=6)
00:00:00.505 
00:00:00.505 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
00:00:00.505   Mountable <integer> = 0x0000000000000001 (1)
00:00:00.505   Type      <string>  = "DVD" (cb=4)
00:00:00.505 
00:00:00.505 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:00.505   Driver <string>  = "MainStatus" (cb=11)
00:00:00.505 
00:00:00.505 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:00.505   First   <integer> = 0x0000000000000000 (0)
00:00:00.505   Last    <integer> = 0x0000000000000003 (3)
00:00:00.505   papLeds <integer> = 0x0000000008e5b104 (149270788)
00:00:00.505 
00:00:00.505 [/Devices/serial/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/usb-ehci/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/usb-ehci/0/] (level 3)
00:00:00.505   PCIDeviceNo   <integer> = 0x000000000000000b (11)
00:00:00.505   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.505   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/Devices/usb-ehci/0/Config/] (level 4)
00:00:00.505 
00:00:00.505 [/Devices/usb-ehci/0/LUN#0/] (level 4)
00:00:00.505   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:00.505 
00:00:00.505 [/Devices/usb-ehci/0/LUN#0/Config/] (level 5)
00:00:00.505 
00:00:00.505 [/Devices/usb-ehci/0/LUN#999/] (level 4)
00:00:00.505   Driver <string>  = "MainStatus" (cb=11)
00:00:00.505 
00:00:00.505 [/Devices/usb-ehci/0/LUN#999/Config/] (level 5)
00:00:00.505   First   <integer> = 0x0000000000000000 (0)
00:00:00.505   Last    <integer> = 0x0000000000000000 (0)
00:00:00.505   papLeds <integer> = 0x0000000008e5b214 (149271060)
00:00:00.505 
00:00:00.505 [/Devices/usb-ohci/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/usb-ohci/0/] (level 3)
00:00:00.505   PCIDeviceNo   <integer> = 0x0000000000000006 (6)
00:00:00.505   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.505   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/Devices/usb-ohci/0/Config/] (level 4)
00:00:00.505 
00:00:00.505 [/Devices/usb-ohci/0/LUN#0/] (level 4)
00:00:00.505   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:00.505 
00:00:00.505 [/Devices/usb-ohci/0/LUN#0/Config/] (level 5)
00:00:00.505 
00:00:00.505 [/Devices/usb-ohci/0/LUN#999/] (level 4)
00:00:00.505   Driver <string>  = "MainStatus" (cb=11)
00:00:00.505 
00:00:00.505 [/Devices/usb-ohci/0/LUN#999/Config/] (level 5)
00:00:00.505   First   <integer> = 0x0000000000000000 (0)
00:00:00.505   Last    <integer> = 0x0000000000000000 (0)
00:00:00.505   papLeds <integer> = 0x0000000008e5b210 (149271056)
00:00:00.505 
00:00:00.505 [/Devices/vga/] (level 2)
00:00:00.505 
00:00:00.505 [/Devices/vga/0/] (level 3)
00:00:00.505   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:00.505   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.505   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/Devices/vga/0/Config/] (level 4)
00:00:00.505   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:00.505   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:00.505   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:00.505   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:00.505   LogoFile         <string>  = "" (cb=1)
00:00:00.505   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:00.505   MonitorCount     <integer> = 0x0000000000000001 (1)
00:00:00.505   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:00.505   VRamSize         <integer> = 0x0000000001000000 (16777216)
00:00:00.505 
00:00:00.505 [/Devices/vga/0/LUN#0/] (level 4)
00:00:00.505   Driver <string>  = "MainDisplay" (cb=12)
00:00:00.505 
00:00:00.505 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:00.505   Object <integer> = 0x0000000008e5b640 (149272128)
00:00:00.505 
00:00:00.505 [/Devices/virtio-net/] (level 2)
00:00:00.505 
00:00:00.505 [/HWVirtExt/] (level 1)
00:00:00.505   64bitEnabled       <integer> = 0x0000000000000000 (0)
00:00:00.505   EnableLargePages   <integer> = 0x0000000000000000 (0)
00:00:00.505   EnableNestedPaging <integer> = 0x0000000000000001 (1)
00:00:00.505   EnableVPID         <integer> = 0x0000000000000001 (1)
00:00:00.505   Enabled            <integer> = 0x0000000000000001 (1)
00:00:00.505   Exclusive          <integer> = 0x0000000000000001 (1)
00:00:00.505 
00:00:00.505 [/PDM/] (level 1)
00:00:00.505 
00:00:00.505 [/PDM/AsyncCompletion/] (level 2)
00:00:00.505 
00:00:00.505 [/PDM/AsyncCompletion/File/] (level 3)
00:00:00.505   CacheEnabled <integer> = 0x0000000000000001 (1)
00:00:00.505   CacheSize    <integer> = 0x0000000000500000 (5242880)
00:00:00.505 
00:00:00.505 [/PDM/Drivers/] (level 2)
00:00:00.505 
00:00:00.505 [/PDM/Drivers/VBoxC/] (level 3)
00:00:00.505   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cb=37)
00:00:00.505 
00:00:00.505 [/TM/] (level 1)
00:00:00.505   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:00.505 
00:00:00.505 [/USB/] (level 1)
00:00:00.505 
00:00:00.505 [/USB/USBProxy/] (level 2)
00:00:00.505 
00:00:00.505 [/USB/USBProxy/GlobalConfig/] (level 3)
00:00:00.505 
00:00:00.505 ********************* End of CFGM dump **********************
00:00:00.505 MM: cbHyperHeap=0x140000 (1310720)
00:00:00.505 Logical host processors: 4, processor active mask: 000000000000000f
00:00:00.505 ************************* CPUID dump ************************
00:00:00.505          RAW Standard CPUIDs
00:00:00.505      Function  eax      ebx      ecx      edx
00:00:00.505 Gst: 00000000  00000005 756e6547 6c65746e 49656e69
00:00:00.505 Hst:           0000000b 756e6547 6c65746e 49656e69
00:00:00.505 Gst: 00000001  00020655 00000800 00000209 078bf1bf
00:00:00.505 Hst:           00020655 00100800 009ae3bd bfebfbff
00:00:00.505 Gst: 00000002  55035a01 00f0b2dd 00000000 09ca212c
00:00:00.505 Hst:           55035a01 00f0b2dd 00000000 09ca212c
00:00:00.505 Gst: 00000003  00000000 00000000 00000000 00000000
00:00:00.505 Hst:           00000000 00000000 00000000 00000000
00:00:00.505 Gst: 00000004  00000000 00000000 00000000 00000000
00:00:00.505 Hst:           1c004121 01c0003f 0000003f 00000000
00:00:00.505 Gst: 00000005  00000040 00000040 00000000 00000000
00:00:00.505 Hst:           00000040 00000040 00000003 00001120
00:00:00.505 Name:                            GenuineIntel
00:00:00.505 Supports:                        0-5
00:00:00.505 Family:                          6      Extended: 0     Effective: 6
00:00:00.505 Model:                           5      Extended: 2     Effective: 37
00:00:00.505 Stepping:                        5
00:00:00.505 Type:                            0 (primary)
00:00:00.505 APIC ID:                         0x00
00:00:00.505 Logical CPUs:                    0
00:00:00.505 CLFLUSH Size:                    8
00:00:00.505 Brand ID:                        0x00
00:00:00.505 Mnemonic - Description                 = guest (host)
00:00:00.505 FPU - x87 FPU on Chip                  = 1 (1)
00:00:00.505 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:00.505 DE - Debugging extensions              = 1 (1)
00:00:00.505 PSE - Page Size Extension              = 1 (1)
00:00:00.505 TSC - Time Stamp Counter               = 1 (1)
00:00:00.505 MSR - Model Specific Registers         = 1 (1)
00:00:00.505 PAE - Physical Address Extension       = 0 (1)
00:00:00.505 MCE - Machine Check Exception          = 1 (1)
00:00:00.505 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:00.505 APIC - APIC On-Chip                    = 0 (1)
00:00:00.505 Reserved                               = 0 (0)
00:00:00.505 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:00.505 MTRR - Memory Type Range Registers     = 1 (1)
00:00:00.505 PGE - PTE Global Bit                   = 1 (1)
00:00:00.505 MCA - Machine Check Architecture       = 1 (1)
00:00:00.505 CMOV - Conditional Move Instructions   = 1 (1)
00:00:00.505 PAT - Page Attribute Table             = 1 (1)
00:00:00.505 PSE-36 - 36-bit Page Size Extention    = 1 (1)
00:00:00.505 PSN - Processor Serial Number          = 0 (0)
00:00:00.505 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:00.505 Reserved                               = 0 (0)
00:00:00.505 DS - Debug Store                       = 0 (1)
00:00:00.505 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
00:00:00.505 MMX - Intel MMX Technology             = 1 (1)
00:00:00.505 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:00.505 SSE - SSE Support                      = 1 (1)
00:00:00.505 SSE2 - SSE2 Support                    = 1 (1)
00:00:00.505 SS - Self Snoop                        = 0 (1)
00:00:00.505 HTT - Hyper-Threading Technolog        = 0 (1)
00:00:00.505 TM - Thermal Monitor                   = 0 (1)
00:00:00.505 30 - Reserved                          = 0 (0)
00:00:00.505 PBE - Pending Break Enable             = 0 (1)
00:00:00.505 Supports SSE3 or not                   = 1 (1)
00:00:00.505 Reserved                               = 0 (0)
00:00:00.505 DS Area 64-bit layout                  = 0 (1)
00:00:00.505 Supports MONITOR/MWAIT                 = 1 (1)
00:00:00.505 CPL-DS - CPL Qualified Debug Store     = 0 (1)
00:00:00.505 VMX - Virtual Machine Technology       = 0 (1)
00:00:00.505 SMX - Safer Mode Extensions            = 0 (0)
00:00:00.505 Enhanced SpeedStep Technology          = 0 (1)
00:00:00.505 Terminal Monitor 2                     = 0 (1)
00:00:00.505 Supports Supplemental SSE3 or not      = 1 (1)
00:00:00.505 L1 Context ID                          = 0 (0)
00:00:00.505 FMA                                    = 0 (0)
00:00:00.505 Reserved                               = 0 (0)
00:00:00.505 CMPXCHG16B                             = 0 (1)
00:00:00.505 xTPR Update Control                    = 0 (1)
00:00:00.505 Perf/Debug Capability MSR              = 0 (1)
00:00:00.505 Reserved                               = 0x0 (0x2)
00:00:00.505 Direct Cache Access                    = 0 (0)
00:00:00.505 Supports SSE4_1 or not                 = 0 (1)
00:00:00.505 Supports SSE4_2 or not                 = 0 (1)
00:00:00.505 Supports the x2APIC extensions         = 0 (0)
00:00:00.505 Supports MOVBE                         = 0 (0)
00:00:00.505 Supports POPCNT                        = 0 (1)
00:00:00.505 Reserved                               = 0x0 (0x0)
00:00:00.505 Supports XSAVE                         = 0 (0)
00:00:00.505 Supports OSXSAVE                       = 0 (0)
00:00:00.505 Reserved                               = 0x0 (0x0)
00:00:00.505 
00:00:00.505          RAW Extended CPUIDs
00:00:00.505      Function  eax      ebx      ecx      edx
00:00:00.505 Gst: 80000000  80000008 00000000 00000000 00000000
00:00:00.505 Hst:           80000008 00000000 00000000 00000000
00:00:00.505 Gst: 80000001  00000000 00000000 00000000 00000000
00:00:00.505 Hst:           00000000 00000000 00000001 28100000
00:00:00.505 Gst: 80000002  65746e49 2952286c 726f4320 4d542865
00:00:00.505 Hst:           65746e49 2952286c 726f4320 4d542865
00:00:00.505 Gst: 80000003  33692029 55504320 20202020 4d202020
00:00:00.505 Hst:           33692029 55504320 20202020 4d202020
00:00:00.505 Gst: 80000004  30373320 20402020 30342e32 007a4847
00:00:00.505 Hst:           30373320 20402020 30342e32 007a4847
00:00:00.505 Gst: 80000005  00000000 00000000 00000000 00000000
00:00:00.505 Hst:           00000000 00000000 00000000 00000000
00:00:00.505 Gst: 80000006  00000000 00000000 01006040 00000000
00:00:00.505 Hst:           00000000 00000000 01006040 00000000
00:00:00.505 Gst: 80000007  00000000 00000000 00000000 00000000
00:00:00.505 Hst:           00000000 00000000 00000000 00000100
00:00:00.505 Gst: 80000008  00003024 00000000 00000000 00000000
00:00:00.505 Hst:           00003024 00000000 00000000 00000000
00:00:00.505 Gst: 80000009  00000000 00000000 00000001 00000000*
00:00:00.505 Hst:           00000000 00000000 00000070 00000000
00:00:00.505 Ext Name:                        
00:00:00.505 Ext Supports:                    0x80000000-0x80000008
00:00:00.505 Family:                          0      Extended: 0     Effective: 0
00:00:00.505 Model:                           0      Extended: 0     Effective: 0
00:00:00.505 Stepping:                        0
00:00:00.505 Brand ID:                        0x000
00:00:00.505 Mnemonic - Description                 = guest (host)
00:00:00.505 FPU - x87 FPU on Chip                  = 0 (0)
00:00:00.505 VME - Virtual 8086 Mode Enhancements   = 0 (0)
00:00:00.505 DE - Debugging extensions              = 0 (0)
00:00:00.505 PSE - Page Size Extension              = 0 (0)
00:00:00.505 TSC - Time Stamp Counter               = 0 (0)
00:00:00.505 MSR - K86 Model Specific Registers     = 0 (0)
00:00:00.505 PAE - Physical Address Extension       = 0 (0)
00:00:00.505 MCE - Machine Check Exception          = 0 (0)
00:00:00.505 CX8 - CMPXCHG8B instruction            = 0 (0)
00:00:00.505 APIC - APIC On-Chip                    = 0 (0)
00:00:00.505 10 - Reserved                          = 0 (0)
00:00:00.505 SEP - SYSCALL and SYSRET               = 0 (0)
00:00:00.505 MTRR - Memory Type Range Registers     = 0 (0)
00:00:00.505 PGE - PTE Global Bit                   = 0 (0)
00:00:00.505 MCA - Machine Check Architecture       = 0 (0)
00:00:00.505 CMOV - Conditional Move Instructions   = 0 (0)
00:00:00.505 PAT - Page Attribute Table             = 0 (0)
00:00:00.505 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:00.505 18 - Reserved                          = 0 (0)
00:00:00.505 19 - Reserved                          = 0 (0)
00:00:00.505 NX - No-Execute Page Protection        = 0 (1)
00:00:00.505 DS - Debug Store                       = 0 (0)
00:00:00.505 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
00:00:00.505 MMX - Intel MMX Technology             = 0 (0)
00:00:00.505 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
00:00:00.505 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
00:00:00.505 26 - 1 GB large page support           = 0 (0)
00:00:00.505 27 - RDTSCP instruction                = 0 (1)
00:00:00.505 28 - Reserved                          = 0 (0)
00:00:00.505 29 - AMD Long Mode                     = 0 (1)
00:00:00.505 30 - AMD Extensions to 3DNow           = 0 (0)
00:00:00.505 31 - AMD 3DNow                         = 0 (0)
00:00:00.505 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
00:00:00.505 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
00:00:00.505 SVM - AMD VM Extensions                = 0 (0)
00:00:00.505 APIC registers starting at 0x400       = 0 (0)
00:00:00.505 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:00.505 Advanced bit manipulation              = 0 (0)
00:00:00.505 SSE4A instruction support              = 0 (0)
00:00:00.505 Misaligned SSE mode                    = 0 (0)
00:00:00.505 PREFETCH and PREFETCHW instruction     = 0 (0)
00:00:00.505 OS visible workaround                  = 0 (0)
00:00:00.505 Instruction based sampling             = 0 (0)
00:00:00.505 SSE5 support                           = 0 (0)
00:00:00.505 SKINIT, STGI, and DEV support          = 0 (0)
00:00:00.505 Watchdog timer support.                = 0 (0)
00:00:00.505 31:14 - Reserved                       = 0x0 (0x0)
00:00:00.505 Full Name:                       Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
00:00:00.505 TLB 2/4M Instr/Uni:              res0     0 entries
00:00:00.505 TLB 2/4M Data:                   res0     0 entries
00:00:00.505 TLB 4K Instr/Uni:                res0     0 entries
00:00:00.505 TLB 4K Data:                     res0     0 entries
00:00:00.505 L1 Instr Cache Line Size:        0 bytes
00:00:00.505 L1 Instr Cache Lines Per Tag:    0
00:00:00.505 L1 Instr Cache Associativity:    res0  
00:00:00.505 L1 Instr Cache Size:             0 KB
00:00:00.505 L1 Data Cache Line Size:         0 bytes
00:00:00.505 L1 Data Cache Lines Per Tag:     0
00:00:00.505 L1 Data Cache Associativity:     res0  
00:00:00.505 L1 Data Cache Size:              0 KB
00:00:00.505 L2 TLB 2/4M Instr/Uni:           off       0 entries
00:00:00.505 L2 TLB 2/4M Data:                off       0 entries
00:00:00.505 L2 TLB 4K Instr/Uni:             off       0 entries
00:00:00.505 L2 TLB 4K Data:                  off       0 entries
00:00:00.505 L2 Cache Line Size:              0 bytes
00:00:00.505 L2 Cache Lines Per Tag:          0
00:00:00.505 L2 Cache Associativity:          off   
00:00:00.505 L2 Cache Size:                   0 KB
00:00:00.505 APM Features:                   
00:00:00.505 Physical Address Width:          36 bits
00:00:00.505 Virtual Address Width:           48 bits
00:00:00.505 Guest Physical Address Width:    0 bits
00:00:00.505 Physical Core Count:             0
00:00:00.505 
00:00:00.505          RAW Centaur CPUIDs
00:00:00.505      Function  eax      ebx      ecx      edx
00:00:00.505 Gst: c0000000  00000000 00000000 00000001 00000000
00:00:00.505 Hst:           00000000 00000000 00000070 00000000
00:00:00.505 Gst: c0000001  00000000 00000000 00000001 00000000*
00:00:00.505 Hst:           00000000 00000000 00000070 00000000
00:00:00.505 Gst: c0000002  00000000 00000000 00000001 00000000*
00:00:00.505 Hst:           00000000 00000000 00000070 00000000
00:00:00.505 Gst: c0000003  00000000 00000000 00000001 00000000*
00:00:00.505 Hst:           00000000 00000000 00000070 00000000
00:00:00.505 Centaur Supports:                0xc0000000-0x00000000
00:00:00.505 
00:00:00.505 ******************** End of CPUID dump **********************
00:00:00.505 pgmR3PoolInit: cMaxPages=0x400 cMaxUsers=0x800 cMaxPhysExts=0x800 fCacheEnable=true 
00:00:00.505 REM: VBoxREM32
00:00:00.516 TM: GIP - u32Mode=1 (SyncTSC) u32UpdateHz=83
00:00:00.553 TM: cTSCTicksPerSecond=0x5ef89390 (1 593 349 008) fTSCVirtualized=true  fTSCUseRealTSC=false
00:00:00.553 TM: fMaybeUseOffsettedHostTSC=true  TSCTiedToExecution=false TSCNotTiedToHalt=false
00:00:00.553 CoreCode: R3=027df000 R0=fdb91000 RC=a05ad000 Phys=0000000005cd0000 cb=0x3000
00:00:00.553 AIOMgr: Default manager type is "Async"
00:00:00.553 AIOMgr: Default file backend is "NonBuffered"
00:00:00.553 AIOMgr: Cache successfully initialised. Cache size is 5242880 bytes
00:00:00.553 AIOMgr: Cache commit interval is 10000 ms
00:00:00.553 AIOMgr: Cache commit threshold is 2621440 bytes
00:00:00.553 AIOMgr: I/O bandwidth not limited
00:00:00.553 [SMP] BIOS with 1 CPUs
00:00:00.559 SUP: Opened VBoxDDR0.r0 (/usr/lib/virtualbox/VBoxDDR0.r0) at 0xfeaca020.
00:00:00.560 SUP: Opened VBoxDD2R0.r0 (/usr/lib/virtualbox/VBoxDD2R0.r0) at 0xfeaff020.
00:00:00.560 Activating Local APIC
00:00:00.560 CPUMSetGuestCpuIdFeature: Enabled APIC
00:00:00.560 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:00:00.561 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:00.563 Shared Folders service loaded.
00:00:00.571 DrvBlock: Flushes will be ignored
00:00:00.571 DrvBlock: Async flushes will be passed to the disk
00:00:00.572 VDInit finished
00:00:00.572 PIIX3 ATA: LUN#0: disk, PCHS=14563/16/63, total number of sectors 14680064
00:00:00.572 PIIX3 ATA: LUN#1: no unit
00:00:00.572 DrvBlock: Flushes will be ignored
00:00:00.572 DrvBlock: Async flushes will be passed to the disk
00:00:00.572 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 0, passthrough disabled
00:00:00.572 PIIX3 ATA: LUN#3: no unit
00:00:00.572 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:00.572 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:00.584 NAT: value of BindIP has been ignored
00:00:00.584 Audio: Trying driver 'pulse'.
00:00:00.607 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:00.608 Pulse: open PCM_IN rate=44100Hz channels=2 format=s16le
00:00:00.608 Pulse: Requested record buffer attributes: maxlength=26460 fragsize=17640
00:00:00.622 Pulse:  Obtained record buffer attributes: maxlength=26460 fragsize=8820
00:00:00.622 Pulse: open PCM_OUT rate=44100Hz channels=2 format=s16le
00:00:00.622 Pulse: Requested playback buffer attributes: maxlength=26460 tlength=17640 prebuf=-1 minreq=-1
00:00:00.654 Pulse:  Obtained playback buffer attributes: maxlength=26460 tlength=13408 prebuf=9884 minreq=3528
00:00:00.657 DevPcBios: ATA LUN#0 LCHS=913/255/63
00:00:00.657 PGMR3InitFinalize: 4 MB PSE mask 0000000fffffffff
00:00:00.683 HWACCM: Host CR4=000006D0
00:00:00.683 HWACCM: MSR_IA32_FEATURE_CONTROL      = 5
00:00:00.683 HWACCM: MSR_IA32_VMX_BASIC_INFO       = da04000000000f
00:00:00.683 HWACCM: VMCS id                       = f
00:00:00.683 HWACCM: VMCS size                     = 400
00:00:00.683 HWACCM: VMCS physical address limit   = None
00:00:00.683 HWACCM: VMCS memory type              = 6
00:00:00.683 HWACCM: Dual monitor treatment        = 1
00:00:00.683 HWACCM: MSR_IA32_VMX_PINBASED_CTLS    = 7f00000016
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_EXT_INT_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_NMI_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_VIRTUAL_NMI
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_PREEMPT_TIMER
00:00:00.683 HWACCM: MSR_IA32_VMX_PROCBASED_CTLS   = fff9fffe0401e172
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_IRQ_WINDOW_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_TSC_OFFSET
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_HLT_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_INVLPG_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MWAIT_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_RDPMC_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_RDTSC_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_LOAD_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_STORE_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR8_LOAD_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR8_STORE_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_TPR_SHADOW
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_NMI_WINDOW_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MOV_DR_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_UNCOND_IO_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_IO_BITMAPS
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MONITOR_TRAP_FLAG
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_MSR_BITMAPS
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MONITOR_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_PAUSE_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_USE_SECONDARY_EXEC_CTRL
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_LOAD_EXIT *must* be set
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_STORE_EXIT *must* be set
00:00:00.683 HWACCM: MSR_IA32_VMX_PROCBASED_CTLS2  = ff00000000
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_VIRT_APIC
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_EPT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_DESCRIPTOR_INSTR_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_RDTSCP_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_X2APIC
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_VPID
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_WBINVD_EXIT
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_REAL_MODE
00:00:00.683 HWACCM: MSR_IA32_VMX_ENTRY_CTLS       = ffff000011ff
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_DEBUG
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_IA64_MODE
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_ENTRY_SMM
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_DEACTIVATE_DUALMON
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_GUEST_PERF_MSR
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_GUEST_PAT_MSR
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_GUEST_EFER_MSR
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_DEBUG *must* be set
00:00:00.683 HWACCM: MSR_IA32_VMX_EXIT_CTLS        = 7fffff00036dff
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_DEBUG
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_HOST_AMD64
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_ACK_EXTERNAL_IRQ
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_GUEST_PAT_MSR
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_LOAD_HOST_PAT_MSR
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_GUEST_EFER_MSR
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_LOAD_HOST_EFER_MSR
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_VMX_PREEMPT_TIMER
00:00:00.683 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_DEBUG *must* be set
00:00:00.683 HWACCM: MSR_IA32_VMX_EPT_VPID_CAPS    = f0106114141
00:00:00.683 HWACCM:    MSR_IA32_VMX_EPT_CAPS_RWX_X_ONLY
00:00:00.683 HWACCM:    MSR_IA32_VMX_EPT_CAPS_GAW_48_BITS
00:00:00.683 HWACCM:    MSR_IA32_VMX_EPT_CAPS_EMT_UC
00:00:00.683 HWACCM:    MSR_IA32_VMX_EPT_CAPS_EMT_WB
00:00:00.683 HWACCM:    MSR_IA32_VMX_EPT_CAPS_SP_21_BITS
00:00:00.683 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVEPT
00:00:00.683 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVEPT_CAPS_CONTEXT
00:00:00.683 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVEPT_CAPS_ALL
00:00:00.683 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID
00:00:00.683 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID_CAPS_INDIV
00:00:00.683 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID_CAPS_CONTEXT
00:00:00.683 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID_CAPS_ALL
00:00:00.683 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID_CAPS_CONTEXT_GLOBAL
00:00:00.683 HWACCM: MSR_IA32_VMX_MISC             = 401e7
00:00:00.683 HWACCM:    MSR_IA32_VMX_MISC_PREEMPT_TSC_BIT 7 - erratum detected, using 0 instead
00:00:00.683 HWACCM:    MSR_IA32_VMX_MISC_ACTIVITY_STATES 7
00:00:00.683 HWACCM:    MSR_IA32_VMX_MISC_CR3_TARGET      4
00:00:00.683 HWACCM:    MSR_IA32_VMX_MISC_MAX_MSR         200
00:00:00.683 HWACCM:    MSR_IA32_VMX_MISC_MSEG_ID         0
00:00:00.683 HWACCM: MSR_IA32_VMX_CR0_FIXED0       = 80000021
00:00:00.683 HWACCM: MSR_IA32_VMX_CR0_FIXED1       = ffffffff
00:00:00.683 HWACCM: MSR_IA32_VMX_CR4_FIXED0       = 2000
00:00:00.683 HWACCM: MSR_IA32_VMX_CR4_FIXED1       = 227ff
00:00:00.683 HWACCM: MSR_IA32_VMX_VMCS_ENUM        = 2a
00:00:00.683 HWACCM: TPR shadow physaddr           = 000000000bdcd000
00:00:00.683 HWACCM: VCPU0: MSR bitmap physaddr      = 000000000ee6a000
00:00:00.683 HWACCM: VCPU0: VMCS physaddr            = 000000000bdd7000
00:00:00.683 CPUMSetGuestCpuIdFeature: Enabled sysenter/exit
00:00:00.683 HWACCM: 32-bit guests supported.
00:00:00.683 HWACCM: VMX enabled!
00:00:00.683 HWACCM: Enabled nested paging
00:00:00.683 HWACCM: EPT root page                 = 0000000005cad000
00:00:00.683 HWACCM: Unrestricted guest execution enabled!
00:00:00.683 HWACCM: enmFlushPage    1
00:00:00.683 HWACCM: enmFlushContext 1
00:00:00.683 HWACCM: TPR Patching disabled.
00:00:00.683 HWACCM: Using the VMX-preemption timer (cPreemptTimerShift=0)
00:00:00.683 HWACCM:    VT-x/AMD-V init method: GLOBAL
00:00:00.697 VM: Halt method global1 (5)
00:00:00.697 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:00.698 Changing the VM state from 'CREATED' to 'POWERING_ON'.
00:00:00.698 Changing the VM state from 'POWERING_ON' to 'RUNNING'.
00:00:00.700 Guest Log: BIOS: VirtualBox 3.2.12
00:00:00.700 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:00.747 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:00.747 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:00.747 Guest Log: BIOS: ata0-0: PCHS=14563/16/63 LCHS=913/255/63
00:00:00.747 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:00.747 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:00.747 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:00.763 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b3a97000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:00.775 2D video acceleration is disabled.
00:00:03.229 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:03.236 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:03.236 Guest Log: BIOS: Boot from Floppy 0 failed
00:00:03.237 Guest Log: BIOS: CDROM boot failure code : 0003
00:00:03.237 Guest Log: BIOS: Boot from CD-ROM failed
00:00:03.237 Guest Log: BIOS: Booting from Hard Disk...
00:00:03.484 Guest Log: BIOS: int13_harddisk: function 15, unmapped device for ELDL=81
00:00:06.761 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:00:06.829 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b3a97000 w=640 h=480 bpp=0 cbLine=0x140
00:00:08.631 PIIX3 ATA: LUN#0: IDLE IMMEDIATE, CmdIf=0xef (-1 usec ago)
00:00:08.631 PIIX3 ATA: LUN#0: aborting current command
00:00:09.651 Guest Additions information report: Interface = 0x00010004 osType = 0x00034000
00:00:09.666 Guest reported fixed hypervisor window at 0xf2800000 (size = 0xc00000, rc = VINF_SUCCESS)
00:00:10.303 VMMDev::SetVideoModeHint: got a video mode hint (652x479x0) at 0
00:00:13.674 EHCI: Hardware reset
00:00:13.675 EHCI: USB Operational
00:00:13.680 Guest Log: VBoxVideo: using HGSMI
00:00:13.710 PCNet#0: Init: ss32=1 GCRDRA=0x05c9f420[64] GCTDRA=0x05c9f020[64]
00:00:14.725 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:14.731 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:14.737 OHCI: Software reset
00:00:14.737 OHCI: USB Reset
00:00:14.737 OHCI: USB Operational
00:00:14.797 VMMDev::SetVideoModeHint: got a video mode hint (640x484x0) at 0
00:00:14.829 SharedFolders host service: connected, u32ClientID = 1
00:00:14.843 PCNet#0: Init: ss32=1 GCRDRA=0x05c9f420[64] GCTDRA=0x05c9f020[64]
00:00:14.845 PCNet#0: Init: ss32=1 GCRDRA=0x05c9f420[64] GCTDRA=0x05c9f020[64]
00:00:15.738 EHCI: USB Suspended
00:00:15.785 OHCI: USB Suspended
00:00:27.168 Guest Log: VBoxDisp[0]: VBVA enabled
00:00:27.168 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b3a97000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:27.191 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b3a97000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:27.468 Guest Log: VBoxService.exe: Started. Verbose level = 0
00:00:27.495 Guest Log: VBoxService.exe: Error: Exec: Sysprep executable not found! Search path=C:\sysprep\sysprep.exe
00:00:28.092 PCNet#0: Init: ss32=1 GCRDRA=0x05c9f420[64] GCTDRA=0x05c9f020[64]
00:02:02.278 rtldrNativeLoad: dlopen('libvdeplug.so.2', RTLD_NOW | RTLD_LOCAL) failed: libvdeplug.so.2: cannot open shared object file: No such file or directory
00:02:02.340 rtldrNativeLoad: dlopen('libvdeplug.so.2', RTLD_NOW | RTLD_LOCAL) failed: libvdeplug.so.2: cannot open shared object file: No such file or directory
00:02:02.369 rtldrNativeLoad: dlopen('libvdeplug.so.2', RTLD_NOW | RTLD_LOCAL) failed: libvdeplug.so.2: cannot open shared object file: No such file or directory
00:02:02.430 rtldrNativeLoad: dlopen('libvdeplug.so.2', RTLD_NOW | RTLD_LOCAL) failed: libvdeplug.so.2: cannot open shared object file: No such file or directory
00:02:07.849 Changing the VM state from 'RUNNING' to 'SUSPENDING'.
00:02:08.005 Changing the VM state from 'SUSPENDING' to 'SUSPENDED'.
00:02:08.020 NAT: zone(nm:mbuf, used:25)
00:02:08.020 NAT: zone(nm:mbuf_cluster, used:23)
00:02:08.020 NAT: zone(nm:mbuf_packet, used:0)
00:02:08.020 NAT: zone(nm:mbuf_jumbo_pagesize, used:0)
00:02:08.020 NAT: zone(nm:mbuf_jumbo_9k, used:0)
00:02:08.020 NAT: zone(nm:mbuf_jumbo_16k, used:0)
00:02:08.143 NAT: value of BindIP has been ignored
00:02:08.153 Changing the VM state from 'SUSPENDED' to 'RESUMING'.
00:02:08.153 Changing the VM state from 'RESUMING' to 'RUNNING'.
00:02:08.161 Changing the VM state from 'RUNNING' to 'SUSPENDING'.
00:02:08.164 Changing the VM state from 'SUSPENDING' to 'SUSPENDED'.
00:02:08.165 NAT: zone(nm:mbuf, used:0)
00:02:08.165 NAT: zone(nm:mbuf_cluster, used:0)
00:02:08.165 NAT: zone(nm:mbuf_packet, used:0)
00:02:08.165 NAT: zone(nm:mbuf_jumbo_pagesize, used:0)
00:02:08.166 NAT: zone(nm:mbuf_jumbo_9k, used:0)
00:02:08.166 NAT: zone(nm:mbuf_jumbo_16k, used:0)
00:02:08.180 IntNet#0: szNetwork={intnet} enmTrunkType=2 szTrunk={} fFlags=0x0 cbRecv=325632 cbSend=196608
00:02:08.190 Changing the VM state from 'SUSPENDED' to 'RESUMING'.
00:02:08.191 Changing the VM state from 'RESUMING' to 'RUNNING'.
00:02:13.218 PCNet#0: The link is back up again after the restore.
00:02:17.045 Guest Log: VBoxTray: 3.1.2 r56127 started.
00:02:17.072 Starting host clipboard service
00:02:17.072 Initializing X11 clipboard backend
00:02:17.396 Shared clipboard: starting shared clipboard thread
00:02:17.402 Guest Additions capability report: (0x5) seamless: yes, hostWindowMapping: no, graphics: yes
00:02:17.689 Guest Log: VBoxDisp[0]: VBVA enabled
00:02:17.690 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b3a97000 w=640 h=484 bpp=32 cbLine=0xA00
00:02:18.018 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b3a97000 w=640 h=484 bpp=32 cbLine=0xA00
00:02:27.650 Guest Log: Guest Additions update found! Please upgrade this machine to the latest Guest Additions.
00:03:25.816 Guest Log: VBOXNP: DLL loaded.

```

---

### Post by An Sanct on 2011-05-09
I see an error, try to troubleshoot this
> 00:00:27.468 Guest Log: VBoxService.exe: Started. Verbose level = 0
00:00:27.495 Guest Log: VBoxService.exe: Error: Exec: Sysprep executable not found! Search path=C:\sysprep\sysprep.exe
00:00:28.092 PCNet#0: Init: ss32=1 GCRDRA=0x05c9f420[64] GCTDRA=0x05c9f020[64]
00:02:02.278 rtldrNativeLoad: dlopen('libvdeplug.so.2', RTLD_NOW |  RTLD_LOCAL) failed: **libvdeplug.so.2: cannot open shared object file: No  such file or directory**
00:02:02.340 rtldrNativeLoad: dlopen('libvdeplug.so.2', RTLD_NOW |  RTLD_LOCAL) failed: **libvdeplug.so.2: cannot open shared object file: No  such file or directory**
00:02:02.369 rtldrNativeLoad: dlopen('libvdeplug.so.2', RTLD_NOW |  RTLD_LOCAL) failed: **libvdeplug.so.2: cannot open shared object file: No  such file or directory**...

The log also states, that you should update Guest Additions, since a new (maybe natty compatible) version is found.

---

### Post by Toz on 2011-05-09
Hmmmm, version 3.2 is installed. What does:```
dpkg -l | grep -i virtualbox
```return?

---

### Post by Toz on 2011-05-09
and also:```
apt-cache search virtualbox
```?

---

### Post by An Sanct on 2011-05-10
```
an@drak:~$ [B]dpkg -l | grep -i virtualbox
[/B] ii  virtualbox-4.0                        4.0.6-71344~Ubuntu~maverick                       Oracle VM VirtualBox
an@drak:~$ 
``````

an@drak:~$** apt-cache search virtualbox**
imvirt - detects several virtualizations
libimvirt-perl - Perl module for detecting several virtualizations
testdrive-cli - run the daily Ubuntu ISO in a virtual machine (command line)
testdrive-common - run the daily Ubuntu ISO in a virtual machine (common files)
testdrive-gtk - run the daily Ubuntu ISO in a virtual machine (GTK Front-end)
virtualbox-ose - x86 virtualization solution - base binaries
virtualbox-ose-dbg - x86 virtualization solution - debugging symbols
virtualbox-ose-dkms - x86 virtualization solution - kernel module sources for dkms
virtualbox-ose-fuse - x86 virtualization solution - virtual filesystem
virtualbox-ose-guest-dkms - x86 virtualization solution - guest addition module source for dkms
virtualbox-ose-guest-utils - x86 virtualization solution - non-X11 guest utilities
virtualbox-ose-guest-x11 - x86 virtualization solution - X11 guest utilities
virtualbox-ose-qt - x86 virtualization solution - Qt based user interface
xmount - tool to crossmount between multiple input and output harddisk images
virtualbox-guest-additions - guest additions iso image for VirtualBox
libvirt-bin - the programs for the libvirt library
libvirt-dev - development files for the libvirt library
libvirt-doc - documentation for the libvirt library
libvirt0 - library for interfacing with different virtualization systems
libvirt0-dbg - library for interfacing with different virtualization systems
python-libvirt - libvirt Python bindings
virtualbox-4.0 - Oracle VM VirtualBox

```Virtualbox is long beyond 3.2 and for a good reason too.

If you still use 3.2, do this: export every machine ("Export Appliance") 
In the menu 'File' -> 'Export Appliance' or Ctrl + E

I personally would use "Write legacy OVF 0.9", this is used for backward compatibility. I also don't mind the little extra space that it requires, since it is backwards compatible.

When all machines are exported, uninstall VirtualBox 100%. Download and install the OSE edition from [here]("http://www.virtualbox.org/wiki/Linux_Downloads"), also download the USB plugin from [here]("http://download.virtualbox.org/virtualbox/4.0.6/Oracle_VM_VirtualBox_Extension_Pack-4.0.6-71344.vbox-extpack") and install into VB through 'File' -> 'Preferences' -> 'Extensions' (this is OSE USB support)

Its 4.0 now, since OSE supports USB through plugins now, no need anymore for the binary build for that.

EDIT2: Don't mind the 'edit' note on the bottom! .... Software Center has VB version 3.2, download from VB site in the links above.

... first edit left for historical reasons :)

Edit: PS. Note, that the VirtualBox from "Ubuntu Software Center" could be the same (or even a better choice then manual download) .... I don't remember how I installed it, anyhow, VB checks for updates automatically, maybe from the SC, Ubuntu checks also...

---

### Post by rockinruler on 2011-05-12
> dpkg -l | grep -i virtualboxGives this:
> 
ii  virtualbox-3.2                       3.2.12-68302~Ubuntu~lucid                       Oracle VM VirtualBox
And

> apt-cache search virtualboxgives this:
> 
amit@amit-laptop:~$ apt-cache search virtualbox
imvirt - detects several virtualizations
vboxgtk - simple GTK+ frontend for VirtualBox
virtualbox-ose - x86 virtualization solution - base binaries
virtualbox-ose-dbg - x86 virtualization solution - debugging symbols
virtualbox-ose-dkms - x86 virtualization solution - kernel module sources for dkms
virtualbox-ose-fuse - x86 virtualization solution - virtual filesystem
virtualbox-ose-guest-dkms - x86 virtualization solution - guest addition module source for dkms
virtualbox-ose-guest-source - Transitional package for virtualbox-ose-guest-dkms
virtualbox-ose-guest-utils - x86 virtualization solution - non-X11 guest utilities
virtualbox-ose-guest-x11 - x86 virtualization solution - X11 guest utilities
virtualbox-ose-qt - x86 virtualization solution - Qt based user interface
virtualbox-ose-source - Transitional package for virtualbox-ose-dkms
xmount - tool to crossmount between multiple input and output harddisk images
virtualbox-guest-additions - guest additions iso image for VirtualBox
libvirt-bin - the programs for the libvirt library
libvirt-dev - development files for the libvirt library
libvirt-doc - documentation for the libvirt library
libvirt0 - library for interfacing with different virtualization systems
libvirt0-dbg - library for interfacing with different virtualization systems
python-libvirt - libvirt Python bindings
testdrive - run the daily Ubuntu ISO in a virtual machine
virtualbox-3.1 - Sun VirtualBox
virtualbox-3.2 - Oracle VM VirtualBox



I've been trying to see if there's anything that the two Virtual systems share since a couple of days now, and I can't find anything. Also, the systems run just fine individually, the problem only occurs when both are run simultaneously.


@An Sanct

Do you want me to export appliance back from the Windows system from where the virtual machines were installed?
I'm sorry if this was really important, but I forgot to mention that the installations of both the virtual OSes were performed on windows 7. Then I just used the .vdi files to load the same OSes up in my Ubuntu VirtualBox.

---

### Post by An Sanct on 2011-05-12
> **rockinruler said:**
> Do you want me to export appliance back from the Windows system from where the virtual machines were installed?
I'm sorry if this was really important, but I forgot to mention that the installations of both the virtual OSes were performed on windows 7. Then I just used the .vdi files to load the same OSes up in my Ubuntu VirtualBox.

The "Export Appliance" part can be done under any running installation of Virtualbox, it is merely a *backup* of your Virtual Machine(s).

Its also a way to cleanly and safely upgrade/reinstall.

Run VB -> Create backups (exports appliance(s)) -> 
uninstall VB 3.2 -> install VB 4.0 -> Import appliance(s)

The files created via "Export Appliance" will be the same, if they are exported from within Win7 or Ubuntu (or any other OS), since they are portable.

---

### Post by Toz on 2011-05-12
Virtualbox 4 isn't showing up as available for you. What does your /etc/apt/sources.list file contain?

---

### Post by An Sanct on 2011-05-12
He's using 10.04, I have 10.10 and still have only Virtualbox 3.2.8-dfsg-2ubuntu1 available in Software Center.

---

### Post by Toz on 2011-05-12
I'm also using 10.10 (on my main machine) and I have virtualbox-4.0 available to me (and installed). I used the instructions from the Virtualbox download page that I transcribed in post #2 for lucid installs.

What does your /etc/apt/sources.list look like?
```
$ cat /etc/apt/sources.list
# deb cdrom:[Xubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101008.1)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick universe
deb http://ca.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

[COLOR="Red"]#virtualbox
deb http://download.virtualbox.org/virtualbox/debian maverick contrib non-free[/COLOR]

```
```
$ apt-cache policy virtualbox-4.0
virtualbox-4.0:
  Installed: 4.0.6-71344~Ubuntu~maverick
  Candidate: 4.0.6-71344~Ubuntu~maverick
  Version table:
 *** 4.0.6-71344~Ubuntu~maverick 0
        500 http://download.virtualbox.org/virtualbox/debian/ maverick/contrib i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by rockinruler on 2011-05-12
> #deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free


This is what it contains

---

### Post by Toz on 2011-05-12
Change the last line to:```
deb http://download.virtualbox.org/virtualbox/debian lucid contrib non-free
```then:```
sudo apt-get update
```then:```
apt-cache search virtualbox
```

---

### Post by rockinruler on 2011-05-15
I tried that, but I'm still facing the same prob :(
I think I'm gonna give up now.

---

### Post by An Sanct on 2011-05-15
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

download and install ... don't give up!

---

### Post by Toz on 2011-05-15
> **rockinruler said:**
> I tried that, but I'm still facing the same prob :(
I think I'm gonna give up now.

Post back the contents of /etc/apt/sources.list and the results of:```
apt-cache search virtualbox
```

---

### Post by rockinruler on 2011-05-17
Thanks a ton for all the help. :) I though I was probably bothering you guys wayy too much :-s
An Sanct, I'm downloading that right now. Will let you know as soon as it's done.

Toz, there:

> #deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid contrib non-free

And from the terminal:

> amit@amit-laptop:~$ apt-cache search virtualbox
imvirt - detects several virtualizations
vboxgtk - simple GTK+ frontend for VirtualBox
virtualbox-ose - x86 virtualization solution - base binaries
virtualbox-ose-dbg - x86 virtualization solution - debugging symbols
virtualbox-ose-dkms - x86 virtualization solution - kernel module sources for dkms
virtualbox-ose-fuse - x86 virtualization solution - virtual filesystem
virtualbox-ose-guest-dkms - x86 virtualization solution - guest addition module source for dkms
virtualbox-ose-guest-source - Transitional package for virtualbox-ose-guest-dkms
virtualbox-ose-guest-utils - x86 virtualization solution - non-X11 guest utilities
virtualbox-ose-guest-x11 - x86 virtualization solution - X11 guest utilities
virtualbox-ose-qt - x86 virtualization solution - Qt based user interface
virtualbox-ose-source - Transitional package for virtualbox-ose-dkms
xmount - tool to crossmount between multiple input and output harddisk images
virtualbox-guest-additions - guest additions iso image for VirtualBox
libvirt-bin - the programs for the libvirt library
libvirt-dev - development files for the libvirt library
libvirt-doc - documentation for the libvirt library
libvirt0 - library for interfacing with different virtualization systems
libvirt0-dbg - library for interfacing with different virtualization systems
python-libvirt - libvirt Python bindings
testdrive - run the daily Ubuntu ISO in a virtual machine
virtualbox-4.0 - Oracle VM VirtualBox
virtualbox-3.1 - Sun VirtualBox
virtualbox-3.2 - Oracle VM VirtualBox


---

### Post by rockinruler on 2011-05-17
Toz, it shows me
> Error: Conflicts with the installed package 'virtualbox-3.2'

Now, I tried to look up on how to uninstall 3.2 on Google, but I can't get anything,
That's what I'll have to do right?

---

### Post by An Sanct on 2011-05-17
Find "virtualbox" in your Software Center, there is an option to remove it (a "remove" button) next to the name.

edit: Before you remove it, make sure that you backed-up your VMs! (the export appliance thing I was talking about...)

---

### Post by rockinruler on 2011-05-17
That worked :D Both the Virtual OSes work fine now, simultaneously.
Thank you very much An Sanct and Toz for taking the trouble of keeping up on this thread :) Your help is highly appreciated :D

Btw, so the problem was not having the right version, right?

---

### Post by An Sanct on 2011-05-17
It seems so, but I cannot be sure.

We are happy to help, that's what this forum is all about :)

Please mark the thread as solved. ;)

---

