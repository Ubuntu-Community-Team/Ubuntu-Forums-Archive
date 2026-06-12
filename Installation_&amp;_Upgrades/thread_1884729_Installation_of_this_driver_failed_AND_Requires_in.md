---
title: "Installation of this driver failed AND Requires installation of untrusted packages"
date: 2011-11-21
forum: Installation &amp; Upgrades
---

### Post by cric2085 on 2011-11-21
I just bought Asus 1215B and installed ubuntu 11.10.  Please excuse me I am totally new to ubuntu and I mean virgin new

I tried to update drivers and I am getting this message:
"Sorry, installation of this driver failed.  Please have a look at the log file for details: /var/log/jockey.log"  
I dont know where to find this log file in my computer

Second problem,
I have 233 update under the update manager.  When I tried to update all the important security updates, I get the following message:
"Requires installation of untrusted packages.  The action would require the installation of packages from unauthenticated sources."
I am not too sure what is the message referring and hence would not let me install any updates.

Any help would be really appreciated, and please keep in mind I am a complete newbie to linux.

Thanks,

---

### Post by dino99 on 2011-11-22
use "nautilus" to browse your files/folders
use "synaptic" to deal with updates/upgrades

more info following the links below

---

### Post by Mark Phelps on 2011-11-22
The first problem is referring to installing restricted drivers -- which failed.  The log file is in the location it told you: /var/log/jockey.log.

To find that, you have to click on the home icon in the launcher.  You'll probably see something there labeled filesystem.  Double-click that and Nautilus file manager will open.  Then, you have to navigate to /var, and then to /log under that. Once there, you should see the log file.  Double-click on that and it will be opened with Gedit.

---

### Post by cric2085 on 2011-11-22
Hello Thanks for you reply..... I have decided to reinstall the OS (ubuntu)... Every thing went well (which includes the installing all the updates) but I am still having problems with the Installation of this driver.   For some reasons, my computer does not want to activate the driver and throws an error dialog box.

The current Driver I am trying to activate are:
1) ATI/AMD proprietary FGLRX Graphics Driver (Post Release Update)
2) ATI/AMD proprietary FGLRX Graphics Driver

Additionally I have a small black watermark box on my bottom right of the screen with message "AMD Unsupported hardware"  
[EDIT]  The watermark box disappeared after I restarted my computer but the still not able to activate the driver.

