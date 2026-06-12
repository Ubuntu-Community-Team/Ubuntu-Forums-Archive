---
title: "nvidia laptop drivers problem"
date: 2013-02-27
forum: Installation &amp; Upgrades
---

### Post by D0Ct0Rh4cK on 2013-02-27
just  a quick text

I've ubuntu 12.10 and I have been trying to install my video card's drivers as far as I have an invidia geforce gt 520M, also been reading google's results as well as searching here, but when I install drivers when I log into my ubuntu's account (after having installed drivers) it just doesn't load status bar, no icons, no shell, nothing I can only double click but all of its interface has gone away, so I see myself constricted to remove again all of invidia's drivers by the command

sudo apt-get remove nvidia*

is there a way get a way out of this so that I can install my video card as far as I think ubuntu's native drivers doesn't get the most out of my videocard's power?

P.S also tried by installing jockey, but things don't change, if you were thinking so.

---

### Post by oldfred on 2013-02-27
# You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic 


Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*

---

### Post by D0Ct0Rh4cK on 2013-03-03
I have been trying several times, I have a geforce GT 520M, tried to install by several methods until I tried the method with binaries, downloaded proper .run from nvidia's official site, installed, then same problem, a gigantic screen with low resolution, and still can't do nothing.... I am desperated... please help....

---

### Post by darkod on 2013-03-03
I assume you tried the basic first. Did you need the nomodeset parameter to load the desktop the first time?

After that if you open Additional Drivers (not sure if the package is there by default in 12.10, it is in 12.04) and activate the driver?

You can try the 12.04 LTS version, it has longer support anyway because it's LTS.

nvidia is very bad with drivers, as you can see even their own drivers don't work in an easy way. In the future don't buy a computer with integrated nvidia for ubuntu. :)

---

### Post by D0Ct0Rh4cK on 2013-03-03
> **darkod said:**
> I assume you tried the basic first. Did you need  the nomodeset parameter to load the desktop the first time?

After that if you open Additional Drivers (not sure if the package is  there by default in 12.10, it is in 12.04) and activate the driver?

You can try the 12.04 LTS version, it has longer support anyway because it's LTS.

nvidia is very bad with drivers, as you can see even their own drivers  don't work in an easy way. In the future don't buy a computer with  integrated nvidia for ubuntu. :smile:

Ok... I post you a screenshot of my additional drivers screen... (ignore the .run file in the desktop as I won't use it)

[IMG]http://img109.imageshack.us/img109/7703/screenshotfrom201303031.png[/IMG]

As you can see, I tried to install experimental one as far as I have seen in the document located here  [https://plus.google.com/u/0/118125769023950376556/posts/bHW91CsG4bP](https://plus.google.com/u/0/118125769023950376556/posts/bHW91CsG4bP)  that my GPU is supported, so I prefered to test this.... but I got an  error and told me to look at /var/log/jockey.log and here I past you its  content

```
2013-03-03 12:20:17,610 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f450e0>
2013-03-03 12:20:19,847 DEBUG: reading modalias file /lib/modules/3.5.0-17-generic/modules.alias
2013-03-03 12:20:19,967 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-03-03 12:20:19,967 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-03-03 12:20:20,022 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-03-03 12:20:20,111 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-03-03 12:20:20,112 DEBUG: Firmware for DVB cards not available
2013-03-03 12:20:20,112 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-03-03 12:20:20,118 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-03-03 12:20:20,131 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-03-03 12:20:20,132 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-03-03 12:20:20,132 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-03-03 12:20:20,135 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-03-03 12:20:20,136 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-03-03 12:20:20,136 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-03-03 12:20:20,136 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-03-03 12:20:20,151 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-03-03 12:20:20,158 DEBUG: Software modem not available
2013-03-03 12:20:20,158 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-03-03 12:20:20,160 WARNING: Invalid custom handler module /usr/share/jockey/handlers/fglrx.py
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 950, in get_handlers
    execfile(mod, symb)
  File "/usr/share/jockey/handlers/fglrx.py", line 11, in <module>
    from NvidiaDetector.alternatives import Alternatives
ImportError: No module named NvidiaDetector.alternatives
2013-03-03 12:20:20,160 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-03-03 12:20:20,162 WARNING: Invalid custom handler module /usr/share/jockey/handlers/nvidia.py
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 950, in get_handlers
    execfile(mod, symb)
  File "/usr/share/jockey/handlers/nvidia.py", line 12, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection
ImportError: No module named NvidiaDetector.nvidiadetector
2013-03-03 12:20:20,163 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-03-03 12:20:20,166 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-03-03 12:20:20,166 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-03-03 12:20:20,179 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-03-03 12:20:20,179 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-03-03 12:20:20,186 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-03-03 12:20:20,190 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-03-03 12:20:20,276 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-03-03 12:20:20,276 DEBUG: all custom handlers loaded
2013-03-03  12:20:20,277 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'pci:v00008086d00001C2Dsv00001043sd00001277bc0Csc03i20')
2013-03-03  12:20:20,595 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-03-03 12:20:20,600 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:20:20,814 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:20,815 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:20:20,815 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:20,815  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-03-03  12:20:20,815 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'pci:v00008086d00001C26sv00001043sd00001277bc0Csc03i20')
2013-03-03  12:20:20,822 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'pci:v00008086d00001C20sv00001043sd00001AC3bc04sc03i00')
2013-03-03  12:20:20,829 DEBUG: searching handler for driver ID {'driver_type':  'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-03-03  12:20:20,829 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:20,830  DEBUG: searching handler for driver ID {'driver_type': 'kernel_module',  'kernel_module': 'snd_hda_intel'}
2013-03-03 12:20:20,830 DEBUG: no  corresponding handler available for {'driver_type': 'kernel_module',  'kernel_module': 'snd_hda_intel', 'jockey_handler':  'KernelModuleHandler'}
2013-03-03 12:20:20,830 DEBUG: querying driver  db <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'platform:microcode')
2013-03-03  12:20:20,831 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'usb:v0BDAp0139d3960dcFFdscFFdpFFicFFisc06ip50')
2013-03-03 12:20:20,874 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rts5139'}
2013-03-03  12:20:20,874 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'rts5139',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:20,874  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-03-03  12:20:20,874 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-03-03 12:20:20,874 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:20:20,874 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:20,874  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'platform:coretemp')
2013-03-03  12:20:20,875 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'acpi:PNP0103:')
2013-03-03  12:20:20,875 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-03-03  12:20:20,875 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'platform:pcspkr')
2013-03-03 12:20:20,876 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-03-03  12:20:20,876 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:20,876 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-03-03  12:20:20,876 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:20,876  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-03-03 12:20:20,876 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:20:20,876 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:20,876 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:20:20,876 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:20,876  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'platform:asus-nb-wmi')
2013-03-03  12:20:20,877 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'wmi:0B3CBB35-E3C2-45ED-91C2-4C5A6D195D1C')
2013-03-03 12:20:20,877 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'asus_nb_wmi'}
2013-03-03  12:20:20,877 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'asus_nb_wmi',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:20,877  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'pci:v00008086d00000116sv00001043sd00001682bc03sc00i00')
2013-03-03 12:20:20,881 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2013-03-03  12:20:20,881 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'i915',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:20,881  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'pci:v00008086d00001C49sv00001043sd00001277bc06sc01i00')
2013-03-03 12:20:20,884 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-03-03  12:20:20,884 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:20,884  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-03-03 12:20:20,884 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2013-03-03  12:20:20,884 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:20,884  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-03-03  12:20:20,885 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2013-03-03  12:20:20,885 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'pci:v00008086d00001C3Asv00001043sd00001277bc07sc80i00')
2013-03-03 12:20:20,888 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2013-03-03  12:20:20,888 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mei',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:20,888  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'pci:v000010DEd00001050sv00001043sd00001682bc03sc00i00')
2013-03-03  12:20:21,127 DEBUG: searching handler for driver ID {'driver_type':  'kernel_module', 'kernel_module': 'nvidia_current', 'package':  'nvidia-current'}
2013-03-03 12:20:21,131 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-03-03 12:20:21,147 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-03-03  12:20:21,147 DEBUG: got handler  kmod:nvidia_current([KernelModuleHandler, nonfree, disabled] NVIDIA  binary Xorg driver, kernel module and VDPAU library)
2013-03-03  12:20:21,147 DEBUG: searching handler for driver ID {'driver_type':  'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package':  'nvidia-experimental-310'}
2013-03-03 12:20:21,150 WARNING: modinfo  for module nvidia_experimental_310 failed: ERROR: modinfo: could not  find module nvidia_experimental_310

2013-03-03 12:20:21,177  WARNING: modinfo for module nvidia_experimental_310 failed: ERROR:  modinfo: could not find module nvidia_experimental_310

2013-03-03  12:20:21,178 DEBUG: got handler  kmod:nvidia_experimental_310([KernelModuleHandler, nonfree, disabled]  Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library)
2013-03-03  12:20:21,178 DEBUG: searching handler for driver ID {'driver_type':  'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package':  'nvidia-current-updates'}
2013-03-03 12:20:21,183 WARNING: modinfo  for module nvidia_current_updates failed: ERROR: modinfo: could not find  module nvidia_current_updates

2013-03-03 12:20:21,199 WARNING:  modinfo for module nvidia_current_updates failed: ERROR: modinfo: could  not find module nvidia_current_updates

2013-03-03 12:20:21,200  DEBUG: got handler kmod:nvidia_current_updates([KernelModuleHandler,  nonfree, disabled] NVIDIA binary Xorg driver, kernel module and VDPAU  library)
2013-03-03 12:20:21,200 DEBUG: searching handler for driver  ID {'driver_type': 'kernel_module', 'kernel_module':  'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-03-03  12:20:21,205 WARNING: modinfo for module nvidia_experimental_304  failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-03-03  12:20:21,226 WARNING: modinfo for module nvidia_experimental_304  failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-03-03  12:20:21,227 DEBUG: got handler  kmod:nvidia_experimental_304([KernelModuleHandler, nonfree, disabled]  Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library)
2013-03-03 12:20:21,228 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-03-03  12:20:21,228 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,228 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-03-03  12:20:21,229 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'nouveau',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,229  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-03-03  12:20:21,229 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'usb:v12D1p1001d0000dc00dsc00dp00ic08isc06ip50')
2013-03-03 12:20:21,273 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-03-03  12:20:21,273 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'uas',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,273  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-03-03 12:20:21,274 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:20:21,274 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,274 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:20:21,274 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,274  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,8C,94,96,A3,A4,A5,A6,A9,B9,BF,D4,D7,E2,E3,E5,E6,ED,EE,F0,F5,F7,1AF,ram4,lsfw')
2013-03-03 12:20:21,274 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:20:21,274 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,274 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:20:21,274 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,274  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-03-03 12:20:21,275 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:20:21,275 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,275  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'acpi:INT0800:')
2013-03-03  12:20:21,275 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-03-03 12:20:21,275 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:20:21,275 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,275  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'acpi:PNP0100:')
2013-03-03  12:20:21,275 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'dmi:bvnAmericanMegatrendsInc.:bvrK53SJ.209:bd03/15/2011:svnASUSTeKComputerInc.:pnK53SJ:pvr1.0:rvnASUSTeKComputerInc.:rnK53SJ:rvr1.0:cvnASUSTeKComputerInc.:ct10:cvr1.0:')
2013-03-03  12:20:21,287 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-03-03  12:20:21,288 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'pci:v00008086d00001C22sv00001043sd00001277bc0Csc05i00')
2013-03-03 12:20:21,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-03-03  12:20:21,291 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,291  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-03-03  12:20:21,291 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'usb:v058FpA014d0001dcEFdsc02dp01ic0Eisc01ip00')
2013-03-03 12:20:21,293 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-03-03  12:20:21,293 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,293  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'pci:v000010ECd00008168sv00001043sd00001277bc02sc00i00')
2013-03-03 12:20:21,301 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-03-03  12:20:21,301 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'r8169',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,301  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2013-03-03 12:20:21,301 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:20:21,302 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,302 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-03-03  12:20:21,302 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'joydev',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,302 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-03-03  12:20:21,302 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'joydev',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,302 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-03-03  12:20:21,302 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'joydev',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,302 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:20:21,302 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,302  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'acpi:PNP0000:')
2013-03-03  12:20:21,302 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'pci:v00008086d00001C03sv00001043sd00001277bc01sc06i01')
2013-03-03  12:20:21,305 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'acpi:ETD0101:PNP0F0E:PNP0F03:PNP0F12:PNP0F0B:')
2013-03-03  12:20:21,306 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'platform:regulatory')
2013-03-03  12:20:21,306 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'usb:v12D1p1001d0000dc00dsc00dp00icFFiscFFipFF')
2013-03-03 12:20:21,307 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'option'}
2013-03-03  12:20:21,307 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'option',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,307  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'acpi:PNP0200:')
2013-03-03  12:20:21,307 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'pci:v00008086d00000104sv00001043sd00001277bc06sc00i00')
2013-03-03  12:20:21,310 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2013-03-03 12:20:21,310  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'usb:v058FpA014d0001dcEFdsc02dp01ic0Eisc02ip00')
2013-03-03  12:20:21,310 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-03-03 12:20:21,311 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:20:21,311 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,311  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-03-03  12:20:21,311 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'pci:v0000168Cd0000002Bsv00001A3Bsd00001089bc02sc80i00')
2013-03-03 12:20:21,321 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2013-03-03  12:20:21,321 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'ath9k',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,321  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'x86cpu:vendor:0000:family:0006:model:002A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,009A,009B,009C,00C0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104')
2013-03-03 12:20:21,326 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-03-03  12:20:21,326 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,326 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-03-03  12:20:21,326 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'microcode',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,326 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-03-03  12:20:21,327 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'coretemp',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,327  DEBUG: searching handler for driver ID {'driver_type': 'kernel_module',  'kernel_module': 'ghash_clmulni_intel'}
2013-03-03 12:20:21,327  DEBUG: no corresponding handler available for {'driver_type':  'kernel_module', 'kernel_module': 'ghash_clmulni_intel',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,327  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-03-03 12:20:21,335 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-03-03  12:20:21,335 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,335 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-03-03  12:20:21,336 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'psmouse',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,336  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-03-03 12:20:21,336 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:20:21,336 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,336 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:20:21,336 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,336  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-03-03  12:20:21,336 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias',  'input:b0003v058FpA014e0001-e0,1,kD4,ramlsfw')
2013-03-03 12:20:21,336 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:20:21,336 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,337 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:20:21,337 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:20:21,337  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1f450e0> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2013-03-03  12:20:21,337 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'pci:v00008086d00001C2Dsv00001043sd00001277bc0Csc03i20')
2013-03-03  12:20:21,337 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-03-03  12:20:21,337 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'acpi:PNP0C02:')
2013-03-03 12:20:21,337  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x229c3b0> about HardwareID('modalias',  'pci:v00008086d00001C26sv00001043sd00001277bc0Csc03i20')
2013-03-03  12:20:21,337 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'pci:v00008086d00001C20sv00001043sd00001AC3bc04sc03i00')
2013-03-03  12:20:21,337 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'platform:microcode')
2013-03-03  12:20:21,337 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'usb:v0BDAp0139d3960dcFFdscFFdpFFicFFisc06ip50')
2013-03-03  12:20:21,337 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-03-03  12:20:21,337 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-03-03 12:20:21,338  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x229c3b0> about HardwareID('modalias',  'platform:coretemp')
2013-03-03 12:20:21,338 DEBUG: querying driver  db <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'acpi:PNP0103:')
2013-03-03 12:20:21,338  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x229c3b0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-03-03  12:20:21,338 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'platform:pcspkr')
2013-03-03  12:20:21,338 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-03-03  12:20:21,338 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'platform:asus-nb-wmi')
2013-03-03  12:20:21,338 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'wmi:0B3CBB35-E3C2-45ED-91C2-4C5A6D195D1C')
2013-03-03  12:20:21,338 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'pci:v00008086d00000116sv00001043sd00001682bc03sc00i00')
2013-03-03  12:20:21,338 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'pci:v00008086d00001C49sv00001043sd00001277bc06sc01i00')
2013-03-03  12:20:21,338 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-03-03  12:20:21,338 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'acpi:PNP0C04:')
2013-03-03 12:20:21,338  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x229c3b0> about HardwareID('modalias',  'acpi:PNP0303:PNP030B:')
2013-03-03 12:20:21,338 DEBUG: querying  driver db <jockey.detection.OpenPrintingDriverDB instance at  0x229c3b0> about HardwareID('modalias',  'pci:v00008086d00001C3Asv00001043sd00001277bc07sc80i00')
2013-03-03  12:20:21,339 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'pci:v000010DEd00001050sv00001043sd00001682bc03sc00i00')
2013-03-03  12:20:21,339 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'acpi:PNP0B00:')
2013-03-03 12:20:21,339  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x229c3b0> about HardwareID('modalias',  'usb:v12D1p1001d0000dc00dsc00dp00ic08isc06ip50')
2013-03-03  12:20:21,339 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-03-03  12:20:21,339 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,8C,94,96,A3,A4,A5,A6,A9,B9,BF,D4,D7,E2,E3,E5,E6,ED,EE,F0,F5,F7,1AF,ram4,lsfw')
2013-03-03  12:20:21,339 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-03-03  12:20:21,339 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'acpi:INT0800:')
2013-03-03 12:20:21,339  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x229c3b0> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-03-03 12:20:21,339  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x229c3b0> about HardwareID('modalias', 'acpi:PNP0100:')
2013-03-03  12:20:21,339 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'dmi:bvnAmericanMegatrendsInc.:bvrK53SJ.209:bd03/15/2011:svnASUSTeKComputerInc.:pnK53SJ:pvr1.0:rvnASUSTeKComputerInc.:rnK53SJ:rvr1.0:cvnASUSTeKComputerInc.:ct10:cvr1.0:')
2013-03-03  12:20:21,339 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-03-03  12:20:21,339 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'pci:v00008086d00001C22sv00001043sd00001277bc0Csc05i00')
2013-03-03  12:20:21,339 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-03-03  12:20:21,339 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'usb:v058FpA014d0001dcEFdsc02dp01ic0Eisc01ip00')
2013-03-03  12:20:21,340 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'pci:v000010ECd00008168sv00001043sd00001277bc02sc00i00')
2013-03-03  12:20:21,340 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2013-03-03  12:20:21,340 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'acpi:PNP0000:')
2013-03-03 12:20:21,340  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x229c3b0> about HardwareID('modalias',  'pci:v00008086d00001C03sv00001043sd00001277bc01sc06i01')
2013-03-03  12:20:21,340 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'acpi:ETD0101:PNP0F0E:PNP0F03:PNP0F12:PNP0F0B:')
2013-03-03  12:20:21,340 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'platform:regulatory')
2013-03-03  12:20:21,340 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'usb:v12D1p1001d0000dc00dsc00dp00icFFiscFFipFF')
2013-03-03  12:20:21,340 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'acpi:PNP0200:')
2013-03-03 12:20:21,340  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x229c3b0> about HardwareID('modalias',  'pci:v00008086d00000104sv00001043sd00001277bc06sc00i00')
2013-03-03  12:20:21,340 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2013-03-03  12:20:21,340 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'usb:v058FpA014d0001dcEFdsc02dp01ic0Eisc02ip00')
2013-03-03  12:20:21,340 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-03-03 12:20:21,340  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x229c3b0> about HardwareID('modalias', 'platform:Fixed  MDIO bus')
2013-03-03 12:20:21,341 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'pci:v0000168Cd0000002Bsv00001A3Bsd00001089bc02sc80i00')
2013-03-03  12:20:21,341 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'x86cpu:vendor:0000:family:0006:model:002A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,009A,009B,009C,00C0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104')
2013-03-03  12:20:21,341 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-03-03  12:20:21,341 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias',  'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-03-03  12:20:21,341 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'acpi:PNP0C01:')
2013-03-03 12:20:21,341  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x229c3b0> about HardwareID('modalias',  'input:b0003v058FpA014e0001-e0,1,kD4,ramlsfw')
2013-03-03  12:20:21,341 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x229c3b0>  about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2013-03-03 12:32:36,327 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x19da0e0>
2013-03-03 12:32:41,568 DEBUG: reading modalias file /lib/modules/3.5.0-17-generic/modules.alias
2013-03-03 12:32:41,704 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-03-03 12:32:41,715 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-03-03 12:32:41,785 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-03-03 12:32:41,904 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-03-03 12:32:41,905 DEBUG: Firmware for DVB cards not available
2013-03-03 12:32:41,905 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-03-03 12:32:41,912 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-03-03 12:32:41,941 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-03-03 12:32:41,942 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-03-03 12:32:41,942 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-03-03 12:32:41,951 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-03-03 12:32:41,952 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-03-03 12:32:41,953 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-03-03 12:32:41,953 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-03-03 12:32:41,983 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-03-03 12:32:42,016 DEBUG: Software modem not available
2013-03-03 12:32:42,017 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-03-03 12:32:42,022 WARNING: Invalid custom handler module /usr/share/jockey/handlers/fglrx.py
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 950, in get_handlers
    execfile(mod, symb)
  File "/usr/share/jockey/handlers/fglrx.py", line 11, in <module>
    from NvidiaDetector.alternatives import Alternatives
ImportError: No module named NvidiaDetector.alternatives
2013-03-03 12:32:42,023 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-03-03 12:32:42,028 WARNING: Invalid custom handler module /usr/share/jockey/handlers/nvidia.py
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 950, in get_handlers
    execfile(mod, symb)
  File "/usr/share/jockey/handlers/nvidia.py", line 12, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection
ImportError: No module named NvidiaDetector.nvidiadetector
2013-03-03 12:32:42,029 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-03-03 12:32:42,035 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-03-03 12:32:42,035 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-03-03 12:32:42,063 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-03-03 12:32:42,064 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-03-03 12:32:42,075 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-03-03 12:32:42,084 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-03-03 12:32:42,231 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-03-03 12:32:42,232 DEBUG: all custom handlers loaded
2013-03-03  12:32:42,232 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'pci:v00008086d00001C2Dsv00001043sd00001277bc0Csc03i20')
2013-03-03  12:32:42,512 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-03-03 12:32:42,516 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:32:42,713 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:42,713 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:32:42,714 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:42,714  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-03-03  12:32:42,714 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'pci:v00008086d00001C26sv00001043sd00001277bc0Csc03i20')
2013-03-03  12:32:42,718 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'pci:v00008086d00001C20sv00001043sd00001AC3bc04sc03i00')
2013-03-03  12:32:42,721 DEBUG: searching handler for driver ID {'driver_type':  'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-03-03  12:32:42,721 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:42,721  DEBUG: searching handler for driver ID {'driver_type': 'kernel_module',  'kernel_module': 'snd_hda_intel'}
2013-03-03 12:32:42,721 DEBUG: no  corresponding handler available for {'driver_type': 'kernel_module',  'kernel_module': 'snd_hda_intel', 'jockey_handler':  'KernelModuleHandler'}
2013-03-03 12:32:42,721 DEBUG: querying driver  db <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'platform:microcode')
2013-03-03  12:32:42,722 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'usb:v0BDAp0139d3960dcFFdscFFdpFFicFFisc06ip50')
2013-03-03 12:32:42,748 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rts5139'}
2013-03-03  12:32:42,748 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'rts5139',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:42,748  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-03-03  12:32:42,748 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-03-03 12:32:42,748 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:32:42,749 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:42,749  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'platform:coretemp')
2013-03-03  12:32:42,749 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'acpi:PNP0103:')
2013-03-03  12:32:42,749 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-03-03  12:32:42,749 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'platform:pcspkr')
2013-03-03 12:32:42,750 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-03-03  12:32:42,750 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:42,750 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-03-03  12:32:42,750 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:42,750  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-03-03 12:32:42,750 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:32:42,750 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:42,750 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:32:42,751 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:42,751  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'platform:asus-nb-wmi')
2013-03-03  12:32:42,751 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'wmi:0B3CBB35-E3C2-45ED-91C2-4C5A6D195D1C')
2013-03-03 12:32:42,751 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'asus_nb_wmi'}
2013-03-03  12:32:42,751 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'asus_nb_wmi',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:42,751  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'pci:v00008086d00000116sv00001043sd00001682bc03sc00i00')
2013-03-03 12:32:42,754 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2013-03-03  12:32:42,755 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'i915',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:42,755  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'pci:v00008086d00001C49sv00001043sd00001277bc06sc01i00')
2013-03-03 12:32:42,758 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-03-03  12:32:42,758 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:42,758  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-03-03 12:32:42,758 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2013-03-03  12:32:42,758 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:42,758  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-03-03  12:32:42,758 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2013-03-03  12:32:42,758 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'pci:v00008086d00001C3Asv00001043sd00001277bc07sc80i00')
2013-03-03 12:32:42,761 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2013-03-03  12:32:42,761 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mei',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:42,761  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'pci:v000010DEd00001050sv00001043sd00001682bc03sc00i00')
2013-03-03  12:32:42,988 DEBUG: searching handler for driver ID {'driver_type':  'kernel_module', 'kernel_module': 'nvidia_current', 'package':  'nvidia-current'}
2013-03-03 12:32:42,994 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-03-03 12:32:43,029 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-03-03  12:32:43,030 DEBUG: got handler  kmod:nvidia_current([KernelModuleHandler, nonfree, disabled] NVIDIA  binary Xorg driver, kernel module and VDPAU library)
2013-03-03  12:32:43,030 DEBUG: searching handler for driver ID {'driver_type':  'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package':  'nvidia-experimental-310'}
2013-03-03 12:32:43,037 WARNING: modinfo  for module nvidia_experimental_310 failed: ERROR: modinfo: could not  find module nvidia_experimental_310

2013-03-03 12:32:43,071  WARNING: modinfo for module nvidia_experimental_310 failed: ERROR:  modinfo: could not find module nvidia_experimental_310

2013-03-03  12:32:43,073 DEBUG: got handler  kmod:nvidia_experimental_310([KernelModuleHandler, nonfree, disabled]  Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library)
2013-03-03  12:32:43,073 DEBUG: searching handler for driver ID {'driver_type':  'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package':  'nvidia-current-updates'}
2013-03-03 12:32:43,080 WARNING: modinfo  for module nvidia_current_updates failed: ERROR: modinfo: could not find  module nvidia_current_updates

2013-03-03 12:32:43,116 WARNING:  modinfo for module nvidia_current_updates failed: ERROR: modinfo: could  not find module nvidia_current_updates

2013-03-03 12:32:43,117  DEBUG: got handler kmod:nvidia_current_updates([KernelModuleHandler,  nonfree, disabled] NVIDIA binary Xorg driver, kernel module and VDPAU  library)
2013-03-03 12:32:43,118 DEBUG: searching handler for driver  ID {'driver_type': 'kernel_module', 'kernel_module':  'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-03-03  12:32:43,124 WARNING: modinfo for module nvidia_experimental_304  failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-03-03  12:32:43,161 WARNING: modinfo for module nvidia_experimental_304  failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-03-03  12:32:43,162 DEBUG: got handler  kmod:nvidia_experimental_304([KernelModuleHandler, nonfree, disabled]  Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library)
2013-03-03 12:32:43,162 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-03-03  12:32:43,163 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,163 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-03-03  12:32:43,163 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'nouveau',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,164  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-03-03  12:32:43,164 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'usb:v12D1p1001d0000dc00dsc00dp00ic08isc06ip50')
2013-03-03 12:32:43,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-03-03  12:32:43,213 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'uas',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,213  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-03-03 12:32:43,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:32:43,213 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:32:43,213 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,213  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,8C,94,96,A3,A4,A5,A6,A9,B9,BF,D4,D7,E2,E3,E5,E6,ED,EE,F0,F5,F7,1AF,ram4,lsfw')
2013-03-03 12:32:43,214 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:32:43,214 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,214 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:32:43,214 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,214  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-03-03 12:32:43,214 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:32:43,214 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,214  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'acpi:INT0800:')
2013-03-03  12:32:43,214 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-03-03 12:32:43,214 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:32:43,214 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,215  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'acpi:PNP0100:')
2013-03-03  12:32:43,215 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'dmi:bvnAmericanMegatrendsInc.:bvrK53SJ.209:bd03/15/2011:svnASUSTeKComputerInc.:pnK53SJ:pvr1.0:rvnASUSTeKComputerInc.:rnK53SJ:rvr1.0:cvnASUSTeKComputerInc.:ct10:cvr1.0:')
2013-03-03  12:32:43,227 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-03-03  12:32:43,227 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'pci:v00008086d00001C22sv00001043sd00001277bc0Csc05i00')
2013-03-03 12:32:43,230 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-03-03  12:32:43,230 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,231  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-03-03  12:32:43,231 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'usb:v058FpA014d0001dcEFdsc02dp01ic0Eisc01ip00')
2013-03-03 12:32:43,233 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-03-03  12:32:43,233 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,233  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'pci:v000010ECd00008168sv00001043sd00001277bc02sc00i00')
2013-03-03 12:32:43,240 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-03-03  12:32:43,241 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'r8169',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,241  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2013-03-03 12:32:43,241 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:32:43,241 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,241 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-03-03  12:32:43,241 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'joydev',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,241 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-03-03  12:32:43,241 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'joydev',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,241 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-03-03  12:32:43,241 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'joydev',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,242 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:32:43,242 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,242  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'acpi:PNP0000:')
2013-03-03  12:32:43,242 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'pci:v00008086d00001C03sv00001043sd00001277bc01sc06i01')
2013-03-03  12:32:43,245 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'acpi:ETD0101:PNP0F0E:PNP0F03:PNP0F12:PNP0F0B:')
2013-03-03  12:32:43,245 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'platform:regulatory')
2013-03-03  12:32:43,245 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'usb:v12D1p1001d0000dc00dsc00dp00icFFiscFFipFF')
2013-03-03 12:32:43,246 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'option'}
2013-03-03  12:32:43,246 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'option',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,246  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'acpi:PNP0200:')
2013-03-03  12:32:43,246 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'pci:v00008086d00000104sv00001043sd00001277bc06sc00i00')
2013-03-03  12:32:43,249 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2013-03-03 12:32:43,249  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'usb:v058FpA014d0001dcEFdsc02dp01ic0Eisc02ip00')
2013-03-03  12:32:43,250 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-03-03 12:32:43,250 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:32:43,250 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,250  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-03-03  12:32:43,250 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'pci:v0000168Cd0000002Bsv00001A3Bsd00001089bc02sc80i00')
2013-03-03 12:32:43,260 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2013-03-03  12:32:43,260 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'ath9k',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,260  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'x86cpu:vendor:0000:family:0006:model:002A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,009A,009B,009C,00C0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104')
2013-03-03 12:32:43,265 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-03-03  12:32:43,265 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,265 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-03-03  12:32:43,265 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'microcode',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,265 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-03-03  12:32:43,265 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'coretemp',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,265  DEBUG: searching handler for driver ID {'driver_type': 'kernel_module',  'kernel_module': 'ghash_clmulni_intel'}
2013-03-03 12:32:43,265  DEBUG: no corresponding handler available for {'driver_type':  'kernel_module', 'kernel_module': 'ghash_clmulni_intel',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,265  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-03-03 12:32:43,273 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-03-03  12:32:43,273 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,273 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-03-03  12:32:43,273 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'psmouse',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,273  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-03-03 12:32:43,273 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:32:43,273 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,273 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:32:43,273 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,274  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-03-03  12:32:43,274 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias',  'input:b0003v058FpA014e0001-e0,1,kD4,ramlsfw')
2013-03-03 12:32:43,274 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:32:43,274 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,274 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:32:43,274 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:32:43,274  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x19da0e0> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2013-03-03  12:32:43,274 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'pci:v00008086d00001C2Dsv00001043sd00001277bc0Csc03i20')
2013-03-03  12:32:43,274 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-03-03  12:32:43,274 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'acpi:PNP0C02:')
2013-03-03 12:32:43,274  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x1d313b0> about HardwareID('modalias',  'pci:v00008086d00001C26sv00001043sd00001277bc0Csc03i20')
2013-03-03  12:32:43,274 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'pci:v00008086d00001C20sv00001043sd00001AC3bc04sc03i00')
2013-03-03  12:32:43,275 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'platform:microcode')
2013-03-03  12:32:43,275 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'usb:v0BDAp0139d3960dcFFdscFFdpFFicFFisc06ip50')
2013-03-03  12:32:43,275 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-03-03  12:32:43,275 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-03-03 12:32:43,275  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x1d313b0> about HardwareID('modalias',  'platform:coretemp')
2013-03-03 12:32:43,275 DEBUG: querying driver  db <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'acpi:PNP0103:')
2013-03-03 12:32:43,275  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x1d313b0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-03-03  12:32:43,275 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'platform:pcspkr')
2013-03-03  12:32:43,275 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-03-03  12:32:43,275 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'platform:asus-nb-wmi')
2013-03-03  12:32:43,275 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'wmi:0B3CBB35-E3C2-45ED-91C2-4C5A6D195D1C')
2013-03-03  12:32:43,275 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'pci:v00008086d00000116sv00001043sd00001682bc03sc00i00')
2013-03-03  12:32:43,275 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'pci:v00008086d00001C49sv00001043sd00001277bc06sc01i00')
2013-03-03  12:32:43,275 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-03-03  12:32:43,275 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'acpi:PNP0C04:')
2013-03-03 12:32:43,276  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x1d313b0> about HardwareID('modalias',  'acpi:PNP0303:PNP030B:')
2013-03-03 12:32:43,276 DEBUG: querying  driver db <jockey.detection.OpenPrintingDriverDB instance at  0x1d313b0> about HardwareID('modalias',  'pci:v00008086d00001C3Asv00001043sd00001277bc07sc80i00')
2013-03-03  12:32:43,276 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'pci:v000010DEd00001050sv00001043sd00001682bc03sc00i00')
2013-03-03  12:32:43,276 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'acpi:PNP0B00:')
2013-03-03 12:32:43,276  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x1d313b0> about HardwareID('modalias',  'usb:v12D1p1001d0000dc00dsc00dp00ic08isc06ip50')
2013-03-03  12:32:43,276 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-03-03  12:32:43,276 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,8C,94,96,A3,A4,A5,A6,A9,B9,BF,D4,D7,E2,E3,E5,E6,ED,EE,F0,F5,F7,1AF,ram4,lsfw')
2013-03-03  12:32:43,276 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-03-03  12:32:43,276 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'acpi:INT0800:')
2013-03-03 12:32:43,276  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x1d313b0> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-03-03 12:32:43,276  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x1d313b0> about HardwareID('modalias', 'acpi:PNP0100:')
2013-03-03  12:32:43,276 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'dmi:bvnAmericanMegatrendsInc.:bvrK53SJ.209:bd03/15/2011:svnASUSTeKComputerInc.:pnK53SJ:pvr1.0:rvnASUSTeKComputerInc.:rnK53SJ:rvr1.0:cvnASUSTeKComputerInc.:ct10:cvr1.0:')
2013-03-03  12:32:43,276 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-03-03  12:32:43,276 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'pci:v00008086d00001C22sv00001043sd00001277bc0Csc05i00')
2013-03-03  12:32:43,277 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-03-03  12:32:43,277 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'usb:v058FpA014d0001dcEFdsc02dp01ic0Eisc01ip00')
2013-03-03  12:32:43,277 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'pci:v000010ECd00008168sv00001043sd00001277bc02sc00i00')
2013-03-03  12:32:43,277 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2013-03-03  12:32:43,277 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'acpi:PNP0000:')
2013-03-03 12:32:43,277  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x1d313b0> about HardwareID('modalias',  'pci:v00008086d00001C03sv00001043sd00001277bc01sc06i01')
2013-03-03  12:32:43,277 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'acpi:ETD0101:PNP0F0E:PNP0F03:PNP0F12:PNP0F0B:')
2013-03-03  12:32:43,277 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'platform:regulatory')
2013-03-03  12:32:43,277 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'usb:v12D1p1001d0000dc00dsc00dp00icFFiscFFipFF')
2013-03-03  12:32:43,277 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'acpi:PNP0200:')
2013-03-03 12:32:43,277  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x1d313b0> about HardwareID('modalias',  'pci:v00008086d00000104sv00001043sd00001277bc06sc00i00')
2013-03-03  12:32:43,277 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2013-03-03  12:32:43,277 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'usb:v058FpA014d0001dcEFdsc02dp01ic0Eisc02ip00')
2013-03-03  12:32:43,277 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-03-03 12:32:43,277  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x1d313b0> about HardwareID('modalias', 'platform:Fixed  MDIO bus')
2013-03-03 12:32:43,278 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'pci:v0000168Cd0000002Bsv00001A3Bsd00001089bc02sc80i00')
2013-03-03  12:32:43,278 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'x86cpu:vendor:0000:family:0006:model:002A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,009A,009B,009C,00C0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104')
2013-03-03  12:32:43,278 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-03-03  12:32:43,278 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias',  'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-03-03  12:32:43,278 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'acpi:PNP0C01:')
2013-03-03 12:32:43,278  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x1d313b0> about HardwareID('modalias',  'input:b0003v058FpA014e0001-e0,1,kD4,ramlsfw')
2013-03-03  12:32:43,278 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x1d313b0>  about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2013-03-03 12:33:28,427 DEBUG: Installing package: nvidia-current
2013-03-03 12:33:29,181 DEBUG: download progress <Package: name:'nvidia-current' architecture='amd64' id:16003L> 0.000000
2013-03-03 12:33:29,182 DEBUG: download progress <Package: name:'nvidia-current' architecture='amd64' id:16003L> 0.000000
2013-03-03 12:33:29,184 DEBUG: download progress <Package: name:'nvidia-current' architecture='amd64' id:16003L> 0.000000
2013-03-03 12:33:29,185 DEBUG: download progress <Package: name:'nvidia-current' architecture='amd64' id:16003L> 0.000000
2013-03-03  12:33:29,186 ERROR: Package fetching failed: Failed to fetch  http://it.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu1.1_all.deb  Could not resolve 'it.archive.ubuntu.com'
Failed to fetch  http://it.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.18.4-2_amd64.deb  Could not resolve 'it.archive.ubuntu.com'
Failed to fetch  http://it.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-current_304.51.really.304.43-0ubuntu1_amd64.deb  Could not resolve 'it.archive.ubuntu.com'
Failed to fetch  http://it.archive.ubuntu.com/ubuntu/pool/main/s/screen-resolution-extra/screen-resolution-extra_0.15_all.deb  Could not resolve 'it.archive.ubuntu.com'
Failed to fetch  http://it.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_304.51-0ubuntu2_amd64.deb  Could not resolve 'it.archive.ubuntu.com'

2013-03-03 12:33:29,303 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-03-03 12:33:29,304 WARNING: /sys/module/nvidia_current/drivers does not exist, cannot rebind nvidia_current driver
2013-03-03 12:35:23,277 DEBUG: Installing package: nvidia-current-updates
2013-03-03  12:35:23,962 DEBUG: download progress <Package:  name:'nvidia-current-updates' architecture='amd64' id:16005L>  0.000000
2013-03-03 12:35:23,963 DEBUG: download progress  <Package: name:'nvidia-current-updates' architecture='amd64'  id:16005L> 0.000000
2013-03-03 12:35:23,965 DEBUG: download  progress <Package: name:'nvidia-current-updates' architecture='amd64'  id:16005L> 0.000000
2013-03-03 12:35:23,965 DEBUG: download  progress <Package: name:'nvidia-current-updates' architecture='amd64'  id:16005L> 0.000000
2013-03-03 12:35:23,966 ERROR: Package  fetching failed: Failed to fetch  http://it.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu1.1_all.deb  Could not resolve 'it.archive.ubuntu.com'
Failed to fetch  http://it.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.18.4-2_amd64.deb  Could not resolve 'it.archive.ubuntu.com'
Failed to fetch  http://it.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-updates/nvidia-current-updates_304.51-0ubuntu1_amd64.deb  Could not resolve 'it.archive.ubuntu.com'
Failed to fetch  http://it.archive.ubuntu.com/ubuntu/pool/main/s/screen-resolution-extra/screen-resolution-extra_0.15_all.deb  Could not resolve 'it.archive.ubuntu.com'
Failed to fetch  http://it.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-settings-updates/nvidia-settings-updates_304.51-0ubuntu2_amd64.deb  Could not resolve 'it.archive.ubuntu.com'

2013-03-03  12:35:24,065 WARNING: modinfo for module nvidia_current_updates failed:  ERROR: modinfo: could not find module nvidia_current_updates

2013-03-03  12:35:24,066 WARNING: /sys/module/nvidia_current_updates/drivers does  not exist, cannot rebind nvidia_current_updates driver
2013-03-03 12:51:32,428 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1dcc248>
2013-03-03 12:51:37,673 DEBUG: reading modalias file /lib/modules/3.5.0-17-generic/modules.alias
2013-03-03 12:51:37,810 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-03-03 12:51:37,821 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-03-03 12:51:37,902 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-03-03 12:51:38,022 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-03-03 12:51:38,024 DEBUG: Firmware for DVB cards not available
2013-03-03 12:51:38,024 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-03-03 12:51:38,031 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-03-03 12:51:38,060 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-03-03 12:51:38,061 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-03-03 12:51:38,061 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-03-03 12:51:38,070 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-03-03 12:51:38,071 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-03-03 12:51:38,071 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-03-03 12:51:38,071 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-03-03 12:51:38,099 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-03-03 12:51:38,134 DEBUG: Software modem not available
2013-03-03 12:51:38,134 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-03-03 12:51:38,139 WARNING: Invalid custom handler module /usr/share/jockey/handlers/fglrx.py
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 950, in get_handlers
    execfile(mod, symb)
  File "/usr/share/jockey/handlers/fglrx.py", line 11, in <module>
    from NvidiaDetector.alternatives import Alternatives
ImportError: No module named NvidiaDetector.alternatives
2013-03-03 12:51:38,141 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-03-03 12:51:38,146 WARNING: Invalid custom handler module /usr/share/jockey/handlers/nvidia.py
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 950, in get_handlers
    execfile(mod, symb)
  File "/usr/share/jockey/handlers/nvidia.py", line 12, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection
ImportError: No module named NvidiaDetector.nvidiadetector
2013-03-03 12:51:38,147 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-03-03 12:51:38,154 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-03-03 12:51:38,154 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-03-03 12:51:38,185 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-03-03 12:51:38,186 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-03-03 12:51:38,197 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-03-03 12:51:38,206 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-03-03 12:51:38,318 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-03-03 12:51:38,318 DEBUG: all custom handlers loaded
2013-03-03  12:51:38,318 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'pci:v00008086d00001C2Dsv00001043sd00001277bc0Csc03i20')
2013-03-03  12:51:38,588 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-03-03 12:51:38,593 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:51:38,781 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,781 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:51:38,781 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,781  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-03-03  12:51:38,781 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'pci:v00008086d00001C26sv00001043sd00001277bc0Csc03i20')
2013-03-03  12:51:38,785 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'pci:v00008086d00001C20sv00001043sd00001AC3bc04sc03i00')
2013-03-03  12:51:38,788 DEBUG: searching handler for driver ID {'driver_type':  'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-03-03  12:51:38,788 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,788  DEBUG: searching handler for driver ID {'driver_type': 'kernel_module',  'kernel_module': 'snd_hda_intel'}
2013-03-03 12:51:38,788 DEBUG: no  corresponding handler available for {'driver_type': 'kernel_module',  'kernel_module': 'snd_hda_intel', 'jockey_handler':  'KernelModuleHandler'}
2013-03-03 12:51:38,788 DEBUG: querying driver  db <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'platform:microcode')
2013-03-03  12:51:38,788 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'usb:v0BDAp0139d3960dcFFdscFFdpFFicFFisc06ip50')
2013-03-03 12:51:38,815 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rts5139'}
2013-03-03  12:51:38,815 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'rts5139',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,815  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-03-03  12:51:38,815 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-03-03 12:51:38,815 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:51:38,815 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,815  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'platform:coretemp')
2013-03-03  12:51:38,816 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'acpi:PNP0100:')
2013-03-03  12:51:38,816 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-03-03  12:51:38,816 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'platform:pcspkr')
2013-03-03 12:51:38,817 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-03-03  12:51:38,817 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,817 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-03-03  12:51:38,817 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,817  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-03-03 12:51:38,817 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:51:38,817 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,817 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:51:38,817 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,817  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'platform:asus-nb-wmi')
2013-03-03  12:51:38,818 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'wmi:0B3CBB35-E3C2-45ED-91C2-4C5A6D195D1C')
2013-03-03 12:51:38,818 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'asus_nb_wmi'}
2013-03-03  12:51:38,818 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'asus_nb_wmi',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,818  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'pci:v00008086d00000116sv00001043sd00001682bc03sc00i00')
2013-03-03 12:51:38,821 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2013-03-03  12:51:38,821 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'i915',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,821  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'pci:v00008086d00001C03sv00001043sd00001277bc01sc06i01')
2013-03-03  12:51:38,824 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-03-03 12:51:38,824 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2013-03-03  12:51:38,824 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,824  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-03-03  12:51:38,824 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2013-03-03  12:51:38,825 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'pci:v00008086d00001C3Asv00001043sd00001277bc07sc80i00')
2013-03-03 12:51:38,827 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2013-03-03  12:51:38,827 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mei',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,828  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'pci:v00008086d00001C49sv00001043sd00001277bc06sc01i00')
2013-03-03 12:51:38,830 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-03-03  12:51:38,831 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,831  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2013-03-03  12:51:38,831 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'usb:v058FpA014d0001dcEFdsc02dp01ic0Eisc02ip00')
2013-03-03  12:51:38,832 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'usb:v045Ep0737d0104dc00dsc00dp00ic03isc01ip02')
2013-03-03 12:51:38,880 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-03-03  12:51:38,880 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'usbhid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,880 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-03-03  12:51:38,880 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,880  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-03-03 12:51:38,880 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:51:38,880 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,880 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:51:38,881 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,881  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,8C,94,96,A3,A4,A5,A6,A9,B9,BF,D4,D7,E2,E3,E5,E6,ED,EE,F0,F5,F7,1AF,ram4,lsfw')
2013-03-03 12:51:38,881 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:51:38,881 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,881 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:51:38,881 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,881  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-03-03 12:51:38,881 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:51:38,881 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,881  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'acpi:ETD0101:PNP0F0E:PNP0F03:PNP0F12:PNP0F0B:')
2013-03-03  12:51:38,881 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-03-03 12:51:38,882 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:51:38,882 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,882  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'acpi:PNP0000:')
2013-03-03  12:51:38,882 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'dmi:bvnAmericanMegatrendsInc.:bvrK53SJ.209:bd03/15/2011:svnASUSTeKComputerInc.:pnK53SJ:pvr1.0:rvnASUSTeKComputerInc.:rnK53SJ:rvr1.0:cvnASUSTeKComputerInc.:ct10:cvr1.0:')
2013-03-03  12:51:38,894 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-03-03  12:51:38,894 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'input:b0003v045Ep0737e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2013-03-03 12:51:38,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:51:38,894 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:51:38,894 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,895  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'usb:v12D1p1001d0000dc00dsc00dp00icFFiscFFipFF')
2013-03-03 12:51:38,933 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'option'}
2013-03-03  12:51:38,933 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'option',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,933  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-03-03  12:51:38,933 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'usb:v058FpA014d0001dcEFdsc02dp01ic0Eisc01ip00')
2013-03-03 12:51:38,933 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-03-03  12:51:38,933 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,934  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'pci:v0000168Cd0000002Bsv00001A3Bsd00001089bc02sc80i00')
2013-03-03 12:51:38,943 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2013-03-03  12:51:38,943 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'ath9k',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,943  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2013-03-03 12:51:38,943 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:51:38,944 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,944 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-03-03  12:51:38,944 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'joydev',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,944 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-03-03  12:51:38,944 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'joydev',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,944 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-03-03  12:51:38,944 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'joydev',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,944 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:51:38,944 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,944  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'acpi:INT0800:')
2013-03-03  12:51:38,944 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'pci:v000010ECd00008168sv00001043sd00001277bc02sc00i00')
2013-03-03 12:51:38,952 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-03-03  12:51:38,952 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'r8169',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,952  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-03-03  12:51:38,952 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'platform:regulatory')
2013-03-03  12:51:38,953 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'usb:v12D1p1001d0000dc00dsc00dp00ic08isc06ip50')
2013-03-03 12:51:38,954 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-03-03  12:51:38,954 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'uas',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,954  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'acpi:PNP0103:')
2013-03-03  12:51:38,954 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'pci:v00008086d00000104sv00001043sd00001277bc06sc00i00')
2013-03-03  12:51:38,957 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'hid:b0003g0001v0000045Ep00000737')
2013-03-03 12:51:38,999 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic'}
2013-03-03  12:51:38,999 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:38,999  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'usb:v05E3p0606d0702dc09dsc00dp00ic09isc00ip00')
2013-03-03  12:51:39,001 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-03-03 12:51:39,001 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:51:39,001 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:39,002  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-03-03  12:51:39,002 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-03-03  12:51:39,002 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'pci:v000010DEd00001050sv00001043sd00001682bc03sc00i00')
2013-03-03  12:51:39,235 DEBUG: searching handler for driver ID {'driver_type':  'kernel_module', 'kernel_module': 'nvidia_current', 'package':  'nvidia-current'}
2013-03-03 12:51:39,241 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-03-03 12:51:39,276 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-03-03  12:51:39,277 DEBUG: got handler  kmod:nvidia_current([KernelModuleHandler, nonfree, disabled] NVIDIA  binary Xorg driver, kernel module and VDPAU library)
2013-03-03  12:51:39,277 DEBUG: searching handler for driver ID {'driver_type':  'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package':  'nvidia-experimental-310'}
2013-03-03 12:51:39,284 WARNING: modinfo  for module nvidia_experimental_310 failed: ERROR: modinfo: could not  find module nvidia_experimental_310

2013-03-03 12:51:39,321  WARNING: modinfo for module nvidia_experimental_310 failed: ERROR:  modinfo: could not find module nvidia_experimental_310

2013-03-03  12:51:39,322 DEBUG: got handler  kmod:nvidia_experimental_310([KernelModuleHandler, nonfree, disabled]  Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library)
2013-03-03  12:51:39,322 DEBUG: searching handler for driver ID {'driver_type':  'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package':  'nvidia-current-updates'}
2013-03-03 12:51:39,329 WARNING: modinfo  for module nvidia_current_updates failed: ERROR: modinfo: could not find  module nvidia_current_updates

2013-03-03 12:51:39,366 WARNING:  modinfo for module nvidia_current_updates failed: ERROR: modinfo: could  not find module nvidia_current_updates

2013-03-03 12:51:39,367  DEBUG: got handler kmod:nvidia_current_updates([KernelModuleHandler,  nonfree, disabled] NVIDIA binary Xorg driver, kernel module and VDPAU  library)
2013-03-03 12:51:39,367 DEBUG: searching handler for driver  ID {'driver_type': 'kernel_module', 'kernel_module':  'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-03-03  12:51:39,374 WARNING: modinfo for module nvidia_experimental_304  failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-03-03  12:51:39,407 WARNING: modinfo for module nvidia_experimental_304  failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-03-03  12:51:39,409 DEBUG: got handler  kmod:nvidia_experimental_304([KernelModuleHandler, nonfree, disabled]  Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library)
2013-03-03 12:51:39,409 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-03-03  12:51:39,409 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:39,409 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-03-03  12:51:39,410 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'nouveau',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:39,410  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'x86cpu:vendor:0000:family:0006:model:002A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,009A,009B,009C,00C0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104')
2013-03-03 12:51:39,421 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-03-03  12:51:39,421 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:39,421 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-03-03  12:51:39,421 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'microcode',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:39,421 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-03-03  12:51:39,421 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'coretemp',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:39,421  DEBUG: searching handler for driver ID {'driver_type': 'kernel_module',  'kernel_module': 'ghash_clmulni_intel'}
2013-03-03 12:51:39,421  DEBUG: no corresponding handler available for {'driver_type':  'kernel_module', 'kernel_module': 'ghash_clmulni_intel',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:39,422  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-03-03 12:51:39,429 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-03-03  12:51:39,429 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:39,429 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-03-03  12:51:39,429 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'psmouse',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:39,429  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-03-03 12:51:39,430 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:51:39,430 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:39,430 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:51:39,430 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:39,430  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias', 'acpi:PNP0200:')
2013-03-03  12:51:39,430 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'input:b0003v058FpA014e0001-e0,1,kD4,ramlsfw')
2013-03-03 12:51:39,430 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-03-03  12:51:39,430 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'evbug',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:39,430 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-03-03  12:51:39,430 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:39,430  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'pci:v00008086d00001C22sv00001043sd00001277bc0Csc05i00')
2013-03-03 12:51:39,434 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-03-03  12:51:39,434 DEBUG: no corresponding handler available for  {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801',  'jockey_handler': 'KernelModuleHandler'}
2013-03-03 12:51:39,434  DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x1dcc248> about HardwareID('modalias',  'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2013-03-03 12:51:39,434  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x2124518> about HardwareID('modalias',  'pci:v00008086d00001C2Dsv00001043sd00001277bc0Csc03i20')
2013-03-03  12:51:39,434 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-03-03  12:51:39,435 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'acpi:PNP0B00:')
2013-03-03 12:51:39,435  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x2124518> about HardwareID('modalias',  'pci:v00008086d00001C26sv00001043sd00001277bc0Csc03i20')
2013-03-03  12:51:39,435 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'pci:v00008086d00001C20sv00001043sd00001AC3bc04sc03i00')
2013-03-03  12:51:39,435 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'platform:microcode')
2013-03-03  12:51:39,435 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'usb:v0BDAp0139d3960dcFFdscFFdpFFicFFisc06ip50')
2013-03-03  12:51:39,435 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-03-03  12:51:39,435 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-03-03 12:51:39,435  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x2124518> about HardwareID('modalias',  'platform:coretemp')
2013-03-03 12:51:39,435 DEBUG: querying driver  db <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'acpi:PNP0100:')
2013-03-03 12:51:39,435  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x2124518> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-03-03  12:51:39,435 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'platform:pcspkr')
2013-03-03  12:51:39,435 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-03-03  12:51:39,435 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'platform:asus-nb-wmi')
2013-03-03  12:51:39,435 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'wmi:0B3CBB35-E3C2-45ED-91C2-4C5A6D195D1C')
2013-03-03  12:51:39,435 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'pci:v00008086d00000116sv00001043sd00001682bc03sc00i00')
2013-03-03  12:51:39,436 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'pci:v00008086d00001C03sv00001043sd00001277bc01sc06i01')
2013-03-03  12:51:39,436 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-03-03  12:51:39,436 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'acpi:PNP0C02:')
2013-03-03 12:51:39,436  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x2124518> about HardwareID('modalias',  'acpi:INT340E:PNP0C02:')
2013-03-03 12:51:39,436 DEBUG: querying  driver db <jockey.detection.OpenPrintingDriverDB instance at  0x2124518> about HardwareID('modalias',  'pci:v00008086d00001C3Asv00001043sd00001277bc07sc80i00')
2013-03-03  12:51:39,436 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'pci:v00008086d00001C49sv00001043sd00001277bc06sc01i00')
2013-03-03  12:51:39,436 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2013-03-03  12:51:39,436 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'usb:v058FpA014d0001dcEFdsc02dp01ic0Eisc02ip00')
2013-03-03  12:51:39,436 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'usb:v045Ep0737d0104dc00dsc00dp00ic03isc01ip02')
2013-03-03  12:51:39,436 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-03-03  12:51:39,436 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,8C,94,96,A3,A4,A5,A6,A9,B9,BF,D4,D7,E2,E3,E5,E6,ED,EE,F0,F5,F7,1AF,ram4,lsfw')
2013-03-03  12:51:39,436 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-03-03  12:51:39,436 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'acpi:ETD0101:PNP0F0E:PNP0F03:PNP0F12:PNP0F0B:')
2013-03-03  12:51:39,436 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-03-03 12:51:39,436  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x2124518> about HardwareID('modalias', 'acpi:PNP0000:')
2013-03-03  12:51:39,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'dmi:bvnAmericanMegatrendsInc.:bvrK53SJ.209:bd03/15/2011:svnASUSTeKComputerInc.:pnK53SJ:pvr1.0:rvnASUSTeKComputerInc.:rnK53SJ:rvr1.0:cvnASUSTeKComputerInc.:ct10:cvr1.0:')
2013-03-03  12:51:39,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'acpi:PNP0C04:')
2013-03-03 12:51:39,437  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x2124518> about HardwareID('modalias',  'input:b0003v045Ep0737e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2013-03-03  12:51:39,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'usb:v12D1p1001d0000dc00dsc00dp00icFFiscFFipFF')
2013-03-03  12:51:39,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-03-03  12:51:39,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'usb:v058FpA014d0001dcEFdsc02dp01ic0Eisc01ip00')
2013-03-03  12:51:39,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'pci:v0000168Cd0000002Bsv00001A3Bsd00001089bc02sc80i00')
2013-03-03  12:51:39,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2013-03-03  12:51:39,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'acpi:INT0800:')
2013-03-03 12:51:39,437  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x2124518> about HardwareID('modalias',  'pci:v000010ECd00008168sv00001043sd00001277bc02sc00i00')
2013-03-03  12:51:39,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-03-03  12:51:39,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'platform:regulatory')
2013-03-03  12:51:39,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'usb:v12D1p1001d0000dc00dsc00dp00ic08isc06ip50')
2013-03-03  12:51:39,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'acpi:PNP0103:')
2013-03-03 12:51:39,437  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x2124518> about HardwareID('modalias',  'pci:v00008086d00000104sv00001043sd00001277bc06sc00i00')
2013-03-03  12:51:39,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'hid:b0003g0001v0000045Ep00000737')
2013-03-03  12:51:39,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'usb:v05E3p0606d0702dc09dsc00dp00ic09isc00ip00')
2013-03-03  12:51:39,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-03-03 12:51:39,438  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x2124518> about HardwareID('modalias', 'platform:Fixed  MDIO bus')
2013-03-03 12:51:39,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'acpi:PNP0C01:')
2013-03-03 12:51:39,438  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x2124518> about HardwareID('modalias',  'pci:v000010DEd00001050sv00001043sd00001682bc03sc00i00')
2013-03-03  12:51:39,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'x86cpu:vendor:0000:family:0006:model:002A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,009A,009B,009C,00C0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104')
2013-03-03  12:51:39,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-03-03  12:51:39,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-03-03  12:51:39,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'acpi:PNP0200:')
2013-03-03 12:51:39,438  DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB  instance at 0x2124518> about HardwareID('modalias',  'input:b0003v058FpA014e0001-e0,1,kD4,ramlsfw')
2013-03-03  12:51:39,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias',  'pci:v00008086d00001C22sv00001043sd00001277bc0Csc05i00')
2013-03-03  12:51:39,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x2124518>  about HardwareID('modalias', 'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2013-03-03 12:54:13,313 DEBUG: Installing package: nvidia-experimental-310
2013-03-03  12:54:14,070 DEBUG: download progress <Package:  name:'nvidia-experimental-310' architecture='amd64' id:89594L>  0.000000
2013-03-03 12:54:14,071 DEBUG: download progress  <Package: name:'nvidia-experimental-310' architecture='amd64'  id:89594L> 0.000000
2013-03-03 12:54:14,331 DEBUG: download  progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.000000
2013-03-03 12:54:14,440  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.000000
2013-03-03 12:54:14,675  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.000000
2013-03-03 12:54:15,176  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.058374
2013-03-03 12:54:15,319  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.103549
2013-03-03 12:54:15,320  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.103549
2013-03-03 12:54:15,512  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.103549
2013-03-03 12:54:15,932  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.231462
2013-03-03 12:54:15,933  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.231462
2013-03-03 12:54:16,144  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.231462
2013-03-03 12:54:16,645  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.390480
2013-03-03 12:54:17,147  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.493137
2013-03-03 12:54:17,648  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.599820
2013-03-03 12:54:18,150  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.712542
2013-03-03 12:54:18,651  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.829289
2013-03-03 12:54:19,152  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.913831
2013-03-03 12:54:19,653  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 0.988307
2013-03-03 12:54:20,154  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 1.034604
2013-03-03 12:54:20,655  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 1.094990
2013-03-03 12:54:21,157  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 1.199661
2013-03-03 12:54:21,658  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 1.324460
2013-03-03 12:54:22,160  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 1.454479
2013-03-03 12:54:22,661  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 1.597394
2013-03-03 12:54:23,163  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 1.714142
2013-03-03 12:54:23,664  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 1.824851
2013-03-03 12:54:24,166  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 1.928500
2013-03-03 12:54:24,667  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 2.049273
2013-03-03 12:54:25,168  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 2.139853
2013-03-03 12:54:25,670  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 2.209498
2013-03-03 12:54:26,684  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 2.382745
2013-03-03 12:54:27,185  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 2.507544
2013-03-03 12:54:27,687  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 2.616240
2013-03-03 12:54:28,188  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 2.690717
2013-03-03 12:54:28,690  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 2.781024
2013-03-03 12:54:29,191  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 2.889720
2013-03-03 12:54:29,692  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 2.968223
2013-03-03 12:54:30,194  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 3.058803
2013-03-03 12:54:30,695  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 3.160793
2013-03-03 12:54:31,197  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 3.271502
2013-03-03 12:54:31,698  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 3.366107
2013-03-03 12:54:32,199  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 3.456687
2013-03-03 12:54:32,700  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 3.549007
2013-03-03 12:54:33,202  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 3.631536
2013-03-03 12:54:33,703  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 3.728154
2013-03-03 12:54:34,205  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 3.828799
2013-03-03 12:54:34,706  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 3.939235
2013-03-03 12:54:35,207  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 4.035854
2013-03-03 12:54:35,709  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 4.132472
2013-03-03 12:54:36,210  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 4.231104
2013-03-03 12:54:36,712  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 4.309334
2013-03-03 12:54:37,213  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 4.405952
2013-03-03 12:54:37,714  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 4.500558
2013-03-03 12:54:38,216  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 4.583086
2013-03-03 12:54:38,717  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 4.679705
2013-03-03 12:54:39,218  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 4.794439
2013-03-03 12:54:39,720  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 4.897694
2013-03-03 12:54:40,221  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 4.994313
2013-03-03 12:54:40,722  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 5.060738
2013-03-03 12:54:41,224  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 5.211705
2013-03-03 12:54:41,725  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 5.316375
2013-03-03 12:54:42,226  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 5.393462
2013-03-03 12:54:42,727  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 5.467939
2013-03-03 12:54:43,228  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 5.542416
2013-03-03 12:54:43,729  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 5.588712
2013-03-03 12:54:44,230  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 5.624944
2013-03-03 12:54:44,731  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 5.697408
2013-03-03 12:54:45,232  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 5.790001
2013-03-03 12:54:45,733  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 5.888632
2013-03-03 12:54:46,234  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 5.968127
2013-03-03 12:54:46,735  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 6.072797
2013-03-03 12:54:47,237  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 6.127145
2013-03-03 12:54:47,738  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 6.276099
2013-03-03 12:54:48,239  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 6.426792
2013-03-03 12:54:48,740  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 6.579772
2013-03-03 12:54:49,241  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 6.728453
2013-03-03 12:54:49,743  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 6.871368
2013-03-03 12:54:50,244  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 7.028373
2013-03-03 12:54:50,745  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 7.142046
2013-03-03 12:54:51,247  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 7.270871
2013-03-03 12:54:51,748  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 7.349374
2013-03-03 12:54:52,249  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 7.494301
2013-03-03 12:54:52,750  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 7.610382
2013-03-03 12:54:53,251  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 7.741219
2013-03-03 12:54:53,752  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 7.853941
2013-03-03 12:54:54,253  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 7.968676
2013-03-03 12:54:54,755  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 8.089449
2013-03-03 12:54:55,256  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 8.216858
2013-03-03 12:54:55,757  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 8.303413
2013-03-03 12:54:56,258  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 8.375876
2013-03-03 12:54:56,760  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 8.458405
2013-03-03 12:54:57,261  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 8.558382
2013-03-03 12:54:57,762  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 8.634872
2013-03-03 12:54:58,263  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 8.743568
2013-03-03 12:54:58,764  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 8.866354
2013-03-03 12:54:59,265  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 8.988867
2013-03-03 12:54:59,766  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 9.107628
2013-03-03 12:55:00,267  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 9.224375
2013-03-03 12:55:00,768  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 9.330786
2013-03-03 12:55:01,269  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 9.453572
2013-03-03 12:55:01,770  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 9.590448
2013-03-03 12:55:02,272  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 9.701157
2013-03-03 12:55:02,773  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 9.815891
2013-03-03 12:55:03,274  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 9.935249
2013-03-03 12:55:03,775  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 10.056023
2013-03-03 12:55:04,276  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 10.186860
2013-03-03 12:55:04,777  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 10.307633
2013-03-03 12:55:05,278  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 10.415308
2013-03-03 12:55:05,780  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 10.530043
2013-03-03 12:55:06,281  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 10.636726
2013-03-03 12:55:06,782  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 10.751461
2013-03-03 12:55:07,283  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 10.853845
2013-03-03 12:55:07,784  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 10.964554
2013-03-03 12:55:08,285  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 11.067211
2013-03-03 12:55:08,786  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 11.181673
2013-03-03 12:55:09,287  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 11.298421
2013-03-03 12:55:09,788  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 11.395039
2013-03-03 12:55:10,289  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 11.483606
2013-03-03 12:55:10,791  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 11.581965
2013-03-03 12:55:11,292  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 11.694687
2013-03-03 12:55:11,793  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 11.835589
2013-03-03 12:55:12,294  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 11.927909
2013-03-03 12:55:12,795  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 12.052708
2013-03-03 12:55:13,296  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 12.169456
2013-03-03 12:55:13,797  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 12.308072
2013-03-03 12:55:14,298  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 12.455013
2013-03-03 12:55:14,799  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 12.559683
2013-03-03 12:55:15,300  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 12.666093
2013-03-03 12:55:15,801  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 12.770764
2013-03-03 12:55:16,302  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 12.865369
2013-03-03 12:55:16,803  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 12.986143
2013-03-03 12:55:17,305  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 13.090146
2013-03-03 12:55:17,806  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 13.227022
2013-03-03 12:55:18,307  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 13.365911
2013-03-03 12:55:18,808  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 13.484399
2013-03-03 12:55:19,309  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 13.605172
2013-03-03 12:55:19,810  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 13.719907
2013-03-03 12:55:20,311  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 13.812500
2013-03-03 12:55:20,812  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 13.920923
2013-03-03 12:55:21,313  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 14.027606
2013-03-03 12:55:21,814  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 14.154418
2013-03-03 12:55:22,315  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 14.272905
2013-03-03 12:55:22,816  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 14.395692
2013-03-03 12:55:23,318  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 14.488284
2013-03-03 12:55:23,819  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 14.610798
2013-03-03 12:55:24,320  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 14.751700
2013-03-03 12:55:24,821  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 14.884551
2013-03-03 12:55:25,322  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 14.997000
2013-03-03 12:55:25,822  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 15.135889
2013-03-03 12:55:26,323  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 15.278804
2013-03-03 12:55:26,824  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 15.429498
2013-03-03 12:55:27,325  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 15.562348
2013-03-03 12:55:27,826  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 15.675070
2013-03-03 12:55:28,327  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 15.821738
2013-03-03 12:55:28,828  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 15.958614
2013-03-03 12:55:29,330  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 16.085426
2013-03-03 12:55:29,831  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 16.211966
2013-03-03 12:55:30,332  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 16.340790
2013-03-03 12:55:30,833  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 16.473641
2013-03-03 12:55:31,334  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 16.610245
2013-03-03 12:55:31,835  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 16.708876
2013-03-03 12:55:32,336  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 16.829649
2013-03-03 12:55:32,837  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 16.956189
2013-03-03 12:55:33,338  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 17.083001
2013-03-03 12:55:33,839  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 17.195722
2013-03-03 12:55:34,340  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 17.296094
2013-03-03 12:55:34,841  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 17.436996
2013-03-03 12:55:35,342  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 17.571860
2013-03-03 12:55:35,843  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 17.692360
2013-03-03 12:55:36,345  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 17.821185
2013-03-03 12:55:36,846  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 17.937932
2013-03-03 12:55:37,347  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 18.064077
2013-03-03 12:55:37,848  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 18.180825
2013-03-03 12:55:38,349  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 18.295559
2013-03-03 12:55:38,851  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 18.416060
2013-03-03 12:55:39,352  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 18.536833
2013-03-03 12:55:39,853  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 18.653581
2013-03-03 12:55:40,354  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 18.776367
2013-03-03 12:55:40,855  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 18.860635
2013-03-03 12:55:41,356  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 18.973357
2013-03-03 12:55:41,858  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 19.096143
2013-03-03 12:55:42,359  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 19.180412
2013-03-03 12:55:42,859  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 19.289108
2013-03-03 12:55:43,360  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 19.409881
2013-03-03 12:55:43,861  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 19.536693
2013-03-03 12:55:44,362  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 19.651155
2013-03-03 12:55:44,863  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 19.753812
2013-03-03 12:55:45,365  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 19.848418
2013-03-03 12:55:45,866  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 19.965165
2013-03-03 12:55:46,367  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 20.089964
2013-03-03 12:55:46,868  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 20.193219
2013-03-03 12:55:47,369  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 20.322044
2013-03-03 12:55:47,870  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 20.444830
2013-03-03 12:55:48,371  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 20.541448
2013-03-03 12:55:48,872  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 20.634993
2013-03-03 12:55:49,373  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 20.749727
2013-03-03 12:55:49,875  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 20.856410
2013-03-03 12:55:50,375  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 20.974898
2013-03-03 12:55:50,876  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 21.085607
2013-03-03 12:55:51,378  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 21.190277
2013-03-03 12:55:51,879  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 21.288908
2013-03-03 12:55:52,380  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 21.377475
2013-03-03 12:55:52,881  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 21.478120
2013-03-03 12:55:53,382  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 21.587413
2013-03-03 12:55:53,882  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 21.688057
2013-03-03 12:55:54,384  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 21.790715
2013-03-03 12:55:54,885  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 21.881295
2013-03-03 12:55:55,386  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 21.996029
2013-03-03 12:55:55,887  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 22.105323
2013-03-03 12:55:56,387  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 22.216031
2013-03-03 12:55:56,889  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 22.298560
2013-03-03 12:55:57,390  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 22.415307
2013-03-03 12:55:57,891  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 22.493537
2013-03-03 12:55:58,393  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 22.600220
2013-03-03 12:55:58,894  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 22.698852
2013-03-03 12:55:59,395  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 22.793457
2013-03-03 12:55:59,896  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 22.901486
2013-03-03 12:56:00,397  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 23.004144
2013-03-03 12:56:00,898  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 23.102775
2013-03-03 12:56:01,399  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 23.203419
2013-03-03 12:56:01,900  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 23.299765
2013-03-03 12:56:02,401  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 23.398397
2013-03-03 12:56:02,902  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 23.480925
2013-03-03 12:56:03,403  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 23.589621
2013-03-03 12:56:03,905  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 23.692006
2013-03-03 12:56:04,406  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 23.806740
2013-03-03 12:56:04,907  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 23.905372
2013-03-03 12:56:05,408  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 24.004003
2013-03-03 12:56:05,909  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 24.102635
2013-03-03 12:56:06,410  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 24.203877
2013-03-03 12:56:06,911  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 24.310560
2013-03-03 12:56:07,412  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 24.421268
2013-03-03 12:56:07,913  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 24.531977
2013-03-03 12:56:08,414  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 24.632622
2013-03-03 12:56:08,915  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 24.752374
2013-03-03 12:56:09,417  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 24.861070
2013-03-03 12:56:09,918  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 24.951650
2013-03-03 12:56:10,419  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 25.060346
2013-03-03 12:56:10,920  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 25.176032
2013-03-03 12:56:11,421  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 25.290766
2013-03-03 12:56:11,922  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 25.355179
2013-03-03 12:56:12,424  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 25.471926
2013-03-03 12:56:12,925  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 25.592699
2013-03-03 12:56:13,426  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 25.705421
2013-03-03 12:56:13,926  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 25.786534
2013-03-03 12:56:14,428  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 25.903281
2013-03-03 12:56:14,929  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 25.999900
2013-03-03 12:56:15,430  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 26.096519
2013-03-03 12:56:15,932  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 26.198903
2013-03-03 12:56:16,433  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 26.311625
2013-03-03 12:56:16,934  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 26.400192
2013-03-03 12:56:17,435  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 26.512641
2013-03-03 12:56:17,936  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 26.621337
2013-03-03 12:56:18,437  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 26.713930
2013-03-03 12:56:18,938  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 26.810548
2013-03-03 12:56:19,439  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 26.912538
2013-03-03 12:56:19,940  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 27.019221
2013-03-03 12:56:20,441  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 27.105776
2013-03-03 12:56:20,942  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 27.212459
2013-03-03 12:56:21,444  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 27.308410
2013-03-03 12:56:21,945  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 27.405029
2013-03-03 12:56:22,446  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 27.479506
2013-03-03 12:56:22,947  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 27.564047
2013-03-03 12:56:23,448  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 27.656640
2013-03-03 12:56:23,949  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 27.749232
2013-03-03 12:56:24,450  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 27.852882
2013-03-03 12:56:24,951  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 27.957552
2013-03-03 12:56:25,452  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 28.062222
2013-03-03 12:56:25,953  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 28.164879
2013-03-03 12:56:26,454  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 28.257199
2013-03-03 12:56:26,956  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 28.371934
2013-03-03 12:56:27,457  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 28.478617
2013-03-03 12:56:27,958  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 28.589326
2013-03-03 12:56:28,459  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 28.681252
2013-03-03 12:56:28,960  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 28.793973
2013-03-03 12:56:29,462  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 28.898643
2013-03-03 12:56:29,963  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 28.999288
2013-03-03 12:56:30,463  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 29.127840
2013-03-03 12:56:30,964  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 29.258678
2013-03-03 12:56:31,466  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 29.371399
2013-03-03 12:56:31,967  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 29.497938
2013-03-03 12:56:32,468  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 29.630789
2013-03-03 12:56:32,969  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 29.769678
2013-03-03 12:56:33,470  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 29.887377
2013-03-03 12:56:33,971  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 30.030292
2013-03-03 12:56:34,472  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 30.128924
2013-03-03 12:56:34,973  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 30.205413
2013-03-03 12:56:35,475  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 30.312096
2013-03-03 12:56:35,976  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 30.415351
2013-03-03 12:56:36,477  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 30.526060
2013-03-03 12:56:36,978  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 30.618653
2013-03-03 12:56:37,478  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 30.701181
2013-03-03 12:56:37,980  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 30.805851
2013-03-03 12:56:38,481  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 30.914547
2013-03-03 12:56:38,982  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 31.020209
2013-03-03 12:56:39,483  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 31.130918
2013-03-03 12:56:39,984  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 31.241627
2013-03-03 12:56:40,485  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 31.344011
2013-03-03 12:56:40,986  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 31.454720
2013-03-03 12:56:41,488  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 31.555365
2013-03-03 12:56:41,989  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 31.672112
2013-03-03 12:56:42,490  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 31.778522
2013-03-03 12:56:42,991  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 31.891244
2013-03-03 12:56:43,492  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 31.999940
2013-03-03 12:56:43,994  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 32.112389
2013-03-03 12:56:44,495  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 32.223098
2013-03-03 12:56:44,996  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 32.329781
2013-03-03 12:56:45,497  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 32.438477
2013-03-03 12:56:45,998  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 32.548124
2013-03-03 12:56:46,499  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 32.662859
2013-03-03 12:56:47,000  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 32.771555
2013-03-03 12:56:47,501  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 32.874212
2013-03-03 12:56:48,002  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 32.982908
2013-03-03 12:56:48,503  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 33.090583
2013-03-03 12:56:49,005  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 33.197266
2013-03-03 12:56:49,506  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 33.301936
2013-03-03 12:56:50,007  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 33.414658
2013-03-03 12:56:50,508  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 33.533145
2013-03-03 12:56:51,009  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 33.645867
2013-03-03 12:56:51,511  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 33.772679
2013-03-03 12:56:52,012  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 33.896811
2013-03-03 12:56:52,513  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 34.015571
2013-03-03 12:56:53,014  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 34.114203
2013-03-03 12:56:53,515  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 34.190692
2013-03-03 12:56:54,016  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 34.293350
2013-03-03 12:56:54,517  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 34.399012
2013-03-03 12:56:55,018  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 34.503682
2013-03-03 12:56:55,519  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 34.614391
2013-03-03 12:56:56,020  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 34.723087
2013-03-03 12:56:56,522  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 34.823458
2013-03-03 12:56:57,023  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 34.940206
2013-03-03 12:56:57,538  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 35.054940
2013-03-03 12:56:58,039  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 35.163364
2013-03-03 12:56:58,540  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 35.259982
2013-03-03 12:56:59,041  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 35.380755
2013-03-03 12:56:59,542  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 35.499516
2013-03-03 12:57:00,043  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 35.603913
2013-03-03 12:57:00,544  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 35.714622
2013-03-03 12:57:01,046  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 35.833382
2013-03-03 12:57:01,547  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 35.905574
2013-03-03 12:57:02,048  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 36.022321
2013-03-03 12:57:02,549  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 36.137056
2013-03-03 12:57:03,050  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 36.263868
2013-03-03 12:57:03,551  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 36.363845
2013-03-03 12:57:04,053  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 36.468515
2013-03-03 12:57:04,554  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 36.575198
2013-03-03 12:57:05,055  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 36.655714
2013-03-03 12:57:05,556  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 36.754345
2013-03-03 12:57:06,057  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 36.860007
2013-03-03 12:57:06,558  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 36.974742
2013-03-03 12:57:07,059  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 37.059283
2013-03-03 12:57:07,560  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 37.178043
2013-03-03 12:57:08,061  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 37.284454
2013-03-03 12:57:08,562  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 37.393150
2013-03-03 12:57:09,064  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 37.463601
2013-03-03 12:57:09,565  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 37.574310
2013-03-03 12:57:10,066  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 37.680720
2013-03-03 12:57:10,567  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 37.781364
2013-03-03 12:57:11,068  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 37.791429
2013-03-03 12:57:11,569  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 37.892073
2013-03-03 12:57:12,070  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 38.002509
2013-03-03 12:57:12,572  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 38.123282
2013-03-03 12:57:13,072  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 38.181656
2013-03-03 12:57:13,573  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 38.298404
2013-03-03 12:57:14,074  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 38.411125
2013-03-03 12:57:14,576  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 38.533911
2013-03-03 12:57:15,077  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 38.556053
2013-03-03 12:57:15,578  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 38.677424
2013-03-03 12:57:16,079  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 38.798197
2013-03-03 12:57:16,580  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 38.910919
2013-03-03 12:57:17,081  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 38.912932
2013-03-03 12:57:17,583  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 38.977344
2013-03-03 12:57:18,084  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 39.077989
2013-03-03 12:57:18,585  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 39.181638
2013-03-03 12:57:19,086  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 39.252089
2013-03-03 12:57:19,587  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 39.286308
2013-03-03 12:57:20,088  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 39.298385
2013-03-03 12:57:20,589  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 39.386952
2013-03-03 12:57:21,090  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 39.495376
2013-03-03 12:57:21,592  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 39.610110
2013-03-03 12:57:22,093  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 39.714780
2013-03-03 12:57:22,595  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 39.843605
2013-03-03 12:57:23,096  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 39.968131
2013-03-03 12:57:23,598  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 40.100982
2013-03-03 12:57:24,099  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 40.223768
2013-03-03 12:57:24,600  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 40.342256
2013-03-03 12:57:25,101  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 40.456990
2013-03-03 12:57:25,602  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 40.573738
2013-03-03 12:57:26,103  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 40.690213
2013-03-03 12:57:26,605  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 40.808973
2013-03-03 12:57:27,106  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 40.919682
2013-03-03 12:57:27,608  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 41.031736
2013-03-03 12:57:28,109  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 41.142445
2013-03-03 12:57:28,610  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 41.251141
2013-03-03 12:57:29,111  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 41.357824
2013-03-03 12:57:29,613  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 41.460209
2013-03-03 12:57:30,114  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 41.548776
2013-03-03 12:57:30,614  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 41.653446
2013-03-03 12:57:31,116  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 41.746039
2013-03-03 12:57:31,617  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 41.816490
2013-03-03 12:57:32,118  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 41.937263
2013-03-03 12:57:32,619  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 42.058634
2013-03-03 12:57:33,120  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 42.165317
2013-03-03 12:57:33,621  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 42.274013
2013-03-03 12:57:34,123  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 42.368740
2013-03-03 12:57:34,624  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 42.483475
2013-03-03 12:57:35,125  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 42.600222
2013-03-03 12:57:35,626  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 42.731060
2013-03-03 12:57:36,128  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 42.897463
2013-03-03 12:57:36,629  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 43.038365
2013-03-03 12:57:37,131  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 43.216845
2013-03-03 12:57:37,632  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 43.383914
2013-03-03 12:57:38,133  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 43.544945
2013-03-03 12:57:38,634  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 43.697925
2013-03-03 12:57:39,135  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 43.789102
2013-03-03 12:57:39,637  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 43.990391
2013-03-03 12:57:40,138  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 44.135319
2013-03-03 12:57:40,639  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 44.267148
2013-03-03 12:57:41,140  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 44.418115
2013-03-03 12:57:41,642  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 44.567068
2013-03-03 12:57:42,143  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 44.703278
2013-03-03 12:57:42,644  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 44.834115
2013-03-03 12:57:43,145  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 44.954889
2013-03-03 12:57:43,647  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 45.096742
2013-03-03 12:57:44,148  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 45.219528
2013-03-03 12:57:44,649  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 45.340301
2013-03-03 12:57:45,151  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 45.463088
2013-03-03 12:57:45,652  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 45.576366
2013-03-03 12:57:46,153  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 45.697139
2013-03-03 12:57:46,654  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 45.819926
2013-03-03 12:57:47,155  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 45.946070
2013-03-03 12:57:47,657  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 46.068856
2013-03-03 12:57:48,158  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 46.195668
2013-03-03 12:57:48,660  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 46.318454
2013-03-03 12:57:49,161  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 46.466741
2013-03-03 12:57:49,662  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 46.585501
2013-03-03 12:57:50,163  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 46.716339
2013-03-03 12:57:50,664  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 46.852943
2013-03-03 12:57:51,165  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 47.001896
2013-03-03 12:57:51,666  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 47.136487
2013-03-03 12:57:52,167  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 47.263299
2013-03-03 12:57:52,668  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 47.384072
2013-03-03 12:57:53,170  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 47.508871
2013-03-03 12:57:53,671  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 47.659838
2013-03-03 12:57:54,172  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 47.799325
2013-03-03 12:57:54,674  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 47.940227
2013-03-03 12:57:55,175  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 48.073077
2013-03-03 12:57:55,676  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 48.213979
2013-03-03 12:57:56,177  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 48.363925
2013-03-03 12:57:56,679  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 48.516904
2013-03-03 12:57:57,180  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 48.670835
2013-03-03 12:57:57,681  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 48.827840
2013-03-03 12:57:58,183  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 48.980820
2013-03-03 12:57:58,684  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 49.121722
2013-03-03 12:57:59,185  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 49.255170
2013-03-03 12:57:59,686  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 49.394059
2013-03-03 12:58:00,187  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 49.538987
2013-03-03 12:58:00,688  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 49.687941
2013-03-03 12:58:01,189  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 49.833861
2013-03-03 12:58:01,690  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 50.000930
2013-03-03 12:58:02,191  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 50.165714
2013-03-03 12:58:02,693  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 50.334797
2013-03-03 12:58:03,194  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 50.497841
2013-03-03 12:58:03,696  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 50.658599
2013-03-03 12:58:04,197  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 50.809566
2013-03-03 12:58:04,698  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 50.946169
2013-03-03 12:58:05,199  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 51.070968
2013-03-03 12:58:05,700  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 51.187716
2013-03-03 12:58:06,201  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 51.298425
2013-03-03 12:58:06,702  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 51.414505
2013-03-03 12:58:07,203  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 51.517162
2013-03-03 12:58:07,704  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 51.645987
2013-03-03 12:58:08,205  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 51.802992
2013-03-03 12:58:08,706  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 51.938453
2013-03-03 12:58:09,207  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 52.109549
2013-03-03 12:58:09,708  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 52.262528
2013-03-03 12:58:10,209  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 52.427585
2013-03-03 12:58:10,711  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 52.597659
2013-03-03 12:58:11,212  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 52.750639
2013-03-03 12:58:11,714  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 52.909384
2013-03-03 12:58:12,215  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 53.072428
2013-03-03 12:58:12,716  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 53.245536
2013-03-03 12:58:13,218  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 53.413163
2013-03-03 12:58:13,718  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 53.562117
2013-03-03 12:58:14,219  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 53.712811
2013-03-03 12:58:14,720  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 53.861764
2013-03-03 12:58:15,221  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 54.012731
2013-03-03 12:58:15,722  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 54.159399
2013-03-03 12:58:16,224  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 54.326469
2013-03-03 12:58:16,725  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 54.490858
2013-03-03 12:58:17,226  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 54.625722
2013-03-03 12:58:17,727  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 54.776688
2013-03-03 12:58:18,228  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 54.895449
2013-03-03 12:58:18,730  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 55.047407
2013-03-03 12:58:19,231  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 55.200386
2013-03-03 12:58:19,732  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 55.325185
2013-03-03 12:58:20,233  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 55.445292
2013-03-03 12:58:20,734  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 55.551975
2013-03-03 12:58:21,235  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 55.668722
2013-03-03 12:58:21,736  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 55.733135
2013-03-03 12:58:22,237  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 55.865985
2013-03-03 12:58:22,739  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 55.981712
2013-03-03 12:58:23,240  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 56.106511
2013-03-03 12:58:23,740  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 56.243387
2013-03-03 12:58:24,241  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 56.313565
2013-03-03 12:58:24,742  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 56.422261
2013-03-03 12:58:25,243  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 56.514854
2013-03-03 12:58:25,744  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 56.643679
2013-03-03 12:58:26,246  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 56.703793
2013-03-03 12:58:26,747  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 56.824566
2013-03-03 12:58:27,248  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 56.899043
2013-03-03 12:58:27,749  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 57.001700
2013-03-03 12:58:28,250  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 57.052022
2013-03-03 12:58:28,751  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 57.098046
2013-03-03 12:58:29,252  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 57.206742
2013-03-03 12:58:29,754  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 57.297322
2013-03-03 12:58:30,255  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 57.422121
2013-03-03 12:58:30,756  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 57.428160
2013-03-03 12:58:31,257  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 57.526519
2013-03-03 12:58:31,758  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 57.655343
2013-03-03 12:58:32,259  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 57.786181
2013-03-03 12:58:32,760  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 57.918364
2013-03-03 12:58:33,261  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 58.057254
2013-03-03 12:58:33,762  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 58.198156
2013-03-03 12:58:34,263  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 58.324695
2013-03-03 12:58:34,764  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 58.437417
2013-03-03 12:58:35,265  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 58.550138
2013-03-03 12:58:35,766  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 58.674270
2013-03-03 12:58:36,268  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 58.815172
2013-03-03 12:58:36,769  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 58.984255
2013-03-03 12:58:37,270  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 59.128910
2013-03-03 12:58:37,771  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 59.257735
2013-03-03 12:58:38,272  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 59.392598
2013-03-03 12:58:38,773  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 59.518349
2013-03-03 12:58:39,274  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 59.639122
2013-03-03 12:58:39,775  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 59.753857
2013-03-03 12:58:40,276  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 59.871950
2013-03-03 12:58:40,778  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 60.014865
2013-03-03 12:58:41,278  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 60.139664
2013-03-03 12:58:41,779  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 60.254399
2013-03-03 12:58:42,280  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 60.383223
2013-03-03 12:58:42,781  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 60.508620
2013-03-03 12:58:43,282  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 60.591148
2013-03-03 12:58:43,784  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 60.707896
2013-03-03 12:58:44,284  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 60.828396
2013-03-03 12:58:44,785  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 60.963260
2013-03-03 12:58:45,286  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 61.084033
2013-03-03 12:58:45,788  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 61.200780
2013-03-03 12:58:46,289  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 61.298350
2013-03-03 12:58:46,790  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 61.388930
2013-03-03 12:58:47,291  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 61.505678
2013-03-03 12:58:47,792  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 61.622153
2013-03-03 12:58:48,293  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 61.726823
2013-03-03 12:58:48,794  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 61.805325
2013-03-03 12:58:49,295  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 61.871751
2013-03-03 12:58:49,796  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 61.978434
2013-03-03 12:58:50,298  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 62.074385
2013-03-03 12:58:50,799  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 62.181068
2013-03-03 12:58:51,300  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 62.225352
2013-03-03 12:58:51,801  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 62.325996
2013-03-03 12:58:52,302  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 62.426368
2013-03-03 12:58:52,803  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 62.529025
2013-03-03 12:58:53,304  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 62.593437
2013-03-03 12:58:53,805  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 62.708172
2013-03-03 12:58:54,306  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 62.822239
2013-03-03 12:58:54,808  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 62.949051
2013-03-03 12:58:55,309  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 63.053721
2013-03-03 12:58:55,810  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 63.170469
2013-03-03 12:58:56,311  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 63.296614
2013-03-03 12:58:56,812  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 63.409335
2013-03-03 12:58:57,313  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 63.530109
2013-03-03 12:58:57,814  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 63.630753
2013-03-03 12:58:58,315  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 63.743475
2013-03-03 12:58:58,816  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 63.828613
2013-03-03 12:58:59,318  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 63.941335
2013-03-03 12:58:59,819  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 64.066134
2013-03-03 12:59:00,320  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 64.184895
2013-03-03 12:59:00,821  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 64.307681
2013-03-03 12:59:01,322  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 64.439510
2013-03-03 12:59:01,823  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 64.556258
2013-03-03 12:59:02,324  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 64.668979
2013-03-03 12:59:02,826  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 64.797532
2013-03-03 12:59:03,327  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 64.894150
2013-03-03 12:59:03,828  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 64.978691
2013-03-03 12:59:04,329  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 65.045117
2013-03-03 12:59:04,830  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 65.117308
2013-03-03 12:59:05,331  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 65.169643
2013-03-03 12:59:05,833  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 65.268275
2013-03-03 12:59:06,334  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 65.362880
2013-03-03 12:59:06,835  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 65.443396
2013-03-03 12:59:07,336  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 65.537729
2013-03-03 12:59:07,838  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 65.602141
2013-03-03 12:59:08,339  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 65.652463
2013-03-03 12:59:08,840  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 65.694734
2013-03-03 12:59:09,341  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 65.741030
2013-03-03 12:59:09,842  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 65.815507
2013-03-03 12:59:10,343  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 65.889984
2013-03-03 12:59:10,844  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 65.996667
2013-03-03 12:59:11,345  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 66.109986
2013-03-03 12:59:11,846  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 66.212644
2013-03-03 12:59:12,347  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 66.329391
2013-03-03 12:59:12,849  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 66.441840
2013-03-03 12:59:13,350  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 66.560600
2013-03-03 12:59:13,851  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 66.679361
2013-03-03 12:59:14,352  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 66.797849
2013-03-03 12:59:14,854  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 66.902519
2013-03-03 12:59:15,355  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 66.995111
2013-03-03 12:59:15,856  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 67.097769
2013-03-03 12:59:16,358  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 67.192102
2013-03-03 12:59:16,859  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 67.292746
2013-03-03 12:59:17,360  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 67.407481
2013-03-03 12:59:17,861  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 67.508125
2013-03-03 12:59:18,362  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 67.618561
2013-03-03 12:59:18,863  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 67.729270
2013-03-03 12:59:19,365  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 67.833940
2013-03-03 12:59:19,866  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 67.930286
2013-03-03 12:59:20,367  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 68.030931
2013-03-03 12:59:20,868  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 68.135601
2013-03-03 12:59:21,369  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 68.246309
2013-03-03 12:59:21,871  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 68.364797
2013-03-03 12:59:22,371  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 68.497648
2013-03-03 12:59:22,872  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 68.632511
2013-03-03 12:59:23,373  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 68.777166
2013-03-03 12:59:23,874  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 68.912030
2013-03-03 12:59:24,375  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 69.038842
2013-03-03 12:59:24,876  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 69.155317
2013-03-03 12:59:25,378  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 69.276090
2013-03-03 12:59:25,879  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 69.396863
2013-03-03 12:59:26,380  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 69.518588
2013-03-03 12:59:26,881  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 69.647412
2013-03-03 12:59:27,382  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 69.772211
2013-03-03 12:59:27,884  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 69.915126
2013-03-03 12:59:28,385  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 70.073083
2013-03-03 12:59:28,886  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 70.203921
2013-03-03 12:59:29,387  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 70.344550
2013-03-03 12:59:29,888  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 70.489478
2013-03-03 12:59:30,389  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 70.628367
2013-03-03 12:59:30,890  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 70.777048
2013-03-03 12:59:31,391  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 70.915938
2013-03-03 12:59:31,893  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 71.074683
2013-03-03 12:59:32,394  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 71.229675
2013-03-03 12:59:32,895  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 71.370577
2013-03-03 12:59:33,396  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 71.510418
2013-03-03 12:59:33,897  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 71.657359
2013-03-03 12:59:34,398  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 71.802287
2013-03-03 12:59:34,900  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 71.946942
2013-03-03 12:59:35,401  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 72.087844
2013-03-03 12:59:35,902  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 72.240823
2013-03-03 12:59:36,403  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 72.393530
2013-03-03 12:59:36,904  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 72.528394
2013-03-03 12:59:37,405  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 72.691165
2013-03-03 12:59:37,906  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 72.813951
2013-03-03 12:59:38,407  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 72.972969
2013-03-03 12:59:38,908  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 73.125282
2013-03-03 12:59:39,409  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 73.209823
2013-03-03 12:59:39,910  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 73.344686
2013-03-03 12:59:40,411  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 73.483303
2013-03-03 12:59:40,913  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 73.585960
2013-03-03 12:59:41,414  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 73.672514
2013-03-03 12:59:41,915  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 73.817442
2013-03-03 12:59:42,416  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 73.958344
2013-03-03 12:59:42,917  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 74.069651
2013-03-03 12:59:43,418  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 74.228669
2013-03-03 12:59:43,920  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 74.401504
2013-03-03 12:59:44,421  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 74.558509
2013-03-03 12:59:44,922  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 74.723566
2013-03-03 12:59:45,423  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 74.885549
2013-03-03 12:59:45,924  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 75.040541
2013-03-03 12:59:46,425  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 75.199286
2013-03-03 12:59:46,926  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 75.358304
2013-03-03 12:59:47,428  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 75.525374
2013-03-03 12:59:47,929  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 75.690158
2013-03-03 12:59:48,430  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 75.853202
2013-03-03 12:59:48,931  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 76.009935
2013-03-03 12:59:49,432  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 76.104540
2013-03-03 12:59:49,933  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 76.311595
2013-03-03 12:59:50,434  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 76.472626
2013-03-03 12:59:50,935  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 76.621580
2013-03-03 12:59:51,437  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 76.784351
2013-03-03 12:59:51,938  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 76.945382
2013-03-03 12:59:52,439  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 77.103733
2013-03-03 12:59:52,941  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 77.264764
2013-03-03 12:59:53,442  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 77.433847
2013-03-03 12:59:53,943  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 77.604669
2013-03-03 12:59:54,444  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 77.773752
2013-03-03 12:59:54,945  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 77.946588
2013-03-03 12:59:55,446  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 78.111644
2013-03-03 12:59:55,948  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 78.304881
2013-03-03 12:59:56,449  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 78.450407
2013-03-03 12:59:56,951  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 78.597348
2013-03-03 12:59:57,452  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 78.754353
2013-03-03 12:59:57,953  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 78.927461
2013-03-03 12:59:58,455  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 79.074999
2013-03-03 12:59:58,956  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 79.217914
2013-03-03 12:59:59,458  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 79.374920
2013-03-03 12:59:59,959  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 79.533938
2013-03-03 13:00:00,460  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 79.669793
2013-03-03 13:00:00,962  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 79.830824
2013-03-03 13:00:01,463  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 79.991582
2013-03-03 13:00:01,964  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 80.142549
2013-03-03 13:00:02,465  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 80.311359
2013-03-03 13:00:02,967  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 80.466351
2013-03-03 13:00:03,468  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 80.641472
2013-03-03 13:00:03,969  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 80.809888
2013-03-03 13:00:04,470  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 80.958841
2013-03-03 13:00:04,971  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 81.109535
2013-03-03 13:00:05,472  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 81.258489
2013-03-03 13:00:05,973  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 81.387314
2013-03-03 13:00:06,475  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 81.519892
2013-03-03 13:00:06,976  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 81.652742
2013-03-03 13:00:07,477  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 81.743322
2013-03-03 13:00:07,978  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 81.877913
2013-03-03 13:00:08,480  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 82.006738
2013-03-03 13:00:08,981  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 82.093292
2013-03-03 13:00:09,482  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 82.222117
2013-03-03 13:00:09,983  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 82.336184
2013-03-03 13:00:10,484  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 82.446893
2013-03-03 13:00:10,985  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 82.551563
2013-03-03 13:00:11,486  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 82.712594
2013-03-03 13:00:11,987  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 82.812218
2013-03-03 13:00:12,489  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 82.943055
2013-03-03 13:00:12,990  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 83.073893
2013-03-03 13:00:13,491  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 83.206471
2013-03-03 13:00:13,992  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 83.327244
2013-03-03 13:00:14,493  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 83.448017
2013-03-03 13:00:14,994  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 83.572544
2013-03-03 13:00:15,495  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 83.715459
2013-03-03 13:00:15,997  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 83.856361
2013-03-03 13:00:16,498  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 83.989211
2013-03-03 13:00:16,999  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 84.122062
2013-03-03 13:00:17,500  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 84.255510
2013-03-03 13:00:18,001  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 84.366219
2013-03-03 13:00:18,502  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 84.486992
2013-03-03 13:00:19,003  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 84.617557
2013-03-03 13:00:19,504  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 84.744369
2013-03-03 13:00:20,005  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 84.871181
2013-03-03 13:00:20,506  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 85.012640
2013-03-03 13:00:21,007  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 85.145490
2013-03-03 13:00:21,509  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 85.274315
2013-03-03 13:00:22,010  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 85.406893
2013-03-03 13:00:22,511  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 85.539744
2013-03-03 13:00:23,012  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 85.674607
2013-03-03 13:00:23,513  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 85.815237
2013-03-03 13:00:24,014  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 85.927958
2013-03-03 13:00:24,515  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 86.018538
2013-03-03 13:00:25,016  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 86.148314
2013-03-03 13:00:25,517  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 86.287204
2013-03-03 13:00:26,018  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 86.409990
2013-03-03 13:00:26,519  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 86.546866
2013-03-03 13:00:27,021  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 86.675024
2013-03-03 13:00:27,522  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 86.787746
2013-03-03 13:00:28,023  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 86.882351
2013-03-03 13:00:28,524  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 86.990380
2013-03-03 13:00:29,025  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 87.111153
2013-03-03 13:00:29,526  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 87.225888
2013-03-03 13:00:30,027  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 87.332571
2013-03-03 13:00:30,528  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 87.442613
2013-03-03 13:00:31,030  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 87.561373
2013-03-03 13:00:31,531  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 87.688185
2013-03-03 13:00:32,032  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 87.825061
2013-03-03 13:00:32,533  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 87.957680
2013-03-03 13:00:33,035  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 88.090530
2013-03-03 13:00:33,536  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 88.221490
2013-03-03 13:00:34,037  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 88.362392
2013-03-03 13:00:34,538  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 88.495242
2013-03-03 13:00:35,039  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 88.630106
2013-03-03 13:00:35,540  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 88.767934
2013-03-03 13:00:36,041  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 88.896758
2013-03-03 13:00:36,542  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 89.031349
2013-03-03 13:00:37,043  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 89.166213
2013-03-03 13:00:37,544  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 89.295037
2013-03-03 13:00:38,045  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 89.450030
2013-03-03 13:00:38,546  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 89.601553
2013-03-03 13:00:39,047  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 89.744468
2013-03-03 13:00:39,548  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 89.891409
2013-03-03 13:00:40,049  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 90.033262
2013-03-03 13:00:40,550  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 90.170139
2013-03-03 13:00:41,051  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 90.300704
2013-03-03 13:00:41,553  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 90.433554
2013-03-03 13:00:42,054  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 90.566405
2013-03-03 13:00:42,555  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 90.713346
2013-03-03 13:00:43,056  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 90.855240
2013-03-03 13:00:43,557  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 90.996142
2013-03-03 13:00:44,058  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 91.139057
2013-03-03 13:00:44,559  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 91.286119
2013-03-03 13:00:45,060  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 91.451176
2013-03-03 13:00:45,561  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 91.600130
2013-03-03 13:00:46,062  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 91.750075
2013-03-03 13:00:46,564  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 91.905068
2013-03-03 13:00:47,065  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 92.039931
2013-03-03 13:00:47,566  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 92.176535
2013-03-03 13:00:48,067  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 92.341592
2013-03-03 13:00:48,568  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 92.474442
2013-03-03 13:00:49,069  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 92.602205
2013-03-03 13:00:49,570  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 92.759211
2013-03-03 13:00:50,071  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 92.912190
2013-03-03 13:00:50,572  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 93.041177
2013-03-03 13:00:51,074  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 93.180067
2013-03-03 13:00:51,575  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 93.335059
2013-03-03 13:00:52,076  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 93.435036
2013-03-03 13:00:52,577  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 93.594054
2013-03-03 13:00:53,078  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 93.757098
2013-03-03 13:00:53,579  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 93.824869
2013-03-03 13:00:54,080  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 93.981874
2013-03-03 13:00:54,582  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 94.150957
2013-03-03 13:00:55,083  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 94.235226
2013-03-03 13:00:55,584  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 94.384179
2013-03-03 13:00:56,085  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 94.533133
2013-03-03 13:00:56,586  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 94.709600
2013-03-03 13:00:57,087  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 94.868618
2013-03-03 13:00:57,588  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 95.001196
2013-03-03 13:00:58,089  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 95.113918
2013-03-03 13:00:58,590  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 95.228652
2013-03-03 13:00:59,091  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 95.335335
2013-03-03 13:00:59,592  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 95.436931
2013-03-03 13:01:00,093  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 95.533550
2013-03-03 13:01:00,594  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 95.642245
2013-03-03 13:01:01,095  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 95.746916
2013-03-03 13:01:01,596  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 95.861377
2013-03-03 13:01:02,097  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 95.966048
2013-03-03 13:01:02,598  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 96.076756
2013-03-03 13:01:03,099  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 96.179414
2013-03-03 13:01:03,601  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 96.293481
2013-03-03 13:01:04,102  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 96.408216
2013-03-03 13:01:04,603  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 96.512886
2013-03-03 13:01:05,104  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 96.623322
2013-03-03 13:01:05,605  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 96.727992
2013-03-03 13:01:06,106  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 96.826624
2013-03-03 13:01:06,607  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 96.935320
2013-03-03 13:01:07,108  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.039717
2013-03-03 13:01:07,609  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.150426
2013-03-03 13:01:08,111  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.261135
2013-03-03 13:01:08,612  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.350172
2013-03-03 13:01:09,112  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.350172
2013-03-03 13:01:09,614  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.350172
2013-03-03 13:01:09,631  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.350173
2013-03-03 13:01:09,632  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.350173
2013-03-03 13:01:09,633  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.350173
2013-03-03 13:01:09,834  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.350173
2013-03-03 13:01:10,031  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.350173
2013-03-03 13:01:10,324  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.369227
2013-03-03 13:01:10,324  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.369227
2013-03-03 13:01:10,491  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.369227
2013-03-03 13:01:10,992  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.451756
2013-03-03 13:01:11,493  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.574542
2013-03-03 13:01:11,994  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.677199
2013-03-03 13:01:12,495  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.779856
2013-03-03 13:01:12,996  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.882514
2013-03-03 13:01:13,496  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 97.987184
2013-03-03 13:01:13,998  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 98.069712
2013-03-03 13:01:14,499  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 98.174382
2013-03-03 13:01:15,000  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 98.275027
2013-03-03 13:01:15,501  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 98.359568
2013-03-03 13:01:16,002  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 98.454174
2013-03-03 13:01:16,504  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 98.547961
2013-03-03 13:01:17,005  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 98.642567
2013-03-03 13:01:17,506  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 98.708992
2013-03-03 13:01:18,007  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 98.809637
2013-03-03 13:01:18,509  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 98.912021
2013-03-03 13:01:19,010  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 99.010653
2013-03-03 13:01:19,511  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 99.115323
2013-03-03 13:01:20,012  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 99.226032
2013-03-03 13:01:20,513  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 99.330702
2013-03-03 13:01:21,014  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 99.437385
2013-03-03 13:01:21,515  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 99.540640
2013-03-03 13:01:22,017  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 99.639271
2013-03-03 13:01:22,518  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 99.749980
2013-03-03 13:01:23,019  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 99.856390
2013-03-03 13:01:23,520  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 99.965086
2013-03-03 13:01:23,671  DEBUG: download progress <Package: name:'nvidia-experimental-310'  architecture='amd64' id:89594L> 100.000000
2013-03-03 13:01:24,767 DEBUG: install progress dpkg-exec 0.000000
2013-03-03 13:01:26,597 DEBUG: install progress dkms 0.000000
2013-03-03 13:01:26,697 DEBUG: install progress dkms 4.000000
2013-03-03 13:01:27,412 DEBUG: install progress dkms 8.000000
2013-03-03 13:01:27,497 DEBUG: install progress dkms 12.000000
2013-03-03 13:01:27,931 DEBUG: install progress fakeroot 12.000000
2013-03-03 13:01:28,032 DEBUG: install progress fakeroot 16.000000
2013-03-03 13:01:28,378 DEBUG: install progress fakeroot 20.000000
2013-03-03 13:01:28,466 DEBUG: install progress fakeroot 24.000000
2013-03-03 13:01:29,074 DEBUG: install progress nvidia-experimental-310 24.000000
2013-03-03 13:01:29,075 DEBUG: install progress nvidia-experimental-310 28.000000
2013-03-03 13:01:38,164 DEBUG: install progress nvidia-experimental-310 32.000000
2013-03-03 13:01:38,242 DEBUG: install progress nvidia-experimental-310 36.000000
2013-03-03 13:01:38,591 DEBUG: install progress screen-resolution-extra 36.000000
2013-03-03 13:01:38,692 DEBUG: install progress screen-resolution-extra 40.000000
2013-03-03 13:01:38,909 DEBUG: install progress screen-resolution-extra 44.000000
2013-03-03 13:01:38,986 DEBUG: install progress screen-resolution-extra 48.000000
2013-03-03 13:01:39,328 DEBUG: install progress nvidia-settings-experimental-310 48.000000
2013-03-03 13:01:39,428 DEBUG: install progress nvidia-settings-experimental-310 52.000000
2013-03-03 13:01:39,767 DEBUG: install progress nvidia-settings-experimental-310 56.000000
2013-03-03 13:01:39,845 DEBUG: install progress nvidia-settings-experimental-310 60.000000
2013-03-03 13:01:39,927 DEBUG: install progress man-db 60.000000
2013-03-03 13:01:42,912 DEBUG: install progress desktop-file-utils 60.000000
2013-03-03 13:01:43,160 DEBUG: install progress bamfdaemon 60.000000
2013-03-03 13:01:43,340 DEBUG: install progress gnome-menus 60.000000
2013-03-03 13:01:43,704 DEBUG: install progress dpkg-exec 60.000000
2013-03-03 13:01:43,742 DEBUG: install progress dkms 60.000000
2013-03-03 13:01:45,019 DEBUG: install progress dkms 64.000000
2013-03-03 13:01:45,100 DEBUG: install progress dkms 68.000000
2013-03-03 13:01:45,177 DEBUG: install progress fakeroot 68.000000
2013-03-03 13:01:45,256 DEBUG: install progress fakeroot 72.000000
2013-03-03 13:01:45,705 DEBUG: install progress fakeroot 76.000000
2013-03-03 13:01:45,883 DEBUG: install progress nvidia-experimental-310 76.000000
2013-03-03 13:01:46,109 DEBUG: install progress nvidia-experimental-310 80.000000
2013-03-03 13:01:47,474 DEBUG: install progress nvidia-experimental-310 84.000000
2013-03-03 13:01:47,808 DEBUG: install progress screen-resolution-extra 84.000000
2013-03-03 13:01:47,943 DEBUG: install progress screen-resolution-extra 88.000000
2013-03-03 13:01:48,819 DEBUG: install progress screen-resolution-extra 92.000000
2013-03-03 13:01:48,948 DEBUG: install progress nvidia-settings-experimental-310 92.000000
2013-03-03 13:01:49,015 DEBUG: install progress nvidia-settings-experimental-310 96.000000
2013-03-03 13:01:49,333 DEBUG: install progress nvidia-settings-experimental-310 100.000000
2013-03-03 13:01:49,524 DEBUG: install progress bamfdaemon 100.000000
2013-03-03 13:01:49,818 DEBUG: install progress initramfs-tools 100.000000
2013-03-03 13:02:09,265 DEBUG: Selecting previously unselected package dkms.
(Reading database ... 158674 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1.1ubuntu1.1_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.4-2_amd64.deb) ...
Selecting previously unselected package nvidia-experimental-310.
Unpacking nvidia-experimental-310 (from .../nvidia-experimental-310_310.14-0ubuntu1_amd64.deb) ...
Selecting previously unselected package screen-resolution-extra.
Unpacking screen-resolution-extra (from .../screen-resolution-extra_0.15_all.deb) ...
Selecting previously unselected package nvidia-settings-experimental-310.
Unpacking nvidia-settings-experimental-310 (from .../nvidia-settings-experimental-310_310.14-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up dkms (2.2.0.3-1.1ubuntu1.1) ...
Setting up fakeroot (1.18.4-2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up nvidia-experimental-310 (310.14-0ubuntu1) ...
update-alternatives:  using /usr/lib/nvidia-experimental-310/ld.so.conf to provide  /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in  auto mode
update-alternatives: using  /usr/lib/nvidia-experimental-310/alt_ld.so.conf to provide  /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in  auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-experimental-310
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Loading new nvidia-experimental-310-310.14 DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-17-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Setting up screen-resolution-extra (0.15) ...
Setting up nvidia-settings-experimental-310 (310.14-0ubuntu1) ...
update-alternatives:  using /usr/lib/nvidia-settings-experimental-310/ld.so.conf to provide  /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in auto  mode
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic

2013-03-03  13:02:09,378 WARNING: modinfo for module nvidia_experimental_310  failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-03-03  13:02:09,379 WARNING: /sys/module/nvidia_experimental_310/drivers does  not exist, cannot rebind nvidia_experimental_310 driver
```

I think this mean I need to install binary ones, or whatelse? also I had ran command sudo apt-get install linux-headers-generic and installed headers.

---

### Post by D0Ct0Rh4cK on 2013-03-03
Also When I run jockey-kde it says me Error: "/var/tmp/kdecache-d0ct0r-h4ck" is owned by uid 1000 instead of uid 0.

I don't know if it's somehow related to such a problem.

ran by sudo of course.

I have been constrict to format my pc, so we are starting by a situation without drivers to let you assist me from scratch, so can I install binary ones by additional drivers, and see what's next?

---

### Post by darkod on 2013-03-03
So, did you try activating any of the other drivers? I would never use experimental, regardless what you read. Don't forget that what works for few people might not work for all. If they are still called experimental, I would ignore them.
That screen shows that no other driver is activated. I assume you tried activating one of the others.

---

### Post by D0Ct0Rh4cK on 2013-03-03
> **darkod said:**
> So, did you try activating any of the other drivers? I would never use experimental, regardless what you read. Don't forget that what works for few people might not work for all. If they are still called experimental, I would ignore them.
That screen shows that no other driver is activated. I assume you tried activating one of the others.

As far as I told you above by such screen that I messed up before with drivers, I have been constrict to format in order to help you help me to start from scratch, (I don't know for what reason it shows 4 drivers but basically are just two, one experimental and one binary), now I am installing binary to see what happens next.... when I had been installing it, it had shown me a screen missing the top and lateral bars, so I wasn't able to do nothing... will install it and eventually will screen you what the situation really is.

EDIT: when I tried to install it by additional drivers it says me same error got for experimental ones..... now what?

---

### Post by oldfred on 2013-03-03
Did you install headers first. It says you do not have kernel source.

>  First Installation: checking all kernels...
Building only for 3.5.0-17-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.



       # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic


 #To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
 # [ using the correct names] for each driver, before running: 
sudo apt-get purge nvidia*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

---

### Post by D0Ct0Rh4cK on 2013-03-04
everythings I try it's all useless... whatever I install I get same result... screen with low resolution 640x480 missing lateral and top bars.... I am about to give up at this point.....

---

### Post by oldfred on 2013-03-04
Did you turn off the Intel Video in UEFI/BIOS or disable the nVidia. Many have to install with one or the other. Then maybe bumblebee will work.

       Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

---

### Post by D0Ct0Rh4cK on 2013-03-04
> **oldfred said:**
> Did you turn off the Intel Video in UEFI/BIOS or disable the nVidia. Many have to install with one or the other. Then maybe bumblebee will work.

       Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

Are you sure about the fact that it works also with a video card like mine which is Nvidia Geforce GT 520M 512MB? sorry if I am utterly skeptical about that but the word optimus makes me think it's about more recent video cards, but I can be wrong as well.

Thanks

---

### Post by oldfred on 2013-03-04
[http://www.geforce.com/hardware/notebook-gpus/geforce-gt-520m](http://www.geforce.com/hardware/notebook-gpus/geforce-gt-520m)
> *NVIDIA*® *GeForce*® *GT 520M* GPUs deliver 2X the performance of integrated graphics and long battery life you demand with *NVIDIA*® Optimus™ technology, **...**

---

### Post by Mr. Shannon on 2013-03-04
If you have an NVIDIA optimus setup, integrated Intel with a dedicated NVIDIA card, then you need [http://bumblebee-project.org](http://bumblebee-project.org).  Please do not attempt to use the ubuntu-x-swat PPA (that is for older Ubuntu versions).  
```

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install linux-headers-generic
sudo apt-get install bumblebee bumblebee-nvidia

```
You could also switch to all integrated or all dedicated graphics in your BIOS.

You should verify that your BIOS is set to optimus graphics before installing bumblebee.

---

### Post by D0Ct0Rh4cK on 2013-03-05
YAHOOOOO looks like it works... now let's explain a few things... as far  as this is a particular process I wanna share as much details as  possible in order to help people who need to get rid of this the fastest  way as possible.

here it is what I've done....

let's say we got a CLEAN ubuntu installation without drivers nor anything else( otherwise let's get rid of them by using --purge command)

also... first thing we have to do is installing headers as most guys out there skip such a step by typing:

[PHP]sudo apt-get install linux-headers-generic[/PHP]

then I've ran following commands:

This installs repository needed to find bumblebee's package otherwise it will say unable to locate package:

[PHP]sudo add-apt-repository ppa:bumblebee/stable && sudo apt-get update[/PHP]

At this point you just have to follow what's explained in this post:

[http://ubuntuforums.org/showthread.php?t=2077451&p=12324348#post12324348](http://ubuntuforums.org/showthread.php?t=2077451&p=12324348#post12324348)

It doesn't explain where to find repository command then I've felt it fair to unite all in a single post because I know how messy it is being in such a situation.

After that just reboot and everything should be setup and ready to go as it was with me!

just don't be scared if it doesn't show your video card in system settings as I guess this is and has always been an ubuntu's bug... also I don't know why if I run

sudo nvidia-settings it says:

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

but by typing nvidia-xconfig on a terminal 

it just answers:

nvidia-xconfig: command not found

I guess this happens because of bumblebee's mood as an alternative way to install is there someone else who can confirm it?

For the rest I am satisfied :D :D

EDIT: I almost forgot if you need to get .deb file get it from here as it's not said in the post linked above [https://launchpad.net/ubuntu/raring/amd64/nvidia-current/](https://launchpad.net/ubuntu/raring/amd64/nvidia-current/)

---

