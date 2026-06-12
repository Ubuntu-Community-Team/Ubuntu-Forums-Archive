---
title: "Alternate bluetooth adapter?"
date: 2016-04-06
forum: MINT
---

### Post by j1e100 on 2016-04-06
Greetings!

Please help!  I am running Linux Mint 17.3/Cinnamon 64-bit on an Intel NUC D54250WYKH.  I too would like to disable the internal Bluetooth and use an Ariel AI-BTD6610 super long range Bluetooth USB dongle as the primary Bluetooth adapter.  I have tried BOTH methods described here, creating a blacklist file and deleting the files in the firmware directory, but NEITHER method works.  Can you please give me some advice?  I just cannot turn off the internal Bluetooth adapter.

Thanks for your help!

Jeremy


 
The blacklist file I created is named 81-bluetooth-hci.rules.  I tried this in the /etc/udev/rules.d and /lib/udev/rules.d  directories, both one at a time and in both directories.  After each time I placed the file in the different directories, I rebooted the machine.  Each time the internal Bluetooth adapter remained enabled and the command udevadm info -a -p /sys/class/bluetooth/hci1 showed ATTRS{authorized}=="1", despite setting it to &#8220;0&#8221; in the blacklist file.
 
The adapter I want to be the default is on hci0
 
The blacklist file 81-bluetooth-hci.rules is:
 
# Intel based HCI should be disabled
SUBSYSTEM=="usb", ATTRS{idVendor}==&#8220;8087&#8221;, ATTRS{idProduct}==&#8220;07dc&#8221;, ATTR{authorized}="0"

This is a two line file and is word-wrapped only in this posting.
 
Below is A LOT of background information to help trouble-shoot the problem:
 
The lsusb command for the two adapters shows:
 
Bus 002 Device 005: ID 8087:07dc Intel Corp.
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

I want to keep Bus 002 Device 004 and disable Bus 002 Device 005.

Command &#8220;bluez-test-adapter list&#8221; shows:
 
