---
title: "HP Pavilion A64x2 install problems"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by daffy_ on 2005-11-13
I just bought a HP Pavilion w5296 (similar to w5295), but I can't get linux to boot on it. I have downloaded the 64bit version of 5.10, and when trying to install I get this errormessage:

```
ohci_hcd 000:00:13.0: Unlink after no_IRQ?
Controller is probably using the wrong IRQ
```

I have tried assorted methods to get this working, including:

noapic nolapic
pci=biosirq
pci=noacpi
debian-somethign-/probe/usb=false
acpi=off

But to no avail. I managed to start the 5.04 live cd by using the "usb=false" and "pci=noacpi" parameters, but on 5.10 64-bit they don't help either.


The box consists of the following hardware:
MSI [MS-7184]("http://www.emachineupgraders.info/dir1/motherboards/socket939/msi7184.shtml") Mainboard
AMD 64 X2 4200+
2GB PC3200 RAM
Creative X-Fi (Xtreme Music) soundcard
Nvidia geForce 7800GTX (bios 5.70.02.11.01)
Wi-Fi: Liteon Card PCI 802.11, WN5401A
Tv-card: Asus TV-Tuner, Philips Saa7131E chip
WD250JS 250GB HDD (s-ata)


If I try to boot with "pci=noacpi", I don't get any error-messages, but the entire install still does not work. The last lines look like this:

```

Running /etc/hotplug/pci.rc
   SCSI subsystem initialized
   ata1: SATA max UDMA/100 ... (lots of numbers++) ... irq 11
   ata2: SATA max UDMA/100 ... (lots of numbers++) ... irq 11
   ata1: dev 0 ATA, max UDMA/100, 488397168 sectors: lba48

```


I have tried Knoppix 4.0.2 and Mandriva 2006, just to check if this is a Ubuntu only problem, and I get similar errors with them. (Mandriva came into graphical installer, but complained shortly that it found no valid HDD location.)


All help is greatly appreciated! :)


I have learned that if I want to run linux, I should always be careful with what hardware I buy, but I got this computer at such a low price that I could not resist. And I am beginning to regret that I bought it :(

---

### Post by nbhaskar on 2005-12-11
I bought a AMD 64 X2 3800 processor with ECS nForce4 A939 mother board and ATI X700 PCI-E graphics card. I tried booting from Ubuntu 5.10 live CD, I'm also getting error message while the Graphics drivers are loaded. Some body please help me.

---

### Post by daffy_ on 2005-12-12
I am not sure, but some of my problems were that my s-ata controller was not properly recognized. I'm currently running SuSE 10.0 (64 bit) which recognized my controller (correctly) and uses the sata_sil drivers.

I believe that they were not my only problems, since I had irq-problem-messages on boot as well. From what I have found, the chipset on my mo-bo is a bit strange and not well supported at the moment. However, I'm now happily running SuSE 10.0. I have had reports saying that Fedora Core 4 also works well.

Try one of those distro's if you can't get ubuntu to work. As an old debian-fan, I am really missing apt-get/aptitude, but the SuSE YaST is not too bad once you get used to it. (For Fedora, I recommend yum as the package manager of choice).

---

### Post by nbhaskar on 2006-01-05
[QUOTE=nbhaskar]I bought a AMD 64 X2 3800 processor with ECS nForce4 A939 mother board and ATI X700 PCI-E graphics card. I tried booting from Ubuntu 5.10 live CD, I'm also getting error message while the Graphics drivers are loaded. Some body please help me.[/QUOTE]

I got this working finally, thanks to Gabor. When I changed "ati" to "radeon" in xorg.conf file, the system booted up and I'm able to login.

thanks
:p

---

