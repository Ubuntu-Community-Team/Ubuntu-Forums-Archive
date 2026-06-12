---
title: "Alternate CD Install does not see Netgear WG311v2 Wireless Card"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by dlbolton on 2006-12-29
When I go to the Networking applet, I do not see my Netgear WG311v2 wireless networking card listed.  I do see it in the Device Manager, although there is no wlan setting associated with it. I ran the text-mode install on the Ubuntu 6.10 Alternate CD.  My machine is a 900MHz (i think) Duron with 512 MB of ram.

What really confuses me about this is that the Desktop/Live CD sees this card fine!  The reason I used the Alternate CD to install is becase the installer hung up on screen 2/6 (location/time zone).

The help command/menu suggested I should install ndiswrapper.  Am I missing something? Maybe I overlooked something when I was doing the install.  It would seem that the Alternate CD should be able to install a system equivalent to what is on the Desktop CD.

Thanks,

Dave in Denver

---

### Post by dlbolton on 2007-01-04
Since I have solved this issue, thought I would post the details.  Maybe they will help someone else.

1. enter the command: sudo lshw
this is what it showed:
        *-network:0 UNCLAIMED
             description: Network controller
             product: ACX 111 54Mbps Wireless Interface
             vendor: Texas Instruments
             physical id: 6
             bus info: pci@00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:ee020000-ee021fff iomemory:ee000000-ee01ffff irq:201
obviously ubuntu is recognizing my card, but not binding it to a driver (it does not appear in  System -> Administration -> Networking)

2. entered the command:	sudo lspci -v  
this is what it shows:(only the output related to my wireless card)
00:06.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
        Subsystem: Netgear Unknown device 4c00
        Flags: medium devsel, IRQ 201
        Memory at ee020000 (32-bit, non-prefetchable) [size=8K]
        Memory at ee000000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: [40] Power Management version 2

3.  added the following line to /etc/modprobe.d/options (I used vi, but you can use gedit or other text editor):

options acx firmware_ver=1.2.1.34

note this means ubuntu will look for the file tiacx111c16 in /lib/firmware/2.6.17-10-generic/acx/1.2.1.34  
(my kernel version is 2.6.17-10-generic, use the command uname -r to show it)

4. went to acx100.sourceforge.net/wiki/Firmware
downloaded version 1.2.1.34
placed it in /lib/firmware/2.6.17-10-generic/acx/1.2.1.34
renamed it tiacx111c16
then the following commands: 
sudo modprobe -r acx
sudo modprobe acx
sudo iwlist wlan0 scan 

this is what I saw:
 wlan0     Failed to read scan data : Resource temporarily unavailable
hmmm ... this is different (maybe it is not working yet because it needs my SSID)
then entered: sudo dmesg | grep acx
saw the following (new lines only): 
[17245192.648000] usbcore: registered new driver acx_usb
[17251875.916000] usbcore: deregistering driver acx_usb
[17251892.140000] acx: Loaded combined PCI/USB driver, firmware_ver=1.2.1.34
[17251892.140000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[17251892.156000] acx: found ACX111-based wireless network card at 0000:00:06.0, irq:201, phymem1:0xEE020000, phymem2:0xEE000000, mem1:0xccd00000, mem1_size:8192, mem2:0xccdc0000, mem2_size:131072
[17251892.980000] acx: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 (Radia), EEPROM version 0x05, uploaded firmware 'Rev 1.2.1.34' (0x03010101)
[17251892.984000] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 20 and Linux 2.6.17-10-generic
[17251892.984000] usbcore: registered new driver acx_usb


Now wireless network card appears in System -> Administration -> Networking

Entered ESSID and activated. It now appears to be working!

I was so thrilled!

By the way, it has worked flawlessly since.   Thanks to all on this forum for their helpful comments.

---

### Post by Eberulf on 2007-12-01
I have a similar problem, but a different result when I try the same things as above.  I get the following:

jane@jane-desktop:~/Desktop$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

Any suggestions???  I have a WG311v2 as well.

---

