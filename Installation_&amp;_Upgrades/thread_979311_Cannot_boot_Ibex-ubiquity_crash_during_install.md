---
title: "Cannot boot Ibex-ubiquity crash during install"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by fewjr on 2008-11-11
Hello All,
     I still cannot find any information to help me get Ibex to boot up. I get through install all the way up to the end where I get a Ubiquity crash error. This is the Launchpad bug report link:[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/292350](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/292350). When I reboot I get an grub error. I cannot mount the partition from Ubuntu Hardy. The partition editor shows the partition populated with what was installed, but there is no way to boot it. Can anyone help me? I am trying to find any info in the forum myself but haven't found anything yet.

Thanks
fewjr

---

### Post by Herman on 2008-11-12
:) Hello fewjr,
Can you provide a little more information?

You said you're getting a GRUB Error, exactly what GRUB Error is that?

I have a list of GRUB Errors in 'Trouble Shooting Section:   [Common Booting Errors and Some Possible Cures]("http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible")  ' which is slightly more verbose than the Gnu Grub Manual. We might be able to look up your error message there for some ideas.

Usually, the output from 'sudo fdisk -lu' or a screencap from Gnome Partition Editor will help a lot.
```
sudo fdisk -lu
```Otherwise, if it's a hardware problem, maybe the output from one or two of the commands here will help someone to help you, [Hardware Detection and Testing]("http://users.bigpond.net.au/hermanzone/p8.html#Hardware_Detection_and_Testing"). 
For example, maybe '[FONT=Bitstream Vera Sans Mono]sudo dmidecode[/FONT][FONT=Bitstream Vera Sans Mono]' [/FONT]will provide some clues. ```
 [FONT=Bitstream Vera Sans Mono]sudo dmidecode[/FONT][FONT=Bitstream Vera Sans Mono]
 [/FONT]
```[FONT=Bitstream Vera Sans Mono]
[/FONT]
Regards, Herman :)

---

### Post by fewjr on 2008-11-14
Hi Herman,
I tried to boot from SGD, but it doesn't see Ibex. Here are the command outputs sda10 is Ibex:

```
goblin@goblin-lanbox:~$ sudo fdisk -lu
[sudo] password for goblin: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e557f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   124310969    62155453+   7  HPFS/NTFS
/dev/sda2       124310970   976768064   426228547+   5  Extended
/dev/sda5       124311033   334023479   104856223+  83  Linux
/dev/sda6       334023543   438879734    52428096   83  Linux
/dev/sda7       438879798   439088579      104391   83  Linux
/dev/sda8       439088643   443281544     2096451   82  Linux swap / Solaris
/dev/sda9       443281608   548137799    52428096   83  Linux
/dev/sda10      548137863   976768064   214315101   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000487cb

   Device Boot      Start         End      Blocks   Id  System


```



