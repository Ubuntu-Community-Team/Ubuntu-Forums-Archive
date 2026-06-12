---
title: "SONY Vaio PCG-FX101 Howto successfully install Ubuntu 6.0.6 and upgrade"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by peterwatson on 2006-10-04
First steps are to successfully boot the LIVE CD. To accomplish this I pressed F6 at the boot screen of Ubuntu and added 'acpi=off' to the boot command.
	
	This allows the Sony Vaio with the doggy SONY ACPI to boot the live CD.
	
	Once the CD had booted I performed the install by double clicking the installer on the desktop.
	
	Once installed, reboot the machine and logon.
	
	After a successful reboot, reboot again but this time.
	
	I inserted my CardBus 32bit (pcmcia) network adapter that will not function with 'acpi=off'.
	
	Press ESC at the GRUB screen to get into the boot loader menu.
	
	Select the Ubuntu entry and press 'E', select the kernel line and press 'E' again. go to the end of this line and 	remove 'acpi=off', press 'enter' key you should now be able to press 'B' this will boot Ubuntu without the 'acpi=off'.
	
	The system appears to hang at the 'Loading kernel [OK]...' but be patient. After a while the screen will suddenly change straight to the GDM logon screen.
	
	Once logged on the network should be functional.
	
	Open synaptic, at this point DO NOT UPGRADE, I did first time and it made the Vaio unusable with 'acpi=off'
	
**** The below parts are instructions I found on the Ubuntu forums ****
	
	In synaptic Search for 'ndis'. From the results mark ndisgtk, this in turn will mark ndiswrapper-utils. Choose yes if needed.
	
	Then click Apply on the toolbar
	
	Once these are installed close Synaptic.
	
	I then installed the wireless drivers straight of the Driver CD that came with my USB wireless device.
	
	Go to System->Administration->Wireless Windows Drivers
	
	Click Add browse to the folder where your *.inf or *.sys files for your hardware are located and then click install.
	
	At this point you can test you hardware. Mine worked fine at this point.
	
	Next I again rebooted removed the CardBus (pcmcia) card and allowed the machine to restart with the 'acpi=off' command.
	
Once rebooted with ‘acpi=off’ you can upgrade.

	The Vaio started and the USB wireless started at boot and
	Hey presto I now have a Microsoft loving Sony VAIO PCG-FX101 running Ubuntu with a wireless USB dongle.

---