```
[ /org/bluez/503/hci1 ]
   
Name = NUC Built-in Bluetooth  
Powered = 1

Devices = dbus.Array([dbus.ObjectPath('/org/bluez/503/hci1/dev_00_1C_97_FE_A9_94'), dbus.ObjectPath('/org/bluez/503/hci1/dev_CC_C5_0A_06_B0_DA')], signature=dbus.Signature('o'), variant_level=1)
   
DiscoverableTimeout = 0
PairableTimeout = 0   
Discoverable = 0  
Address = 48:51:B7:41:C6:06  
Discovering = 0
Pairable = 1
Class = 0x000000
   
UUIDs = dbus.Array([dbus.String(u'00001000-0000-1000-8000-00805f9b34fb'), dbus.String(u'00001000-0000-1000-8000-00805f9b34fb'), dbus.String(u'00001001-0000-1000-8000-00805f9b34fb'), dbus.String(u'00001001-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000112d-0000-1000-8000-00805f9b34fb'), dbus.String(u'00001112-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000111f-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000111e-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000110c-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000110e-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000110a-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000110b-0000-1000-8000-00805f9b34fb')], signature=dbus.Signature('s'), variant_level=1)
 
[ /org/bluez/503/hci0 ]
   
Name = High Power MedTracker  
Powered = 1
   
Devices = dbus.Array([dbus.ObjectPath('/org/bluez/503/hci0/dev_CC_C5_0A_06_B0_DA'), dbus.ObjectPath('/org/bluez/503/hci0/dev_00_1C_97_FE_A9_94'), dbus.ObjectPath('/org/bluez/503/hci0/dev_00_01_95_20_31_16'), dbus.ObjectPath('/org/bluez/503/hci0/dev_BC_71_72_C1_5E_01')], signature=dbus.Signature('o'), variant_level=1)
   
DiscoverableTimeout = 0
PairableTimeout = 0  
Discoverable = 0
Address = 00:15:83:12:16:87
Discovering = 0
Pairable = 1 
Class = 0x000000
   
UUIDs = dbus.Array([dbus.String(u'00001000-0000-1000-8000-00805f9b34fb'), dbus.String(u'00001001-0000-1000-8000-00805f9b34fb'), dbus.String(u'00001112-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000111f-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000111e-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000110c-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000110e-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000110a-0000-1000-8000-00805f9b34fb'), dbus.String(u'0000110b-0000-1000-8000-00805f9b34fb')], signature=dbus.Signature('s'), variant_level=1)

The command udevadm info -a -p /sys/class/bluetooth/hci1 shows:
 
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.
 
looking at device '/devices/pci0000:00/0000:00:14.0/usb2/2-7/2-7:1.0/bluetooth/hci1':
   
KERNEL=="hci1"
SUBSYSTEM=="bluetooth"
DRIVER==""
ATTR{name}=="NUC Built-in Bluetooth"
ATTR{type}=="BR/EDR"
ATTR{address}=="48:51:b7:41:c6:06"

looking at parent device '/devices/pci0000:00/0000:00:14.0/usb2/2-7/2-7:1.0':

KERNELS=="2-7:1.0"
SUBSYSTEMS=="usb"
DRIVERS=="btusb"
ATTRS{bInterfaceClass}=="e0"
ATTRS{bInterfaceSubClass}=="01"
ATTRS{bInterfaceProtocol}=="01"
ATTRS{bNumEndpoints}=="03"
ATTRS{supports_autosuspend}=="1"
ATTRS{bAlternateSetting}==" 0"
ATTRS{bInterfaceNumber}=="00"

 
looking at parent device '/devices/pci0000:00/0000:00:14.0/usb2/2-7':

KERNELS=="2-7"
SUBSYSTEMS=="usb"
DRIVERS=="usb"
ATTRS{bDeviceSubClass}=="01"
ATTRS{bDeviceProtocol}=="01"
ATTRS{devpath}=="7"
ATTRS{idVendor}=="8087"
ATTRS{speed}=="12"
ATTRS{bNumInterfaces}==" 2"
ATTRS{bConfigurationValue}=="1"
ATTRS{bMaxPacketSize0}=="64"
ATTRS{busnum}=="2"
ATTRS{devnum}=="5"
ATTRS{configuration}==""
ATTRS{bMaxPower}=="100mA"
ATTRS{authorized}=="1"
ATTRS{bmAttributes}=="e0"
ATTRS{bNumConfigurations}=="1"
ATTRS{maxchild}=="0"
ATTRS{bcdDevice}=="0001"
ATTRS{avoid_reset_quirk}=="0"
ATTRS{quirks}=="0x0"
ATTRS{version}==" 2.00"
ATTRS{urbnum}=="101"
ATTRS{ltm_capable}=="no"
ATTRS{removable}=="unknown"
ATTRS{idProduct}=="07dc"
ATTRS{bDeviceClass}=="e0"

looking at parent device '/devices/pci0000:00/0000:00:14.0/usb2':

KERNELS=="usb2"
SUBSYSTEMS=="usb"
DRIVERS=="usb"
ATTRS{bDeviceSubClass}=="00"
ATTRS{bDeviceProtocol}=="01"
ATTRS{devpath}=="0"
ATTRS{idVendor}=="1d6b"
ATTRS{speed}=="480"
ATTRS{bNumInterfaces}==" 1"
ATTRS{bConfigurationValue}=="1"
ATTRS{bMaxPacketSize0}=="64"
ATTRS{authorized_default}=="1"
ATTRS{busnum}=="2"
ATTRS{devnum}=="1"
ATTRS{configuration}==""
ATTRS{bMaxPower}=="0mA"
ATTRS{authorized}=="1"
ATTRS{bmAttributes}=="e0"
ATTRS{bNumConfigurations}=="1"
ATTRS{maxchild}=="9"
ATTRS{bcdDevice}=="0316"
ATTRS{avoid_reset_quirk}=="0"
ATTRS{quirks}=="0x0"
ATTRS{serial}=="0000:00:14.0"
ATTRS{version}==" 2.00"
ATTRS{urbnum}=="66"
ATTRS{ltm_capable}=="no"
ATTRS{manufacturer}=="Linux 3.16.0-38-generic xhci_hcd"
ATTRS{removable}=="unknown"
ATTRS{idProduct}=="0002"
ATTRS{bDeviceClass}=="09"
ATTRS{product}=="xHCI Host Controller"
 
looking at parent device '/devices/pci0000:00/0000:00:14.0':
   
KERNELS=="0000:00:14.0"
SUBSYSTEMS=="pci"
DRIVERS=="xhci_hcd"
ATTRS{irq}=="58"
ATTRS{subsystem_vendor}=="0x8086"
ATTRS{broken_parity_status}=="0"
ATTRS{class}=="0x0c0330"
ATTRS{driver_override}=="(null)"
ATTRS{consistent_dma_mask_bits}=="64"
ATTRS{dma_mask_bits}=="64"
ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,0000000f"
ATTRS{device}=="0x9c31"
ATTRS{enable}=="1"
ATTRS{msi_bus}==""
ATTRS{local_cpulist}=="0-3"  
ATTRS{vendor}=="0x8086" 
ATTRS{subsystem_device}=="0x2054"
ATTRS{numa_node}=="-1" 
ATTRS{d3cold_allowed}=="1"
 
looking at parent device '/devices/pci0000:00':
   
KERNELS=="pci0000:00"
SUBSYSTEMS==""
DRIVERS==""
```