```
goblin@goblin-lanbox:~$ sudo dmidecode
# dmidecode 2.9
SMBIOS 2.4 present.
34 structures occupying 1936 bytes.
Table at 0x000F0100.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Award Software International, Inc.
	Version: F1
	Release Date: 04/22/2008
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
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
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Gigabyte Technology Co., Ltd.
	Product Name: M78SM-S2H
	Version:  
	Serial Number:  
	UUID: 30303146-4430-3542-3938-4434FFFFFFFF
	Wake-up Type: Power Switch
	SKU Number:  
	Family:  

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: nVIDIA
	Product Name: M78SM-S2H
	Version:  
	Serial Number: OEM

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
	Manufacturer: Gigabyte Technology Co., Ltd.
	Type: Desktop
	Lock: Not Present
	Version:  
	Serial Number:  
	Asset Tag:  
	Boot-up State: Unknown
	Power Supply State: Unknown
	Thermal State: Unknown
	Security Status: Unknown
	OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: Socket M2
	Type: Central Processor
	Family: Athlon
	Manufacturer: AMD
	ID: B2 0F 06 00 FF FB 8B 17
	Signature: Family 15, Model 107, Stepping 2
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		HTT (Hyper-threading technology)
	Version: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
	Voltage: 1.1 V
	External Clock: 200 MHz
	Max Speed: 500 MHz
	Current Speed: 2600 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0008
	L2 Cache Handle: 0x0009
	L3 Cache Handle: Not Provided
	Serial Number:  
	Asset Tag:  
	Part Number:  

Handle 0x0005, DMI type 5, 20 bytes
Memory Controller Information
	Error Detecting Method: 64-bit ECC
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 32 MB
	Maximum Total Memory Size: 64 MB
	Supported Speeds:
		70 ns
		60 ns
	Supported Memory Types:
		Standard
		EDO
	Memory Module Voltage: 5.0 V
	Associated Memory Slots: 2
		0x0006
		0x0007
	Enabled Error Correcting Capabilities:
		None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A0
	Bank Connections: 0 1
	Current Speed: 32 ns
	Type: Other Unknown EDO
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A1
	Bank Connections: 2 3
	Current Speed: 32 ns
	Type: Other Unknown EDO
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0008, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Internal Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 128 KB
	Maximum Size: 128 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x0009, DMI type 7, 19 bytes
Cache Information
	Socket Designation: External Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 512 KB
	Maximum Size: 512 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: PRIMARY IDE
	Internal Connector Type: On Board IDE
	External Reference Designator:  
	External Connector Type: None
	Port Type: Other

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SECONDARY IDE
	Internal Connector Type: On Board IDE
	External Reference Designator:  
	External Connector Type: None
	Port Type: Other

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: FDD
	Internal Connector Type: On Board Floppy
	External Reference Designator:  
	External Connector Type: None
	Port Type: 8251 FIFO Compatible

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: COM1
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator:  
	External Connector Type: DB-9 male
	Port Type: Serial Port 16450 Compatible

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: COM2
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator:  
	External Connector Type: DB-9 male
	Port Type: Serial Port 16450 Compatible

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: LPT1
	Internal Connector Type: DB-25 female
	External Reference Designator:  
	External Connector Type: DB-25 female
	Port Type: Parallel Port ECP/EPP

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Keyboard
	Internal Connector Type: Other
	External Reference Designator:  
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: PS/2 Mouse
	Internal Connector Type: PS/2
	External Reference Designator: Detected
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB
	Internal Connector Type: None
	External Reference Designator:  
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0013, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 6
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0014, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 7
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0015, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 3
		n|US|iso8859-1
		n|US|iso8859-1
		r|CA|iso8859-1
	Currently Installed Language: n|US|iso8859-1

Handle 0x0016, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 1 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x0017, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0016
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: A0
	Bank Locator: Bank0/1
	Type: Unknown
	Type Detail: None
	Speed: 800 MHz (1.2 ns)
	Manufacturer: None
	Serial Number: None
	Asset Tag: None
	Part Number: None

Handle 0x0018, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0016
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: A1
	Bank Locator: Bank2/3
	Type: Unknown
	Type Detail: None
	Speed: 800 MHz (1.2 ns)
	Manufacturer: None
	Serial Number: None
	Asset Tag: None
	Part Number: None

Handle 0x0019, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Physical Array Handle: 0x0016
	Partition Width: 32

Handle 0x001A, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0017
	Memory Array Mapped Address Handle: 0x0019
	Partition Row Position: 1

Handle 0x001B, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00080000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0018
	Memory Array Mapped Address Handle: 0x0019
	Partition Row Position: 1

Handle 0x001C, DMI type 32, 11 bytes
System Boot Information
	Status: No errors detected

Handle 0x001D, DMI type 188, 244 bytes
OEM-specific Type
	Header and Data:
		BC F4 1D 00 00 00 00 E8 00 00 00 00 00 00 00 18
		01 00 00 00 01 06 76 00 00 00 00 00 03 00 00 00
		00 00 17 01 00 00 00 00 01 00 00 00 00 00 00 00
		02 00 00 00 00 00 00 00 03 00 00 00 00 00 00 00
		04 00 00 00 00 00 00 00 05 00 00 00 00 00 00 00
		06 00 00 00 00 00 00 00 07 00 00 00 01 18 00 E8
		40 00 10 0A 00 00 00 00 00 00 0F 00 EF 02 00 5D
		01 00 00 00 01 02 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		E0 3D F8 00 00 00 00 00 00 00 00 00 00 00 00 00
		46 00 00 00 00 00 00 00 05 00 00 00 00 00 00 00
		24 CA 7E 5D 20 13 22 00 10 0C 01 00 6B 00 10 77
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00

Handle 0x001E, DMI type 190, 212 bytes
OEM-specific Type
	Header and Data:
		BE D4 1E 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00

Handle 0x001F, DMI type 192, 244 bytes
OEM-specific Type
	Header and Data:
		C0 F4 1F 00 16 15 16 16 15 15 14 15 16 00 00 00
		15 15 15 15 16 14 16 16 15 00 00 00 2B 00 00 00
		15 15 15 15 15 15 15 15 15 15 15 16 16 15 15 14
		15 15 2E 00 00 00 22 32 11 20 20 25 20 10 22 32
		11 20 20 25 20 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00

Handle 0x0020, DMI type 194, 244 bytes
OEM-specific Type
	Header and Data:
		C2 F4 20 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00

Handle 0x0021, DMI type 127, 4 bytes
End Of Table

goblin@goblin-lanbox:~$ 


```

