---
title: "kernel 3.2.0-52 removed nvidia Additional Drivers"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by orasisd on 2013-08-20
Hi, some mintues ago I installed the new kernel 3.2.0-52
After reboot everything went wrong. The boot screen was plain text, and no drives for nvidia were present in the system anymore.
Within Gnome or KDE or Xfce I can see no menu to 'Additional Drivers', I can see jockey-gtk installed though.

I run in terminal 'sudo jockey-gtk' and it opened.
No drivers were installed as previously. I went on and hit "Activate' on 'NVIDIA accelerated graphics driver (Version 304) [Recommended]' only to find out that after it's been downloaded (again) it dropped me an error saying 'Sorry installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log'

These are the contents of the log:

```

2013-08-20 09:57:02,756 DEBUG: Comparing 3.2.0-48 with 
2013-08-20 09:57:02,772 DEBUG: Comparing 3.2.0-48 with 3.2.0-48
2013-08-20 09:57:02,775 DEBUG: Comparing 3.2.0-49 with 3.2.0-48
2013-08-20 09:57:02,793 DEBUG: Comparing 3.2.0-49 with 3.2.0-49
2013-08-20 09:57:02,797 DEBUG: Comparing 3.2.0-51 with 3.2.0-49
2013-08-20 09:57:02,800 DEBUG: Comparing 3.2.0-51 with 3.2.0-51
2013-08-20 09:57:02,809 DEBUG: Comparing 3.2.0-52 with 3.2.0-51
2013-08-20 09:57:02,814 DEBUG: Comparing 3.2.0-52 with 3.2.0-52
2013-08-20 09:57:03,350 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c>
2013-08-20 09:57:07,433 DEBUG: reading modalias file /lib/modules/3.2.0-52-generic-pae/modules.alias
2013-08-20 09:57:07,579 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-08-20 09:57:07,607 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-08-20 09:57:07,699 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-08-20 09:57:07,845 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-08-20 09:57:09,224 DEBUG: linux-lts-raring installed: False
linux-lts-saucy installed: False
linux minor version: 2
xserver ABI: 11
xserver-lts-quantal: False
2013-08-20 09:57:09,226 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-08-20 09:57:09,226 DEBUG: cdv.available: falling back to default
2013-08-20 09:57:10,007 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-08-20 09:57:10,008 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-08-20 09:57:10,019 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-08-20 09:57:10,020 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-08-20 09:57:10,081 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-08-20 09:57:10,081 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-08-20 09:57:10,102 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-08-20 09:57:10,102 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-08-20 09:57:10,102 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-08-20 09:57:10,102 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-08-20 09:57:10,140 WARNING: modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12

2013-08-20 09:57:10,163 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental12 from name FglrxDriverExperimental12
2013-08-20 09:57:10,163 DEBUG: fglrx.available: falling back to default
2013-08-20 09:57:12,184 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-08-20 09:57:12,187 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-08-20 09:57:12,194 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-08-20 09:57:12,195 DEBUG: fglrx.available: falling back to default
2013-08-20 09:57:15,765 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-08-20 09:57:15,768 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-08-20 09:57:15,793 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2013-08-20 09:57:15,793 DEBUG: fglrx.available: falling back to default
2013-08-20 09:57:19,015 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-08-20 09:57:19,020 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-08-20 09:57:19,028 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverHybrid from name FglrxDriverHybrid
2013-08-20 09:57:19,028 DEBUG: fglrx.available: falling back to default
2013-08-20 09:57:24,928 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-08-20 09:57:24,934 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-08-20 09:57:24,945 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-08-20 09:57:24,945 DEBUG: fglrx.available: falling back to default
2013-08-20 09:57:29,635 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-08-20 09:57:29,639 WARNING: modinfo for module fglrx_experimental_13 failed: ERROR: modinfo: could not find module fglrx_experimental_13

2013-08-20 09:57:29,678 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental13 from name FglrxDriverExperimental13
2013-08-20 09:57:29,678 DEBUG: fglrx.available: falling back to default
2013-08-20 09:57:31,870 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-08-20 09:57:31,870 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-08-20 09:57:31,906 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-08-20 09:57:31,912 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-08-20 09:57:32,652 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-08-20 09:57:32,652 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-08-20 09:57:32,673 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-08-20 09:57:32,698 DEBUG: Software modem not available
2013-08-20 09:57:32,698 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-08-20 09:57:32,742 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304

2013-08-20 09:57:32,748 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver304 from name NvidiaDriver304
2013-08-20 09:57:32,748 DEBUG: nvidia.available: falling back to default
2013-08-20 09:57:38,572 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-08-20 09:57:38,576 WARNING: modinfo for module nvidia_304_updates failed: ERROR: modinfo: could not find module nvidia_304_updates

2013-08-20 09:57:38,584 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver304Updates from name NvidiaDriver304Updates
2013-08-20 09:57:38,585 DEBUG: nvidia.available: falling back to default
2013-08-20 09:57:44,937 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-08-20 09:57:44,944 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-08-20 09:57:44,950 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-08-20 09:57:44,951 DEBUG: nvidia.available: falling back to default
2013-08-20 09:57:44,977 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-08-20 09:57:44,983 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-08-20 09:57:45,024 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-08-20 09:57:45,025 DEBUG: nvidia.available: falling back to default
2013-08-20 09:57:45,056 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-08-20 09:57:45,062 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-08-20 09:57:45,073 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-08-20 09:57:45,073 DEBUG: nvidia.available: falling back to default
2013-08-20 09:57:45,103 DEBUG: NVIDIA accelerated graphics driver not available
2013-08-20 09:57:45,107 WARNING: modinfo for module nvidia_319 failed: ERROR: modinfo: could not find module nvidia_319

2013-08-20 09:57:45,113 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver319 from name NvidiaDriver319
2013-08-20 09:57:45,113 DEBUG: nvidia.available: falling back to default
2013-08-20 09:57:49,429 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-08-20 09:57:49,435 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-08-20 09:57:49,446 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-08-20 09:57:49,446 DEBUG: nvidia.available: falling back to default
2013-08-20 09:57:56,568 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-08-20 09:57:56,650 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-08-20 09:57:56,650 DEBUG: nvidia.available: falling back to default
2013-08-20 09:58:06,603 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-08-20 09:58:06,607 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-08-20 09:58:06,629 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-08-20 09:58:06,630 DEBUG: nvidia.available: falling back to default
2013-08-20 09:58:06,662 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-08-20 09:58:06,668 WARNING: modinfo for module nvidia_319_updates failed: ERROR: modinfo: could not find module nvidia_319_updates

2013-08-20 09:58:06,678 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver319Updates from name NvidiaDriver319Updates
2013-08-20 09:58:06,679 DEBUG: nvidia.available: falling back to default
2013-08-20 09:58:10,828 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-08-20 09:58:10,833 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-08-20 09:58:10,845 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-08-20 09:58:10,846 DEBUG: nvidia.available: falling back to default
2013-08-20 09:58:14,361 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-08-20 09:58:14,366 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-08-20 09:58:14,376 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-08-20 09:58:14,376 DEBUG: nvidia.available: falling back to default
2013-08-20 09:58:16,137 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-08-20 09:58:16,137 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-08-20 09:58:16,137 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-08-20 09:58:16,142 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-08-20 09:58:16,168 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-08-20 09:58:16,169 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-08-20 09:58:16,169 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-08-20 09:58:16,292 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-08-20 09:58:16,293 DEBUG: Firmware for DVB cards not available
2013-08-20 09:58:16,293 DEBUG: all custom handlers loaded
2013-08-20 09:58:16,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00008086d000027D8sv0000103Csd000030BBbc04sc03i00')
2013-08-20 09:58:16,640 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-08-20 09:58:16,802 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:16,802 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-08-20 09:58:16,802 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:16,803 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-08-20 09:58:16,808 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 09:58:16,808 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:16,808 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 09:58:16,808 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:16,808 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030BBbc08sc80i00')
2013-08-20 09:58:16,813 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r592'}
2013-08-20 09:58:16,813 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r592', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:16,813 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030BBbc08sc05i00')
2013-08-20 09:58:16,813 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2013-08-20 09:58:16,813 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:16,813 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2013-08-20 09:58:16,813 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:16,814 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-08-20 09:58:16,814 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-08-20 09:58:16,814 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00008086d00004222sv0000103Csd0000135Cbc02sc80i00')
2013-08-20 09:58:16,818 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwl3945'}
2013-08-20 09:58:16,818 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwl3945', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:16,818 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-08-20 09:58:16,818 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 09:58:16,818 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:16,818 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'platform:regulatory')
2013-08-20 09:58:16,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-08-20 09:58:16,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030BBbc08sc80i00')
2013-08-20 09:58:16,834 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r852'}
2013-08-20 09:58:16,834 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r852', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:16,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-08-20 09:58:16,834 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 09:58:16,834 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:16,835 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 09:58:16,835 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:16,835 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'acpi:PNP0C32:')
2013-08-20 09:58:16,835 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00008086d000027B9sv0000103Csd000030BBbc06sc01i00')
2013-08-20 09:58:16,838 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng'}
2013-08-20 09:58:16,838 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:16,838 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2013-08-20 09:58:16,839 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:16,839 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'leds_ss4200'}
2013-08-20 09:58:16,839 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'leds_ss4200', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:16,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-08-20 09:58:16,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00008086d000027CAsv0000103Csd000030BBbc0Csc03i00')
2013-08-20 09:58:16,843 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'platform:hp-wmi')
2013-08-20 09:58:16,843 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-08-20 09:58:16,844 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00008086d000027A0sv0000103Csd000030BBbc06sc00i00')
2013-08-20 09:58:16,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2013-08-20 09:58:16,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'usb:v0C45p62C0d0210dcEFdsc02dp01ic0Eisc01ip00')
2013-08-20 09:58:16,883 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-08-20 09:58:16,883 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:16,883 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'acpi:HPQ0006:')
2013-08-20 09:58:16,883 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-08-20 09:58:16,883 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v000010DEd000001D8sv0000103Csd000030BBbc03sc00i00')
2013-08-20 09:58:17,204 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173_updates'}
2013-08-20 09:58:17,319 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt /usr/lib/nvidia-173-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-173-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:58:17,319 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-20 09:58:17,205 DEBUG: found match in handler pool xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-20 09:58:17,330 DEBUG: nvidia.available: falling back to default
2013-08-20 09:58:27,302 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt /usr/lib/nvidia-173-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-173-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:58:27,302 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-20 09:58:27,286 DEBUG: got handler xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-20 09:58:27,303 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-08-20 09:58:27,303 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:27,303 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-08-20 09:58:27,303 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:58:27,303 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173_updates', 'package': 'nvidia-173-updates'}
2013-08-20 09:58:27,323 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt /usr/lib/nvidia-173-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-173-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:58:27,324 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-20 09:58:27,304 DEBUG: found match in handler pool xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-20 09:58:27,334 DEBUG: nvidia.available: falling back to default
2013-08-20 09:58:37,549 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt /usr/lib/nvidia-173-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-173-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:58:37,549 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-20 09:58:37,538 DEBUG: got handler xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-20 09:58:37,549 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_96_updates', 'package': 'nvidia-96-updates'}
2013-08-20 09:58:37,561 DEBUG: NVidia(nvidia_96_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:58:37,561 DEBUG: nvidia_96_updates is not the alternative in use
2013-08-20 09:58:37,549 DEBUG: found match in handler pool xorg:nvidia_96_updates([NvidiaDriver96Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-20 09:58:37,564 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-08-20 09:58:37,572 DEBUG: nvidia.available: falling back to default
2013-08-20 09:58:39,324 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-08-20 09:58:39,336 DEBUG: NVidia(nvidia_96_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:58:39,337 DEBUG: nvidia_96_updates is not the alternative in use
2013-08-20 09:58:39,324 DEBUG: ignoring unavailable handler xorg:nvidia_96_updates([NvidiaDriver96Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-20 09:58:39,337 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_96', 'package': 'nvidia-96'}
2013-08-20 09:58:39,356 DEBUG: NVidia(nvidia_96).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:58:39,356 DEBUG: nvidia_96 is not the alternative in use
2013-08-20 09:58:39,337 DEBUG: found match in handler pool xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-08-20 09:58:39,362 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-08-20 09:58:39,373 DEBUG: nvidia.available: falling back to default
2013-08-20 09:58:42,950 DEBUG: NVidia(nvidia_96).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:58:42,950 DEBUG: nvidia_96 is not the alternative in use
2013-08-20 09:58:42,939 DEBUG: got handler xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-08-20 09:58:42,951 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173', 'package': 'nvidia-173'}
2013-08-20 09:58:42,961 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:58:42,961 DEBUG: nvidia_173 is not the alternative in use
2013-08-20 09:58:42,951 DEBUG: found match in handler pool xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-08-20 09:58:42,964 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-08-20 09:58:42,970 DEBUG: nvidia.available: falling back to default
2013-08-20 09:58:50,579 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:58:50,579 DEBUG: nvidia_173 is not the alternative in use
2013-08-20 09:58:50,568 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-08-20 09:58:50,579 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_304_updates', 'package': 'nvidia-304-updates'}
2013-08-20 09:58:50,592 DEBUG: NVidia(nvidia_304_updates).enabled(): target_alt /usr/lib/nvidia-304-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:58:50,593 DEBUG: KMH enabled: False
2013-08-20 09:58:50,579 DEBUG: found match in handler pool xorg:nvidia_304_updates([NvidiaDriver304Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-20 09:58:50,597 WARNING: modinfo for module nvidia_304_updates failed: ERROR: modinfo: could not find module nvidia_304_updates

2013-08-20 09:58:50,608 DEBUG: nvidia.available: falling back to default
2013-08-20 09:58:56,580 DEBUG: NVidia(nvidia_304_updates).enabled(): target_alt /usr/lib/nvidia-304-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:58:56,581 DEBUG: KMH enabled: False
2013-08-20 09:58:56,567 DEBUG: got handler xorg:nvidia_304_updates([NvidiaDriver304Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-20 09:58:56,581 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_304', 'package': 'nvidia-304'}
2013-08-20 09:58:56,598 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:58:56,599 DEBUG: nvidia_304 is not the alternative in use
2013-08-20 09:58:56,581 DEBUG: found match in handler pool xorg:nvidia_304([NvidiaDriver304, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-08-20 09:58:56,604 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304

2013-08-20 09:58:56,615 DEBUG: nvidia.available: falling back to default
2013-08-20 09:59:02,447 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:02,447 DEBUG: nvidia_304 is not the alternative in use
2013-08-20 09:59:02,434 DEBUG: got handler xorg:nvidia_304([NvidiaDriver304, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-08-20 09:59:02,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2013-08-20 09:59:02,448 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'acpi:PNP0303:')
2013-08-20 09:59:02,448 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2013-08-20 09:59:02,448 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-08-20 09:59:02,448 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'usb:v0BDAp58BBd5801dcEFdsc02dp01ic0Eisc02ip00')
2013-08-20 09:59:02,472 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00008086d000027C5sv0000103Csd000030BBbc01sc06i01')
2013-08-20 09:59:02,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00008086d0000109Asv0000103Csd000030BBbc02sc00i00')
2013-08-20 09:59:02,480 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'e1000e'}
2013-08-20 09:59:02,480 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e1000e', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,480 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030BBbc0Csc00i10')
2013-08-20 09:59:02,480 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-08-20 09:59:02,480 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,480 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-08-20 09:59:02,481 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 09:59:02,481 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,481 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'input:b0003v046DpC062e0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2013-08-20 09:59:02,481 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 09:59:02,481 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,481 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 09:59:02,481 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,481 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'usb:v0BDAp58BBd5801dcEFdsc02dp01ic01isc02ip00')
2013-08-20 09:59:02,482 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2013-08-20 09:59:02,482 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 09:59:02,482 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,482 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-08-20 09:59:02,482 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,483 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-08-20 09:59:02,483 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,483 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 09:59:02,483 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'acpi:SYN012B:SYN0100:SYN0002:PNP0F13:')
2013-08-20 09:59:02,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.2E:bd03/22/2010:svnHewlett-Packard:pnHPPaviliondv6000(RR399EA#B1A):pvrRev1:rvnQuanta:rn30BC:rvr66.42:cvnQuanta:ct10:cvrN/A:')
2013-08-20 09:59:02,501 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-08-20 09:59:02,501 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2013-08-20 09:59:02,501 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 09:59:02,501 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,501 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 09:59:02,501 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,501 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'usb:v046DpC062d3100dc00dsc00dp00ic03isc01ip02')
2013-08-20 09:59:02,532 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-08-20 09:59:02,532 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,532 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-08-20 09:59:02,532 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,532 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-08-20 09:59:02,532 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-08-20 09:59:02,532 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-08-20 09:59:02,532 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00008086d00002448sv0000103Csd000030BBbc06sc04i01')
2013-08-20 09:59:02,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'usb:v0BDAp58BBd5801dcEFdsc02dp01ic01isc01ip00')
2013-08-20 09:59:02,537 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2013-08-20 09:59:02,537 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,537 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2013-08-20 09:59:02,537 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2013-08-20 09:59:02,537 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,537 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00008086d000027DAsv0000103Csd000030BBbc0Csc05i00')
2013-08-20 09:59:02,541 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-08-20 09:59:02,541 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,541 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00008086d000027CCsv0000103Csd000030BBbc0Csc03i20')
2013-08-20 09:59:02,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00008086d000027C8sv0000103Csd000030BBbc0Csc03i00')
2013-08-20 09:59:02,548 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'platform:pcspkr')
2013-08-20 09:59:02,548 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-08-20 09:59:02,548 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,549 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-08-20 09:59:02,549 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2013-08-20 09:59:02,549 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 09:59:02,549 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,549 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 09:59:02,549 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2013-08-20 09:59:02,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'usb:v0BDAp58BBd5801dcEFdsc02dp01ic0Eisc01ip00')
2013-08-20 09:59:02,550 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-08-20 09:59:02,550 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00008086d000027C9sv0000103Csd000030BBbc0Csc03i00')
2013-08-20 09:59:02,554 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'platform:eisa')
2013-08-20 09:59:02,554 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00008086d000027DFsv0000103Csd000030BBbc01sc01i8a')
2013-08-20 09:59:02,558 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-08-20 09:59:02,567 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-08-20 09:59:02,567 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,567 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-08-20 09:59:02,567 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,567 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'usb:v0C45p62C0d0210dcEFdsc02dp01ic0Eisc02ip00')
2013-08-20 09:59:02,568 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'input:b0003v0C45p62C0e0210-e0,1,kD4,ramlsfw')
2013-08-20 09:59:02,568 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 09:59:02,568 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,569 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 09:59:02,569 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,569 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'pci:v00008086d000027CBsv0000103Csd000030BBbc0Csc03i00')
2013-08-20 09:59:02,572 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-08-20 09:59:02,572 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 09:59:02,573 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,573 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 09:59:02,573 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,573 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'input:b0003v0BDAp58BBe5801-e0,1,kD4,ramlsfw')
2013-08-20 09:59:02,573 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 09:59:02,573 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,573 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 09:59:02,573 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 09:59:02,574 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9f4552c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-08-20 09:59:02,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00008086d000027D8sv0000103Csd000030BBbc04sc03i00')
2013-08-20 09:59:02,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-08-20 09:59:02,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030BBbc08sc80i00')
2013-08-20 09:59:02,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030BBbc08sc05i00')
2013-08-20 09:59:02,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-08-20 09:59:02,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-08-20 09:59:02,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00008086d00004222sv0000103Csd0000135Cbc02sc80i00')
2013-08-20 09:59:02,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-08-20 09:59:02,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'platform:regulatory')
2013-08-20 09:59:02,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-08-20 09:59:02,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030BBbc08sc80i00')
2013-08-20 09:59:02,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-08-20 09:59:02,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'acpi:PNP0C32:')
2013-08-20 09:59:02,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00008086d000027B9sv0000103Csd000030BBbc06sc01i00')
2013-08-20 09:59:02,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-08-20 09:59:02,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00008086d000027CAsv0000103Csd000030BBbc0Csc03i00')
2013-08-20 09:59:02,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'platform:hp-wmi')
2013-08-20 09:59:02,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-08-20 09:59:02,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00008086d000027A0sv0000103Csd000030BBbc06sc00i00')
2013-08-20 09:59:02,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2013-08-20 09:59:02,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'usb:v0C45p62C0d0210dcEFdsc02dp01ic0Eisc01ip00')
2013-08-20 09:59:02,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'acpi:HPQ0006:')
2013-08-20 09:59:02,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-08-20 09:59:02,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v000010DEd000001D8sv0000103Csd000030BBbc03sc00i00')
2013-08-20 09:59:02,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2013-08-20 09:59:02,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'acpi:PNP0303:')
2013-08-20 09:59:02,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2013-08-20 09:59:02,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-08-20 09:59:02,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'usb:v0BDAp58BBd5801dcEFdsc02dp01ic0Eisc02ip00')
2013-08-20 09:59:02,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00008086d000027C5sv0000103Csd000030BBbc01sc06i01')
2013-08-20 09:59:02,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00008086d0000109Asv0000103Csd000030BBbc02sc00i00')
2013-08-20 09:59:02,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030BBbc0Csc00i10')
2013-08-20 09:59:02,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-08-20 09:59:02,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'input:b0003v046DpC062e0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2013-08-20 09:59:02,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'usb:v0BDAp58BBd5801dcEFdsc02dp01ic01isc02ip00')
2013-08-20 09:59:02,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2013-08-20 09:59:02,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'acpi:SYN012B:SYN0100:SYN0002:PNP0F13:')
2013-08-20 09:59:02,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.2E:bd03/22/2010:svnHewlett-Packard:pnHPPaviliondv6000(RR399EA#B1A):pvrRev1:rvnQuanta:rn30BC:rvr66.42:cvnQuanta:ct10:cvrN/A:')
2013-08-20 09:59:02,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-08-20 09:59:02,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2013-08-20 09:59:02,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'usb:v046DpC062d3100dc00dsc00dp00ic03isc01ip02')
2013-08-20 09:59:02,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-08-20 09:59:02,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-08-20 09:59:02,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-08-20 09:59:02,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00008086d00002448sv0000103Csd000030BBbc06sc04i01')
2013-08-20 09:59:02,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'usb:v0BDAp58BBd5801dcEFdsc02dp01ic01isc01ip00')
2013-08-20 09:59:02,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2013-08-20 09:59:02,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00008086d000027DAsv0000103Csd000030BBbc0Csc05i00')
2013-08-20 09:59:02,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00008086d000027CCsv0000103Csd000030BBbc0Csc03i20')
2013-08-20 09:59:02,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00008086d000027C8sv0000103Csd000030BBbc0Csc03i00')
2013-08-20 09:59:02,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'platform:pcspkr')
2013-08-20 09:59:02,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2013-08-20 09:59:02,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2013-08-20 09:59:02,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'usb:v0BDAp58BBd5801dcEFdsc02dp01ic0Eisc01ip00')
2013-08-20 09:59:02,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00008086d000027C9sv0000103Csd000030BBbc0Csc03i00')
2013-08-20 09:59:02,579 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'platform:eisa')
2013-08-20 09:59:02,579 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00008086d000027DFsv0000103Csd000030BBbc01sc01i8a')
2013-08-20 09:59:02,579 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-08-20 09:59:02,579 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'usb:v0C45p62C0d0210dcEFdsc02dp01ic0Eisc02ip00')
2013-08-20 09:59:02,579 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'input:b0003v0C45p62C0e0210-e0,1,kD4,ramlsfw')
2013-08-20 09:59:02,579 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'pci:v00008086d000027CBsv0000103Csd000030BBbc0Csc03i00')
2013-08-20 09:59:02,579 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-08-20 09:59:02,579 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'input:b0003v0BDAp58BBe5801-e0,1,kD4,ramlsfw')
2013-08-20 09:59:02,579 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa5df82c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-08-20 09:59:02,645 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:02,646 DEBUG: nvidia_173 is not the alternative in use
2013-08-20 09:59:03,912 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt /usr/lib/nvidia-173-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-173-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:03,912 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-20 09:59:05,124 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:05,124 DEBUG: nvidia_304 is not the alternative in use
2013-08-20 09:59:06,351 DEBUG: NVidia(nvidia_304_updates).enabled(): target_alt /usr/lib/nvidia-304-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:06,351 DEBUG: KMH enabled: False
2013-08-20 09:59:07,584 DEBUG: NVidia(nvidia_96).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:07,585 DEBUG: nvidia_96 is not the alternative in use
2013-08-20 09:59:08,866 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:08,866 DEBUG: nvidia_173 is not the alternative in use
2013-08-20 09:59:08,913 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt /usr/lib/nvidia-173-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-173-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:08,913 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-20 09:59:08,959 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:08,959 DEBUG: nvidia_304 is not the alternative in use
2013-08-20 09:59:09,006 DEBUG: NVidia(nvidia_304_updates).enabled(): target_alt /usr/lib/nvidia-304-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:09,006 DEBUG: KMH enabled: False
2013-08-20 09:59:09,052 DEBUG: NVidia(nvidia_96).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:09,052 DEBUG: nvidia_96 is not the alternative in use
2013-08-20 09:59:09,101 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt /usr/lib/nvidia-173-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-173-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:09,101 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-20 09:59:27,183 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:27,184 DEBUG: nvidia_304 is not the alternative in use
2013-08-20 09:59:30,943 DEBUG: NVidia(nvidia_96).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:30,943 DEBUG: nvidia_96 is not the alternative in use
2013-08-20 09:59:32,511 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:32,512 DEBUG: nvidia_304 is not the alternative in use
2013-08-20 09:59:34,824 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:34,824 DEBUG: nvidia_304 is not the alternative in use
2013-08-20 09:59:34,853 DEBUG: _check_polkit_privilege: sender :1.74 on connection <dbus._dbus.SystemBus (system) at 0xa298c2c> pid 6401 is not authorized for com.ubuntu.devicedriver.install: dbus.Dictionary({dbus.String(u'polkit.retains_authorization_after_challenge'): dbus.String(u'1')}, signature=dbus.Signature('ss'))
2013-08-20 09:59:47,409 DEBUG: NVidia(nvidia_96).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:47,409 DEBUG: nvidia_96 is not the alternative in use
2013-08-20 09:59:47,840 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:47,840 DEBUG: nvidia_304 is not the alternative in use
2013-08-20 09:59:49,384 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 09:59:49,385 DEBUG: nvidia_304 is not the alternative in use
2013-08-20 09:59:49,415 DEBUG: _check_polkit_privilege: sender :1.74 on connection <dbus._dbus.SystemBus (system) at 0xa298c2c> pid 6401 is not authorized for com.ubuntu.devicedriver.install: dbus.Dictionary({dbus.String(u'polkit.retains_authorization_after_challenge'): dbus.String(u'1')}, signature=dbus.Signature('ss'))
2013-08-20 10:20:59,837 DEBUG: Comparing 3.2.0-48 with 
2013-08-20 10:20:59,856 DEBUG: Comparing 3.2.0-48 with 3.2.0-48
2013-08-20 10:20:59,862 DEBUG: Comparing 3.2.0-49 with 3.2.0-48
2013-08-20 10:20:59,869 DEBUG: Comparing 3.2.0-49 with 3.2.0-49
2013-08-20 10:20:59,875 DEBUG: Comparing 3.2.0-51 with 3.2.0-49
2013-08-20 10:20:59,881 DEBUG: Comparing 3.2.0-51 with 3.2.0-51
2013-08-20 10:20:59,895 DEBUG: Comparing 3.2.0-52 with 3.2.0-51
2013-08-20 10:20:59,902 DEBUG: Comparing 3.2.0-52 with 3.2.0-52
2013-08-20 10:21:00,444 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c>
2013-08-20 10:21:02,699 DEBUG: reading modalias file /lib/modules/3.2.0-52-generic-pae/modules.alias
2013-08-20 10:21:02,845 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-08-20 10:21:02,929 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-08-20 10:21:03,021 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-08-20 10:21:03,123 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-08-20 10:21:04,487 DEBUG: linux-lts-raring installed: False
linux-lts-saucy installed: False
linux minor version: 2
xserver ABI: 11
xserver-lts-quantal: False
2013-08-20 10:21:04,490 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-08-20 10:21:04,490 DEBUG: cdv.available: falling back to default
2013-08-20 10:21:05,266 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-08-20 10:21:05,266 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-08-20 10:21:05,287 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-08-20 10:21:05,288 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-08-20 10:21:05,318 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-08-20 10:21:05,319 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-08-20 10:21:05,338 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-08-20 10:21:05,338 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-08-20 10:21:05,339 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-08-20 10:21:05,339 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-08-20 10:21:05,371 WARNING: modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12

2013-08-20 10:21:05,393 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental12 from name FglrxDriverExperimental12
2013-08-20 10:21:05,393 DEBUG: fglrx.available: falling back to default
2013-08-20 10:21:07,381 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-08-20 10:21:07,385 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-08-20 10:21:07,391 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-08-20 10:21:07,392 DEBUG: fglrx.available: falling back to default
2013-08-20 10:21:10,963 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-08-20 10:21:10,968 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-08-20 10:21:11,012 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2013-08-20 10:21:11,012 DEBUG: fglrx.available: falling back to default
2013-08-20 10:21:14,241 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-08-20 10:21:14,245 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-08-20 10:21:14,251 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverHybrid from name FglrxDriverHybrid
2013-08-20 10:21:14,252 DEBUG: fglrx.available: falling back to default
2013-08-20 10:21:18,834 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-08-20 10:21:18,839 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-08-20 10:21:18,849 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-08-20 10:21:18,850 DEBUG: fglrx.available: falling back to default
2013-08-20 10:21:23,426 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-08-20 10:21:23,430 WARNING: modinfo for module fglrx_experimental_13 failed: ERROR: modinfo: could not find module fglrx_experimental_13

2013-08-20 10:21:23,451 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental13 from name FglrxDriverExperimental13
2013-08-20 10:21:23,451 DEBUG: fglrx.available: falling back to default
2013-08-20 10:21:25,634 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-08-20 10:21:25,635 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-08-20 10:21:25,652 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-08-20 10:21:25,660 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-08-20 10:21:26,401 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-08-20 10:21:26,402 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-08-20 10:21:26,424 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-08-20 10:21:26,453 DEBUG: Software modem not available
2013-08-20 10:21:26,453 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-08-20 10:21:26,487 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304

2013-08-20 10:21:26,493 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver304 from name NvidiaDriver304
2013-08-20 10:21:26,494 DEBUG: nvidia.available: falling back to default
2013-08-20 10:21:32,513 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-08-20 10:21:32,517 WARNING: modinfo for module nvidia_304_updates failed: ERROR: modinfo: could not find module nvidia_304_updates

2013-08-20 10:21:32,527 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver304Updates from name NvidiaDriver304Updates
2013-08-20 10:21:32,527 DEBUG: nvidia.available: falling back to default
2013-08-20 10:21:38,347 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-08-20 10:21:38,353 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-08-20 10:21:38,363 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-08-20 10:21:38,364 DEBUG: nvidia.available: falling back to default
2013-08-20 10:21:38,402 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-08-20 10:21:38,409 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-08-20 10:21:38,448 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-08-20 10:21:38,449 DEBUG: nvidia.available: falling back to default
2013-08-20 10:21:38,480 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-08-20 10:21:38,486 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-08-20 10:21:38,496 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-08-20 10:21:38,497 DEBUG: nvidia.available: falling back to default
2013-08-20 10:21:38,536 DEBUG: NVIDIA accelerated graphics driver not available
2013-08-20 10:21:38,542 WARNING: modinfo for module nvidia_319 failed: ERROR: modinfo: could not find module nvidia_319

2013-08-20 10:21:38,553 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver319 from name NvidiaDriver319
2013-08-20 10:21:38,553 DEBUG: nvidia.available: falling back to default
2013-08-20 10:21:42,713 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-08-20 10:21:42,716 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-08-20 10:21:42,722 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-08-20 10:21:42,722 DEBUG: nvidia.available: falling back to default
2013-08-20 10:21:49,599 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-08-20 10:21:49,683 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-08-20 10:21:49,684 DEBUG: nvidia.available: falling back to default
2013-08-20 10:21:59,668 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-08-20 10:21:59,674 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-08-20 10:21:59,715 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-08-20 10:21:59,715 DEBUG: nvidia.available: falling back to default
2013-08-20 10:21:59,746 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-08-20 10:21:59,752 WARNING: modinfo for module nvidia_319_updates failed: ERROR: modinfo: could not find module nvidia_319_updates

2013-08-20 10:21:59,763 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver319Updates from name NvidiaDriver319Updates
2013-08-20 10:21:59,763 DEBUG: nvidia.available: falling back to default
2013-08-20 10:22:03,919 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-08-20 10:22:03,925 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-08-20 10:22:03,935 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-08-20 10:22:03,936 DEBUG: nvidia.available: falling back to default
2013-08-20 10:22:07,527 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-08-20 10:22:07,533 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-08-20 10:22:07,543 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-08-20 10:22:07,544 DEBUG: nvidia.available: falling back to default
2013-08-20 10:22:09,342 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-08-20 10:22:09,342 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-08-20 10:22:09,342 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-08-20 10:22:09,357 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-08-20 10:22:09,377 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-08-20 10:22:09,377 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-08-20 10:22:09,377 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-08-20 10:22:09,480 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-08-20 10:22:09,481 DEBUG: Firmware for DVB cards not available
2013-08-20 10:22:09,481 DEBUG: all custom handlers loaded
2013-08-20 10:22:09,481 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00008086d000027D8sv0000103Csd000030BBbc04sc03i00')
2013-08-20 10:22:09,820 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-08-20 10:22:09,983 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:09,983 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-08-20 10:22:09,983 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:09,984 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-08-20 10:22:09,989 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 10:22:09,990 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:09,990 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 10:22:09,990 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:09,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030BBbc08sc80i00')
2013-08-20 10:22:09,994 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r592'}
2013-08-20 10:22:09,994 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r592', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:09,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030BBbc08sc05i00')
2013-08-20 10:22:09,994 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2013-08-20 10:22:09,995 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:09,995 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2013-08-20 10:22:09,995 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:09,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-08-20 10:22:09,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-08-20 10:22:09,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00008086d00004222sv0000103Csd0000135Cbc02sc80i00')
2013-08-20 10:22:09,999 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwl3945'}
2013-08-20 10:22:09,999 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwl3945', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:09,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-08-20 10:22:10,000 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 10:22:10,000 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:10,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'platform:regulatory')
2013-08-20 10:22:10,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-08-20 10:22:10,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030BBbc08sc80i00')
2013-08-20 10:22:10,015 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r852'}
2013-08-20 10:22:10,015 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r852', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:10,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-08-20 10:22:10,016 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 10:22:10,016 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:10,016 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 10:22:10,016 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:10,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'acpi:PNP0C32:')
2013-08-20 10:22:10,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00008086d000027B9sv0000103Csd000030BBbc06sc01i00')
2013-08-20 10:22:10,020 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng'}
2013-08-20 10:22:10,020 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:10,020 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2013-08-20 10:22:10,020 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:10,020 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'leds_ss4200'}
2013-08-20 10:22:10,020 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'leds_ss4200', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:10,020 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-08-20 10:22:10,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00008086d000027CAsv0000103Csd000030BBbc0Csc03i00')
2013-08-20 10:22:10,024 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'platform:hp-wmi')
2013-08-20 10:22:10,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-08-20 10:22:10,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00008086d000027A0sv0000103Csd000030BBbc06sc00i00')
2013-08-20 10:22:10,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2013-08-20 10:22:10,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'usb:v0C45p62C0d0210dcEFdsc02dp01ic0Eisc01ip00')
2013-08-20 10:22:10,064 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-08-20 10:22:10,064 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:10,064 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'acpi:HPQ0006:')
2013-08-20 10:22:10,064 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-08-20 10:22:10,064 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v000010DEd000001D8sv0000103Csd000030BBbc03sc00i00')
2013-08-20 10:22:10,377 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173_updates'}
2013-08-20 10:22:10,474 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt /usr/lib/nvidia-173-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-173-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:10,474 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-20 10:22:10,377 DEBUG: found match in handler pool xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-20 10:22:10,480 DEBUG: nvidia.available: falling back to default
2013-08-20 10:22:20,785 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt /usr/lib/nvidia-173-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-173-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:20,785 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-20 10:22:20,773 DEBUG: got handler xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-20 10:22:20,785 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-08-20 10:22:20,786 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:20,786 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-08-20 10:22:20,786 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:20,786 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173_updates', 'package': 'nvidia-173-updates'}
2013-08-20 10:22:20,804 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt /usr/lib/nvidia-173-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-173-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:20,805 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-20 10:22:20,786 DEBUG: found match in handler pool xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-20 10:22:20,816 DEBUG: nvidia.available: falling back to default
2013-08-20 10:22:30,791 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt /usr/lib/nvidia-173-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-173-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:30,791 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-20 10:22:30,780 DEBUG: got handler xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-20 10:22:30,791 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_96_updates', 'package': 'nvidia-96-updates'}
2013-08-20 10:22:30,803 DEBUG: NVidia(nvidia_96_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:30,803 DEBUG: nvidia_96_updates is not the alternative in use
2013-08-20 10:22:30,792 DEBUG: found match in handler pool xorg:nvidia_96_updates([NvidiaDriver96Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-20 10:22:30,806 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-08-20 10:22:30,812 DEBUG: nvidia.available: falling back to default
2013-08-20 10:22:32,559 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2013-08-20 10:22:32,575 DEBUG: NVidia(nvidia_96_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:32,575 DEBUG: nvidia_96_updates is not the alternative in use
2013-08-20 10:22:32,559 DEBUG: ignoring unavailable handler xorg:nvidia_96_updates([NvidiaDriver96Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-20 10:22:32,575 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_96', 'package': 'nvidia-96'}
2013-08-20 10:22:32,594 DEBUG: NVidia(nvidia_96).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:32,594 DEBUG: nvidia_96 is not the alternative in use
2013-08-20 10:22:32,576 DEBUG: found match in handler pool xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-08-20 10:22:32,600 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-08-20 10:22:32,612 DEBUG: nvidia.available: falling back to default
2013-08-20 10:22:36,116 DEBUG: NVidia(nvidia_96).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:36,117 DEBUG: nvidia_96 is not the alternative in use
2013-08-20 10:22:36,096 DEBUG: got handler xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-08-20 10:22:36,118 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173', 'package': 'nvidia-173'}
2013-08-20 10:22:36,139 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:36,139 DEBUG: nvidia_173 is not the alternative in use
2013-08-20 10:22:36,118 DEBUG: found match in handler pool xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-08-20 10:22:36,142 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-08-20 10:22:36,148 DEBUG: nvidia.available: falling back to default
2013-08-20 10:22:43,009 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:43,010 DEBUG: nvidia_173 is not the alternative in use
2013-08-20 10:22:42,998 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-08-20 10:22:43,010 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_304_updates', 'package': 'nvidia-304-updates'}
2013-08-20 10:22:43,023 DEBUG: NVidia(nvidia_304_updates).enabled(): target_alt /usr/lib/nvidia-304-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:43,023 DEBUG: KMH enabled: False
2013-08-20 10:22:43,010 DEBUG: found match in handler pool xorg:nvidia_304_updates([NvidiaDriver304Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-20 10:22:43,028 WARNING: modinfo for module nvidia_304_updates failed: ERROR: modinfo: could not find module nvidia_304_updates

2013-08-20 10:22:43,039 DEBUG: nvidia.available: falling back to default
2013-08-20 10:22:48,866 DEBUG: NVidia(nvidia_304_updates).enabled(): target_alt /usr/lib/nvidia-304-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:48,866 DEBUG: KMH enabled: False
2013-08-20 10:22:48,854 DEBUG: got handler xorg:nvidia_304_updates([NvidiaDriver304Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-20 10:22:48,866 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_304', 'package': 'nvidia-304'}
2013-08-20 10:22:48,879 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:48,879 DEBUG: nvidia_304 is not the alternative in use
2013-08-20 10:22:48,867 DEBUG: found match in handler pool xorg:nvidia_304([NvidiaDriver304, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-08-20 10:22:48,882 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304

2013-08-20 10:22:48,888 DEBUG: nvidia.available: falling back to default
2013-08-20 10:22:54,696 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:54,697 DEBUG: nvidia_304 is not the alternative in use
2013-08-20 10:22:54,685 DEBUG: got handler xorg:nvidia_304([NvidiaDriver304, nonfree, disabled] NVIDIA accelerated graphics driver)
2013-08-20 10:22:54,697 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2013-08-20 10:22:54,697 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'acpi:PNP0303:')
2013-08-20 10:22:54,697 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2013-08-20 10:22:54,697 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-08-20 10:22:54,698 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'usb:v0BDAp58BBd5801dcEFdsc02dp01ic0Eisc02ip00')
2013-08-20 10:22:54,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00008086d000027C5sv0000103Csd000030BBbc01sc06i01')
2013-08-20 10:22:54,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00008086d0000109Asv0000103Csd000030BBbc02sc00i00')
2013-08-20 10:22:54,729 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'e1000e'}
2013-08-20 10:22:54,729 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e1000e', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030BBbc0Csc00i10')
2013-08-20 10:22:54,730 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-08-20 10:22:54,730 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-08-20 10:22:54,730 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 10:22:54,730 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'input:b0003v046DpC062e0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2013-08-20 10:22:54,731 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 10:22:54,731 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,731 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 10:22:54,731 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'usb:v0BDAp58BBd5801dcEFdsc02dp01ic01isc02ip00')
2013-08-20 10:22:54,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2013-08-20 10:22:54,732 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 10:22:54,732 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,732 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-08-20 10:22:54,732 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,732 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-08-20 10:22:54,732 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,732 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 10:22:54,733 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,733 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'acpi:SYN012B:SYN0100:SYN0002:PNP0F13:')
2013-08-20 10:22:54,733 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.2E:bd03/22/2010:svnHewlett-Packard:pnHPPaviliondv6000(RR399EA#B1A):pvrRev1:rvnQuanta:rn30BC:rvr66.42:cvnQuanta:ct10:cvrN/A:')
2013-08-20 10:22:54,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-08-20 10:22:54,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2013-08-20 10:22:54,750 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 10:22:54,750 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,750 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 10:22:54,751 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,751 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'usb:v046DpC062d3100dc00dsc00dp00ic03isc01ip02')
2013-08-20 10:22:54,780 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-08-20 10:22:54,780 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,780 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-08-20 10:22:54,780 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,780 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-08-20 10:22:54,781 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-08-20 10:22:54,781 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-08-20 10:22:54,781 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00008086d00002448sv0000103Csd000030BBbc06sc04i01')
2013-08-20 10:22:54,784 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'usb:v0BDAp58BBd5801dcEFdsc02dp01ic01isc01ip00')
2013-08-20 10:22:54,785 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2013-08-20 10:22:54,785 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,785 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2013-08-20 10:22:54,785 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2013-08-20 10:22:54,785 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00008086d000027DAsv0000103Csd000030BBbc0Csc05i00')
2013-08-20 10:22:54,789 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-08-20 10:22:54,789 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,789 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00008086d000027CCsv0000103Csd000030BBbc0Csc03i20')
2013-08-20 10:22:54,793 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00008086d000027C8sv0000103Csd000030BBbc0Csc03i00')
2013-08-20 10:22:54,796 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'platform:pcspkr')
2013-08-20 10:22:54,797 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-08-20 10:22:54,797 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,797 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-08-20 10:22:54,797 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,797 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2013-08-20 10:22:54,797 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 10:22:54,797 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,798 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 10:22:54,798 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2013-08-20 10:22:54,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'usb:v0BDAp58BBd5801dcEFdsc02dp01ic0Eisc01ip00')
2013-08-20 10:22:54,798 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-08-20 10:22:54,799 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,799 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00008086d000027C9sv0000103Csd000030BBbc0Csc03i00')
2013-08-20 10:22:54,802 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'platform:eisa')
2013-08-20 10:22:54,803 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00008086d000027DFsv0000103Csd000030BBbc01sc01i8a')
2013-08-20 10:22:54,806 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-08-20 10:22:54,815 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-08-20 10:22:54,815 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,815 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-08-20 10:22:54,815 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,815 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'usb:v0C45p62C0d0210dcEFdsc02dp01ic0Eisc02ip00')
2013-08-20 10:22:54,816 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'input:b0003v0C45p62C0e0210-e0,1,kD4,ramlsfw')
2013-08-20 10:22:54,816 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 10:22:54,816 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,817 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 10:22:54,817 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'pci:v00008086d000027CBsv0000103Csd000030BBbc0Csc03i00')
2013-08-20 10:22:54,820 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-08-20 10:22:54,820 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 10:22:54,820 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,821 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 10:22:54,821 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,821 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'input:b0003v0BDAp58BBe5801-e0,1,kD4,ramlsfw')
2013-08-20 10:22:54,821 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-20 10:22:54,821 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,821 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-20 10:22:54,821 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-20 10:22:54,821 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8acf52c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-08-20 10:22:54,821 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00008086d000027D8sv0000103Csd000030BBbc04sc03i00')
2013-08-20 10:22:54,822 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-08-20 10:22:54,822 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030BBbc08sc80i00')
2013-08-20 10:22:54,822 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030BBbc08sc05i00')
2013-08-20 10:22:54,822 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-08-20 10:22:54,822 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-08-20 10:22:54,822 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00008086d00004222sv0000103Csd0000135Cbc02sc80i00')
2013-08-20 10:22:54,822 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-08-20 10:22:54,822 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'platform:regulatory')
2013-08-20 10:22:54,822 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-08-20 10:22:54,822 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030BBbc08sc80i00')
2013-08-20 10:22:54,822 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-08-20 10:22:54,823 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'acpi:PNP0C32:')
2013-08-20 10:22:54,823 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00008086d000027B9sv0000103Csd000030BBbc06sc01i00')
2013-08-20 10:22:54,823 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-08-20 10:22:54,823 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00008086d000027CAsv0000103Csd000030BBbc0Csc03i00')
2013-08-20 10:22:54,823 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'platform:hp-wmi')
2013-08-20 10:22:54,823 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-08-20 10:22:54,823 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00008086d000027A0sv0000103Csd000030BBbc06sc00i00')
2013-08-20 10:22:54,823 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2013-08-20 10:22:54,823 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'usb:v0C45p62C0d0210dcEFdsc02dp01ic0Eisc01ip00')
2013-08-20 10:22:54,823 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'acpi:HPQ0006:')
2013-08-20 10:22:54,823 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-08-20 10:22:54,824 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v000010DEd000001D8sv0000103Csd000030BBbc03sc00i00')
2013-08-20 10:22:54,824 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2013-08-20 10:22:54,824 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'acpi:PNP0303:')
2013-08-20 10:22:54,824 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2013-08-20 10:22:54,824 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-08-20 10:22:54,824 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'usb:v0BDAp58BBd5801dcEFdsc02dp01ic0Eisc02ip00')
2013-08-20 10:22:54,824 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00008086d000027C5sv0000103Csd000030BBbc01sc06i01')
2013-08-20 10:22:54,824 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00008086d0000109Asv0000103Csd000030BBbc02sc00i00')
2013-08-20 10:22:54,824 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030BBbc0Csc00i10')
2013-08-20 10:22:54,824 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-08-20 10:22:54,824 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'input:b0003v046DpC062e0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2013-08-20 10:22:54,824 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'usb:v0BDAp58BBd5801dcEFdsc02dp01ic01isc02ip00')
2013-08-20 10:22:54,825 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2013-08-20 10:22:54,825 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'acpi:SYN012B:SYN0100:SYN0002:PNP0F13:')
2013-08-20 10:22:54,825 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.2E:bd03/22/2010:svnHewlett-Packard:pnHPPaviliondv6000(RR399EA#B1A):pvrRev1:rvnQuanta:rn30BC:rvr66.42:cvnQuanta:ct10:cvrN/A:')
2013-08-20 10:22:54,825 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-08-20 10:22:54,825 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2013-08-20 10:22:54,825 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'usb:v046DpC062d3100dc00dsc00dp00ic03isc01ip02')
2013-08-20 10:22:54,825 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-08-20 10:22:54,825 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-08-20 10:22:54,825 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-08-20 10:22:54,825 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00008086d00002448sv0000103Csd000030BBbc06sc04i01')
2013-08-20 10:22:54,825 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'usb:v0BDAp58BBd5801dcEFdsc02dp01ic01isc01ip00')
2013-08-20 10:22:54,825 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2013-08-20 10:22:54,826 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00008086d000027DAsv0000103Csd000030BBbc0Csc05i00')
2013-08-20 10:22:54,826 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00008086d000027CCsv0000103Csd000030BBbc0Csc03i20')
2013-08-20 10:22:54,826 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00008086d000027C8sv0000103Csd000030BBbc0Csc03i00')
2013-08-20 10:22:54,826 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'platform:pcspkr')
2013-08-20 10:22:54,826 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2013-08-20 10:22:54,826 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2013-08-20 10:22:54,826 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'usb:v0BDAp58BBd5801dcEFdsc02dp01ic0Eisc01ip00')
2013-08-20 10:22:54,826 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00008086d000027C9sv0000103Csd000030BBbc0Csc03i00')
2013-08-20 10:22:54,826 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'platform:eisa')
2013-08-20 10:22:54,826 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00008086d000027DFsv0000103Csd000030BBbc01sc01i8a')
2013-08-20 10:22:54,826 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-08-20 10:22:54,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'usb:v0C45p62C0d0210dcEFdsc02dp01ic0Eisc02ip00')
2013-08-20 10:22:54,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'input:b0003v0C45p62C0e0210-e0,1,kD4,ramlsfw')
2013-08-20 10:22:54,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'pci:v00008086d000027CBsv0000103Csd000030BBbc0Csc03i00')
2013-08-20 10:22:54,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-08-20 10:22:54,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'input:b0003v0BDAp58BBe5801-e0,1,kD4,ramlsfw')
2013-08-20 10:22:54,827 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x916982c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-08-20 10:22:54,904 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:54,904 DEBUG: nvidia_173 is not the alternative in use
2013-08-20 10:22:56,244 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt /usr/lib/nvidia-173-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-173-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:56,245 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-20 10:22:57,482 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:57,482 DEBUG: nvidia_304 is not the alternative in use
2013-08-20 10:22:58,698 DEBUG: NVidia(nvidia_304_updates).enabled(): target_alt /usr/lib/nvidia-304-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:22:58,698 DEBUG: KMH enabled: False
2013-08-20 10:23:00,306 DEBUG: NVidia(nvidia_96).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:23:00,306 DEBUG: nvidia_96 is not the alternative in use
2013-08-20 10:23:01,588 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:23:01,588 DEBUG: nvidia_173 is not the alternative in use
2013-08-20 10:23:01,632 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:23:01,632 DEBUG: nvidia_173 is not the alternative in use
2013-08-20 10:23:01,671 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt /usr/lib/nvidia-173-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-173-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:23:01,671 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-20 10:23:01,711 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:23:01,712 DEBUG: nvidia_304 is not the alternative in use
2013-08-20 10:23:01,750 DEBUG: NVidia(nvidia_304_updates).enabled(): target_alt /usr/lib/nvidia-304-updates/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:23:01,751 DEBUG: KMH enabled: False
2013-08-20 10:23:01,789 DEBUG: NVidia(nvidia_96).enabled(): target_alt None current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:23:01,789 DEBUG: nvidia_96 is not the alternative in use
2013-08-20 10:23:08,141 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:23:08,142 DEBUG: nvidia_304 is not the alternative in use
2013-08-20 10:23:11,837 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:23:11,837 DEBUG: nvidia_304 is not the alternative in use
2013-08-20 10:23:14,906 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304-updates/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304-updates/alt_ld.so.conf
2013-08-20 10:23:14,906 DEBUG: nvidia_304 is not the alternative in use
2013-08-20 10:23:15,112 DEBUG: Installing package: linux-generic
2013-08-20 10:23:15,682 DEBUG: download progress <Package: name:'linux-generic' architecture='i386' id:46629L> 0.000000
2013-08-20 10:23:15,684 DEBUG: download progress <Package: name:'linux-generic' architecture='i386' id:46629L> 0.000000
2013-08-20 10:23:15,915 DEBUG: download progress <Package: name:'linux-generic' architecture='i386' id:46629L> 0.000000
2013-08-20 10:23:16,065 DEBUG: download progress <Package: name:'linux-generic' architecture='i386' id:46629L> 0.000000
2013-08-20 10:23:16,224 DEBUG: download progress <Package: name:'linux-generic' architecture='i386' id:46629L> 0.116332
2013-08-20 10:23:16,725 DEBUG: download progress <Package: name:'linux-generic' architecture='i386' id:46629L> 12.557999
2013-08-20 10:23:17,226 DEBUG: download progress <Package: name:'linux-generic' architecture='i386' id:46629L> 42.477245
2013-08-20 10:23:17,728 DEBUG: download progress <Package: name:'linux-generic' architecture='i386' id:46629L> 96.243020
2013-08-20 10:23:17,851 DEBUG: download progress <Package: name:'linux-generic' architecture='i386' id:46629L> 99.582398
2013-08-20 10:23:17,852 DEBUG: download progress <Package: name:'linux-generic' architecture='i386' id:46629L> 99.823188
2013-08-20 10:23:17,871 DEBUG: download progress <Package: name:'linux-generic' architecture='i386' id:46629L> 99.999897
2013-08-20 10:23:17,872 DEBUG: download progress <Package: name:'linux-generic' architecture='i386' id:46629L> 100.000000
2013-08-20 10:23:18,657 DEBUG: install progress dpkg-exec 0.000000
2013-08-20 10:23:25,334 DEBUG: install progress linux-headers-3.2.0-52-generic 0.000000
2013-08-20 10:23:25,334 DEBUG: install progress linux-headers-3.2.0-52-generic 6.666670
2013-08-20 10:23:28,979 DEBUG: install progress linux-headers-3.2.0-52-generic 13.333300
2013-08-20 10:23:29,096 DEBUG: install progress linux-headers-3.2.0-52-generic 20.000000
2013-08-20 10:23:29,347 DEBUG: install progress linux-headers-generic 20.000000
2013-08-20 10:23:29,347 DEBUG: install progress linux-headers-generic 26.666700
2013-08-20 10:23:29,623 DEBUG: install progress linux-headers-generic 33.333300
2013-08-20 10:23:29,695 DEBUG: install progress linux-headers-generic 40.000000
2013-08-20 10:23:29,924 DEBUG: install progress linux-generic 40.000000
2013-08-20 10:23:29,924 DEBUG: install progress linux-generic 46.666700
2013-08-20 10:23:30,178 DEBUG: install progress linux-generic 53.333300
2013-08-20 10:23:30,273 DEBUG: install progress linux-generic 60.000000
2013-08-20 10:23:31,060 DEBUG: install progress dpkg-exec 60.000000
2013-08-20 10:23:31,147 DEBUG: install progress linux-headers-3.2.0-52-generic 60.000000
2013-08-20 10:23:31,248 DEBUG: install progress linux-headers-3.2.0-52-generic 66.666700
2013-08-20 10:24:45,435 DEBUG: install progress linux-headers-3.2.0-52-generic 73.333300
2013-08-20 10:24:45,780 DEBUG: install progress linux-headers-generic 73.333300
2013-08-20 10:24:45,882 DEBUG: install progress linux-headers-generic 80.000000
2013-08-20 10:24:45,972 DEBUG: install progress linux-headers-generic 86.666700
2013-08-20 10:24:46,063 DEBUG: install progress linux-generic 86.666700
2013-08-20 10:24:46,164 DEBUG: install progress linux-generic 93.333300
2013-08-20 10:24:46,255 DEBUG: install progress linux-generic 100.000000
2013-08-20 10:24:48,761 DEBUG: Selecting previously unselected package linux-headers-3.2.0-52-generic.
(Reading database ... 380827 files and directories currently installed.)
Unpacking linux-headers-3.2.0-52-generic (from .../linux-headers-3.2.0-52-generic_3.2.0-52.78_i386.deb) ...
Selecting previously unselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_3.2.0.52.62_i386.deb) ...
Selecting previously unselected package linux-generic.
Unpacking linux-generic (from .../linux-generic_3.2.0.52.62_i386.deb) ...
Setting up linux-headers-3.2.0-52-generic (3.2.0-52.78) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-52-generic /boot/vmlinuz-3.2.0-52-generic
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
Setting up linux-headers-generic (3.2.0.52.62) ...
Setting up linux-generic (3.2.0.52.62) ...

2013-08-20 10:24:49,398 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304

2013-08-20 10:24:49,399 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-08-20 10:25:48,725 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-20 10:25:48,725 DEBUG: KMH enabled: False
2013-08-20 10:25:48,756 DEBUG: NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf current_alt /usr/lib/nvidia-304/ld.so.conf other target alt /usr/lib/nvidia-304/alt_ld.so.conf other current alt /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-20 10:25:48,757 DEBUG: KMH enabled: False

```