The log file are as follows:
```

2011-11-22 13:45:06,632 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c>
2011-11-22 13:45:10,322 DEBUG: reading modalias file /lib/modules/3.0.0-13-generic-pae/modules.alias
2011-11-22 13:45:10,703 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-11-22 13:45:10,722 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-11-22 13:45:10,815 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-11-22 13:45:10,869 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-11-22 13:45:10,925 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-11-22 13:45:10,926 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-11-22 13:45:10,926 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-11-22 13:45:10,926 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-11-22 13:45:10,965 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-11-22 13:45:10,965 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-11-22 13:45:10,965 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-11-22 13:45:11,048 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-11-22 13:45:11,055 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-11-22 13:45:11,056 DEBUG: nvidia.available: falling back to default
2011-11-22 13:45:11,279 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-22 13:45:11,285 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-11-22 13:45:11,291 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-11-22 13:45:11,291 DEBUG: nvidia.available: falling back to default
2011-11-22 13:45:11,351 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-22 13:45:11,360 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-11-22 13:45:11,369 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-11-22 13:45:11,370 DEBUG: nvidia.available: falling back to default
2011-11-22 13:45:11,458 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-22 13:45:11,458 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-11-22 13:45:11,489 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-11-22 13:45:11,500 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-11-22 13:45:11,501 DEBUG: nvidia.available: falling back to default
2011-11-22 13:45:11,578 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-22 13:45:11,584 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-11-22 13:45:11,590 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-11-22 13:45:11,591 DEBUG: nvidia.available: falling back to default
2011-11-22 13:45:11,653 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-22 13:45:11,659 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-11-22 13:45:11,665 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-11-22 13:45:11,666 DEBUG: nvidia.available: falling back to default
2011-11-22 13:45:11,730 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-22 13:45:11,730 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-11-22 13:45:11,796 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-11-22 13:45:11,918 DEBUG: Software modem not available
2011-11-22 13:45:11,919 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-11-22 13:45:11,952 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-11-22 13:45:11,953 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-11-22 13:45:11,987 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-11-22 13:45:11,987 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-11-22 13:45:12,029 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-22 13:45:12,039 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-11-22 13:45:12,039 DEBUG: fglrx.available: falling back to default
2011-11-22 13:45:12,152 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-22 13:45:12,159 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-22 13:45:12,165 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-11-22 13:45:12,166 DEBUG: fglrx.available: falling back to default
2011-11-22 13:45:12,257 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-11-22 13:45:12,258 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-11-22 13:45:12,368 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-11-22 13:45:12,369 DEBUG: Firmware for DVB cards not available
2011-11-22 13:45:12,369 DEBUG: all custom handlers loaded
2011-11-22 13:45:12,369 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001002d00001314sv00001043sd000084E3bc04sc03i00')
2011-11-22 13:45:12,988 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-22 13:45:13,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:13,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-11-22 13:45:13,223 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 13:45:13,223 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:13,224 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2011-11-22 13:45:13,253 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-11-22 13:45:13,253 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:13,254 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2011-11-22 13:45:13,254 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-22 13:45:13,254 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-22 13:45:13,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001A3Bsd00002047bc02sc80i00')
2011-11-22 13:45:13,344 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2011-11-22 13:45:13,512 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:13,345 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-11-22 13:45:13,653 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:13,512 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-11-22 13:45:13,654 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2011-11-22 13:45:13,654 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:13,654 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2011-11-22 13:45:13,655 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:13,655 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2011-11-22 13:45:13,791 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:13,655 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-11-22 13:45:13,924 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:13,792 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-11-22 13:45:13,924 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-22 13:45:13,925 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-22 13:45:13,926 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 13:45:13,926 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:13,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'platform:pcspkr')
2011-11-22 13:45:13,927 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-11-22 13:45:13,927 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:13,928 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-11-22 13:45:13,928 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:13,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-22 13:45:13,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2011-11-22 13:45:13,972 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-22 13:45:13,972 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 13:45:13,973 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:13,973 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-22 13:45:13,974 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-22 13:45:13,974 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2011-11-22 13:45:13,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-11-22 13:45:13,976 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2011-11-22 13:45:13,984 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'platform:regulatory')
2011-11-22 13:45:13,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'wmi:ABBC0F72-8EA1-11D1-00A0-C90629100000')
2011-11-22 13:45:13,985 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'eeepc_wmi'}
2011-11-22 13:45:13,985 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'eeepc_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:13,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001022d00001510sv00001022sd00001510bc06sc00i00')
2011-11-22 13:45:13,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2011-11-22 13:45:13,987 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001969d00002062sv00001043sd00008468bc02sc00i00')
2011-11-22 13:45:13,994 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'atl1c'}
2011-11-22 13:45:13,995 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:13,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-22 13:45:13,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001002d00009806sv00001043sd000084E3bc03sc00i00')
2011-11-22 13:45:14,003 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-11-22 13:45:14,569 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 13:45:14,569 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 13:45:14,003 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-22 13:45:14,579 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-22 13:45:14,587 DEBUG: fglrx.available: falling back to default
2011-11-22 13:45:14,698 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 13:45:14,698 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 13:45:14,650 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-22 13:45:14,699 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-11-22 13:45:14,744 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 13:45:14,744 DEBUG: fglrx is not the alternative in use
2011-11-22 13:45:14,699 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-22 13:45:14,754 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-22 13:45:14,762 DEBUG: fglrx.available: falling back to default
2011-11-22 13:45:14,844 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 13:45:14,844 DEBUG: fglrx is not the alternative in use
2011-11-22 13:45:14,801 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-22 13:45:14,845 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-11-22 13:45:14,845 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-22 13:45:14,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001002d00004391sv00001002sd00004390bc01sc06i01')
2011-11-22 13:45:14,854 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-22 13:45:14,854 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,854 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-22 13:45:14,854 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-22 13:45:14,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-22 13:45:14,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-11-22 13:45:14,856 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2011-11-22 13:45:14,857 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001002d00004385sv00001002sd00004385bc0Csc05i00')
2011-11-22 13:45:14,865 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2011-11-22 13:45:14,865 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,866 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2011-11-22 13:45:14,866 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,866 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2011-11-22 13:45:14,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-22 13:45:14,867 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 13:45:14,867 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'input:b0003v13D3p5702e0322-e0,1,kD4,ramlsfw')
2011-11-22 13:45:14,868 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 13:45:14,868 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,868 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-11-22 13:45:14,868 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 13:45:14,869 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,869 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-11-22 13:45:14,876 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0401:bd06/17/2011:svnASUSTeKComputerINC.:pn1215B:pvrx.x:rvnASUSTeKComputerINC.:rn1215B:rvrx.xx:cvnASUSTeKComputerINC.:ct10:cvrx.x:')
2011-11-22 13:45:14,906 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-22 13:45:14,906 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-11-22 13:45:14,906 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 13:45:14,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-22 13:45:14,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'usb:v13D3p5702d0322dcEFdsc02dp01ic0Eisc01ip00')
2011-11-22 13:45:14,941 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-11-22 13:45:14,942 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-22 13:45:14,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-22 13:45:14,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2011-11-22 13:45:14,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-11-22 13:45:14,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'wmi:466747A0-70EC-11DE-8A39-0800200C9A66')
2011-11-22 13:45:14,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001B21d00001042sv00001043sd00008488bc0Csc03i30')
2011-11-22 13:45:14,944 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2011-11-22 13:45:14,945 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,945 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000841Cbc04sc03i00')
2011-11-22 13:45:14,955 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-22 13:45:14,956 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,956 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-22 13:45:14,958 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,958 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'platform:eeepc-wmi')
2011-11-22 13:45:14,964 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-11-22 13:45:14,965 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 13:45:14,965 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,965 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-22 13:45:14,965 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,966 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-22 13:45:14,966 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,966 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-22 13:45:14,966 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,966 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-22 13:45:14,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'usb:v13D3p5702d0322dcEFdsc02dp01ic0Eisc02ip00')
2011-11-22 13:45:14,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-11-22 13:45:14,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'platform:eisa')
2011-11-22 13:45:14,969 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2011-11-22 13:45:14,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-11-22 13:45:14,986 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-11-22 13:45:14,986 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,987 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-11-22 13:45:14,988 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-22 13:45:14,989 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 13:45:14,990 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-11-22 13:45:14,997 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,94,98,AB,B8,B9,BF,D4,E3,EE,F0,F4,215,216,217,218,219,21A,ram4,lsfw')
2011-11-22 13:45:14,998 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 13:45:14,998 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,998 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-11-22 13:45:14,998 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 13:45:14,999 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 13:45:14,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72d564c> about HardwareID('modalias', 'acpi:SYN0A13:SYN0A00:SYN0002:PNP0F03:PNP0F13:PNP0F12:')
2011-11-22 13:45:14,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001002d00001314sv00001043sd000084E3bc04sc03i00')
2011-11-22 13:45:14,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-11-22 13:45:14,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2011-11-22 13:45:15,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2011-11-22 13:45:15,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-22 13:45:15,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-22 13:45:15,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001A3Bsd00002047bc02sc80i00')
2011-11-22 13:45:15,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-22 13:45:15,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-22 13:45:15,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'platform:pcspkr')
2011-11-22 13:45:15,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-22 13:45:15,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2011-11-22 13:45:15,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-22 13:45:15,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-22 13:45:15,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-22 13:45:15,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2011-11-22 13:45:15,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-11-22 13:45:15,002 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2011-11-22 13:45:15,002 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'platform:regulatory')
2011-11-22 13:45:15,002 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'wmi:ABBC0F72-8EA1-11D1-00A0-C90629100000')
2011-11-22 13:45:15,002 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001022d00001510sv00001022sd00001510bc06sc00i00')
2011-11-22 13:45:15,002 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2011-11-22 13:45:15,002 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001969d00002062sv00001043sd00008468bc02sc00i00')
2011-11-22 13:45:15,002 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-22 13:45:15,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001002d00009806sv00001043sd000084E3bc03sc00i00')
2011-11-22 13:45:15,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-22 13:45:15,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001002d00004391sv00001002sd00004390bc01sc06i01')
2011-11-22 13:45:15,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-22 13:45:15,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-22 13:45:15,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-11-22 13:45:15,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2011-11-22 13:45:15,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001002d00004385sv00001002sd00004385bc0Csc05i00')
2011-11-22 13:45:15,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2011-11-22 13:45:15,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-22 13:45:15,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'input:b0003v13D3p5702e0322-e0,1,kD4,ramlsfw')
2011-11-22 13:45:15,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-11-22 13:45:15,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-11-22 13:45:15,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0401:bd06/17/2011:svnASUSTeKComputerINC.:pn1215B:pvrx.x:rvnASUSTeKComputerINC.:rn1215B:rvrx.xx:cvnASUSTeKComputerINC.:ct10:cvrx.x:')
2011-11-22 13:45:15,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-22 13:45:15,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-11-22 13:45:15,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-22 13:45:15,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'usb:v13D3p5702d0322dcEFdsc02dp01ic0Eisc01ip00')
2011-11-22 13:45:15,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-22 13:45:15,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-22 13:45:15,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2011-11-22 13:45:15,006 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-11-22 13:45:15,006 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'wmi:466747A0-70EC-11DE-8A39-0800200C9A66')
2011-11-22 13:45:15,006 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001B21d00001042sv00001043sd00008488bc0Csc03i30')
2011-11-22 13:45:15,006 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000841Cbc04sc03i00')
2011-11-22 13:45:15,006 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'platform:eeepc-wmi')
2011-11-22 13:45:15,006 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-11-22 13:45:15,006 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-22 13:45:15,007 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'usb:v13D3p5702d0322dcEFdsc02dp01ic0Eisc02ip00')
2011-11-22 13:45:15,007 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-11-22 13:45:15,007 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'platform:eisa')
2011-11-22 13:45:15,007 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2011-11-22 13:45:15,007 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-11-22 13:45:15,007 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-22 13:45:15,007 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-11-22 13:45:15,008 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,94,98,AB,B8,B9,BF,D4,E3,EE,F0,F4,215,216,217,218,219,21A,ram4,lsfw')
2011-11-22 13:45:15,008 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-11-22 13:45:15,008 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69ca7ac> about HardwareID('modalias', 'acpi:SYN0A13:SYN0A00:SYN0002:PNP0F03:PNP0F13:PNP0F12:')
2011-11-22 13:45:15,195 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 13:45:15,195 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 13:45:15,253 DEBUG: handler xorg:fglrx_updates previously unseen
2011-11-22 13:45:15,254 DEBUG: handler kmod:wl previously unseen
2011-11-22 13:45:15,525 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:15,526 DEBUG: handler kmod:wl previously unused
2011-11-22 13:45:15,526 DEBUG: handler xorg:fglrx previously unseen
2011-11-22 13:45:15,526 DEBUG: writing back check cache /var/cache/jockey/check
2011-11-22 13:45:15,566 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 13:45:15,566 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 13:45:15,700 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:15,701 DEBUG: kmod:wl is already enabled or not available, not announcing
2011-11-22 13:45:15,742 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 13:45:15,742 DEBUG: fglrx is not the alternative in use
2011-11-22 13:45:15,925 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:16,196 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:16,270 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 13:45:16,270 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 13:45:16,364 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 13:45:16,365 DEBUG: fglrx is not the alternative in use
2011-11-22 13:45:16,524 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:16,794 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:16,945 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 13:45:16,945 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 13:45:17,162 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 13:45:17,162 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 13:45:17,423 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:17,769 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:34,711 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:34,989 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:35,130 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 13:45:35,131 DEBUG: fglrx is not the alternative in use
2011-11-22 13:45:36,176 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:36,454 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:36,593 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 13:45:36,593 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 13:45:37,758 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:38,032 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:39,722 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 13:45:39,723 DEBUG: fglrx is not the alternative in use
2011-11-22 13:45:41,351 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:41,627 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 13:45:41,766 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 13:45:41,767 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 13:51:37,282 DEBUG: Shutting down
2011-11-22 14:10:04,663 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c>
2011-11-22 14:10:10,367 DEBUG: reading modalias file /lib/modules/3.0.0-13-generic-pae/modules.alias
2011-11-22 14:10:10,693 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-11-22 14:10:10,701 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-11-22 14:10:10,802 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-11-22 14:10:10,832 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-11-22 14:10:10,894 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-11-22 14:10:10,895 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-11-22 14:10:10,896 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-11-22 14:10:10,896 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-11-22 14:10:10,981 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-11-22 14:10:10,982 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-11-22 14:10:10,983 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-11-22 14:10:11,061 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-11-22 14:10:11,069 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-11-22 14:10:11,069 DEBUG: nvidia.available: falling back to default
2011-11-22 14:10:11,273 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-22 14:10:11,279 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-11-22 14:10:11,285 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-11-22 14:10:11,286 DEBUG: nvidia.available: falling back to default
2011-11-22 14:10:11,345 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-22 14:10:11,351 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-11-22 14:10:11,357 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-11-22 14:10:11,357 DEBUG: nvidia.available: falling back to default
2011-11-22 14:10:11,417 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-22 14:10:11,417 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-11-22 14:10:11,448 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-11-22 14:10:11,460 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-11-22 14:10:11,461 DEBUG: nvidia.available: falling back to default
2011-11-22 14:10:11,524 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-22 14:10:11,531 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-11-22 14:10:11,538 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-11-22 14:10:11,538 DEBUG: nvidia.available: falling back to default
2011-11-22 14:10:11,606 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-22 14:10:11,612 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-11-22 14:10:11,619 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-11-22 14:10:11,619 DEBUG: nvidia.available: falling back to default
2011-11-22 14:10:11,678 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-22 14:10:11,679 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-11-22 14:10:11,733 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-11-22 14:10:11,763 DEBUG: Software modem not available
2011-11-22 14:10:11,764 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-11-22 14:10:11,771 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-11-22 14:10:11,771 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-11-22 14:10:11,826 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-11-22 14:10:11,826 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-11-22 14:10:11,860 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-22 14:10:11,871 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-11-22 14:10:11,872 DEBUG: fglrx.available: falling back to default
2011-11-22 14:10:11,945 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-22 14:10:11,950 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-22 14:10:11,957 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-11-22 14:10:11,957 DEBUG: fglrx.available: falling back to default
2011-11-22 14:10:12,049 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-11-22 14:10:12,049 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-11-22 14:10:12,144 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-11-22 14:10:12,145 DEBUG: Firmware for DVB cards not available
2011-11-22 14:10:12,145 DEBUG: all custom handlers loaded
2011-11-22 14:10:12,145 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001002d00001314sv00001043sd000084E3bc04sc03i00')
2011-11-22 14:10:12,808 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-22 14:10:13,028 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:13,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-11-22 14:10:13,041 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:10:13,042 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:13,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2011-11-22 14:10:13,071 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-11-22 14:10:13,071 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:13,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2011-11-22 14:10:13,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-22 14:10:13,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-22 14:10:13,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001A3Bsd00002047bc02sc80i00')
2011-11-22 14:10:13,158 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2011-11-22 14:10:13,342 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:10:13,158 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-11-22 14:10:13,482 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:10:13,342 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-11-22 14:10:13,483 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2011-11-22 14:10:13,483 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:13,483 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2011-11-22 14:10:13,483 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:13,484 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2011-11-22 14:10:13,611 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:10:13,484 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-11-22 14:10:13,750 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:10:13,612 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-11-22 14:10:13,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-22 14:10:13,752 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-22 14:10:13,752 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:10:13,752 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:13,752 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'platform:pcspkr')
2011-11-22 14:10:13,753 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-11-22 14:10:13,754 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:13,754 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-11-22 14:10:13,754 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:13,754 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-22 14:10:13,797 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2011-11-22 14:10:13,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-22 14:10:13,798 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:10:13,798 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:13,799 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-22 14:10:13,800 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-22 14:10:13,800 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2011-11-22 14:10:13,800 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'platform:regulatory')
2011-11-22 14:10:13,801 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2011-11-22 14:10:13,809 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-11-22 14:10:13,811 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'wmi:ABBC0F72-8EA1-11D1-00A0-C90629100000')
2011-11-22 14:10:13,811 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'eeepc_wmi'}
2011-11-22 14:10:13,811 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'eeepc_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:13,811 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001022d00001510sv00001022sd00001510bc06sc00i00')
2011-11-22 14:10:13,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2011-11-22 14:10:13,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001969d00002062sv00001043sd00008468bc02sc00i00')
2011-11-22 14:10:13,820 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'atl1c'}
2011-11-22 14:10:13,820 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:13,820 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-22 14:10:13,820 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001002d00009806sv00001043sd000084E3bc03sc00i00')
2011-11-22 14:10:13,828 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-11-22 14:10:14,471 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 14:10:14,472 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:10:13,828 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-22 14:10:14,480 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-22 14:10:14,489 DEBUG: fglrx.available: falling back to default
2011-11-22 14:10:14,564 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 14:10:14,564 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:10:14,524 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-22 14:10:14,564 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-11-22 14:10:14,604 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 14:10:14,605 DEBUG: fglrx is not the alternative in use
2011-11-22 14:10:14,565 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-22 14:10:14,611 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-22 14:10:14,617 DEBUG: fglrx.available: falling back to default
2011-11-22 14:10:14,699 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 14:10:14,700 DEBUG: fglrx is not the alternative in use
2011-11-22 14:10:14,652 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-22 14:10:14,700 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-11-22 14:10:14,700 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-22 14:10:14,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001002d00004391sv00001002sd00004390bc01sc06i01')
2011-11-22 14:10:14,709 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-22 14:10:14,709 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,709 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-22 14:10:14,710 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-22 14:10:14,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-22 14:10:14,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-11-22 14:10:14,711 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2011-11-22 14:10:14,712 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001002d00004385sv00001002sd00004385bc0Csc05i00')
2011-11-22 14:10:14,720 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2011-11-22 14:10:14,720 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,720 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2011-11-22 14:10:14,720 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,720 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2011-11-22 14:10:14,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-22 14:10:14,721 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:10:14,722 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'input:b0003v13D3p5702e0322-e0,1,kD4,ramlsfw')
2011-11-22 14:10:14,722 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:10:14,722 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-11-22 14:10:14,723 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:10:14,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-11-22 14:10:14,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0401:bd06/17/2011:svnASUSTeKComputerINC.:pn1215B:pvrx.x:rvnASUSTeKComputerINC.:rn1215B:rvrx.xx:cvnASUSTeKComputerINC.:ct10:cvrx.x:')
2011-11-22 14:10:14,759 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-22 14:10:14,759 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-11-22 14:10:14,760 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:10:14,760 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-22 14:10:14,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'usb:v13D3p5702d0322dcEFdsc02dp01ic0Eisc01ip00')
2011-11-22 14:10:14,794 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-11-22 14:10:14,794 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-22 14:10:14,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-22 14:10:14,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2011-11-22 14:10:14,796 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-11-22 14:10:14,796 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'wmi:466747A0-70EC-11DE-8A39-0800200C9A66')
2011-11-22 14:10:14,797 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001B21d00001042sv00001043sd00008488bc0Csc03i30')
2011-11-22 14:10:14,797 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2011-11-22 14:10:14,797 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,797 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000841Cbc04sc03i00')
2011-11-22 14:10:14,805 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-22 14:10:14,805 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,805 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-22 14:10:14,806 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,806 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'platform:eeepc-wmi')
2011-11-22 14:10:14,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-11-22 14:10:14,807 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:10:14,807 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,808 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-22 14:10:14,808 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,808 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-22 14:10:14,808 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,808 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-22 14:10:14,809 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,809 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-22 14:10:14,809 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'usb:v13D3p5702d0322dcEFdsc02dp01ic0Eisc02ip00')
2011-11-22 14:10:14,810 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-11-22 14:10:14,810 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'platform:eisa')
2011-11-22 14:10:14,811 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2011-11-22 14:10:14,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-11-22 14:10:14,828 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-11-22 14:10:14,828 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,829 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-11-22 14:10:14,829 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,829 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-22 14:10:14,829 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:10:14,829 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,830 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-11-22 14:10:14,837 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,94,98,AB,B8,B9,BF,D4,E3,EE,F0,F4,215,216,217,218,219,21A,ram4,lsfw')
2011-11-22 14:10:14,838 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:10:14,838 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,838 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-11-22 14:10:14,838 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:10:14,839 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:10:14,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb720064c> about HardwareID('modalias', 'acpi:SYN0A13:SYN0A00:SYN0002:PNP0F03:PNP0F13:PNP0F12:')
2011-11-22 14:10:14,839 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001002d00001314sv00001043sd000084E3bc04sc03i00')
2011-11-22 14:10:14,839 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-11-22 14:10:14,839 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2011-11-22 14:10:14,839 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2011-11-22 14:10:14,840 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-22 14:10:14,840 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-22 14:10:14,840 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001A3Bsd00002047bc02sc80i00')
2011-11-22 14:10:14,840 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-22 14:10:14,840 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-22 14:10:14,840 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'platform:pcspkr')
2011-11-22 14:10:14,840 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-22 14:10:14,841 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2011-11-22 14:10:14,841 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-22 14:10:14,841 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-22 14:10:14,841 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-22 14:10:14,841 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2011-11-22 14:10:14,841 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'platform:regulatory')
2011-11-22 14:10:14,841 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2011-11-22 14:10:14,842 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-11-22 14:10:14,842 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'wmi:ABBC0F72-8EA1-11D1-00A0-C90629100000')
2011-11-22 14:10:14,842 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001022d00001510sv00001022sd00001510bc06sc00i00')
2011-11-22 14:10:14,842 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2011-11-22 14:10:14,842 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001969d00002062sv00001043sd00008468bc02sc00i00')
2011-11-22 14:10:14,842 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-22 14:10:14,842 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001002d00009806sv00001043sd000084E3bc03sc00i00')
2011-11-22 14:10:14,843 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-22 14:10:14,843 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001002d00004391sv00001002sd00004390bc01sc06i01')
2011-11-22 14:10:14,843 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-22 14:10:14,843 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-22 14:10:14,843 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-11-22 14:10:14,843 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2011-11-22 14:10:14,844 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001002d00004385sv00001002sd00004385bc0Csc05i00')
2011-11-22 14:10:14,844 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2011-11-22 14:10:14,844 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-22 14:10:14,844 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'input:b0003v13D3p5702e0322-e0,1,kD4,ramlsfw')
2011-11-22 14:10:14,844 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-11-22 14:10:14,844 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-11-22 14:10:14,844 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0401:bd06/17/2011:svnASUSTeKComputerINC.:pn1215B:pvrx.x:rvnASUSTeKComputerINC.:rn1215B:rvrx.xx:cvnASUSTeKComputerINC.:ct10:cvrx.x:')
2011-11-22 14:10:14,845 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-22 14:10:14,845 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-11-22 14:10:14,845 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-22 14:10:14,845 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'usb:v13D3p5702d0322dcEFdsc02dp01ic0Eisc01ip00')
2011-11-22 14:10:14,845 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-22 14:10:14,845 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-22 14:10:14,845 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2011-11-22 14:10:14,845 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-11-22 14:10:14,846 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'wmi:466747A0-70EC-11DE-8A39-0800200C9A66')
2011-11-22 14:10:14,846 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001B21d00001042sv00001043sd00008488bc0Csc03i30')
2011-11-22 14:10:14,846 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000841Cbc04sc03i00')
2011-11-22 14:10:14,846 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'platform:eeepc-wmi')
2011-11-22 14:10:14,846 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-11-22 14:10:14,846 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-22 14:10:14,846 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'usb:v13D3p5702d0322dcEFdsc02dp01ic0Eisc02ip00')
2011-11-22 14:10:14,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-11-22 14:10:14,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'platform:eisa')
2011-11-22 14:10:14,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2011-11-22 14:10:14,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-11-22 14:10:14,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-22 14:10:14,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-11-22 14:10:14,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,94,98,AB,B8,B9,BF,D4,E3,EE,F0,F4,215,216,217,218,219,21A,ram4,lsfw')
2011-11-22 14:10:14,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-11-22 14:10:14,848 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f47ac> about HardwareID('modalias', 'acpi:SYN0A13:SYN0A00:SYN0002:PNP0F03:PNP0F13:PNP0F12:')
2011-11-22 14:10:15,035 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 14:10:15,036 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:10:15,281 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:10:15,539 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:10:15,704 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 14:10:15,704 DEBUG: fglrx is not the alternative in use
2011-11-22 14:10:15,848 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 14:10:15,849 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:10:16,056 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 14:10:16,057 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:10:16,259 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:10:16,543 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:10:37,028 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-11-22 14:10:37,029 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:10:41,086 DEBUG: Installing package: fglrx-updates
2011-11-22 14:10:41,808 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.000000
2011-11-22 14:10:41,812 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.000000
2011-11-22 14:10:41,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.000000
2011-11-22 14:10:42,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.000000
2011-11-22 14:10:42,299 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.003810
2011-11-22 14:10:42,800 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.183837
2011-11-22 14:10:43,302 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.816365
2011-11-22 14:10:43,803 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 2.032763
2011-11-22 14:10:44,305 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 2.217655
2011-11-22 14:10:44,807 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 2.446338
2011-11-22 14:10:45,309 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 2.777199
2011-11-22 14:10:45,810 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 3.312414
2011-11-22 14:10:46,312 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 3.691930
2011-11-22 14:10:46,814 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 4.660183
2011-11-22 14:10:47,316 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 5.438678
2011-11-22 14:10:47,817 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 6.222038
2011-11-22 14:10:48,319 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 7.234082
2011-11-22 14:10:48,821 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 8.250991
2011-11-22 14:10:49,323 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 9.336018
2011-11-22 14:10:49,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 10.352927
2011-11-22 14:10:50,326 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 11.447685
2011-11-22 14:10:50,828 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 12.459729
2011-11-22 14:10:51,330 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 13.573949
2011-11-22 14:10:51,832 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 14.274595
2011-11-22 14:10:52,333 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 14.873063
2011-11-22 14:10:52,835 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 15.510455
2011-11-22 14:10:53,336 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 16.172176
2011-11-22 14:10:53,838 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 16.809569
2011-11-22 14:10:54,340 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 17.578333
2011-11-22 14:10:54,841 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 18.274112
2011-11-22 14:10:55,343 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 18.979623
2011-11-22 14:10:55,845 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 19.675403
2011-11-22 14:10:56,347 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 20.293333
2011-11-22 14:10:56,848 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 21.032904
2011-11-22 14:10:57,350 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 21.738415
2011-11-22 14:10:57,852 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 22.638549
2011-11-22 14:10:58,353 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 23.645727
2011-11-22 14:10:58,855 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 24.764813
2011-11-22 14:10:59,357 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 25.616292
2011-11-22 14:10:59,859 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 25.621158
2011-11-22 14:11:00,361 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 26.696454
2011-11-22 14:11:00,862 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 27.260863
2011-11-22 14:11:01,364 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 27.757153
2011-11-22 14:11:01,866 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 28.885971
2011-11-22 14:11:02,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 30.058579
2011-11-22 14:11:02,869 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 31.012235
2011-11-22 14:11:03,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 31.698284
2011-11-22 14:11:03,873 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 32.486510
2011-11-22 14:11:04,375 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 32.900085
2011-11-22 14:11:04,876 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 33.581268
2011-11-22 14:11:05,378 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 34.437612
2011-11-22 14:11:05,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 35.196645
2011-11-22 14:11:06,381 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 36.082183
2011-11-22 14:11:06,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 36.846081
2011-11-22 14:11:07,385 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 37.644038
2011-11-22 14:11:07,887 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 38.539307
2011-11-22 14:11:08,389 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 39.473501
2011-11-22 14:11:08,890 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 40.261727
2011-11-22 14:11:09,393 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 41.346754
2011-11-22 14:11:09,895 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 42.538825
2011-11-22 14:11:10,397 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 43.614121
2011-11-22 14:11:10,899 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 44.626164
2011-11-22 14:11:11,400 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 45.545761
2011-11-22 14:11:11,902 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 46.698907
2011-11-22 14:11:12,404 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 47.530923
2011-11-22 14:11:12,906 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 48.703531
2011-11-22 14:11:13,407 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 49.666919
2011-11-22 14:11:13,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 50.640037
2011-11-22 14:11:14,411 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 51.608290
2011-11-22 14:11:14,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 52.581409
2011-11-22 14:11:15,414 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 53.705361
2011-11-22 14:11:15,916 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 54.634689
2011-11-22 14:11:16,418 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 55.641867
2011-11-22 14:11:16,919 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 56.707432
2011-11-22 14:11:17,421 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 57.675685
2011-11-22 14:11:17,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 58.746115
2011-11-22 14:11:18,425 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 59.836008
2011-11-22 14:11:18,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 60.969691
2011-11-22 14:11:19,428 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 62.307729
2011-11-22 14:11:19,930 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 63.485203
2011-11-22 14:11:20,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 64.171251
2011-11-22 14:11:20,935 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 65.202757
2011-11-22 14:11:21,436 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 66.278053
2011-11-22 14:11:21,938 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 67.509048
2011-11-22 14:11:22,439 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 68.511360
2011-11-22 14:11:22,941 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 69.562328
2011-11-22 14:11:23,444 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 70.632759
2011-11-22 14:11:23,946 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 71.771308
2011-11-22 14:11:24,449 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 72.900125
2011-11-22 14:11:24,951 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 73.946228
2011-11-22 14:11:25,453 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 75.089642
2011-11-22 14:11:25,954 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 76.169804
2011-11-22 14:11:26,456 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 77.206175
2011-11-22 14:11:26,958 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 78.412842
2011-11-22 14:11:27,459 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 79.561122
2011-11-22 14:11:27,961 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 80.758058
2011-11-22 14:11:28,151 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 80.860971
2011-11-22 14:11:28,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 80.873791
2011-11-22 14:11:28,653 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 81.831321
2011-11-22 14:11:29,155 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 82.945542
2011-11-22 14:11:29,657 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 83.728902
2011-11-22 14:11:30,159 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 84.405220
2011-11-22 14:11:30,661 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 85.178849
2011-11-22 14:11:31,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 86.259011
2011-11-22 14:11:31,665 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 87.524065
2011-11-22 14:11:32,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 88.798850
2011-11-22 14:11:32,668 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 89.986055
2011-11-22 14:11:33,170 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 91.095410
2011-11-22 14:11:33,672 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 92.068529
2011-11-22 14:11:34,173 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 93.031916
2011-11-22 14:11:34,676 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 93.985573
2011-11-22 14:11:35,180 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 94.905170
2011-11-22 14:11:35,681 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 95.956138
2011-11-22 14:11:36,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 97.002240
2011-11-22 14:11:36,685 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 97.989956
2011-11-22 14:11:37,186 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 99.031193
2011-11-22 14:11:37,688 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 99.921596
2011-11-22 14:11:37,866 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 100.000000
2011-11-22 14:11:39,755 DEBUG: install progress dpkg-exec 0.000000
2011-11-22 14:11:43,219 DEBUG: install progress fglrx-updates 0.000000
2011-11-22 14:11:43,320 DEBUG: install progress fglrx-updates 10.000000
2011-11-22 14:11:47,292 DEBUG: install progress fglrx-updates 20.000000
2011-11-22 14:11:47,387 DEBUG: install progress fglrx-updates 30.000000
2011-11-22 14:11:47,639 DEBUG: install progress fglrx-amdcccle-updates 30.000000
2011-11-22 14:11:47,741 DEBUG: install progress fglrx-amdcccle-updates 40.000000
2011-11-22 14:11:48,412 DEBUG: install progress fglrx-amdcccle-updates 50.000000
2011-11-22 14:11:48,506 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2011-11-22 14:11:48,602 DEBUG: install progress ureadahead 60.000000
2011-11-22 14:11:49,070 DEBUG: install progress dpkg-exec 60.000000
2011-11-22 14:11:49,143 DEBUG: install progress fglrx-updates 60.000000
2011-11-22 14:11:49,640 DEBUG: install progress fglrx-updates 70.000000
2011-11-22 14:13:06,729 DEBUG: install progress fglrx-updates 80.000000
2011-11-22 14:13:07,485 DEBUG: install progress bamfdaemon 80.000000
2011-11-22 14:13:07,773 DEBUG: install progress gnome-menus 80.000000
2011-11-22 14:13:08,104 DEBUG: install progress fglrx-amdcccle-updates 80.000000
2011-11-22 14:13:08,237 DEBUG: install progress fglrx-amdcccle-updates 90.000000
2011-11-22 14:13:08,337 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2011-11-22 14:13:08,483 DEBUG: install progress initramfs-tools 100.000000
2011-11-22 14:13:30,919 DEBUG: install progress libc-bin 100.000000
2011-11-22 14:13:32,428 DEBUG: Selecting previously deselected package fglrx-updates.
(Reading database ... 165658 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.902-0ubuntu0.1_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.902-0ubuntu0.1_i386.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up fglrx-updates (2:8.902-0ubuntu0.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
Loading new fglrx-updates-8.902 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-13-generic-pae
Building for architecture i686
Building initial module for 3.0.0-13-generic-pae
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-13-generic-pae/updates/dkms/

depmod.........

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle-updates (2:8.902-0ubuntu0.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-11-22 14:13:32,972 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-11-22 14:13:33,127 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-11-22 14:13:33,358 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:13:33,359 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:13:33,436 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:13:33,436 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:14:09,459 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:14:09,459 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:14:09,538 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:14:09,539 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:14:09,758 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:14:10,042 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:14:10,191 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:14:10,192 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:14:10,350 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:14:10,351 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:14:10,430 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:14:10,431 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:14:10,645 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:14:10,646 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:14:10,717 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:14:10,718 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:14:10,920 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:14:11,201 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:20:59,339 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:20:59,339 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:21:05,476 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:21:05,476 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:21:09,225 DEBUG: Installing package: fglrx
2011-11-22 14:21:09,914 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 0.000000
2011-11-22 14:21:09,918 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 0.000000
2011-11-22 14:21:10,215 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 0.000000
2011-11-22 14:21:10,375 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 0.000000
2011-11-22 14:21:10,556 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 0.000000
2011-11-22 14:21:11,061 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 0.166281
2011-11-22 14:21:11,563 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 0.597413
2011-11-22 14:21:12,065 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 1.662563
2011-11-22 14:21:12,566 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 2.955960
2011-11-22 14:21:13,068 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 4.447170
2011-11-22 14:21:13,570 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 5.441310
2011-11-22 14:21:14,071 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 7.120190
2011-11-22 14:21:14,573 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 8.408514
2011-11-22 14:21:15,075 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 9.681622
2011-11-22 14:21:15,577 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 10.756917
2011-11-22 14:21:16,079 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 11.898149
2011-11-22 14:21:16,580 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 13.079958
2011-11-22 14:21:17,082 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 14.332778
2011-11-22 14:21:17,583 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 15.474010
2011-11-22 14:21:18,085 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 16.686252
2011-11-22 14:21:18,586 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 17.832557
2011-11-22 14:21:19,088 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 18.973789
2011-11-22 14:21:19,590 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 20.160671
2011-11-22 14:21:20,091 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 20.505576
2011-11-22 14:21:20,593 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 20.889182
2011-11-22 14:21:21,094 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 20.962069
2011-11-22 14:21:21,596 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 21.312047
2011-11-22 14:21:22,098 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 21.459139
2011-11-22 14:21:22,600 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 22.143879
2011-11-22 14:21:23,101 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 22.950350
2011-11-22 14:21:23,603 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 23.812614
2011-11-22 14:21:24,105 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 24.679951
2011-11-22 14:21:24,607 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 25.592936
2011-11-22 14:21:25,111 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 26.561716
2011-11-22 14:21:25,615 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 27.591361
2011-11-22 14:21:26,116 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 28.443481
2011-11-22 14:21:26,617 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 29.346323
2011-11-22 14:21:27,119 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 30.213659
2011-11-22 14:21:27,621 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 31.228088
2011-11-22 14:21:28,123 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 32.267877
2011-11-22 14:21:28,625 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 33.322883
2011-11-22 14:21:29,126 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 34.377889
2011-11-22 14:21:29,628 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 35.372029
2011-11-22 14:21:30,130 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 36.381386
2011-11-22 14:21:30,632 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 37.360309
2011-11-22 14:21:31,133 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 38.374738
2011-11-22 14:21:31,635 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 39.450033
2011-11-22 14:21:32,137 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 40.555760
2011-11-22 14:21:32,638 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 41.742641
2011-11-22 14:21:33,147 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 43.030966
2011-11-22 14:21:33,648 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 44.364940
2011-11-22 14:21:34,150 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 45.369224
2011-11-22 14:21:34,651 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 46.535817
2011-11-22 14:21:35,153 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 47.545174
2011-11-22 14:21:35,657 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 48.716839
2011-11-22 14:21:36,159 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 50.015308
2011-11-22 14:21:36,660 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 51.095674
2011-11-22 14:21:37,162 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 52.130391
2011-11-22 14:21:37,664 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 53.210758
2011-11-22 14:21:38,166 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 54.351990
2011-11-22 14:21:38,668 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 55.493223
2011-11-22 14:21:39,169 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 56.675032
2011-11-22 14:21:39,671 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 57.983645
2011-11-22 14:21:40,173 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 59.185743
2011-11-22 14:21:40,674 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 60.286398
2011-11-22 14:21:41,176 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 61.427630
2011-11-22 14:21:41,678 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 62.568863
2011-11-22 14:21:42,179 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 63.831826
2011-11-22 14:21:42,681 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 65.104935
2011-11-22 14:21:43,182 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 66.291816
2011-11-22 14:21:43,684 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 67.580141
2011-11-22 14:21:44,186 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 68.822816
2011-11-22 14:21:44,687 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 69.811884
2011-11-22 14:21:45,189 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 70.998765
2011-11-22 14:21:45,691 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 72.124781
2011-11-22 14:21:46,193 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 73.479044
2011-11-22 14:21:46,695 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 74.894172
2011-11-22 14:21:47,196 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 76.228145
2011-11-22 14:21:47,698 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 77.308512
2011-11-22 14:21:48,200 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 78.317868
2011-11-22 14:21:48,702 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 78.997536
2011-11-22 14:21:49,203 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 80.265572
2011-11-22 14:21:49,348 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 80.423204
2011-11-22 14:21:49,349 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 80.426794
2011-11-22 14:21:49,850 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 81.219250
2011-11-22 14:21:50,352 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 82.101803
2011-11-22 14:21:50,854 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 82.999573
2011-11-22 14:21:51,355 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 84.019073
2011-11-22 14:21:51,857 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 84.932059
2011-11-22 14:21:52,359 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 85.779107
2011-11-22 14:21:52,860 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 86.641372
2011-11-22 14:21:53,362 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 87.544213
2011-11-22 14:21:53,863 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 88.563714
2011-11-22 14:21:54,365 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 89.588287
2011-11-22 14:21:54,867 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 90.719375
2011-11-22 14:21:55,368 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 91.789597
2011-11-22 14:21:55,870 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 92.920685
2011-11-22 14:21:56,371 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 94.058162
2011-11-22 14:21:56,873 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 95.380675
2011-11-22 14:21:57,381 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 96.496546
2011-11-22 14:21:57,883 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 97.607346
2011-11-22 14:21:58,384 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 98.743506
2011-11-22 14:21:58,886 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 99.859378
2011-11-22 14:21:58,932 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 100.000000
2011-11-22 14:21:59,359 DEBUG: install progress dpkg-exec 0.000000
2011-11-22 14:21:59,781 DEBUG: install progress fglrx-amdcccle-updates 0.000000
2011-11-22 14:21:59,874 DEBUG: install progress fglrx-amdcccle-updates 6.250000
2011-11-22 14:21:59,875 DEBUG: install progress fglrx-amdcccle-updates 12.500000
2011-11-22 14:22:00,055 DEBUG: install progress fglrx-amdcccle-updates 18.750000
2011-11-22 14:22:00,575 DEBUG: install progress fglrx-updates 18.750000
2011-11-22 14:22:00,676 DEBUG: install progress fglrx-updates 25.000000
2011-11-22 14:22:05,030 DEBUG: install progress fglrx-updates 31.250000
2011-11-22 14:22:05,704 DEBUG: install progress fglrx-updates 37.500000
2011-11-22 14:22:05,839 DEBUG: install progress bamfdaemon 37.500000
2011-11-22 14:22:06,008 DEBUG: install progress gnome-menus 37.500000
2011-11-22 14:22:06,131 DEBUG: install progress ureadahead 37.500000
2011-11-22 14:22:06,276 DEBUG: install progress initramfs-tools 37.500000
2011-11-22 14:22:27,323 DEBUG: install progress libc-bin 37.500000
2011-11-22 14:22:27,843 DEBUG: install progress dpkg-exec 37.500000
2011-11-22 14:22:28,641 DEBUG: install progress fglrx 37.500000
2011-11-22 14:22:28,742 DEBUG: install progress fglrx 43.750000
2011-11-22 14:22:31,894 DEBUG: install progress fglrx 50.000000
2011-11-22 14:22:32,006 DEBUG: install progress fglrx 56.250000
2011-11-22 14:22:32,319 DEBUG: install progress fglrx-amdcccle 56.250000
2011-11-22 14:22:32,420 DEBUG: install progress fglrx-amdcccle 62.500000
2011-11-22 14:22:33,052 DEBUG: install progress fglrx-amdcccle 68.750000
2011-11-22 14:22:33,182 DEBUG: install progress fglrx-amdcccle 75.000000
2011-11-22 14:22:33,322 DEBUG: install progress ureadahead 75.000000
2011-11-22 14:22:33,758 DEBUG: install progress dpkg-exec 75.000000
2011-11-22 14:22:33,833 DEBUG: install progress fglrx 75.000000
2011-11-22 14:22:34,328 DEBUG: install progress fglrx 81.250000
2011-11-22 14:23:18,707 DEBUG: install progress fglrx 87.500000
2011-11-22 14:23:19,385 DEBUG: install progress bamfdaemon 87.500000
2011-11-22 14:23:19,597 DEBUG: install progress gnome-menus 87.500000
2011-11-22 14:23:19,830 DEBUG: install progress fglrx-amdcccle 87.500000
2011-11-22 14:23:19,929 DEBUG: install progress fglrx-amdcccle 93.750000
2011-11-22 14:23:20,030 DEBUG: install progress fglrx-amdcccle 100.000000
2011-11-22 14:23:20,130 DEBUG: install progress initramfs-tools 100.000000
2011-11-22 14:23:42,582 DEBUG: install progress libc-bin 100.000000
2011-11-22 14:23:44,089 DEBUG: (Reading database ... 165886 files and directories currently installed.)
Removing fglrx-amdcccle-updates ...
Removing fglrx-updates ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package fglrx.
(Reading database ... 165663 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.881-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.881-0ubuntu4.1_i386.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.881-0ubuntu4.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
Loading new fglrx-8.881 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-13-generic-pae
Building for architecture i686
Building initial module for 3.0.0-13-generic-pae
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-13-generic-pae/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle (2:8.881-0ubuntu4.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-11-22 14:24:28,007 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:24:28,007 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:24:28,270 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:24:28,271 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:24:28,617 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:24:28,617 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:24:28,681 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:24:28,681 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:24:28,927 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:24:29,200 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:24:29,356 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:24:29,357 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:24:29,571 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:24:29,571 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:24:29,882 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:24:29,883 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:24:30,104 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:24:30,105 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:24:30,464 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:24:30,464 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:24:30,548 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:24:30,548 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:24:30,760 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:24:31,039 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:24:36,305 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:24:36,306 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:24:36,525 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:24:36,526 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:24:41,741 DEBUG: Shutting down
2011-11-22 14:29:41,084 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c>
2011-11-22 14:29:44,868 DEBUG: reading modalias file /lib/modules/3.0.0-13-generic-pae/modules.alias
2011-11-22 14:29:45,159 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-11-22 14:29:45,167 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-11-22 14:29:45,259 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-11-22 14:29:45,311 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-11-22 14:29:45,388 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-11-22 14:29:45,389 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-11-22 14:29:45,390 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-11-22 14:29:45,390 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-11-22 14:29:45,458 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-11-22 14:29:45,459 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-11-22 14:29:45,459 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-11-22 14:29:45,547 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-11-22 14:29:45,558 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-11-22 14:29:45,559 DEBUG: nvidia.available: falling back to default
2011-11-22 14:29:45,806 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-22 14:29:45,816 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-11-22 14:29:45,828 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-11-22 14:29:45,829 DEBUG: nvidia.available: falling back to default
2011-11-22 14:29:45,932 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-22 14:29:45,941 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-11-22 14:29:45,953 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-11-22 14:29:45,954 DEBUG: nvidia.available: falling back to default
2011-11-22 14:29:46,065 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-22 14:29:46,066 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-11-22 14:29:46,090 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-11-22 14:29:46,102 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-11-22 14:29:46,103 DEBUG: nvidia.available: falling back to default
2011-11-22 14:29:46,202 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-22 14:29:46,211 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-11-22 14:29:46,224 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-11-22 14:29:46,224 DEBUG: nvidia.available: falling back to default
2011-11-22 14:29:46,334 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-22 14:29:46,345 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-11-22 14:29:46,356 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-11-22 14:29:46,357 DEBUG: nvidia.available: falling back to default
2011-11-22 14:29:46,467 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-22 14:29:46,467 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-11-22 14:29:46,536 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-11-22 14:29:46,575 DEBUG: Software modem not available
2011-11-22 14:29:46,576 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-11-22 14:29:46,587 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-11-22 14:29:46,588 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-11-22 14:29:46,666 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-11-22 14:29:46,667 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-11-22 14:29:46,701 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-22 14:29:46,713 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-11-22 14:29:46,714 DEBUG: fglrx.available: falling back to default
2011-11-22 14:29:46,836 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-22 14:29:46,855 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-11-22 14:29:46,856 DEBUG: fglrx.available: falling back to default
2011-11-22 14:29:46,969 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-11-22 14:29:46,969 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-11-22 14:29:47,083 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-11-22 14:29:47,084 DEBUG: Firmware for DVB cards not available
2011-11-22 14:29:47,084 DEBUG: all custom handlers loaded
2011-11-22 14:29:47,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001002d00001314sv00001043sd000084E3bc04sc03i00')
2011-11-22 14:29:47,733 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-22 14:29:47,922 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:47,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-11-22 14:29:47,931 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:29:47,931 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:47,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2011-11-22 14:29:47,960 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-11-22 14:29:47,961 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:47,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2011-11-22 14:29:47,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-22 14:29:47,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-22 14:29:47,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001A3Bsd00002047bc02sc80i00')
2011-11-22 14:29:48,046 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2011-11-22 14:29:48,219 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:29:48,046 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-11-22 14:29:48,363 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:29:48,220 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-11-22 14:29:48,364 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2011-11-22 14:29:48,365 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:48,365 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2011-11-22 14:29:48,366 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:48,366 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2011-11-22 14:29:48,508 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:29:48,366 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-11-22 14:29:48,649 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:29:48,510 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-11-22 14:29:48,650 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-22 14:29:48,652 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-22 14:29:48,653 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:29:48,653 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:48,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'platform:pcspkr')
2011-11-22 14:29:48,655 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-11-22 14:29:48,656 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:48,656 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-11-22 14:29:48,657 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:48,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-22 14:29:48,705 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2011-11-22 14:29:48,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-22 14:29:48,706 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:29:48,707 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:48,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-22 14:29:48,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-22 14:29:48,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2011-11-22 14:29:48,709 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'platform:eeepc-wmi')
2011-11-22 14:29:48,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2011-11-22 14:29:48,718 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'platform:regulatory')
2011-11-22 14:29:48,719 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'wmi:ABBC0F72-8EA1-11D1-00A0-C90629100000')
2011-11-22 14:29:48,719 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'eeepc_wmi'}
2011-11-22 14:29:48,719 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'eeepc_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:48,720 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001022d00001510sv00001022sd00001510bc06sc00i00')
2011-11-22 14:29:48,720 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2011-11-22 14:29:48,720 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001969d00002062sv00001043sd00008468bc02sc00i00')
2011-11-22 14:29:48,728 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'atl1c'}
2011-11-22 14:29:48,728 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:48,728 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-22 14:29:48,729 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001002d00009806sv00001043sd000084E3bc03sc00i00')
2011-11-22 14:29:48,736 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-11-22 14:29:49,433 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:29:49,433 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:29:48,737 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-22 14:29:49,442 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-11-22 14:29:49,453 DEBUG: fglrx.available: falling back to default
2011-11-22 14:29:49,583 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:29:49,584 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:29:49,509 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-22 14:29:49,584 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-11-22 14:29:49,652 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:29:49,653 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:29:49,585 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-22 14:29:49,801 DEBUG: fglrx.available: falling back to default
2011-11-22 14:29:49,934 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:29:49,935 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:29:49,861 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-22 14:29:50,072 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-11-22 14:29:50,073 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,073 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2011-11-22 14:29:50,148 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:29:50,148 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:29:50,073 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-22 14:29:50,305 DEBUG: fglrx.available: falling back to default
2011-11-22 14:29:50,444 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:29:50,445 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:29:50,370 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-22 14:29:50,582 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-22 14:29:50,582 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001002d00004391sv00001002sd00004390bc01sc06i01')
2011-11-22 14:29:50,591 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-22 14:29:50,591 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,591 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-22 14:29:50,592 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-22 14:29:50,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-22 14:29:50,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-11-22 14:29:50,593 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2011-11-22 14:29:50,594 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001002d00004385sv00001002sd00004385bc0Csc05i00')
2011-11-22 14:29:50,602 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2011-11-22 14:29:50,602 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,602 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2011-11-22 14:29:50,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2011-11-22 14:29:50,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-22 14:29:50,604 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:29:50,604 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,604 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'input:b0003v13D3p5702e0322-e0,1,kD4,ramlsfw')
2011-11-22 14:29:50,604 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:29:50,605 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,605 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-11-22 14:29:50,605 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:29:50,605 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,605 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-11-22 14:29:50,613 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0401:bd06/17/2011:svnASUSTeKComputerINC.:pn1215B:pvrx.x:rvnASUSTeKComputerINC.:rn1215B:rvrx.xx:cvnASUSTeKComputerINC.:ct10:cvrx.x:')
2011-11-22 14:29:50,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-22 14:29:50,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-11-22 14:29:50,643 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:29:50,643 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,643 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-22 14:29:50,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'usb:v13D3p5702d0322dcEFdsc02dp01ic0Eisc01ip00')
2011-11-22 14:29:50,677 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-11-22 14:29:50,677 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-22 14:29:50,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-22 14:29:50,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2011-11-22 14:29:50,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-11-22 14:29:50,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'wmi:466747A0-70EC-11DE-8A39-0800200C9A66')
2011-11-22 14:29:50,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001B21d00001042sv00001043sd00008488bc0Csc03i30')
2011-11-22 14:29:50,680 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2011-11-22 14:29:50,680 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000841Cbc04sc03i00')
2011-11-22 14:29:50,688 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-22 14:29:50,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,689 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-22 14:29:50,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-11-22 14:29:50,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-11-22 14:29:50,691 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:29:50,691 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,691 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-22 14:29:50,691 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,692 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-22 14:29:50,692 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,692 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-22 14:29:50,692 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,692 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-22 14:29:50,692 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'usb:v13D3p5702d0322dcEFdsc02dp01ic0Eisc02ip00')
2011-11-22 14:29:50,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-11-22 14:29:50,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'platform:eisa')
2011-11-22 14:29:50,695 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2011-11-22 14:29:50,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-11-22 14:29:50,712 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-11-22 14:29:50,712 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,712 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-11-22 14:29:50,713 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,713 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-22 14:29:50,713 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:29:50,713 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-11-22 14:29:50,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,94,98,AB,B8,B9,BF,D4,E3,EE,F0,F4,215,216,217,218,219,21A,ram4,lsfw')
2011-11-22 14:29:50,722 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:29:50,722 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-11-22 14:29:50,722 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:29:50,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:29:50,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724564c> about HardwareID('modalias', 'acpi:SYN0A13:SYN0A00:SYN0002:PNP0F03:PNP0F13:PNP0F12:')
2011-11-22 14:29:50,723 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001002d00001314sv00001043sd000084E3bc04sc03i00')
2011-11-22 14:29:50,723 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-11-22 14:29:50,723 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2011-11-22 14:29:50,723 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2011-11-22 14:29:50,724 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-22 14:29:50,724 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-22 14:29:50,724 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001A3Bsd00002047bc02sc80i00')
2011-11-22 14:29:50,724 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-22 14:29:50,724 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-22 14:29:50,724 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'platform:pcspkr')
2011-11-22 14:29:50,724 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-22 14:29:50,725 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2011-11-22 14:29:50,725 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-22 14:29:50,725 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-22 14:29:50,725 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-22 14:29:50,725 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2011-11-22 14:29:50,725 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'platform:eeepc-wmi')
2011-11-22 14:29:50,725 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2011-11-22 14:29:50,726 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'platform:regulatory')
2011-11-22 14:29:50,726 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'wmi:ABBC0F72-8EA1-11D1-00A0-C90629100000')
2011-11-22 14:29:50,726 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001022d00001510sv00001022sd00001510bc06sc00i00')
2011-11-22 14:29:50,726 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2011-11-22 14:29:50,726 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001969d00002062sv00001043sd00008468bc02sc00i00')
2011-11-22 14:29:50,726 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-22 14:29:50,726 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001002d00009806sv00001043sd000084E3bc03sc00i00')
2011-11-22 14:29:50,727 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-22 14:29:50,727 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001002d00004391sv00001002sd00004390bc01sc06i01')
2011-11-22 14:29:50,727 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-22 14:29:50,727 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-22 14:29:50,727 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-11-22 14:29:50,727 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2011-11-22 14:29:50,728 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001002d00004385sv00001002sd00004385bc0Csc05i00')
2011-11-22 14:29:50,728 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2011-11-22 14:29:50,728 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-22 14:29:50,728 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'input:b0003v13D3p5702e0322-e0,1,kD4,ramlsfw')
2011-11-22 14:29:50,728 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-11-22 14:29:50,728 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-11-22 14:29:50,728 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0401:bd06/17/2011:svnASUSTeKComputerINC.:pn1215B:pvrx.x:rvnASUSTeKComputerINC.:rn1215B:rvrx.xx:cvnASUSTeKComputerINC.:ct10:cvrx.x:')
2011-11-22 14:29:50,729 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-22 14:29:50,729 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-11-22 14:29:50,729 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-22 14:29:50,729 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'usb:v13D3p5702d0322dcEFdsc02dp01ic0Eisc01ip00')
2011-11-22 14:29:50,729 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-22 14:29:50,729 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-22 14:29:50,729 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2011-11-22 14:29:50,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-11-22 14:29:50,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'wmi:466747A0-70EC-11DE-8A39-0800200C9A66')
2011-11-22 14:29:50,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001B21d00001042sv00001043sd00008488bc0Csc03i30')
2011-11-22 14:29:50,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000841Cbc04sc03i00')
2011-11-22 14:29:50,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-11-22 14:29:50,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-11-22 14:29:50,730 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-22 14:29:50,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'usb:v13D3p5702d0322dcEFdsc02dp01ic0Eisc02ip00')
2011-11-22 14:29:50,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-11-22 14:29:50,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'platform:eisa')
2011-11-22 14:29:50,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2011-11-22 14:29:50,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-11-22 14:29:50,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-22 14:29:50,731 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-11-22 14:29:50,732 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,94,98,AB,B8,B9,BF,D4,E3,EE,F0,F4,215,216,217,218,219,21A,ram4,lsfw')
2011-11-22 14:29:50,732 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-11-22 14:29:50,732 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69396ec> about HardwareID('modalias', 'acpi:SYN0A13:SYN0A00:SYN0002:PNP0F03:PNP0F13:PNP0F12:')
2011-11-22 14:29:50,848 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:29:50,849 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:29:51,199 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:29:51,466 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:29:51,632 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:29:51,633 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:29:52,033 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:29:52,034 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:29:52,248 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:29:52,248 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:29:52,456 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:29:52,728 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:29:56,691 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:29:56,692 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:30:00,485 DEBUG: Installing package: fglrx-updates
2011-11-22 14:30:03,161 DEBUG: install progress dpkg-exec 0.000000
2011-11-22 14:30:06,323 DEBUG: install progress fglrx-amdcccle 0.000000
2011-11-22 14:30:06,329 DEBUG: install progress fglrx-amdcccle 6.250000
2011-11-22 14:30:06,434 DEBUG: install progress fglrx-amdcccle 12.500000
2011-11-22 14:30:06,835 DEBUG: install progress fglrx-amdcccle 18.750000
2011-11-22 14:30:07,375 DEBUG: install progress fglrx 18.750000
2011-11-22 14:30:07,377 DEBUG: install progress fglrx 25.000000
2011-11-22 14:30:36,623 DEBUG: install progress fglrx 31.250000
2011-11-22 14:30:37,740 DEBUG: install progress fglrx 37.500000
2011-11-22 14:30:37,918 DEBUG: install progress bamfdaemon 37.500000
2011-11-22 14:30:38,185 DEBUG: install progress gnome-menus 37.500000
2011-11-22 14:30:38,352 DEBUG: install progress ureadahead 37.500000
2011-11-22 14:30:38,530 DEBUG: install progress initramfs-tools 37.500000
2011-11-22 14:31:04,061 DEBUG: install progress libc-bin 37.500000
2011-11-22 14:31:04,806 DEBUG: install progress dpkg-exec 37.500000
2011-11-22 14:31:05,676 DEBUG: install progress fglrx-updates 37.500000
2011-11-22 14:31:05,778 DEBUG: install progress fglrx-updates 43.750000
2011-11-22 14:31:10,323 DEBUG: install progress fglrx-updates 50.000000
2011-11-22 14:31:10,457 DEBUG: install progress fglrx-updates 56.250000
2011-11-22 14:31:10,744 DEBUG: install progress fglrx-amdcccle-updates 56.250000
2011-11-22 14:31:10,846 DEBUG: install progress fglrx-amdcccle-updates 62.500000
2011-11-22 14:31:11,716 DEBUG: install progress fglrx-amdcccle-updates 68.750000
2011-11-22 14:31:11,810 DEBUG: install progress fglrx-amdcccle-updates 75.000000
2011-11-22 14:31:11,939 DEBUG: install progress ureadahead 75.000000
2011-11-22 14:31:12,398 DEBUG: install progress dpkg-exec 75.000000
2011-11-22 14:31:12,475 DEBUG: install progress fglrx-updates 75.000000
2011-11-22 14:31:12,978 DEBUG: install progress fglrx-updates 81.250000
2011-11-22 14:32:05,372 DEBUG: install progress fglrx-updates 87.500000
2011-11-22 14:32:06,072 DEBUG: install progress bamfdaemon 87.500000
2011-11-22 14:32:06,328 DEBUG: install progress gnome-menus 87.500000
2011-11-22 14:32:06,660 DEBUG: install progress fglrx-amdcccle-updates 87.500000
2011-11-22 14:32:06,803 DEBUG: install progress fglrx-amdcccle-updates 93.750000
2011-11-22 14:32:06,925 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2011-11-22 14:32:07,048 DEBUG: install progress initramfs-tools 100.000000
2011-11-22 14:32:29,906 DEBUG: install progress libc-bin 100.000000
2011-11-22 14:32:31,314 DEBUG: (Reading database ... 165886 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.
update-alternatives: removing manually selected alternative - switching x86_64-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package fglrx-updates.
(Reading database ... 165666 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.902-0ubuntu0.1_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.902-0ubuntu0.1_i386.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.902-0ubuntu0.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
Loading new fglrx-updates-8.902 DKMS files...
Building only for 3.0.0-13-generic-pae
Building for architecture i686
Building initial module for 3.0.0-13-generic-pae
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-13-generic-pae/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle-updates (2:8.902-0ubuntu0.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-11-22 14:32:31,804 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-11-22 14:32:31,965 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-11-22 14:32:32,189 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:32:32,190 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:32:32,270 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:32:32,271 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:32:43,143 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:32:43,144 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:32:43,226 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:32:43,227 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:32:43,443 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:32:43,729 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:32:43,881 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:32:43,882 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:32:44,321 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:32:44,322 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:32:44,401 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:32:44,402 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:32:44,619 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:32:44,620 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:32:44,696 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:32:44,696 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:32:44,898 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:32:45,178 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:33:12,801 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:33:12,802 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:33:13,688 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:33:13,689 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:33:18,472 DEBUG: Shutting down
2011-11-22 14:33:27,693 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c>
2011-11-22 14:33:31,131 DEBUG: reading modalias file /lib/modules/3.0.0-13-generic-pae/modules.alias
2011-11-22 14:33:31,363 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-11-22 14:33:31,364 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-11-22 14:33:31,439 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-11-22 14:33:31,488 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-11-22 14:33:31,501 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-11-22 14:33:31,502 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-11-22 14:33:31,503 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-11-22 14:33:31,503 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-11-22 14:33:31,571 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-11-22 14:33:31,572 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-11-22 14:33:31,573 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-11-22 14:33:31,592 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-11-22 14:33:31,605 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-11-22 14:33:31,605 DEBUG: nvidia.available: falling back to default
2011-11-22 14:33:31,794 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-22 14:33:31,804 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-11-22 14:33:31,816 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-11-22 14:33:31,818 DEBUG: nvidia.available: falling back to default
2011-11-22 14:33:31,933 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-22 14:33:31,942 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-11-22 14:33:31,954 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-11-22 14:33:31,955 DEBUG: nvidia.available: falling back to default
2011-11-22 14:33:32,060 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-22 14:33:32,061 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-11-22 14:33:32,071 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-11-22 14:33:32,083 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-11-22 14:33:32,084 DEBUG: nvidia.available: falling back to default
2011-11-22 14:33:32,196 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-22 14:33:32,205 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-11-22 14:33:32,217 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-11-22 14:33:32,218 DEBUG: nvidia.available: falling back to default
2011-11-22 14:33:32,330 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-11-22 14:33:32,340 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-11-22 14:33:32,351 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-11-22 14:33:32,352 DEBUG: nvidia.available: falling back to default
2011-11-22 14:33:32,464 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-22 14:33:32,465 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-11-22 14:33:32,524 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-11-22 14:33:32,548 DEBUG: Software modem not available
2011-11-22 14:33:32,548 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-11-22 14:33:32,559 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-11-22 14:33:32,560 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-11-22 14:33:32,615 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-11-22 14:33:32,615 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-11-22 14:33:32,649 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-11-22 14:33:32,650 DEBUG: fglrx.available: falling back to default
2011-11-22 14:33:32,775 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-11-22 14:33:32,784 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-22 14:33:32,796 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-11-22 14:33:32,797 DEBUG: fglrx.available: falling back to default
2011-11-22 14:33:32,918 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-11-22 14:33:32,919 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-11-22 14:33:32,984 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-11-22 14:33:32,985 DEBUG: Firmware for DVB cards not available
2011-11-22 14:33:32,986 DEBUG: all custom handlers loaded
2011-11-22 14:33:32,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001002d00001314sv00001043sd000084E3bc04sc03i00')
2011-11-22 14:33:33,635 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-22 14:33:33,764 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:33,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-11-22 14:33:33,774 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:33:33,774 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:33,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2011-11-22 14:33:33,804 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2011-11-22 14:33:33,804 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:33,804 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2011-11-22 14:33:33,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-22 14:33:33,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-22 14:33:33,805 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001A3Bsd00002047bc02sc80i00')
2011-11-22 14:33:33,890 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2011-11-22 14:33:34,023 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:33:33,890 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-11-22 14:33:34,169 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:33:34,024 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-11-22 14:33:34,170 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2011-11-22 14:33:34,170 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:34,171 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2011-11-22 14:33:34,171 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:34,172 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2011-11-22 14:33:34,316 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:33:34,172 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-11-22 14:33:34,459 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:33:34,317 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-11-22 14:33:34,460 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-22 14:33:34,462 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-22 14:33:34,463 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:33:34,463 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:34,464 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'platform:pcspkr')
2011-11-22 14:33:34,466 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-11-22 14:33:34,466 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:34,466 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-11-22 14:33:34,467 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:34,467 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-22 14:33:34,514 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2011-11-22 14:33:34,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-22 14:33:34,515 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:33:34,515 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:34,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-22 14:33:34,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-22 14:33:34,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2011-11-22 14:33:34,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'platform:eeepc-wmi')
2011-11-22 14:33:34,518 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2011-11-22 14:33:34,527 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'platform:regulatory')
2011-11-22 14:33:34,528 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'wmi:ABBC0F72-8EA1-11D1-00A0-C90629100000')
2011-11-22 14:33:34,528 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'eeepc_wmi'}
2011-11-22 14:33:34,528 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'eeepc_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:34,528 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001022d00001510sv00001022sd00001510bc06sc00i00')
2011-11-22 14:33:34,529 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2011-11-22 14:33:34,529 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001969d00002062sv00001043sd00008468bc02sc00i00')
2011-11-22 14:33:34,537 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'atl1c'}
2011-11-22 14:33:34,537 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:34,537 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-22 14:33:34,538 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001002d00009806sv00001043sd000084E3bc03sc00i00')
2011-11-22 14:33:34,545 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-11-22 14:33:34,614 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:33:34,615 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:33:34,546 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-22 14:33:34,627 DEBUG: fglrx.available: falling back to default
2011-11-22 14:33:34,763 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:33:34,764 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:33:34,687 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-22 14:33:34,765 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-11-22 14:33:34,838 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:33:34,839 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:33:34,765 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-22 14:33:34,848 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-11-22 14:33:34,861 DEBUG: fglrx.available: falling back to default
2011-11-22 14:33:34,998 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:33:34,999 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:33:34,922 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-11-22 14:33:34,999 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-11-22 14:33:35,000 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,000 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2011-11-22 14:33:35,077 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:33:35,078 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:33:35,001 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-22 14:33:35,088 DEBUG: fglrx.available: falling back to default
2011-11-22 14:33:35,228 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:33:35,229 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:33:35,152 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-11-22 14:33:35,230 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-22 14:33:35,230 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001002d00004391sv00001002sd00004390bc01sc06i01')
2011-11-22 14:33:35,243 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-22 14:33:35,243 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,244 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-11-22 14:33:35,244 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-22 14:33:35,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-22 14:33:35,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-11-22 14:33:35,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2011-11-22 14:33:35,246 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001002d00004385sv00001002sd00004385bc0Csc05i00')
2011-11-22 14:33:35,254 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2011-11-22 14:33:35,254 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,254 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2011-11-22 14:33:35,255 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2011-11-22 14:33:35,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-22 14:33:35,256 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:33:35,256 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'input:b0003v13D3p5702e0322-e0,1,kD4,ramlsfw')
2011-11-22 14:33:35,257 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:33:35,257 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,257 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-11-22 14:33:35,257 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:33:35,257 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,258 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-11-22 14:33:35,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0401:bd06/17/2011:svnASUSTeKComputerINC.:pn1215B:pvrx.x:rvnASUSTeKComputerINC.:rn1215B:rvrx.xx:cvnASUSTeKComputerINC.:ct10:cvrx.x:')
2011-11-22 14:33:35,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-22 14:33:35,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-11-22 14:33:35,295 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:33:35,295 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,295 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-22 14:33:35,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'usb:v13D3p5702d0322dcEFdsc02dp01ic0Eisc01ip00')
2011-11-22 14:33:35,329 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-11-22 14:33:35,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-22 14:33:35,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-22 14:33:35,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2011-11-22 14:33:35,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-11-22 14:33:35,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'wmi:466747A0-70EC-11DE-8A39-0800200C9A66')
2011-11-22 14:33:35,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001B21d00001042sv00001043sd00008488bc0Csc03i30')
2011-11-22 14:33:35,332 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2011-11-22 14:33:35,332 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000841Cbc04sc03i00')
2011-11-22 14:33:35,340 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-22 14:33:35,341 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,341 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-11-22 14:33:35,341 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-11-22 14:33:35,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-11-22 14:33:35,343 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:33:35,343 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,343 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-22 14:33:35,343 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,343 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-22 14:33:35,344 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,344 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-11-22 14:33:35,344 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,344 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-22 14:33:35,344 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'usb:v13D3p5702d0322dcEFdsc02dp01ic0Eisc02ip00')
2011-11-22 14:33:35,345 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-11-22 14:33:35,346 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'platform:eisa')
2011-11-22 14:33:35,347 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2011-11-22 14:33:35,347 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-11-22 14:33:35,364 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-11-22 14:33:35,364 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,364 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-11-22 14:33:35,364 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-22 14:33:35,365 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:33:35,365 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,365 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-11-22 14:33:35,373 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,94,98,AB,B8,B9,BF,D4,E3,EE,F0,F4,215,216,217,218,219,21A,ram4,lsfw')
2011-11-22 14:33:35,373 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:33:35,374 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,374 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-11-22 14:33:35,374 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-11-22 14:33:35,374 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-11-22 14:33:35,374 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a964c> about HardwareID('modalias', 'acpi:SYN0A13:SYN0A00:SYN0002:PNP0F03:PNP0F13:PNP0F12:')
2011-11-22 14:33:35,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001002d00001314sv00001043sd000084E3bc04sc03i00')
2011-11-22 14:33:35,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-11-22 14:33:35,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2011-11-22 14:33:35,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2011-11-22 14:33:35,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-11-22 14:33:35,375 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-11-22 14:33:35,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001A3Bsd00002047bc02sc80i00')
2011-11-22 14:33:35,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-11-22 14:33:35,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-11-22 14:33:35,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'platform:pcspkr')
2011-11-22 14:33:35,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-11-22 14:33:35,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2011-11-22 14:33:35,376 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-11-22 14:33:35,377 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'platform:reg-dummy')
2011-11-22 14:33:35,377 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-11-22 14:33:35,377 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2011-11-22 14:33:35,377 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'platform:eeepc-wmi')
2011-11-22 14:33:35,377 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2011-11-22 14:33:35,377 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'platform:regulatory')
2011-11-22 14:33:35,377 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'wmi:ABBC0F72-8EA1-11D1-00A0-C90629100000')
2011-11-22 14:33:35,378 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001022d00001510sv00001022sd00001510bc06sc00i00')
2011-11-22 14:33:35,378 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2011-11-22 14:33:35,378 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001969d00002062sv00001043sd00008468bc02sc00i00')
2011-11-22 14:33:35,378 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-11-22 14:33:35,378 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001002d00009806sv00001043sd000084E3bc03sc00i00')
2011-11-22 14:33:35,378 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-11-22 14:33:35,378 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001002d00004391sv00001002sd00004390bc01sc06i01')
2011-11-22 14:33:35,379 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-11-22 14:33:35,379 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-11-22 14:33:35,379 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-11-22 14:33:35,379 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2011-11-22 14:33:35,379 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001002d00004385sv00001002sd00004385bc0Csc05i00')
2011-11-22 14:33:35,379 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2011-11-22 14:33:35,379 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-11-22 14:33:35,380 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'input:b0003v13D3p5702e0322-e0,1,kD4,ramlsfw')
2011-11-22 14:33:35,380 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-11-22 14:33:35,380 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001002sd00004396bc0Csc03i20')
2011-11-22 14:33:35,380 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0401:bd06/17/2011:svnASUSTeKComputerINC.:pn1215B:pvrx.x:rvnASUSTeKComputerINC.:rn1215B:rvrx.xx:cvnASUSTeKComputerINC.:ct10:cvrx.x:')
2011-11-22 14:33:35,380 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-11-22 14:33:35,380 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-11-22 14:33:35,380 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-11-22 14:33:35,381 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'usb:v13D3p5702d0322dcEFdsc02dp01ic0Eisc01ip00')
2011-11-22 14:33:35,381 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'acpi:PNP0103:')
2011-11-22 14:33:35,381 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'acpi:PNP0800:')
2011-11-22 14:33:35,381 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2011-11-22 14:33:35,381 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-11-22 14:33:35,381 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'wmi:466747A0-70EC-11DE-8A39-0800200C9A66')
2011-11-22 14:33:35,381 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001B21d00001042sv00001043sd00008488bc0Csc03i30')
2011-11-22 14:33:35,382 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000841Cbc04sc03i00')
2011-11-22 14:33:35,382 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-11-22 14:33:35,382 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-11-22 14:33:35,382 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-11-22 14:33:35,382 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'usb:v13D3p5702d0322dcEFdsc02dp01ic0Eisc02ip00')
2011-11-22 14:33:35,382 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-11-22 14:33:35,382 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'platform:eisa')
2011-11-22 14:33:35,383 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2011-11-22 14:33:35,383 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-11-22 14:33:35,383 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-11-22 14:33:35,383 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-11-22 14:33:35,383 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,94,98,AB,B8,B9,BF,D4,E3,EE,F0,F4,215,216,217,218,219,21A,ram4,lsfw')
2011-11-22 14:33:35,383 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-11-22 14:33:35,383 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9d6ec> about HardwareID('modalias', 'acpi:SYN0A13:SYN0A00:SYN0002:PNP0F03:PNP0F13:PNP0F12:')
2011-11-22 14:33:35,514 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:33:35,514 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:33:35,708 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:33:35,967 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:33:36,116 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:33:36,117 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-22 14:33:36,412 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:33:36,413 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:33:36,629 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-22 14:33:36,629 DEBUG: fglrx_updates is not the alternative in use
2011-11-22 14:33:36,837 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-11-22 14:33:37,114 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

```Once again thank you for you assistance.

---