What is that error checking method under memory controller information? I can't mount the partition from Ubuntu Hardy either, so I can't look at Ibex's menu.lst. It was an Grub error 15 by the way. I haven't figured out how to save the screenshot from gpartedlivecd yet. It says it saves it to root but....well, I can't find it. I'm still checking.

---

### Post by fewjr on 2008-11-14
Okay, so it isn't hard...I know...lol. Heres the screenshot url:

[http://i260.photobucket.com/albums/ii20/fewjr/gparted.jpg](http://i260.photobucket.com/albums/ii20/fewjr/gparted.jpg)

---

### Post by Herman on 2008-11-14
I think we should try upgrading your stage2 GRUB file in your dedicated GRUB partition with Intrepid Ibex's new version.

If you agree and that is what you want to do, then probably the easiest and fastest way to do that would be to run the grub-install command from your Intrepid Ibex live CD.
Mount your GRUB partition first, and check to make sure you have a directory named /boot in it and another one inside that named /grub, then run the following command,
```
sudo grub-install --root-directory=/media/GRUB /dev/sda 
```
You probably won't notice whether or not anything happened at all.

Now when you boot to your GRUB menu and press your 'c' key for [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), you should be able to run the new uuid command.
(Try it out and see if that works).

Then press your 'Esc' to go back to your GRUB menu and try booting Intrepid to see if it will boot normally now or not. 

Hopefully now it will work normally.
If it doesn't then try going back into [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and booting from there manually. Try this, **[[B]Direct (kernel) Boot**]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.").[/B]
```
root (hd0,9)
kernel /vmlinuz root=/dev/sda10
initrd  /initrd.img
boot
```That should make it boot for sure! :)

---

### Post by fewjr on 2008-11-15
Okay Herman, I will try it. I saw in another post that someone had the same problem and solved it by using the Alternate cd. He never got it resolved with the livecd. I will work on it tomorrow. I got the flu shot on my last night at work and now I feel like crap!. I'm going to bed now..:icon_frown:

---

### Post by Herman on 2008-11-15
> I get through install all the way up to the end where I get a Ubiquity crash error. This is the Launchpad bug report link:[https://bugs.launchpad.net/ubuntu/+s...ty/+bug/292350]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/292350"). When I reboot I get an grub error. I installed Intrepid Ibex dual boot with Hardy Heron in one of my computers and mine had a Ubiquity crash too, it sounds like the exact same issue as you described.
I had chosen the Reiser File System, (but I doubt that would have anything to do with the problem), and I had clicked the 'advanced' button in step 7 of 7 of the install, and selected to install GRUB to the boot sector of Intrepid's own partition. 
The reason for doing that is so I can chainload it from GRUB my dedicated GRUB partition.
I wonder if installing to a boot sector rather than to a MBR is what makes ubuquity crash?

Anyway, I followed the same advice I already gave you and mine booted up okay when I used the 'direct kernel boot' method from the GRUB command line.
There was no menu.lst file in my Intrepid installation, so I ran 'sudo update-grub' to generate a menu.lst file automatically, ```
sudo update-grub
```Ubiquity must have crashed before it had time to run update-grub I guess.

Now that's fixed I don't seem to be having an more issues, I hope yours will turn out okay too, I think it probably will.

It's quite possible that the 'Alternate CD' doesn't have the problem, so yes, installing with the 'Alternate CD could be a good way of avoiding this little problem.  The 'Alternate CD' is an extra download though.
Mine wasn't very hard to fix, but I'm used to using all the commands from lots of practice doing crazy experiments and 'borking' my system just for fun. :)