You know what my problem is ?
I use this system to work and not just look at it and get happy I got linux.
I consider it completely ridiculous for an update/upgrade to brake the system like this.
No more to say, I am completely .....ed off as I use this system for web development and I should be doing other things right now.

If anyone can help please reply.

This is Ubuntu 12.04 i386 on my HP laptop.

EDIT:
As I also noticed huge network latency and sound problems I booted from previous kernel 3.2.0-51 and eveything works as it should.
Of course the boot screen is (once again in the history of ubuntu), guess what ? -> broken.

I would really really appreciate any kind of help on this mess that has been caused to my system.

---

### Post by orasisd on 2013-08-20
If ANYBODY faces the same problem please reply.
If ANY of the developers of the kernel is here, please reply.

---

### Post by oscarsfriend on 2013-08-20
I'm having the same problem.  I've not tried yet, but there is a fix for exactly the same problem mentioned here: [http://askubuntu.com/questions/334902/12-04-update-and-nvidia](http://askubuntu.com/questions/334902/12-04-update-and-nvidia)

---

### Post by orasisd on 2013-08-20
> **oscarsfriend said:**
> I'm having the same problem.  I've not tried yet, but there is a fix for exactly the same problem mentioned here: [http://askubuntu.com/questions/334902/12-04-update-and-nvidia](http://askubuntu.com/questions/334902/12-04-update-and-nvidia)

The thing is I haven't manually added anything related to nvidia on the system.
And as one of the posts there says "*What I don't understand why would I have  problem in the first place if I did proper update, which should have  taken care of properly updating the packages*".
I will try some of those steps though and reply back.

thanks for the reply

---

### Post by oscarsfriend on 2013-08-20
Trying to upgrade to the 319 nvidia driver didn't work for me, and I had to go back to 304. :(

I do get a fully working X (my dual monitors work too), however I get the crappy text boot screen, even when booting the previous kernel.

There were several updates pushed at the same time as the kernel update (or since I installed updates some time last week), including the nvidia-304-updates and related packages.  I'm guessing something broke in the nvidia update (since I get the same problem with previous kernel).

---

### Post by orasisd on 2013-08-20
Ok. Thanks to oscarsfriend and the link he gave, I made it work.
Make sure you booted using kernel 3.2.0-52

I used the following 2 commands only:

```
sudo apt-get purge nvidia*
```
..when that is done,
```
sudo apt-get install nvidia-current-updates-dev
```

then reboot.

Now I see a whole new list in the "Additional Drivers" that are back, and the "nvidia_304_updates" is selected. I honestly don't wanna touch it -- it works, I had enough with this.
I will surely receive a phone call from my girlfriend though that has no idea how to do this and hear her say "my ubuntu broke again" <-- nice.

---

### Post by orasisd on 2013-08-20
> **oscarsfriend said:**
> Trying to upgrade to the 319 nvidia driver didn't work for me, and I had to go back to 304. :(

I do get a fully working X (my dual monitors work too), however I get the crappy text boot screen, even when booting the previous kernel.

There were several updates pushed at the same time as the kernel update (or since I installed updates some time last week), including the nvidia-304-updates and related packages.  I'm guessing something broke in the nvidia update (since I get the same problem with previous kernel).

I am working on developing php alot and I got a habit every time I take a break to check for updates on linux, which makes me update things almost a little while after they are released.
Yes the boot screen broke ONCE AGAIN.
I will try "Boot Repair" because last time I used it, it brought back the proper boot screen.

EDIT:
Nop ! no nice proper boot screen on this computer for a while.
By the way, now it makes a noise while booting, must be enabling audio or something -- I will try not to forget and have it on my speakers loud.
The more updates, the worse things get !

---

### Post by oscarsfriend on 2013-08-20
I don't get any noise on boot.

---

### Post by orasisd on 2013-08-20
It makes that little "paat" noise. It used to in previous versions of ubuntu on laptops and I was using some code to fix it manually.
Then they fixed it.
Now it's back.

---

### Post by oscarsfriend on 2013-08-20
OK, I might have got a small quick noise (I thought you meant something more obvious) around the time X starts, I think, although I thought I always had that.  I don't have my speakers turned up too loud, and they aren't usually on during boot anyway.

---

### Post by orasisd on 2013-08-20
I just checked and unfortunately it is not caused by the same reason -- or it is and the setting changed place.
The solution was to comment out:
```
options snd-hda-intel power_save=10 power_save_controller=N
```
from /etc/modprobe.d/alsa-base.conf

Now it doesn't even exist in there. I don't know what is going on.
I try to be careful with my speakers being loud but you never know!

---

### Post by oscarsfriend on 2013-08-20
File this under tried-and-failed: I tried reinstalling the plymouth boot logo packages (the initramfs update kicks in during re-installation) and rebooting. Didn't work. :(

---

### Post by orasisd on 2013-08-20
I have done too many reboots trying to fix this screen in the past. Most of the times I was giving up.
And when I finally fixed it, some update would break it again.
Last time I fixed it using that 'boot repair' tool but now even that doesn't fix it.
But I don't know 'who' to blame. Once I also got KDE on this system, maybe KDE is playing the 'clever' here.

EDIT:
The shutdown screen is fine.

---

### Post by oscarsfriend on 2013-08-20
Well, I'm using **k**ubuntu and there hasn't been any updates to kde recently, and I hadn't had a problem with the boot screen (other than being very low res) until I updated today.  I *do* have the same problem with the shutdown screen, though.

---

### Post by orasisd on 2013-08-20
Weird because I saw many kde updates about 1 or 2 days ago.
I use Ubuntu and also installed kubuntu-desktop on the same system for testing -- works great.

Did you ever need to do this ?
```

sudo apt-add-repository ppa:kubuntu-ppa/ppa
sudo apt-add-repository ppa:kubuntu-ppa/backports

```

EDIT:
Actually followed by:
```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by oscarsfriend on 2013-08-20
No, I didn't do any of that.  I started with a regular 12.04 (actually 12.04.1) kubuntu installation disk, which I installed way back last year, and haven't added any extra repos related to kde.  You seem to be getting your kde from somewhere other than the regular ubuntu repos. But I don't think that is the problem here.

Here are all the packages installed or upgraded today on my machine during the update.  (Note: I booted the machine today with no problems, then preformed the update, then rebooted with the problems.)

```
Start-Date: 2013-08-20  14:14:49
Install: linux-headers-3.2.0-52-generic:amd64 (3.2.0-52.78, automatic)
linux-headers-3.2.0-52:amd64 (3.2.0-52.78, automatic)
nvidia-304-updates:amd64 (304.88-0ubuntu0.0.3)
nvidia-settings-304-updates:amd64 (304.88-0ubuntu0.0.3, automatic)
linux-image-3.2.0-52-generic:amd64 (3.2.0-52.78)
Upgrade: mythtv-database:amd64 (0.26.0+fixes.20130813.f47e2cf-0ubuntu0mythbuntu1, 0.26.1+fixes.20130820.6a46ea0-0ubuntu0mythbuntu1)
rpm2cpio:amd64 (4.9.1.1-1ubuntu0.1, 4.9.1.1-1ubuntu0.2)
linux-source-3.2.0:amd64 (3.2.0-51.77, 3.2.0-52.78)
linux-source:amd64 (3.2.0.51.61, 3.2.0.52.62)
linux-generic:amd64 (3.2.0.51.61, 3.2.0.52.62)
dosfstools:amd64 (3.0.12-1ubuntu1, 3.0.12-1ubuntu1.1)
librpmio2:amd64 (4.9.1.1-1ubuntu0.1, 4.9.1.1-1ubuntu0.2)
librpm2:amd64 (4.9.1.1-1ubuntu0.1, 4.9.1.1-1ubuntu0.2)
rpm-common:amd64 (4.9.1.1-1ubuntu0.1, 4.9.1.1-1ubuntu0.2)
nvidia-current-updates:amd64 (304.88-0ubuntu0.0.1, 304.88-0ubuntu0.0.3)
libmyth-python:amd64 (0.26.0+fixes.20130813.f47e2cf-0ubuntu0mythbuntu1, 0.26.1+fixes.20130820.6a46ea0-0ubuntu0mythbuntu1)
mythtv-common:amd64 (0.26.0+fixes.20130813.f47e2cf-0ubuntu0mythbuntu1, 0.26.1+fixes.20130820.6a46ea0-0ubuntu0mythbuntu1)
mythweb:amd64 (0.26.0+fixes.20130813.f47e2cf-0ubuntu0mythbuntu1, 0.26.1+fixes.20130820.6a46ea0-0ubuntu0mythbuntu1)
mythtv-backend:amd64 (0.26.0+fixes.20130813.f47e2cf-0ubuntu0mythbuntu1, 0.26.1+fixes.20130820.6a46ea0-0ubuntu0mythbuntu1)
linux-image:amd64 (3.2.0.51.61, 3.2.0.52.62)
nvidia-settings-updates:amd64 (304.88-0ubuntu0.0.2, 304.88-0ubuntu0.0.3)
linux-headers-generic:amd64 (3.2.0.51.61, 3.2.0.52.62)
linux-image-generic:amd64 (3.2.0.51.61, 3.2.0.52.62)
libmythtv-perl:amd64 (0.26.0+fixes.20130813.f47e2cf-0ubuntu0mythbuntu1, 0.26.1+fixes.20130820.6a46ea0-0ubuntu0mythbuntu1)
rpm:amd64 (4.9.1.1-1ubuntu0.1, 4.9.1.1-1ubuntu0.2)
librpmbuild2:amd64 (4.9.1.1-1ubuntu0.1, 4.9.1.1-1ubuntu0.2)
mythtv-backend-master:amd64 (0.26.0+fixes.20130813.f47e2cf-0ubuntu0mythbuntu1, 0.26.1+fixes.20130820.6a46ea0-0ubuntu0mythbuntu1)
jockey-common:amd64 (0.9.7-0ubuntu7.9, 0.9.7-0ubuntu7.10)
php-mythtv:amd64 (0.26.0+fixes.20130813.f47e2cf-0ubuntu0mythbuntu1, 0.26.1+fixes.20130820.6a46ea0-0ubuntu0mythbuntu1)
jockey-kde:amd64 (0.9.7-0ubuntu7.9, 0.9.7-0ubuntu7.10)
mythtv-frontend:amd64 (0.26.0+fixes.20130813.f47e2cf-0ubuntu0mythbuntu1, 0.26.1+fixes.20130820.
6a46ea0-0ubuntu0mythbuntu1)
librpmsign0:amd64 (4.9.1.1-1ubuntu0.1, 4.9.1.1-1ubuntu0.2)
linux-libc-dev:amd64 (3.2.0-51.77, 3.2.0-52.78)
libmyth-0.26-0:amd64 (0.26.0+fixes.20130813.f47e2cf-0ubuntu0mythbuntu1, 0.26.1+fixes.20130820.6a46ea0-0ubuntu0mythbuntu1)
mythtv-transcode-utils:amd64 (0.26.0+fixes.20130813.f47e2cf-0ubuntu0mythbuntu1, 0.26.1+fixes.20130820.6a46ea0-0ubuntu0mythbuntu1)
End-Date: 2013-08-20  14:23:06

```

I took this from /var/log/apt/history.log then tidied it up a bit.

---

### Post by orasisd on 2013-08-20
Well If you ever tried the above you'd see that 1. it takes forever to download and install all those extensions, 2. you end up with a completely new kde that has a lot of things fixed (most probably a lot of other things broken as well).
But no I haven't added any weird repo no. These updates appear after you add the above repos.

---

### Post by Yleeyas on 2013-08-20
Thanx guys, the steps in #6 was what I needed to get me back on track. No other problems so far. If memory serves, this is the second time an nvidia update messed me up, but that was some time back.

---

### Post by kmoneylongshanks on 2013-08-21
> **orasisd said:**
> Ok. Thanks to oscarsfriend and the link he gave, I made it work.
Make sure you booted using kernel 3.2.0-52

I used the following 2 commands only:

```
sudo apt-get purge nvidia*
```
..when that is done,
```
sudo apt-get install nvidia-current-updates-dev
```

then reboot.

Now I see a whole new list in the "Additional Drivers" that are back, and the "nvidia_304_updates" is selected. I honestly don't wanna touch it -- it works, I had enough with this.
I will surely receive a phone call from my girlfriend though that has no idea how to do this and hear her say "my ubuntu broke again" <-- nice.

This is what worked for me too. I had a scared few hours trying to figure out how to fix it. Wish I came across this post before I wasted all that time. BTW, there are these other drivers from nVidia called NVIDIA binary Xorg driver, kernel module and VDPAU library. Has anyone used these instead? Is this what we are supposed to be using now?

---

### Post by orasisd on 2013-08-21
Yeah happy the solution was found fast and was easy too.
I used to have trouble with the nvidia drivers on my old desktop. Since it died everything else, laptop, new desktop etc work good with the 'recommended' ones -- although firefox scrolling lags and some other windows do, even on the new computer (i7 // Intel DP67BG). I am not sure what we are supposed to be using. I have planned to re-install ubuntu 12.04 also on this desktop, I have the nvidia GTX 560 Ti and want to see how it works with steam.

EDIT:
Concerning the nvidia additional drivers that I see now again, they all have the same name except the 'nvidia_304_updates'. First time I see something like that. Choices that are all the same choice. At least it looks like it's got some stuff in there and it is not empty like before the fix.

Also something weird is that this list of drivers lags while using the keyboard arrow keys (or mouse) -- again something new. I feel problems.

---

### Post by krionic on 2013-08-21
I had the same problem described here, but could not get to a screen at all, and it took me a day to fully understand what happened. Here's what I have concluded:
[LIST]
[*]I had multiple versions of the NVidia driver installed.
[*]The drivers were not the latest drivers.
[*]Updating to the latest kernel (3.2.0-52 at this time) and restarting, caused a kernel-level driver problem.
[*]The following packages were updated/installed at the time the error was caused:
[/LIST]

> install linux-image-3.2.0-52-generic <none> 3.2.0-52.78
upgrade jockey-gtk 0.9.7-0ubuntu7.9 0.9.7-0ubuntu7.10
upgrade jockey-common 0.9.7-0ubuntu7.9 0.9.7-0ubuntu7.10
upgrade linux-generic 3.2.0.51.61 3.2.0.52.62
upgrade linux-image-generic 3.2.0.51.61 3.2.0.52.62
install linux-headers-3.2.0-52 <none> 3.2.0-52.78
install linux-headers-3.2.0-52-generic <none> 3.2.0-52.78
upgrade linux-headers-generic 3.2.0.51.61 3.2.0.52.62
upgrade linux-libc-dev 3.2.0-51.77 3.2.0-52.78
install nvidia-304 <none> 304.88-0ubuntu0.0.3
install nvidia-304-updates <none> 304.88-0ubuntu0.0.3
install nvidia-319-updates <none> 319.32-0ubuntu0.0.1
upgrade nvidia-current 304.88-0ubuntu0.0.2 304.88-0ubuntu0.0.3
upgrade nvidia-current-updates 304.88-0ubuntu0.0.1 304.88-0ubuntu0.0.3
upgrade nvidia-experimental-310 310.14-0ubuntu0.3 319.32-0ubuntu0.0.1
install nvidia-settings-304 <none> 304.88-0ubuntu0.0.3
upgrade nvidia-settings 304.88-0ubuntu0.0.2 304.88-0ubuntu0.0.3
install nvidia-settings-304-updates <none> 304.88-0ubuntu0.0.3
install nvidia-settings-319-updates <none> 319.32-0ubuntu0.0.1
upgrade nvidia-settings-experimental-310 310.14-0ubuntu0.1 319.32-0ubuntu0.0.1
upgrade nvidia-settings-updates 304.88-0ubuntu0.0.2 304.88-0ubuntu0.0.3
upgrade spideroak 1:5.0.2 1:5.0.3

I held down SHIFT after my POST screen to get into Grub, and enter the recovery console. I got good video, but it only worked that one time with that kernel, and then the kernel would not give any video. I followed the following steps:
1. Loaded a previous version of the kernel
2. Re-installed the video drivers
3. Logged out and back in

**Permanent solution:**
I found Response #6 useful, but my system failed to expand the nvidia* to individual packages. Below are the steps that worked for me. Beware that if you uninstalled novou

[LIST]
[*]Log in to the recovery console in Grub.
[*]Select the current kernel's recovery mode
[*]Optional: Enable networking (it gave me some errors, but it should work). If this doesn't work, you will have to wait to re-install packages until after a restart.
[*]Drop down to the Root command line option
[*]Re-mount the drive as read-write:
```
mount -o rw,remount /
```
[*]Enter the following command to get a list of nvidia packages to purge:
```
dpkg --get-selections | grep nvidia
```
[*]Remove each package:
```
apt-get --purge remove {package_name}
```
[*]One of these packages may require the removal of ubuntu-desktop. I proceeded, making note of it for re-installation later with:
```
apt-get install ubuntu-desktop
```
[*]*If you previously uninstalled the default video drivers, you need to reinstall them with:
```
apt-get install xserver-xorg-video-nouveau
```
[*]Do some cleaning up of configuration files in order to get a clean installation:
```
apt-get clean
apt-get --purge autoremove
```
[*]Finally, rename the xorg.conf file, or the system will be looking for drivers you just deleted:
```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.oldconfig
```
[*]Reboot your system, and it should start into the desktop with default video drivers *unless you previously uninstalled them and did not re-install them.*
[/LIST]

At this point, I:
[LIST]
[*]Re-installed my video drivers from the Additional Drivers menu
[*]Opened a terminal window and ran ```
sudo nvidia-xconfig
```
[*]Restart the system for the drivers to load.
[/LIST]

Hope this helps someone!

---

### Post by orasisd on 2013-08-21
that update was a disaster.
Does anybody see something like this ? Is this normal ? See screenshot:
[IMG]http://s17.postimg.org/5bfsccb9r/ubuntu_laptop.jpg[/IMG]

---

### Post by krionic on 2013-08-21
Orasisd,

I saw the exact same thing on mine, but verified the correct drivers were loaded. I used a post from [Ask Ubuntu]("http://askubuntu.com/questions/23238/how-can-i-find-what-video-driver-is-in-use-on-my-system"), which said to run the command:

```
sudo lshw -c video
```

On mine, the line for the NVidia card shows "configuration: driver=nvidia latency=0", which tells me the driver loaded properly (as opposed to my disabled on-board video, which is still picked up and listed as "configuration: driver=i915 latency=0").

*Edit to correct URL*

---

### Post by orasisd on 2013-08-22
> **krionic said:**
> Orasisd,

I saw the exact same thing on mine, but verified the correct drivers were loaded. I used a post from [Ask Ubuntu]("http://askubuntu.com/questions/23238/how-can-i-find-what-video-driver-is-in-use-on-my-system"), which said to run the command:

```
sudo lshw -c video
```

On mine, the line for the NVidia card shows "configuration: driver=nvidia latency=0", which tells me the driver loaded properly (as opposed to my disabled on-board video, which is still picked up and listed as "configuration: driver=i915 latency=0").

*Edit to correct URL*

Thanks for reply,
this command on mine shows:

```

  *-display               
       description: VGA compatible controller
       product: G72M [GeForce Go 7400]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:dd000000-ddffffff memory:c0000000-cfffffff memory:dc000000-dcffffff

```

What does that mean ? that the additional drivers window shows wrong info ? My mind cannot think it's tired :(

EDIT:
@krionic
Does your additional drivers window work exactly like mine now that you have fixed the system ?

---

### Post by krionic on 2013-08-22
> **orasisd said:**
> Thanks for reply,
this command on mine shows:

```

  *-display               
       description: VGA compatible controller
       product: G72M [GeForce Go 7400]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:dd000000-ddffffff memory:c0000000-cfffffff memory:dc000000-dcffffff

```

What does that mean ? that the additional drivers window shows wrong info ? My mind cannot think it's tired :(

EDIT:
@krionic
Does your additional drivers window work exactly like mine now that you have fixed the system ?

@orasisd: Second line from the bottom on your output shows you're currently using the nvidia driver.

To your second question, yes, it incorrectly shows that I'm not using the driver. However, I was able to see a difference in my screen resolution when I reinstalled the nvidia driver, and my monitor was correctly detected (it was listed as Laptop with the default drivers) in the Displays panel. I see the exact same information in the additional drivers window as you do. Perhaps this will be fixed with the next update to the kernel.

---

### Post by orasisd on 2013-08-22
yeah, me too -- I 'felt' it that the drivers were ON because of the resolution :D

I am preparing a USB stick to install ubuntu 12.04 64bit on this desktop in a while.
I am curious to see the additional drivers there and make a screenshot to show here too.

---

### Post by orasisd on 2013-08-22
ok so:

Installation complete (without errors) of ubuntu-12.04.2-desktop-amd64.iso on this desktop.
First boot without updating the system from kernel 3.5.0-23 -- bootscreen correct and then I see this (as you can see the resolution is correct in the system too 1920x1080 this is my Samsung native):

[IMG]http://s18.postimg.org/3n2axji1l/image.jpg[/IMG]


Now after installing the 316 updates, no more boot screen (this is clean install you see), booted from the new kernel 3.5.0-39 and I see this:

[IMG]http://s13.postimg.org/w11usog2v/image.jpg[/IMG]


Then I activated the recommended driver and rebooted, no boot screen again -- just darkness for a while, then I see this:

[IMG]http://s13.postimg.org/q7rss44fb/image.jpg[/IMG]


Overall, everything fine, except the boot screen that should not have been wiped out, once I did nothing to the system yet !

---

### Post by krionic on 2013-08-22
@orasisd: I'm a little confused. You said you did a fresh install of 12.04LTS, and upgraded to kernel version 3.5.0-39. I thought kernel version 3.5 was being used for Ubuntu 12.10. Just curious, but can you verify your distribution and kernel versions in a terminal?
For me, this is my distribution info:
```
lsb_release -a
```
```
No LSB modules are available.
Distributor ID:	Ubuntu
**Description:	Ubuntu 12.04.3 LTS**
Release:	12.04
Codename:	precise

```
I get my currently-installed kernel version with the following command:
```
uname -r
```
```
3.2.0-52-generic
```

---

### Post by howefield on 2013-08-22
> **krionic said:**
> I thought kernel version 3.5 was being used for Ubuntu 12.10.

Both kernels are available to 12.04 users, just as the 13.04 kernel will be included when 12.04.3 is released, saucy kernel ect ect will also become available.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by orasisd on 2013-08-22
> **krionic said:**
> @orasisd: I'm a little confused. You said you did a fresh install of 12.04LTS, and upgraded to kernel version 3.5.0-39. I thought kernel version 3.5 was being used for Ubuntu 12.10. Just curious, but can you verify your distribution and kernel versions in a terminal?
For me, this is my distribution info:
```
lsb_release -a
```
```
No LSB modules are available.
Distributor ID:    Ubuntu
**Description:    Ubuntu 12.04.3 LTS**
Release:    12.04
Codename:    precise

```
I get my currently-installed kernel version with the following command:
```
uname -r
```
```
3.2.0-52-generic
```

I was also confused when I saw it, then I though that the x64 versions use different kernel ?

lsb_release -a
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

```

uname -a
```
Linux xxxxxx-desktop 3.5.0-39-generic #60~precise1-Ubuntu SMP Wed Aug 14 15:38:41 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

EDIT:
@howefield
By the way, my laptop which is i386 has 3.2.0-52 kernel, could I install the 3.5.0-39 through synaptic ? It's confusing.

---

### Post by krionic on 2013-08-22
@orasisd:
I guess we got a little off-topic here. I must've missed the boat a while back, when Ubuntu 12.04.2 officially released. Apparently, they made a change that allows you to run the hardware stack and kernel from future releases in the LTS, in order to provide better hardware support for said LTS. More info from Ask Ubuntu ([link1]("http://askubuntu.com/questions/257617/how-can-i-upgrade-the-ubuntu-12-04-2-kernel-to-3-5-0-23"), [link2]("http://askubuntu.com/questions/153325/will-linux-kernel-3-5-be-coming-to-12-04")), and from the Ubuntu Wiki ([link]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")). The kernel you are actually running was designed for Ubuntu 12.10 but ported to 12.04 by default with images of Ubuntu 12.04.2 and later. Images of Ubuntu 12.04.0 & 12.04.1 will require a manual upgrade.

The point is that an upgrade to kernel version 3.2.0-52 (for those of us still running the 3.2 kernels) seems to have broken the nvidia drivers for some of us. I'm going to try a manual upgrade to 3.5 as described in the links, and report back later.

---

### Post by krionic on 2013-08-23
Well, I've run the command ```
sudo apt-get install --install-recommends linux-generic-lts-quantal xserver-xorg-lts-quantal libgl1-mesa-glx-lts-quantal
``` as listed on the Ubuntu Wiki, and going through the trouble to uninstall my video and network drivers, and re-install so that they create a module for the new kernel properly. I am back to the Additional Drivers window not showing *any* nvidia drivers. I also tried purging jockey and nvidia and reinstalling to no effect. I also noticed various errors come up between nvidia and compiz whenever I open and close windows, and these are sporratic. I can always reinstall the OS with the latest image, but things are working for now. Stability has really degraded with this update!

---

### Post by orasisd on 2013-08-23
I do not think we are off-topic. The whole thing with the kernel is confusing me always. I better off create a special bank login system with one way hashing, than put me to update ubuntu.
After all it is a kernel update that messed up display drivers. I installed the x64 version of ubuntu on another computer to see if a fresh installation is the same messy as what the update caused. Not off topic at all.

---