---

### Post by howefield on 2016-04-06
Post moved to its own thread within the "*MINT*" SUB forum and tidied up up with code tags.

---

### Post by jeremy31 on 2016-04-06
Do two MAC addresses appear in ```
hcitool dev
```

---

### Post by j1e100 on 2016-04-06
Yes, the one I want to disable is:
hci1	48:51:B7:41:C6:06

Thanks!

Not sure if you were going to suggest using hciconfig hci1 down, to down the adapter, but that does not work either.  I can indeed down the internal adapter, but blueman-manager still "sees" both adapters and is locked on the internal adapter.  I can try selecting the other adapter over and over again, but it never permits me to select the external adapter.

I should have mentioned that earlier, a big part of my problem is that I can "see" both adapters, but I am never able to select the external adapter.  Occasionally I can start up the bluetooth manager and use the external adapter if I leave the computer sitting for a long period.  Unfortunately, even that has not worked for the last several days.

---

### Post by jeremy31 on 2016-04-07
The udev rule has worked for me in /etc/udev/rules.d 
Not sure why it isn't working for you as it should work after a reboot.
What kernel are you using as it may be possible to change the source code so that the Intel bt is ignored

---

### Post by j1e100 on 2016-04-07
First let me say, thank you so much for your help, not only in this thread, but also in the original thread that gave me so many suggestions in the first place!!!  I agree, after I saw your original suggestion of modifying the rules.d, I saw several others had complete success with that.  It is very strange why it does not work.

I was not aware of how to determine the kernel version, but I saw elsewhere to use name -a.  The execution of that gave:

3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

I deleted the inux machine name from the above.

If you need more info, please let me know.

Once again, thanks so much for your help!!!

---

### Post by jeremy31 on 2016-04-07
See if this works to ignore the internal Intel bluetooth
```
sudo apt-get install git linux-headers-generic build-essential
sudo cp /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko.bak
git clone https://github.com/jeremyb31/bluetooth-3.16.git
cd bluetooth-3.16
cp /usr/src/linux-headers-`uname -r`/.config ./
cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp ./btusb.ko  /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
```

Reboot

---

### Post by j1e100 on 2016-04-07
Jeremy31, I am sorry to say, that alone did not do it, but let me ask a couple questions because there is a chance I was suppose to do more.  Upon completion I had a directory called bluetooth-3.16 in my local directory.  Is this the proper location for the directory?  Did I need to do anything besides reboot after completing the steps you outlined?  I performed your steps as my uid, versus root, and only did the sudo at the steps in your script.  I still had the blacklist file in /etc/udev/rules.d directory.

What exactly did your steps do?  Did this modify the OS, such that any OS updates would modify it, or was this at a lower level, not impacted by updates?

FYI, hcitool dev still shows the internal adapter.

Don't get me wrong, I am incredibly appreciative of all your help!!!!!  What do you suggest next?

Thanks so much!!!

---

### Post by jeremy31 on 2016-04-08
This worked on my Ubuntu 14.04 laptop with the 3.16 kernel and the same bluetooth chip.

This should only be affected by a kernel update as I removed support for Intel and generic bluetooth devices from the btusb module 