---

### Post by fewjr on 2008-11-15
I'm glad yours worked out and I thought mine was coming along until I tried to boot. I followed your commands exactly..(triple checked each one before I hit enter). This is the first thing I saw after I ran the sudo grub-install string: 

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/GRUB /dev/sda
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /media/GRUB/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/media/GRUB/boot/grub"] is not on an XFS filesystem
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /media/GRUB/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
(hd1)	/dev/sdb
ubuntu@ubuntu:~$ 




```

Did you get that message? when I ran uuid command I did get this output:

```
grub> uuid
(hd0,0) ntfs 00b23c770c8343cc
(hd0,4) ext3 9568ceb9-d96d-4603-8981-f78bb2df39a8
(hd0,5) ext3 7c2e5ac7-2e2c-4612-bd6e-216caf8f1227
(hd0,6) ext2 94e34668-6da2-4f3b-9822-ec3184871810
(hd0,8) ext3 af05f475-aa2a-44d1-b4cc-7cf7dfc143ef
(hd0,9) ext3 3acffe4f-101b-41aa-8ab0-e92c452564e9
```

So it sees sda10, but when I try to boot from the grub menu I get error 15 still and also when I try to boot the kernel directly. Interesting huh! So does this mean my kernal is not complete or something?

---

### Post by Herman on 2008-11-15
> Did you get that message?  Yes, that's normal.
> when I ran uuid command I did get this output:
grub> uuid
(hd0,0) ntfs 00b23c770c8343cc
(hd0,4) ext3 9568ceb9-d96d-4603-8981-f78bb2df39a8
(hd0,5) ext3 7c2e5ac7-2e2c-4612-bd6e-216caf8f1227
(hd0,6) ext2 94e34668-6da2-4f3b-9822-ec3184871810
(hd0,8 ) ext3 af05f475-aa2a-44d1-b4cc-7cf7dfc143ef
(hd0,9) ext3 3acffe4f-101b-41aa-8ab0-e92c452564e9Good, that proves your dedicated GRUB has been updated with the Intrepid version of GRUB's stage2 file.

---

### Post by Herman on 2008-11-15
> So it sees sda10, but when I try to boot from the grub menu I get error 15 still and also when I try to boot the kernel directly. Interesting huh! So does this mean my kernal is not complete or something?:confused: I don't know. That should have worked as long as we didn't make any spelling mistakes or syntax errors, (like a space in the wrong spot or something like that).
'Tab completion' is a useful feature of GRUB's Command Line Interface. You only need to type the first two or three letters of most commands or filenames manually, then press your 'Tab' key and the rest of the filename or command will most times be automatically completed for us.

:-k
What happens when you boot into your dedicated GRUB and press 'c' from the menu to do into [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and do,
```
find /boot/grub/stage2
find /vmlinuz
find /initrd.img
find /sbin/init
cat (hd0,9)/etc/lsb-release
```If those first three commands return '(hd0,9)', in the list of other partition numbers then you should be able to boot Intrepid.
The last command should identify (hd0,9) as Intrepid's partition.

If yours is like mine was you might not have a menu.lst file in Intrepid yet, so 
```
find /boot/grub/menu.lst
``` might not return '(hd0,9) in the list.
That's the main reason why we need to directly boot it at least for this very first time.

---

### Post by fewjr on 2008-11-16
Ahh...I didn't see this post until just now here at work. I will be home in a few hours and will run those commands. I'll post then. ):P

---

### Post by fewjr on 2008-11-17
Okay...here it is.

```
grub>find /boot/grub/stage2
(hd0,4) #Hardy
(hd0,5) #openSUSE
(hd0,6) #GRUB partition
(hd0,8) #Mandriva
```

No stage2 in (hd0,9).


```
grub>/find /vmlinuz
(hd0,4) #Hardy
(hd0,9) #Ibex
```

That was found in both ubuntu partitions, (hd0,9) being Ibex, but why doesn't it show /vmlinuz for openSUSE and Mandriva (hd0,5)&(hd0,8)


```
grub>find /initrd.img
(hdo,4) #Hardy
```

This is not in (hd0,9). Same here, not in openSUSE and Mandriva (hd0,5)&(hd0,8)



```
grub>find /sbin/init
(hd0,4) #Hardy
(hd0,5) #openSUSE
(hd0,8) #Mandriva
(hd0,9) #Ibex
```

That looks good.

```
grub> cat (hd0,9)/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
```

Thats okay.


```
grub> find /boot/grub/menu.lst
(hd0,4)  #Hardy
(hd0,5)  #openSUSE
(hd0,6) #GRUB partition
(hd0,8) #Mandriva

