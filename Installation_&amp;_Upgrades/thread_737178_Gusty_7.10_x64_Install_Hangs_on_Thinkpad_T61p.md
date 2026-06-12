---
title: "Gusty 7.10 x64 Install Hangs on Thinkpad T61p"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by itsme_n8 on 2008-03-27
Hi all.  I’m a recovering windows addict and trying to make the switch (I have only used UBUNTU once… so I’m a complete NOOB… I have done some low level I.T. so I’m not a complete idiot.).  I am, however experiencing some problems when trying to install UBUNTU 7.10 x64.  I have been reading as many posts as I can on this, and found others that have experienced similar if not the same issues.  I tried the suggestions in this thread: [http://ubuntuforums.org/showthread.php?t=674742&highlight=install+hangs](http://ubuntuforums.org/showthread.php?t=674742&highlight=install+hangs)  , also  modifying some parameters found in another thread, and even downloading the full 4.2 gb DVD image.  When I restart my laptop, the UBUNTU start screen comes up, and I’ve tried multiple ways:  Install, Install with graphics safe mode, pressing F6 and adding some parameter values to the end of text.  The results are all the same.  It says it has to run in low graphics mode (this is for the normal install… I don’t remember seeing this for safe mode), and I click OK, then it quickly says something about allocation of resources (can’t ever make it out as it is only on the screen for a second).  Then the screen just says:
* Checking battery state… 				[OK]
* Running local boot scripts (/etc/rc.local)		[OK]
It will not go beyond that point.  I burned the DVD at the slowest speed I could 2.4x.  I checked the integrity of the disk, which also fails.  Please help, I really don’t want to be relegated to the world of windows.  I have to admit, I haven’t tried the 32 bit version.  My laptop hat 4gb of ram in it, and would like to utilize that ram (as I will need to use VM for my work).  Here is a summary of my laptop (sorry if it's TMI):

EVEREST Home Edition © 2003-2005 Lavalys, Inc. 

Summary 
________________________________________
 		Computer: 
			Operating System   	Microsoft Windows Vista Media Center Edition  (Vista Ultimate 32 bit)
			OS Service Pack   	Service Pack 1 
			DirectX   	4.09.00.0904 (DirectX 9.0c) 
			
		Motherboard: 
			CPU Type   	Intel Pentium III Xeon, 2500 MHz (7.5 x 333) 
			Motherboard Name   	LENOVO 6459CTO 
			Motherboard Chipset   	Unknown 
			System Memory   	3072 MB 
			BIOS Type   	Phoenix  	
			
		Display: 
			Video Adapter   	NVIDIA Quadro FX 570M 
			Video Adapter   	NVIDIA Quadro FX 570M 
			Monitor   	ThinkPad Display 1920x1200 [NoDB] 	
		Storage: 
			IDE Controller   	Intel(R) 82801HEM/HBM SATA AHCI Controller 
			IDE Controller   	Intel(R) ICH8M Ultra ATA Storage Controllers - 2850 
			IDE Controller   	Ricoh Memory Stick Controller 
			IDE Controller   	Ricoh SD/MMC Host Controller 
			IDE Controller   	Ricoh xD-Picture Card Controller 
			SCSI/RAID Controller   	Intel(R) Turbo Memory Controller 
			SCSI/RAID Controller   	Microsoft iSCSI Initiator 
			Disk Drive   	Hitachi HTS722020K9SA00 (186 GB, IDE) 
			Disk Drive   	IMD-0 (512 MB, IDE) 
			Optical Drive   	MATSHITA DVD-RAM UJ-852 ATA Device 
			SMART Hard Disks Status   	OK 
		Partitions: 
			C: (NTFS)   	132474 MB (78022 MB free) 
		Input: 
			Keyboard   	Standard PS/2 Keyboard 
			Mouse   	ThinkPad UltraNav Pointing Device 
		Network: 
			Network Adapter   	Bluetooth Device (Personal Area Network) 
			Network Adapter   	Intel(R) 82566MM Gigabit Network Connection (192.168.212.59) 
			Network Adapter   	Intel(R) Wireless WiFi Link 4965AGN 
			Modem   	ThinkPad Modem 
		 
DMI 
________________________________________  				
	[ Memory Controller ]   					
		Memory Controller Properties: 	
			Error Detection Method   	None 	
			Error Correction   	None 	
			Supported Memory Interleave   	1-Way 	
			Current Memory Interleave   	1-Way 	
			Supported Memory Types   	DIMM, SDRAM 	
			Supported Memory Voltages   	2.9V 	
			Maximum Memory Module Size   	4096 MB 	
			Memory Slots   	2 			
	[ Processors / Intel(R) Core(TM)2 Duo CPU T9300 @ 2.50GHz ] 		
		Processor Properties: 	
			Manufacturer   	GenuineIntel 	
			Version   	Intel(R) Core(TM)2 Duo CPU T9300 @ 2.50GHz 	
			External Clock   	200 MHz 	
			Maximum Clock   	2500 MHz 	
			Current Clock   	2500 MHz 	
			Type   	Central Processor 	
			Voltage   	1.2 V 	
			Status   	Enabled 	
			Upgrade   	None 	
			Socket Designation   	None 			
	[ Caches / Internal L1 Cache ]   					
		Cache Properties: 	
			Type   	Internal 	
			Status   	Enabled 	
			Operational Mode   	Write-Back 	
			Maximum Size   	64 KB 	
			Installed Size   	64 KB 	
			Supported SRAM Type   	Synchronous 	
			Current SRAM Type   	Synchronous 	
			Error Correction   	Single-bit ECC 	
			Socket Designation   	Internal L1 Cache 	
	[ Caches / Internal L1 Cache ]   					
		Cache Properties: 	
			Type   	Internal 	
			Status   	Enabled 	
			Operational Mode   	Write-Back 	
			Maximum Size   	64 KB 	
			Installed Size   	64 KB 	
			Supported SRAM Type   	Synchronous 	
			Current SRAM Type   	Synchronous 	
			Error Correction   	Single-bit ECC 	
			Socket Designation   	Internal L1 Cache 	
	[ Caches / Internal L2 Cache ]   					
		Cache Properties: 	
			Type   	Internal 	
			Status   	Enabled 	
			Operational Mode   	Write-Back 	
			Maximum Size   	6144 KB 	
			Installed Size   	6144 KB 	
			Supported SRAM Type   	Burst 	
			Current SRAM Type   	Burst 	
			Error Correction   	Single-bit ECC 	
			Socket Designation   	Internal L2 Cache 	
	[ Memory Modules / DIMM Slot 1 ]   					
		Memory Module Properties: 	
			Socket Designation   	DIMM Slot 1 	
			Type   	DIMM, SDRAM 	
			Speed   	155 ns 	
			Installed Size   	2048 MB 	
			Enabled Size   	2048 MB 		
	[ Memory Modules / DIMM Slot 2 ]   					
		Memory Module Properties: 	
			Socket Designation   	DIMM Slot 2 	
			Type   	DIMM, SDRAM 	
			Speed   	155 ns 	
			Installed Size   	2048 MB 	
			Enabled Size   	2048 MB 		
	[ Memory Devices / DIMM 1 ]   					
		Memory Device Properties: 	
			Form Factor   	SODIMM 	
			Type Detail   	Synchronous 	
			Size   	2048 MB 	
			Speed   	667 MHz 	
			Total Width   	64-bit 	
			Data Width   	64-bit 	
			Device Locator   	DIMM 1 	
			Bank Locator   	Bank 0/1 			
	[ Memory Devices / DIMM 2 ]   					
		Memory Device Properties: 	
			Form Factor   	SODIMM 	
			Type Detail   	Synchronous 	
			Size   	2048 MB 	
			Speed   	667 MHz 	
			Total Width   	64-bit 	
			Data Width   	64-bit 	
			Device Locator   	DIMM 2 	
			Bank Locator   	Bank 2/3 	
CPU 
________________________________________  				
		CPU Properties: 
			CPU Type   	Intel Pentium III Xeon, 2500 MHz (7.5 x 333) 
			Instruction Set   	x86, x86-64, MMX, SSE, SSE2, SSE3 
			Original Clock   	2500 MHz 
			L1 Code Cache   	32 KB 
			L1 Data Cache   	32 KB 
			L2 Cache   	6 MB (On-Die, ATC, Full-Speed) 		
		Multi CPU: 
			CPU #0   	Intel(R) Core(TM)2 Duo CPU T9300 @ 2.50GHz, 2493 MHz 
			CPU #1   	Intel(R) Core(TM)2 Duo CPU T9300 @ 2.50GHz, 2493 MHz   				
		CPU Manufacturer: 
			Company Name   	Intel Corporation 
			Product Information   	[http://www.intel.com/products/browse/processor.htm](http://www.intel.com/products/browse/processor.htm)   				
		CPU Utilization: 
			CPU #1 / Core #1 / HTT Unit #1   	0 % 
			CPU #1 / Core #1 / HTT Unit #2   	0 % 
Motherboard 
________________________________________  				
		Motherboard Properties: 
			Motherboard ID   	<DMI> 
			Motherboard Name   	LENOVO 6459CTO 	
		Front Side Bus Properties: 
			Bus Type   	Intel AGTL+ 
			Bus Width   	64-bit 
			Real Clock   	333 MHz 
			Effective Clock   	333 MHz 
			Bandwidth   	2667 MB/s 
Windows Video 
________________________________________  				
	[ NVIDIA Quadro FX 570M ]   					
		Video Adapter Properties: 	
			Device Description   	NVIDIA Quadro FX 570M 	
			Adapter String   	Quadro FX 570M 	
			BIOS String   	Version 60.84.51.0.0 	
			Chip Type   	Quadro FX 570M 	
			DAC Type   	Integrated RAMDAC 	
			Installed Drivers   	nvd3dum (7.15.11.5685), nvwgf2um (7.15.11.5685) 	  					
		Video Adapter Manufacturer: 	
			Company Name   	NVIDIA Corporation 	
			Product Information   	[http://www.nvidia.com/view.asp?PAGE=products](http://www.nvidia.com/view.asp?PAGE=products) 
			Driver Download   	[http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp) 				
Monitor 
________________________________________  				
	[ ThinkPad Display 1920x1200 [NoDB] ] 					
		Monitor Properties: 	
			Monitor Name   	ThinkPad Display 1920x1200 [NoDB] 	
			Monitor ID   	LEN4055 	
			Manufacturer   	LP154WU1-TLB1 	
			Manufacture Date   	2007 	
			Serial Number   	None 	
			Max. Visible Display Size   	33 cm x 21 cm (15.4") 	
			Picture Aspect Ratio   	5:3 	
			Gamma   	2.20 	
			DPMS Mode Support   	Standby, Suspend, Active-Off

Thanks,
Nate

---

### Post by itsme_n8 on 2008-03-28
Really?!  Nothin?!  

Ok then... I've seen a lot of recommendations to use the alternate CD... Anybody out there with similar issues having luck with the alt CD?  Also could somebody at least point me to a white paper, or some directions on how to use the alt CD?  I've downloaded it and I'm burning as I type this.  

Thanks
Nate

---

### Post by Pumalite on 2008-03-28
Maybe this helps:
[http://ubuntuforums.org/showthread.php?t=696822](http://ubuntuforums.org/showthread.php?t=696822)
I read splash screen is no good for you.

---

### Post by Whiffle on 2008-03-28
Maybe:

[http://de.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61#My_DVD_drive.2FCD_burner.2FDVD_burner_doesn.27t_work_.28Solved.29](http://de.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61#My_DVD_drive.2FCD_burner.2FDVD_burner_doesn.27t_work_.28Solved.29)

Apparently there is some issue with AHCI, it might be your issue I dunno.  You could try putting it in compatability mode and see if that helps.

---

### Post by itsme_n8 on 2008-03-28
woo hoo... got it installed using the alt CD... wow... that was easy... Kinda disappointed about the lack of drivers for drivers for NVIDIA Quadro FX 570M.  Any advice on that piece?  I'm so stoked now... 


Nate

---

