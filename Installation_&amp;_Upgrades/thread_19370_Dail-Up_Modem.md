---
title: "Dail-Up Modem"
date: 2005-03-11
forum: Installation &amp; Upgrades
---

### Post by LonelyTraveler on 2005-03-11
Hi. Can someone please help me to get my BCM V.92 modem detected. It looks like it's installed, but it doesn't get detected when trying to set up my network connection. Please help.

---

### Post by az on 2005-03-11
[www.linmodems.org](www.linmodems.org)

Get and run scanmodem.

Post the output here.

---

### Post by LonelyTraveler on 2005-03-11
I'm totally new to this. And don't want to disconnect from the internet to run scanmodem before I know what I need to know as we pay for dail up here. Do I just start Ubuntu and double click scanmodem?

---

### Post by LonelyTraveler on 2005-03-11
[QUOTE=LonelyTraveler]I'm totally new to this. And don't want to disconnect from the internet to run scanmodem before I know what I need to know as we pay for dail up here. Do I just start Ubuntu and double click scanmodem?[/QUOTE]
 I went ahead and ran the scan. I don't know if this is what you wanted?:




 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 4.10 kernel 2.6.8.1-3-386
 Occassionally reponses are blocked by an Internet Providers mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_March_3
------------ --------------  System information ------------------------
Ubuntu 4.10 "Warty Warthog" 
 on System with processor: i686
 currently under kernel:   2.6.8.1-3-386
 The kernel was assembled with compiler:  3.3.4
 a gcc package must be installed to support driver compiling

Checking for kernel-headers needed for compiling.
Kernel-header resources are not evident.
Within your Linux distributions resources, search for package names with:
  linux-headers-2.6.8.1-3-386
  kernel-source-2.6.8.1-3-386
  linux-2.6.8.1-3-386
One of which must be installed if compiling drivers to match kernel 2.6.8.1-3-386 proves necessary.
This is necessary for most modem drivers, through some Linux distributions provide some compiled drivers.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
  

 A /dev/modem symbolic link is not set.
 Checking for USB modems
 None found

Modem candidates are at PCI_buses:  0000:00:1f.6
    
Providing detail for device at PCI_bus 0000:00:1f.6
  with vendor-ID:device-ID
	    ----:----
Class 0703: 8086:24c6   Modem: Intel Corp. 82801DB (ICH4) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
  SubSystem 14e4:4d64   Broadcom Corporation: Unknown device 4d64
	Flags: bus master, medium devsel, latency 0, IRQ 201
	I/O ports at b400
	I/O ports at b080 [size=128]
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:24c6 14e4:4d64 debian 2.6.8.1-3-386 3.3.4     i686

       
 The soft modem Subsystem operates under a controller
   8086:24c6 82801DB ICH4 
 capable of supporting under Linux AT LEAST modem Subsystem chips from manufacturers:

	Broadcom
	AgereSystems
	Conexant
	Intel
	Smartlink
Use the SmartLink slmodem software for support.
For this Broadcom subsystem modem, the slmodemd daemon must be used in ALSA mode
	slmodemd --alsa --country=YOURS modem:0
  Driver snd-intel8x0m  may enable codec acquisition 
  === Begin mc97 codec query  ===
File /proc/asound/card1/codec97#0/mc97#1-1
 --------
1-1/0: 0x42434d64 BCM