```

So thats missing too! Now what:confused:

---

### Post by Herman on 2008-11-17
I wasn't expecting a menu.lst file, because mine didn't have one either, Ubiquity must have crashed right at that point, but everything else in my Intrepid install seems to be fine.

I have an OpenSuse install too, and I checked and found that the symlinks (shortcuts) to the kernel and initial ramdisk (/vmlinuz and /initrd.img), are located in /boot in OpenSuse, so it's 'find /boot/vmlinuz', and 'find /boot/initrd.img' for those. That's not important for what we're doing now, just a matter for interest.

The lack of a stage2 file in Intrepid for GRUB would be easy to fix, all we would need to do to fix that would be to run the sudo grub-install command there.
(We could do that with Intrepid booted or from your Live CD like we already did to update your dedicated GRUB).

We can easily run 'sudo update-grub' to make a menu.lst file for your Intrepid too, so that's simple to fix.

What does worry me is the lask of a /initrd.img symlink (shortcut) in the root of your Intrepid partition for your initrd.img, which should be located inside /boot.

Maybe you can boot Hardy Heron and mount your Intrepid Ibex file system from there and take a look and see  if everything's there or not.
It should look something like the illustrations in the following linked section of my GRUB Page, [Orientation]("http://users.bigpond.net.au/hermanzone/p15.htm#orientation"). - a guided tour of some of the most important files needed for booting Linux.

Please take a look at yours and check to see if there's an /boot/initrd.img file there (with a string of numbers and punctuation marks after the name).
If there is then we're in luck, and you can still do a direct boot like this,
root (hd0,9)
kernel /vmlinuz root=/dev/sda10
initrd  /boot/initrd.img<press Tab>
boot(You type 'initrd /boot/init ...and press your tab key for the filename to be completed for you).

If you don't have any initrd.img file in /boot, then your installation is incomplete more than I though. 
That might be a bad omen, it tends to imply that possibly there could be other important files missing too. 
If that's the case, you can chose whether to re-install, (which will take about 30 to 45 minutes probably), or if you want we can have fun trying to fix it and learn some tricks maybe.
We'll hope it's only the initrd.img that we need and we could 'chroot' into your incomplete Intrepid installation from your Intrepid Ibex Live CD and run the 'mkinitrd' command and see what happens, and we could also re-install GRUB and run update-grub. 
Those things might fix it, or, we might need to do more work, I'm not sure.
I've never tried the 'mkinitrd' command, but I have chrooted before a few times.

It's up to you to decide what to do next. (Try to fix it or scrap it and re-install?)
If you do have a /boot/initrd.img it should be okay to keep it though, I think.

Regards, Herman :)

UPDATE: 'mkinitramfs' is the command we use now instead of 'mkinitrd', so I renamed the /boot/initrd.img.2.6.27-7-generic to /boot/initrd.img.2.6.27-7-generic.backup  in an Intrepid installation in one of my computers.
Then I ran 'sudo mkinitramfs -k -o /boot/initrd.img-2.6.27-7-generic -v', and a new initrd.img was created in /boot for me.
I rebooted to test it and it worked!
So even if you have no initrd.img, I should be able to help you make one. :)

---

### Post by fewjr on 2008-11-17
> The lack of a stage2 file in Intrepid for GRUB would be easy to fix, all we would need to do to fix that would be to run the sudo grub-install command there.
(We could do that with Intrepid booted or from your Live CD like we already did to update your dedicated GRUB).



I tried to do that, but maybe I have the path wrong. when we did it to the GRUB partition we did:
```
sudo grub-install --root-directory=/media/GRUB /dev/sda
```
  I'm not sure what to put for sda10. I cannot mount that drive from Hardy either.

---

### Post by Herman on 2008-11-17
> I tried to do that, but maybe I have the path wrong. when we did it to the GRUB partition we did:
     Code:
     sudo grub-install --root-directory=/media/GRUB /dev/sda 
  I'm not sure what to put for sda10. I cannot mount that drive from Hardy either.     :) Okay, probably it's not important to do that yet anyway, and yes, the command will need to be different. Instead of 'GRUB', we'll use whatever your mount point turns out to be called, and '/dev/sda' we will replace with '/dev/sda10'. ...but we'll do that later.

It won't mount?
The first thing to do would be to try a file system check then, (from your Live CD).
You can do that either by open Gnome Partition Editor, right-clicking on the partition, and clicking 'check', 'apply', and confirming 'apply', or you can [Run a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") (command line).

Seeing if you have an initrd.img file in /boot is the next step.
We need one of those, we can boot without the stage 2 file or the menu.lst, but we need at least a kernel and an initrd.img and an /sbin/init.

---

### Post by fewjr on 2008-11-17
Okay Herman, I ran:
```
sudo e2fsck -C0 -p -f -v /dev/sda10
```

It didn't come up with any errors, but I still cannot mount the partition in Hardy. I'll try the heavy duty command next: 
```
sudo e2fsck -y -f -v /dev/sda10
```

I'll post in a bit.

---

### Post by fewjr on 2008-11-18
I'm very sorry, but I was trying to mount the wrong drive. Man do I feel....:oops:. Anyway, I have a couple of screenshots so I'm giving you links to them. I haven't figured out how to put pictures in my post yet. The boot directory is missing the grub directory.

[http://s260.photobucket.com/albums/ii20/fewjr/screenshots/](http://s260.photobucket.com/albums/ii20/fewjr/screenshots/)

---

### Post by fewjr on 2008-11-18
Okay, so what I can see from the Ibex partition, it looks like starting with the top of the directory tree, I am missing the /initrd directory. Then if you look at the /boot directory I am missing the /grub directory and initrd.img. There is a new file in 8.10 that is not in your older orientation picture called 'vmcoreinfo-2.6.27-7generic'.

---

### Post by fewjr on 2008-11-18
Man...I tried this
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo update-grub /dev/sda10
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

ubuntu@ubuntu:~$ mkdir /boot/grub
mkdir: cannot create directory `/boot/grub': Permission denied
ubuntu@ubuntu:~$ sudo mkdir /boot/grub
ubuntu@ubuntu:~$  sudo update-grub /dev/sda10
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