[https://github.com/jeremyb31/bluetooth-3.16/commit/fd7274d085495a7fa57a8cfec14fbaa66308211d](https://github.com/jeremyb31/bluetooth-3.16/commit/fd7274d085495a7fa57a8cfec14fbaa66308211d)

Shows the lines that were removed from the source code

Post ```
dkms status; modinfo btusb | grep alias | tail
```

---

### Post by j1e100 on 2016-04-08
Jeremy31,  Did you want me to post the results from the commands in the code?  If so, here it is:

ndiswrapper, 1.59, 3.13.0-85-generic, x86_64: installed
ndiswrapper, 1.59, 3.16.0-38-generic, x86_64: installed (WARNING! Diff between built and installed module!)
ndiswrapper, 1.59, 3.19.0-32-generic, x86_64: installed
virtualbox-guest, 4.3.36, 3.13.0-85-generic, x86_64: installed
virtualbox-guest, 4.3.36, 3.16.0-38-generic, x86_64: installed (original_module exists)
virtualbox-guest, 4.3.36, 3.19.0-32-generic, x86_64: installed (original_module exists)
alias:          usb:v*p*d*dcE0dsc01dp01ic*isc*ip*in*
depends:        bluetooth
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           disable_scofix:Disable fixup of wrong SCO buffer size (bool)
parm:           force_scofix:Force fixup of wrong SCO buffers size (bool)
parm:           reset:Send HCI reset command on initialization (bool)

---

### Post by jeremy31 on 2016-04-08
Yes, just use [code ] before the terminal output and [/code ] after without the extra space

---

### Post by j1e100 on 2016-04-08
_J_eremy31,  So sorry about that!  I looked high and low for a push button, or drop-down, to add code.  In fact, you may have seen how I made multiple edits trying to drop all the smiley faces.  Thanks for the tip!  Sorry you couldn't read it.  Here is the output:

```
ndiswrapper, 1.59, 3.13.0-85-generic, x86_64: installedndiswrapper, 1.59, 3.16.0-38-generic, x86_64: installed (WARNING! Diff between built and installed module!)
ndiswrapper, 1.59, 3.19.0-32-generic, x86_64: installed
virtualbox-guest, 4.3.36, 3.13.0-85-generic, x86_64: installed
virtualbox-guest, 4.3.36, 3.16.0-38-generic, x86_64: installed (original_module exists)
virtualbox-guest, 4.3.36, 3.19.0-32-generic, x86_64: installed (original_module exists)
alias:          usb:v*p*d*dcE0dsc01dp01ic*isc*ip*in*
depends:        bluetooth
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           disable_scofix:Disable fixup of wrong SCO buffer size (bool)
parm:           force_scofix:Force fixup of wrong SCO buffers size (bool)
parm:           reset:Send HCI reset command on initialization (bool)
```

So sorry, just realized I forgot the grep alias. Here is what you originally requested. Once again, thanks so much for your help!!!

```
ndiswrapper, 1.59, 3.13.0-85-generic, x86_64: installedndiswrapper, 1.59, 3.16.0-38-generic, x86_64: installed (WARNING! Diff between built and installed module!)
ndiswrapper, 1.59, 3.19.0-32-generic, x86_64: installed
virtualbox-guest, 4.3.36, 3.13.0-85-generic, x86_64: installed
virtualbox-guest, 4.3.36, 3.16.0-38-generic, x86_64: installed (original_module exists)
virtualbox-guest, 4.3.36, 3.19.0-32-generic, x86_64: installed (original_module exists)
alias:          usb:v05ACp821Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8218d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8213d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0A5Cp21E1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E8Dp763Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v*p*d*dcE0dsc01dp01ic*isc*ip*in*
```

---

### Post by jeremy31 on 2016-04-08
The modinfo is not from the module that should have been built, but that info is from the 3.19 kernel.  Reboot into the 3.16 kernel and see if the internal bluetooth is found with ```
hcitool dev
```

It is possible to make the same modifications to the 3.19 source code

---

### Post by j1e100 on 2016-04-08
Jeremy31,  I was concerned that something had not taken.  I had previously rebooted several times prior to running the commands.  This time I even cycled power.  Btw, just to be sure I did not skip any steps, or make typos, I had taken your original commands an made a script file to execute them.  I did a copy and paste, so there should not have been and typos at that.

Below are the results of the hcitool as well as yet another run of your previous commands.  This time I dropped both the grep as well as the tail, just so you would get all the data.  Note, both adapters are still visible.

As always, thanks so much for ALL your help!!!

```
hcitool dev:

    Devices:	hci1	48:51:B7:41:C6:06
	hci0	00:15:83:12:16:87


dkms status; mod info btusb:


ndiswrapper, 1.59, 3.13.0-85-generic, x86_64: installed
ndiswrapper, 1.59, 3.16.0-38-generic, x86_64: installed (WARNING! Diff between built and installed module!)
ndiswrapper, 1.59, 3.19.0-32-generic, x86_64: installed
virtualbox-guest, 4.3.36, 3.13.0-85-generic, x86_64: installed
virtualbox-guest, 4.3.36, 3.16.0-38-generic, x86_64: installed (original_module exists)
virtualbox-guest, 4.3.36, 3.19.0-32-generic, x86_64: installed (original_module exists)
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/bluetooth/btusb.ko
license:        GPL
version:        0.6
description:    Generic Bluetooth USB driver ver 0.6
author:         Marcel Holtmann <marcel@holtmann.org>
srcversion:     8C57A82C1953B88596CE7F2
alias:          usb:v8087p0A5Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v050Dp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0B05p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0A5Cp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v04CAp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0489p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v19FFp0239d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3404d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v413Cp8197d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17CBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17B5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp2003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE042d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C10p0000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDBp1002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v044Ep3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v044Ep3001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BFp030Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp3800d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8281d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8218d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8213d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0A5Cp21E1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E8Dp763Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v*p*d*dcE0dsc01dp01ic*isc*ip*in*
depends:        bluetooth
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           disable_scofix:Disable fixup of wrong SCO buffer size (bool)
parm:           force_scofix:Force fixup of wrong SCO buffers size (bool)
parm:           reset:Send HCI reset command on initialization (bool)
```

---

### Post by jeremy31 on 2016-04-08
Result is from the 3.19 kernel where post #7 shows you are using 3.16

I will work on a patched version

```
git clone -b jeremyb31-patch-1 https://github.com/jeremyb31/bluetooth-3.19.git
cd bluetooth-3.19
cp /usr/src/linux-headers-`uname -r`/.config ./
cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp ./btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
```

Reboot

---

### Post by j1e100 on 2016-04-08
Unfortunately Jeremy, I was not able to get your patch.  When I ran your commands in a script file, I got the following error:

```
Cloning into 'bluetooth-3.19'...
fatal: Remote branch jeremyb32-patch-1 not found in upstream origin
Unexpected end of command stream
./nobluetooth2.txt: line 2: cd: bluetooth-3.19: No such file or directory
./nobluetooth2.txt: line 5: 993: command not found
```

Jeremy31, I now see why the original patch you gave me did not work.  Since I knew that a bluetooth-3.16 had been created, I went back and reran the script from that point on.  I also ran it as root to ensure that there were no privilege issues and ran it from the bluetooth-3.16 directory.  These are the steps I ran and the errors I got:

```

#cd bluetooth-3.16
cp /usr/src/linux-headers-`uname -r`/.config ./
cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp ./btusb.ko  /lib/modules/$(uname -r)/kernel/drivers/bluetooth/


These are the comments and errors:

make: Entering directory `/usr/src/linux-headers-3.19.0-32-generic'
  CC [M]  /home/jrgugel/nobluetooth/bluetooth-3.16/hci_vhci.o
  CC [M]  /home/jrgugel/nobluetooth/bluetooth-3.16/hci_ldisc.o
  CC [M]  /home/jrgugel/nobluetooth/bluetooth-3.16/hci_h4.o
  CC [M]  /home/jrgugel/nobluetooth/bluetooth-3.16/hci_bcsp.o
  CC [M]  /home/jrgugel/nobluetooth/bluetooth-3.16/hci_ll.o
  CC [M]  /home/jrgugel/nobluetooth/bluetooth-3.16/hci_ath.o
  CC [M]  /home/jrgugel/nobluetooth/bluetooth-3.16/hci_h5.o
  LD [M]  /home/jrgugel/nobluetooth/bluetooth-3.16/hci_uart.o
  CC [M]  /home/jrgugel/nobluetooth/bluetooth-3.16/bcm203x.o
  CC [M]  /home/jrgugel/nobluetooth/bluetooth-3.16/bpa10x.o
  CC [M]  /home/jrgugel/nobluetooth/bluetooth-3.16/bfusb.o
  CC [M]  /home/jrgugel/nobluetooth/bluetooth-3.16/dtl1_cs.o
  CC [M]  /home/jrgugel/nobluetooth/bluetooth-3.16/bt3c_cs.o
  CC [M]  /home/jrgugel/nobluetooth/bluetooth-3.16/bluecard_cs.o
  CC [M]  /home/jrgugel/nobluetooth/bluetooth-3.16/btuart_cs.o
  CC [M]  /home/jrgugel/nobluetooth/bluetooth-3.16/btusb.o
/home/jrgugel/nobluetooth/bluetooth-3.16/btusb.c: In function ‘btusb_intr_complete’:
/home/jrgugel/nobluetooth/bluetooth-3.16/btusb.c:337:3: error: implicit declaration of function ‘hci_recv_fragment’ [-Werror=implicit-function-declaration]
   if (hci_recv_fragment(hdev, HCI_EVENT_PKT,
   ^
cc1: some warnings being treated as errors
make[1]: *** [/home/jrgugel/nobluetooth/bluetooth-3.16/btusb.o] Error 1
make: *** [_module_/home/jrgugel/nobluetooth/bluetooth-3.16] Error 2
make: Leaving directory `/usr/src/linux-headers-3.19.0-32-generic' 
```

---

### Post by j1e100 on 2016-04-09
Jeremy31, WOW WAS I WRONG!!!  I "assumed" that the above errors meant that nothing occurred - WRONG!!!  After doing a reboot, I discovered I have a new kernel!!!  Just too restate, this is the code from post #8, that I reran as root after the step that cd into bluetooth3.16.  That's the good news, the bad news is that I now have NO BlueTooth at all, not even my external.  Nothing shows-up with a "hcitool dev" command nor a "hciconfig -a", however I still see BOTH devices with a "lsusb" command.  I am VERY grateful for killing the internal bluetooth, but I need the external.

The problem is on the fourth and fifth line from the bottom, "parm: ignore_csr:Ignore devices with id 0a12:0001 (bool)" and "parm: ignore_sniffer:Ignore devices with id 0a12:0002 (bool)".  I need the device at 0a12:0001, that's the external Bluetooth adapter.  The adapter I wanted to kill is at 8087:07dc.

I reran the "dkms status; mod info btusb" commands and got the output below.  Hopefully this helps determining what went wrong.  As always, thanks so much for your help!  Sorry, I don't know why the code didn't take ground, maybe it was a permission thing...

```
ndiswrapper, 1.59, 3.13.0-85-generic, x86_64: installedndiswrapper, 1.59, 3.16.0-38-generic, x86_64: installed (WARNING! Diff between built and installed module!)
ndiswrapper, 1.59, 3.19.0-32-generic, x86_64: installed
virtualbox-guest, 4.3.36, 3.13.0-85-generic, x86_64: installed
virtualbox-guest, 4.3.36, 3.16.0-38-generic, x86_64: installed (original_module exists)
virtualbox-guest, 4.3.36, 3.19.0-32-generic, x86_64: installed (original_module exists)
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/bluetooth/btusb.ko
license:        GPL
version:        0.6
description:    Generic Bluetooth USB driver ver 0.6
author:         Marcel Holtmann <marcel@holtmann.org>
srcversion:     B79F0B85218C48A00F011C3
alias:          usb:v8087p0A5Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v050Dp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0B05p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0A5Cp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v04CAp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0489p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v19FFp0239d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3404d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v413Cp8197d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17CBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17B5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp2003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE042d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C10p0000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDBp1002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v044Ep3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v044Ep3001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BFp030Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp3800d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8281d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8218d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8213d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0A5Cp21E1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E8Dp763Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp*d*dc*dsc*dp*icFFisc01ip01in*
depends:        bluetooth
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
parm:           ignore_dga:Ignore devices with id 08fd:0001 (bool)
parm:           ignore_csr:Ignore devices with id 0a12:0001 (bool)
parm:           ignore_sniffer:Ignore devices with id 0a12:0002 (bool)
parm:           disable_scofix:Disable fixup of wrong SCO buffer size (bool)
parm:           force_scofix:Force fixup of wrong SCO buffers size (bool)
parm:           reset:Send HCI reset command on initialization (bool)
```

---

### Post by jeremy31 on 2016-04-09
If you want to use the 3.19 kernel, run the commands from post 15 after booting into the 3.19 kernel, I found a typo

The ignore_csr parameter in 3.16 should only disable the 0a12:0001 if you set the parameter to Y or 1, the USB dongle should still show in ```
hcitool dev
```
The bluetooth developers had some issues with the CSR bluetooth modules for quite some time, later they discovered there were fakes on the market

---

### Post by j1e100 on 2016-04-09
Hi Jeremy31!

I "think" we are getting close, but we are just not there yet...  Let's take one Kernel at a time:

Ver 3.16 -  I am not sure what could have go wrong.  Is there a time or place when I am asked whether or not to enable 0a12?  If so, I did not see it.

Ver 3.19.0-58 - I did not know whether I had a local copy of the 3.19 kernel, so I downloaded a version through the software manager.  Since I was not sure which version of 3.19 to use, I grabbed the latest which was 3.19.0-58.  After installing and rebooting, I ran the commands listed in post 15.  As written, I got an error on line #5, the 993 was not understood.  I assumed that was a typo, so I deleted it and reran the commands.  The commands completed without error, BUT no adapters are found :(

Sooooooooooo.....  Unless the bug is obvious, where does that leave us?  Your comment about CSR is very troubling, especially because this unit is coming from China.  It is the Ariel AI-BTBTD6610:  [http://www.ariel-industry.com/product_show.asp?photoid=1146](http://www.ariel-industry.com/product_show.asp?photoid=1146)  As I once said, I questioned whether the FCC would even approve it and have no idea about the integrity of the module.

Is there anything to check in either the 3.16 or 3.19 as to what could have gone wrong?  Could I have messed up somewhere in the sequence?  For the most part, I have been copying and pasting your commands into a script file so that I don't make typos.  I have been following your commands to the letter with the exception that I su into root before running the script, so that all commands are run as root, not just the ones you wrote sudo for.

I know this has taken a lot of time and energy from you and that you are probably at the end of your line, if not past it.  If it's time to cry Uncle, just let me know.  I would truly understand...

Thanks so very much for all your help!!!

---

### Post by jeremy31 on 2016-04-09
I am not sure where 993 came from and I edited the post with the command.  If you are using a script, run as normal user and the terminal will prompt you for password

---

### Post by j1e100 on 2016-04-09
Jeremy31, I may have misunderstood, but I reran the steps from post 15 assuming more had changed than the removal of 993, for I had already removed 993 on my own, but unfortunately no change.  I ran the hcitool dev command and no devices (adapters) were found.

Any ideas?

Many Thanks!!!

---

### Post by jeremy31 on 2016-04-09
Run ```
lsusb -v > lsusb.txt
```

Find the info for the bluetooth, it should start with ```
[COLOR=#000000]Bus 001 Device 007: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```

It is possible that ```
lsusb -v | grep -A25 0001
``` will get the info.  It seems that there was another patch done last August for the fake CSR chips that isn't in Ubuntu's 4.2 kernel even[/COLOR]

---

### Post by j1e100 on 2016-04-09
Hi Jeremy31, thanks so much for hanging in there with all this!

Here is the result for the search in lsusb -v > lsusb.txt

```

Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

```



Here are the results from lsusb -v | grep -A25 0001

```

Device Status:     0x0001
  Self Powered


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.19
  iManufacturer           3 Linux 3.19.0-58-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1d.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
--
Device Status:     0x0001
  Self Powered


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0003 3.0 root hub
  bcdDevice            3.19
  iManufacturer           3 Linux 3.19.0-58-generic xhci-hcd
  iProduct                2 xHCI Host Controller
  iSerial                 1 0000:00:14.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           31
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
--
Device Status:     0x0001
  Self Powered


Bus 001 Device 005: ID 8087:07dc Intel Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x07dc 
  bcdDevice            0.01
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          177
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
--
Device Status:     0x0001
  Self Powered


Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x0a12 Cambridge Silicon Radio, Ltd
  idProduct          0x0001 Bluetooth Dongle (HCI mode)
  bcdDevice           59.41
  iManufacturer           1 Bolutek Technology Co.,Ltd.
  iProduct                2 Bolutek BTD-6610
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          193
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              200mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
--
Device Status:     0x0001
  Self Powered

```

Once again, thanks for hanging in there through all this!

Jeremy

---

### Post by j1e100 on 2016-04-10
Jeremy31,

In addition to the data above, were you also looking for an alternate Cambridge Silicon Radio driver?  I may have found one.  Are you familiar with the company named Sena?  I have used them for nearly a decade for Bluetooth Serial devices.  I also have one of their Bluetooth adapter dongle's, the Parani-UD100.  The dongle works fine without drivers for PCs and Macs, but need third party drivers for Linux.  They called out the Bluesoleil driver.  When I plugged the dongle into my NUC running Linux Mint and ran the lsusb command, to my surprise it listed Cambridge Silicon Radio, not Bluesoleil.  I am assuming then that Bluesoleil is compatible with CSR, at least for the Sena adapter anyway.

My question to you, do you think it is worth trying the Bluesoleil driver to see if it will work with either my Ariel adapter or the Sena dongle?  Currently the Sena adapter is not visible through the hcitool either.  The only other issue is that the Bluesoleil driver was developed for Ubuntu, not Linux Mint.  At the driver level, is Linux Mint close enough to Ubuntu such that this would work?

Just a thought if we needed a CSR driver or at least if we cannot get the Ariel adapter to work and can use the Sena.  What are your thoughts?

---

### Post by jeremy31 on 2016-04-10
The Sena/Bluesoleil driver may work if it is a recent release as there isn't much difference between Ubuntu 14.04 and Linux Mint 17 other than some programs, artwork, and desktop environment.  If it doesn't work a bug report will need to be filed in order to try to get this supported as I haven't found much on the Bolutec BTD-6610 that the lsusb -v reported is the chip model

---

### Post by j1e100 on 2016-04-10
Hi Jeremy31!

Oh my, it looks like we need to pursue both paths.  The driver I found is for Ubuntu 9.1.  I will keep looking, but both paths may have the best chance of fruit.  Too bad, I thought this might have worked.  I will also contact Sena to see if they know where a driver is.

I cannot begin to thank you for all the time and effort you have put into this!   I know it must be discouraging for you as well...  Although this may not have yielded fruit, please let me know if there is anything I can do for your one say!

Admins, please leave this post open for awhile longer, just in case we are able to find an answer to this.

Thanks Again Jeremy31!

Jeremy

---

### Post by j1e100 on 2016-04-12
Jeremy31,

I have both good news and bad news.  I am now running a configuration were my NUC's internal Bluetooth is turned off and my external Sena adapter is running.  The bad news is, I have absolutely NO IDEA how I did this!  I am running Kernel version 4.4.0-18 and removed the blacklist files under both /etc and /lib.  I have rebooted several times, each time the internal adapter was off.  Since I don't know how I got to this desired state, I am a little apprehensive to do much trouble shooting.  Could the new Kernel be smart enough to turn off the internal adapter when an external adapter is plugged in?

Thanks so much for all your help!  I am at least in a desired configuration!

---

### Post by j1e100 on 2016-04-13
Jeremy31,

I got brave enough today to try some trouble shooting.  I powered down, removed the Sena adapter and rebooted.  The internal adapter remained hidden, displayed with lsusb and hciconfig -a, but hidden with hcitool dev.  With the hciconfig -a, the internal is listed as DOWN INIT RUNNING.  Using hciconfig UP, does not do anything, it remains down.

I really wish I could figure out what I did so that it could help others...  I could not even see anything special when I looked at history.

Jeremy31, do you have any ideas?

---

### Post by jeremy31 on 2016-04-16
Not sure what may have happened unless with the new kernel, powering down and then a cold boot with firmware deleted prevented the Intel bluetooth from working

---

### Post by j1e100 on 2016-04-19
Jeremy31,

  Are your deletions still in place, even with the load of a new Kernel?  If so, I'm sure that's what did it!

---

### Post by jeremy31 on 2016-04-19
My changes should have only affected the old kernel

---

### Post by j1e100 on 2016-04-28
Hi Jeremy31!

I didn't think your mods would have remained, but was not sure.  I don't know the reason why it is working, but it is.  I cannot begin to thank you for all your help that you gave me during this process!!!

---

### Post by jeremy31 on 2016-04-28
Not a problem, that is why I post here and on forums.linuxmint.com

Since it works, please use the thread tools dropdown at the top of the page to mark as solved

---

