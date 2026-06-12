---
title: "installed ok, machine hangs after boot?"
date: 2005-03-11
forum: Installation &amp; Upgrades
---

### Post by george29 on 2005-03-11
Hi, I'm new to linux and after looking around a bit thought i'd give UBUNTU a try. I downloaded the warty 4.1 iso, checked the MD5 sum, and burnt the image to CD - all good, stuck the CD in my DVD-ROM drive and the machine booted from the CD, installed UBUNTU onto some free space on my drive in a dual boot configuration with my XP installation. all good. 

The Problem is that when i turn the machine on GRUB loads and i can boot into windows with no problem, however if i choose UBUNTU it asks for the username and password, starts up what i assume is the GNOME desktop and then just sits there with the mouse pointer in the centre of the screen and i can't do anything. the mouse doesn't work and no response to the keyboard either.  ](*,)  ](*,) 

I've tried doing the install not downloading any updates, with downloading and not sure what else to do. 

the PC is a DELL Dimension 4500, P4 - 2.5Ghz, 768Mb RAM, nVidia MX420 64Mb, Creative SB live sound card, USB optical scroll mouse.

If anyone knows what's causing this i'd be really grateful for some help to fix it.

---

### Post by george29 on 2005-03-11
Since i posted earlier i've tried a different distro, libranet 2.8.1 and it's installed fine as far as i can tell everything works. So why doesn't UBUNTU work - I would've thought that with a newer Kernel etc it would better than a 2 year old distro?  

anyone got any ideas as to why GUI freezes after i login? (in UBUNTU that is).

thanks for any help
george

---

### Post by nemin on 2005-03-11
[QUOTE=george29]
The Problem is that when i turn the machine on GRUB loads and i can boot into windows with no problem, however if i choose UBUNTU it asks for the username and password, starts up what i assume is the GNOME desktop and then just sits there with the mouse pointer in the centre of the screen and i can't do anything. the mouse doesn't work and no response to the keyboard either.  ](*,)  ](*,) [/QUOTE]
Can you access the commandline by pressing Ctr+Alt+F1? If you can, try to login and have a look at the logfiles in /var/log, Good luck.

---

### Post by george29 on 2005-03-16
Hi Nemin,

I've finally got round to trying another install of UBUNTU - so now have a triple boot configuration with XP, libranet and UBUNTU. still having the same problem in that UBUNTU boots into the gnome desktop GUI but then hangs, can't access anything using mouse or keyboard. 

I can access the command line via ctrl + alt + F1. and look at /var/log

Here's where i need help what am i looking for??? and how do i go about changing things to get UBUNTU running???? 
will require a bit of handholding on this?

thanks for any help you can give
George

---

### Post by george29 on 2005-03-17
hi, i think i've found the part of the log file which corresponds to the usb system and mouse, hence why the command line works, but not the mouse. can anyone give me an idea as to what i need to change and how.

thanks for any help you can give 

george

