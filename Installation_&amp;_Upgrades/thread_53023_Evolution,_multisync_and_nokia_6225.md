---
title: "Evolution, multisync and nokia 6225"
date: 2005-07-29
forum: Installation &amp; Upgrades
---

### Post by otherpete on 2005-07-29
Hi Folks,
I am a real newbie at this ....first post into a forum ever!
I am trying to sync my nokia 6225 phone with evolution.  The connection between the PC and phone is via a USB/serial converter cable.
Running the command "dmesg | grep -i usb"  I get the following:

usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
uhci_hcd 0000:00:07.2: Intel Corp. 82371AB/EB/MB PIIX4 USB
uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
usb 1-2: new full speed USB device using uhci_hcd and address 2
drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic
usbcore: registered new driver usbserial_generic
usbcore: registered new driver usbserial
drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0
drivers/usb/serial/usb-serial.c: USB Serial support registered for PL-2303
usb 1-2: PL-2303 converter now attached to ttyUSB0
usbcore: registered new driver pl2303
drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver v0.12

By this I assume the usb cable has been detected?

When I start multisync I get the following :

peter@pubuntu:~$ multisync
plugin_API_version
short_name
long_name
plugin_init
[plugin_init:915] here
always_connected
[evo2-sync] DEBUG: start: sync_connect
[evo2-sync] INFORMATION: Loading state from file /home/peter/.multisync/2/localsettings
[evo2-sync] WARNING: File /home/peter/.multisync/2/localsettings does not exist
[evo2-sync] DEBUG: end: sync_connect

I am not sure what the significance of the warning is and whether it is the cause for the syns not to work?

After trying a sync, multisync's log shows the following message:

Failed to get second plugin changes: Unknown error

The second plugin is the phone and I have configured it to run "SyncML".

Any help greatly appreciated.

Peter

---

