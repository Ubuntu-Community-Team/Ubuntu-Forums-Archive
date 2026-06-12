---
title: "Snapstream remote does not work after upgrade from 7.10 to 8.04"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by snsv on 2008-05-11
I upgraded from Gutsy to Hardy.. cant get the snapstream firefly remote to work.. In fact "irw" does not recognize the remote keystrokes. The upgrade was done through the software upgrade icon. Setup Snapstream remote using Myth Control Center. Everything went well.. no errors, but the remote control will not work. Mythtv version is 0.21

While setting up this remote control in Gutsy, I had to change the remote control name to "Snapstream" in hardware.conf and lircd.conf files to make it consistent. Did the same change after this upgrade also after realizing that the remote control is not working

dmesg | grep -i lirc give the following result


admin64@admin64-desktop:/$ dmesg | grep -i lirc
[   42.430454] lirc_dev: IR Remote Control driver registered, major 61 
[   42.431549] lirc_atiusb: no version for "lirc_unregister_plugin" found: kernel tainted.
[   42.440625] lirc_atiusb: USB remote driver for LIRC $Revision: 1.66 $
[   42.440626] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[   42.467490] lirc_dev: lirc_register_plugin: sample_rate: 0
[   42.478160] lirc_atiusb[2]: X10 Wireless Technology Inc USB Receiver on usb1:2
[   42.495181] usbcore: registered new interface driver lirc_atiusb


Not sure what this mean "[   42.431549] lirc_atiusb: no version for "lirc_unregister_plugin" found: kernel tainted." Does this indicate that all the required packages are not installed? or is this because of some incorrect entries in conf files (hardware.conf, lircd.conf etc)


Here is my hardware.conf file

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Snapstream"

# Arguments which will be used when launching lircd
REMOTE_LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
REMOTE_DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
REMOTE_DEVICE="/dev/lirc0"
REMOTE_MODULES="lirc_dev lirc_atiusb"

# Default configuration files for your hardware if any
REMOTE_LIRCD_CONF="atiusb/lircd.conf.atiusb"
LIRCMD_CONF=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
------------------------------------------------

"irw" does not respond to any key press in the remote. Iam on 64bit version

Any help is greatly appreciated.. read through several threads in this form, did not see such an issue reported earlier

Thanks

---