Mar 16 23:41:55 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Mar 16 23:41:55 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 16 23:41:55 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
Mar 16 23:41:55 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Mar 16 23:41:55 localhost kernel: usbcore: registered new driver usbfs
Mar 16 23:41:55 localhost kernel: usbcore: registered new driver hub
Mar 16 23:41:55 localhost kernel: USB Universal Host Controller Interface driver v2.2
Mar 16 23:41:55 localhost kernel: PCI: Found IRQ 11 for device 0000:00:1d.0
Mar 16 23:41:55 localhost kernel: uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB (ICH4) USB UHCI #1
Mar 16 23:41:55 localhost kernel: PCI: Setting latency timer of device 0000:00:1d.0 to 64
Mar 16 23:41:55 localhost kernel: uhci_hcd 0000:00:1d.0: irq 11, io base 0000e800
Mar 16 23:41:55 localhost kernel: uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Mar 16 23:41:55 localhost kernel: hub 1-0:1.0: USB hub found
Mar 16 23:41:55 localhost kernel: hub 1-0:1.0: 2 ports detected
Mar 16 23:41:55 localhost kernel: PCI: Found IRQ 5 for device 0000:00:1d.1
Mar 16 23:41:55 localhost kernel: uhci_hcd 0000:00:1d.1: Intel Corp. 82801DB (ICH4) USB UHCI #2
Mar 16 23:41:55 localhost kernel: PCI: Setting latency timer of device 0000:00:1d.1 to 64
Mar 16 23:41:55 localhost kernel: uhci_hcd 0000:00:1d.1: irq 5, io base 0000e880
Mar 16 23:41:55 localhost kernel: uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Mar 16 23:41:55 localhost kernel: hub 2-0:1.0: USB hub found
Mar 16 23:41:55 localhost kernel: hub 2-0:1.0: 2 ports detected
Mar 16 23:41:55 localhost kernel: PCI: Found IRQ 9 for device 0000:00:1d.2
Mar 16 23:41:55 localhost kernel: PCI: Sharing IRQ 9 with 0000:00:1f.1
Mar 16 23:41:55 localhost kernel: uhci_hcd 0000:00:1d.2: Intel Corp. 82801DB (ICH4) USB UHCI #3
Mar 16 23:41:55 localhost kernel: PCI: Setting latency timer of device 0000:00:1d.2 to 64
Mar 16 23:41:55 localhost kernel: uhci_hcd 0000:00:1d.2: irq 9, io base 0000ec00
Mar 16 23:41:55 localhost kernel: uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Mar 16 23:41:55 localhost kernel: usb 1-2: new low speed USB device using address 2
Mar 16 23:41:55 localhost kernel: hub 3-0:1.0: USB hub found
Mar 16 23:41:55 localhost kernel: hub 3-0:1.0: 2 ports detected
Mar 16 23:41:55 localhost kernel: PCI: Found IRQ 10 for device 0000:00:1d.7
Mar 16 23:41:55 localhost kernel: ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB (ICH4) USB2 EHCI Controller
Mar 16 23:41:55 localhost kernel: PCI: Setting latency timer of device 0000:00:1d.7 to 64
Mar 16 23:41:55 localhost kernel: ehci_hcd 0000:00:1d.7: irq 10, pci mem f0875c00
Mar 16 23:41:55 localhost kernel: ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Mar 16 23:41:55 localhost kernel: PCI: cache line size of 128 is not supported by device 0000:00:1d.7
Mar 16 23:41:55 localhost kernel: ehci_hcd 0000:00:1d.7: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
Mar 16 23:41:55 localhost kernel: hub 4-0:1.0: USB hub found
Mar 16 23:41:55 localhost kernel: hub 4-0:1.0: 6 ports detected
Mar 16 23:41:55 localhost kernel: hw_random hardware driver 1.0.0 loaded
Mar 16 23:41:55 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
Mar 16 23:41:55 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Mar 16 23:41:55 localhost kernel: usb 1-2: control timeout on ep0out
Mar 16 23:41:55 localhost kernel: uhci_hcd 0000:00:1d.0: Unlink after no-IRQ?  Different ACPI or APIC settings may help.
Mar 16 23:41:55 localhost kernel: PCI: Found IRQ 11 for device 0000:02:00.0
Mar 16 23:41:55 localhost kernel: gameport: pci0000:02:00.1 speed 1046 kHz
Mar 16 23:41:55 localhost kernel: dmfe: Davicom DM9xxx net driver, version 1.36.4 (2002-01-17)
Mar 16 23:41:55 localhost kernel: PCI: Found IRQ 11 for device 0000:02:01.0
Mar 16 23:41:55 localhost kernel: eth0: Davicom DM9102 at pci0000:02:01.0, 00:80:ad:7b:27:9e, irq 11.
Mar 16 23:41:55 localhost kernel: Linux Tulip driver version 1.1.13 (May 11, 2002)
Mar 16 23:41:55 localhost kernel: usb 1-2: control timeout on ep0out
Mar 16 23:41:55 localhost kernel: usb 1-2: device not accepting address 2, error -110
Mar 16 23:41:55 localhost kernel: NET: Registered protocol family 17
Mar 16 23:41:55 localhost kernel: NET: Registered protocol family 10
Mar 16 23:41:55 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Mar 16 23:41:55 localhost kernel: IPv6 over IPv4 tunneling driver

---

### Post by nemin on 2005-03-19
[QUOTE=george29]hi, i think i've found the part of the log file which corresponds to the usb system and mouse, hence why the command line works, but not the mouse. 
[dmesg][/QUOTE]
I don't thin the mouse is the problem, but you can easily check that, simply unplug it and check if gnome starts correctly then...
By the way, have a look at /var/log/gdm too, I think there might be also interesting logfiles.

---

### Post by george29 on 2005-03-20
Hi,

not sure what i've done, but i've got the mouse to work - sortof, if i try and reboot rather than shut down and then restart, it won't work.

I'm going to have a go at updating the kernel see if that has any effect on the shutdown problem that i'm having (it looks like it's trying to restart - puts up a message about mounting local file systems etc which you see when the machine boots)

anyway the log file you mentioned is below - is there anything in it that i need to worry about? 

also anyone know any good guides for updating the kernel?

cheers

George

This is a pre-release version of XFree86, and is not supported in any
way.  Bugs may be reported to [email]XFree86@XFree86.Org[/email] and patches submitted
to [email]fixes@XFree86.Org[/email].  Before reporting bugs in pre-release versions,
please check the latest version in the XFree86 CVS repository
([http://www.XFree86.Org/cvs)](http://www.XFree86.Org/cvs)).

XFree86 Version 4.3.0.1 (Ubuntu 4.3.0.dfsg.1-6ubuntu25.2 20050316093755 root@)
Release Date: 15 August 2003
X Protocol Version 11, Revision 0, Release 6.6
Build Operating System: Linux 2.6.8.1 i686 [ELF]
Build Date: 16 March 2005
        Before reporting problems, check [http://www.XFree86.Org/](http://www.XFree86.Org/)
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.8.1-3-386 (buildd@terranova) (gcc version 3.3.4 (De bian 1:3.3.4-9ubuntu5)) #1 Tue Oct 12 12:41:57 BST 2004 T
Markers: (--) probed, (**) from config file, (==) default setting,
         (++) from command line, (!!) notice, (II) informational,
         (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/XFree86.0.log", Time: Sun Mar 20 22:52:26 2005
(==) Using config file: "/etc/X11/XF86Config-4"
(EE) Failed to load module "GLcore" (module does not exist, 0)
Skipping "/usr/X11R6/lib/modules/fonts/libspeedo.a:spencode.o":  No symbols foun d
Symbol __glXActiveScreens from module /usr/X11R6/lib/modules/extensions/libdri.a  is unresolved!
Symbol __glXActiveScreens from module /usr/X11R6/lib/modules/extensions/libdri.a  is unresolved!
(II) Initializing extension GLX
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!

---

