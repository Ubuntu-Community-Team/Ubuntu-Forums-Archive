---
title: "Bluetooth Device Search Not Workin"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by anuraggautam on 2009-11-16
Hi,

I have upgraded my system from 8.04 to 9.04 recently but my bluetooth is not working.

In bluetooth setup device , Device search is not working , it is not able to scan the present available device in the network. Do I need to configure anything more or need to install ?

Need a help from any one regarding this matter.


Thanks in Advance !

---

### Post by Kevbert on 2009-11-16
Have you made the device you want to detect visible to the PC ? The device you are looking for may have a power save option (try turning this off if possible) Also make the PC always visible (at least until you can make connections) by right-clicking on the bluetooth applet (in the top RH corner of the desktop).
You may also need to install gnome-obex-server via Synaptic as this makes file transfers easier. This can be found under Applications-Accessories as Bluetooth File Sharing (run this once bluetooth transmitting on the PC).
A command you can use to scan for devices, via Applications-Accessories-Terminal is ```
hcitool scan
``` You should get a reply in the form
```
00:11:22:33:44:55
``` of any external bluetooth devices.

---

### Post by anuraggautam on 2009-11-17
I got a reply from my system after typing 1st command 

"Device is not available: No such device"

I dunt know why is not detecting blutooth of my system , what to do next ?

---

### Post by Kevbert on 2009-11-17
Was bluetooth working in 8.04 ? What kind of device are you trying to talk to ? Is the bluetooth built in to your computer ? Make and model ? When bluetooth is on do you get a bluetooth icon in the top right-hand corner of the desktop ?

---

### Post by Automat2 on 2009-11-21
> **Kevbert said:**
> Was bluetooth working in 8.04 ? What kind of device are you trying to talk to ? Is the bluetooth built in to your computer ? Make and model ? When bluetooth is on do you get a bluetooth icon in the top right-hand corner of the desktop ?

I've got similar problem. 
[php]jordi@desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 059b:0370 Iomega Corp. 
Bus 001 Device 009: ID 046d:c70a Logitech, Inc. MX5000 Cordless Desktop
Bus 001 Device 008: ID 046d:c70e Logitech, Inc. MX1000 Bluetooth Laser Mouse
Bus 001 Device 006: ID 05a9:4519 OmniVision Technologies, Inc. Webcam Classic
Bus 001 Device 005: ID 08bb:2900 Texas Instruments Japan PCM2900 Audio Codec
Bus 001 Device 004: ID 04a9:220e Canon, Inc. CanoScan N1240U/LiDE 30
Bus 001 Device 003: ID 046d:0b02 Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 001 Device 002: ID 050d:0307 Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jordi@desktop:~$ sudo /etc/init.d/bluetooth status
 * bluetooth is not running[/php]
I have a Logitech BT dongle that worked ok on XP.

---

### Post by anuraggautam on 2009-11-28
I am having same problem on 9.10 ,as i was having it earlier on 8.04.

Can any one tell me what is the solution for this ?

Thanks !

---

### Post by gdesilva on 2009-11-30
Had the same problem.

Try [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8298037](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8298037). This worked for me - thanks to niteshifter.

---

### Post by Aashish1 on 2009-12-30
The above reply do not help much as I do not have any button to change the mode of device.
 
I am using Bluetooth dongle which was working perfectly fine with XP. With Ubuntu 9.10, it gets recognized as the BlueTooth icon comes-up by itself. However, when attempting to search other bluetooth devices (like my Nokia mobile phone) the search goes end-less with no device found.
 
PS: I have turned my mobile phone as 'visible to all'

---

### Post by ffusconi on 2009-12-30
I have the same problem

> I am using Bluetooth dongle which was working perfectly fine with XP. With Ubuntu 9.10, it gets recognized as the BlueTooth icon comes-up by itself. However, when attempting to search other bluetooth devices (like my Nokia mobile phone) the search goes end-less with no device found.

PS: I have turned my mobile phone as 'visible to all' 

I have tried two different USB keys with the same results, both keys seems to work with hcitool:

```
~$ hcitool -i hci0 scan
Scanning ...
	00:1D:E9:7C:81:8E	Nokia 5610d-1
```

but there is no way to send files to the mobile phone nor to receive.
I also tried to install kbluetooth: after several minutes it managed to recognize my phone but when I sent a file the program seemed to hang and I had to kill it.
Here is my /etc/bluetooth/hcid.conf file:

```
#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security auto;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "9879";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}
```

Is there something wrong?

---

### Post by ffusconi on 2010-01-01
found a solution: try to uninstall all bluetooth packages (bluetooth, gnome-bluetooth, kdebluetooth and so on) and blueman too, add the following to /etc/apt/sources.list:

```
deb http://ppa.launchpad.net/blueman/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/blueman/ppa/ubuntu karmic main
``` 

and then 

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install blueman
```

restart your PC and bluetooth works!

Bye, and a Happy New Year

---

### Post by Aashish1 on 2010-01-06
Thanks for the detailed steps, however I am still not able to add bluetooth devices (my nokia mobile is only thing I have). As suggested, I have updated Sources.list and downloaded / upgraded the packages, restarted the machine. And now when I start bluetooth and search for devices, the search is endless and results nothing (as before).

Any sugegstions?

:~$ hcitool scan
Device is not available: No such device

:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0a5c:2021 _**Broadcom Corp. **_
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

PS: This bluetooth device was working with Windows XP without any issues.

---