ubuntu@ubuntu:~$ 


```

If I did it right I should see a /grub directory in /boot. I probably didn't do it right though, cause /grub directory didn't show up in /boot...but where did it go? It looks like it was happy except for not finding splash and any kernel other than memtest86+. It says it created /boot/grub directory and menu.lst. They are still not there though. I mean if I mount the Ibex partition /boot/grub isn't there still, much less the menu.lst file. The directory (sda10) was mounted when I ran those commands. I think my head hurts now

---

### Post by Herman on 2008-11-18
Sorry for the lateness of my reply, I just had to do some things...

Try this, I have tested this sequence of commands and they worked for me.
I hope they will work for you too.

 1. Boot your Intrepid Ibex 'Desktop' Live CD and go: 'Places'-->'Removable Media'-->'Intrepid', and mount your Intrepid file system in the Live CD.
An icon should appear on your Desktop, and there's also a mount point (directory) at the same time in /media.
In my computer they're both labelled 'Intrepid', but yours might just appear as '204GB Media' or 'disk-1' or something.
You might need to go look in your /media directory or use the command 'ls /media' to check on the name for your mount point there because it will be important to know that for some of the commands we'll be using shortly.

  2. Open a terminal and issued the next two commands to 'chroot' into the hard-disk-installed Intrepid Ibex operating system.

```
sudo mount -t proc none /media/intrepid/proc
```* Assuming the mount point (directory in /media) you have is called 'intrepid', if not, change all instances of 'intrepid in this and the commands after this to whatever your mount point for intrepid ibex is called.
```
sudo mount -o bind /dev/ /media/intrepid/dev
``````
sudo chroot /media/intrepid /bin/bash
```*Your prompt should now look like this: root@ubuntu:/# 
```
mkinitramfs -k -o /boot/initrd.img-2.6.27-7-generic -v
```That command should take a minute or two to run and you should see lots of lines of text scrolling impressingly down your terminal.
When it's finished you should have a new initrd.img in /boot in Intrepid.

  3. Next you can make a new empty directory for GRUB,
```
mkdir /boot/grub
``` 4. Then you can fill the empty /boot/grub directory with new grub files and simultaneously install the 'IPL' for Intrepid's GRUB to the boot sector of Intrepid's own partition,
```
grub-install /dev/sda10
``` 5. Now we will run update-grub to make you a /boot/grub/menu.lst file,
```
update-grub
```(type 'y' for 'yes' when it asks if you want a new menu.lst generated for you)

  6. Finished! Type 'exit' to go back into the live CD,
```
exit
``` * Exits the chroot to hard disk and returns you to a normal shell in the LiveCD.
Your prompt should look like this again:ubuntu@ubuntu:~$ 
Now type 'exit' to close the terminal```
exit
```...and reboot.

If all went according to plan you should be able to boot Intrepid from now on! 

Regards, Herman :)

---

### Post by fewjr on 2008-11-18
Hi Herman, 
No problem....I was in bed anyway.

> Boot your Intrepid Ibex 'Desktop' Live CD and go: 'Places'-->'Removable Media'-->'Intrepid', and mount your Intrepid file system in the Live CD.


Well right from the start I can not do this. I am booted into Ibex livecd. I go to places>removable media and I do not see Intrepid there. I see all my file systems including the one Ibex's broken install is on. Also all the usb drives and my dvdrom & dvd burner. The dvdrom is the one the livecd is in but it doesn't say Intrepid. Sooooo.....maybe my cd is broken too? The iso md5sumed okay. Maybe I should reinstall with the 64bit version.I am on a AMD64.

---

### Post by Herman on 2008-11-18
Have you tried running a file system check in the Ibex partition yet? :)

---

### Post by fewjr on 2008-11-18
Oh yeah Herman....I did that back at post 16/17. You know, I have been re-reading some things and when I ran:
```
grub>find /initrd.img
```
it showed that it was only found in (hd0,4). But if you look at my screenshot it is there. What do you think that means. I tried re-installing Ibex, this time using the 64 bit version instead of i386, and I got the same ubiquity crash error, grub error 15 when I try to boot Ibex and the file system came out the same in sda10 like the screenshots show from i386 version. So I tend to think this is all hardware related to tell you the truth. Both versions error the same way. I have had a lot of issues with this chipset and wireless card with Linux in general. I'm still game though! Maybe its time to learn how to use the Alternatecd, unless you want to try something else.

---

### Post by Herman on 2008-11-18
Usually when the partition can't be mounted it needs a file system check was what I was thinking. ...how did you get the screencaps then?
Your third screencap showing the inside of your 129.5GB Media/boot directory shows six files, including your linux kernel (vmlinuz) but with no initrd.img and no grub directory.

Anyway, you can try the 'Alternate' CD if you like, maybe that will work, it would be worth a try. :)

---

### Post by fewjr on 2008-11-18
Didn't you see post 17. That was all my fault. I was trying to mount the wrong drive. I can mount sda10 from live desktop or Hardy, and your exactly right. I am missing /grub and initrd.img in /boot. I'm not sure what to do though. I've never used the Alternate cd yet...so maybe I'll do that.

---

### Post by fewjr on 2008-11-19
Well Herman....I am typing from my Ibex system. I had no trouble booting after installing with the Alternate cd. So if anyone else is having this problem give the Alternate method a try. I don't know what the difference is, but I would like to know. Thanks for the help. I'll be in touch.:)

fewjr

---

### Post by Herman on 2008-11-19
:) Okay, thanks fewjr, I'm interested to read that the 'Alternate' CD worked for you.
The two CDs are both supposed to install the same operating system, except there are a few special things we can do with the 'Alternate' CD.
It's possible that there might be some bug in the 'Desktop CD' that only shows under certain conditions. Maybe I'll try a re-install just to see if ubiquity will fail again in my computer again or if it was just a co-incidence.
 Anyway, I'm glad you got it working. 
Congratulations and happy Ubuntuing!
Regards, Herman :)

---

### Post by dnoyeb on 2008-12-13
I have also had the same problem with the ubiquity crash.  Only thing missing was the initrd.img.  I even have the link to it in '/'.  I tried the server install, and that worked.  Next I will try the alternate install and see if that works too.  I have never used Ubuntu before.

I am wondering if having my swap drive on LVM has anything to do with the crash?

---