Extended modem ID: codec=1 LIN1
Modem status     : GPIO ADC1 DAC1 PRB(res) PRE(ADC2) PRF(DAC2) PRG(HADC) PRH(HDAC)
Line1 rate       : 12000Hz
 --------
 14e4:4d64 has a BCM64 codec
  === End mc97 codec query  ===

 Beginning check for older ac97_codec modems.
 An older ac97_modem codec was not detected.

 Checking through information gathered from LinModem ARCHIVES
 From prior reports, the modem codec type of the Subsystem is: BCM64
 The Subsystem has a Broadcom codec BCM64
 SmartLink software should support this modem
 Only the SmartLink slmodem-2.9.9-alsa software supports this modem
 == Checking PCI IDs through modem chip suppliers ==

 Vendor 14e4 is BroadCom 
   14e4:4212   is a  BCM V.90 56k modem
 There is 2.2.n kernel support at:
    [http://support.ap.dell.com/ap/en/filelib/download/index.asp?fileid=R47114](http://support.ap.dell.com/ap/en/filelib/download/index.asp?fileid=R47114)
 However the code has not been updated for some time.
 For  2.4 kernels, fix by Giacomo Comes must be used. See :
   [http://linmodems.technion.ac.il/archive-third/msg01652.html](http://linmodems.technion.ac.il/archive-third/msg01652.html)
 When serving under softmodem controllers like the Intel ICH series,
 the Broadcom Subsystem 14e4:4d64 has mc97 codec BCM64.
 For 2.6.n kernels, see success reports:
   [http://linmodems.technion.ac.il/archive-fourth/msg03690.html](http://linmodems.technion.ac.il/archive-fourth/msg03690.html)
   [http://oboc.ucdavis.edu/Marik/inspiron/](http://oboc.ucdavis.edu/Marik/inspiron/) 
   The support is achieved through a combination of:
   1) the snd-intel8x0m.ko of 2.6.n kernel releases, which provides a low level interface with the modem;
   2) an slmodemd daemon which creates ports and provides higher level functions.
   Get the slmodem-2.9.9-alsa.tar.gz from  [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
   To compile the slmodemd, it is first Necessary to install a libasound2-dev package, providing alsa headers.
   3) After compilation and installation of slmodemd, initiate service with:
   # modprobe  snd-intel8x0m
   # slmodemd --alsa --country=YOURCOUNTRY hw:0
   Read the slmodem documentation for details and Modem/Slmodem.txt


 SmartLink at [http://www.smlink.com/](http://www.smlink.com/) owns vendor IDs 163c, 2000, 2003, and 2004
 The official download site is:  [http://www.smlink.com/main/index1.php?ln=en&main_id=40](http://www.smlink.com/main/index1.php?ln=en&main_id=40) ,
  but [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) has older packages and new fixes.
      For the emerging 2.6.10 kernels, use the slmodem-2.9.9a.tar.gz  therefrom.
 Read Slmodem.txt  for details.
   
 == Checking PCI IDs through modem chip suppliers ==

 Vendor=8086 is Intel, Inc. producing HaM and 536ep host controller free (HCF) modems, 537 soft modem
 and AC97 and MC97 controllers managing a varierty of non-Intel soft modem Subsystems.
 These subSystems often have PCI_IDs assigned by the modem assembler, rather than the chip provider.
 Download available drivers through:  [http://developer.intel.com/design/modems/support/drivers.htm](http://developer.intel.com/design/modems/support/drivers.htm)  with Intel-537 types at:
 [http://downloadfinder.intel.com/scripts-df/Filter_Results.asp?selCat=all&strOSs=39&ProductID=1230&page_nbr=2](http://downloadfinder.intel.com/scripts-df/Filter_Results.asp?selCat=all&strOSs=39&ProductID=1230&page_nbr=2)
 Also check at: [http://linmodems.technion.ac.il/packages/Intel/537/](http://linmodems.technion.ac.il/packages/Intel/537/)  
 for beta releases and perhaps Already compiled drivers for some Linux distributions
 ---------------------

  ======= PCI_ID checking completed ====== 
 Update=2005_March_3

Analyzing information for PCMCIA device at PCI Bus 02:04.0
GREPping for an inserted PCMCIA modem with filter:        ommunication
 If a PCMCIA modem is currently inserted and the sockets activated by
    /etc/init.d/pcmcia start
 then the PCMCIA bridge is NOT transparent.

 If the modem is known to have a Lucent digital signal processing chipset,
 then PCMCIA.tar.gz variant assembled by Joern Wustenfeld is necessary,
 rather than the standard ltmodem-8.31a9.tar.gz at  [http://ltmodem.heby.de/](http://ltmodem.heby.de/)
GCCversion=
The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias char-major-108 ppp_generic
/etc/modprobe.d/aliases:alias tty-ldisc-3  ppp_async  
/etc/modprobe.d/aliases:alias tty-ldisc-14 ppp_synctty
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe
/etc/modprobe.d/aliases:alias ppp-compress-21 bsd_comp   
/etc/modprobe.d/aliases:alias ppp-compress-24 ppp_deflate
/etc/modprobe.d/aliases:alias ppp-compress-26 ppp_deflate
-------------------------------------
 Resident PPP support modules are properly uncompressed .
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/General.txt

  A port needed for the PPP protocol is absent!!!
  echo "  crw-------    1 root     root     108,   0 Dec 31  1969 /dev/ppp"

A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
  debian is not yet providing pre-compiled drivers for WinModems

---

### Post by alastair on 2005-03-11
It's really what /you/ wanted. Although mich of it /looks/ hard to read, try and scan through it because it actually tells you many details of exactly what you want to do. Very useful script actually.

e.g. Quoting :

For 2.6.n kernels, see success reports:
[http://linmodems.technion.ac.il/arc...h/msg03690.html](http://linmodems.technion.ac.il/arc...h/msg03690.html)
[http://oboc.ucdavis.edu/Marik/inspiron/](http://oboc.ucdavis.edu/Marik/inspiron/)
The support is achieved through a combination of:
.<options>

You want to probably try the slmodem package - do a package search for :

sl-modem-daemon
sl-modem-source (maybe)

and read the docs that come with them.

---

