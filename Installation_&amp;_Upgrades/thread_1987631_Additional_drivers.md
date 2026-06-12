---
title: "Additional drivers"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by AmaterasuEye on 2012-05-26
Can Any One Help me with this error:

when a go to " additional drivers " and clicking active botton this error pops:

" Sorry, this driver installation failed.

Please check the log file for more information: / var / log / jockey.log "

I have this problem with all missing drivers

---

### Post by kc1di on 2012-05-26
unfortunately your image file is not there in your post.

What driver are you trying to install with jockey (additional driver tool)? 

Give us a little more info please.

---

### Post by AmaterasuEye on 2012-05-26
Thanks for your help    "kc1di"    but a have this problem with many drivers like :

usb hid boot protocol mouse drive

input driver event debug model

pc speaker beeper driver

broadcom's specific AMBA driver

intel TCO watchDOG timer Driver

I801 SMBus driver 

broadcom 802.11n wirless LAN driver

pc Speaker driver

---

### Post by roelforg on 2012-05-26
> **AmaterasuEye said:**
> Thanks for your help    "kc1di"    but a have this problem with many drivers like :

usb hid boot protocol mouse drive

input driver event debug model

pc speaker beeper driver

broadcom's specific AMBA driver

intel TCO watchDOG timer Driver

I801 SMBus driver 

broadcom 802.11n wirless LAN driver

pc Speaker driver

You could use imagebin.org for the picture.

---

### Post by AmaterasuEye on 2012-05-26
Thanks all, this is the problem:



this is the missing drivers:

[http://imagebin.org/213938](http://imagebin.org/213938)

and this what happens when i try to install them: 


[http://imagebin.org/213939](http://imagebin.org/213939)

---

### Post by roelforg on 2012-05-26
EDIT: Wrong tab... Oops...

Anyway, could you post /var/log/jockey.log ?

---

### Post by AmaterasuEye on 2012-05-26
how can i do it brother roelforg cuz im new to ubuntu???

---

### Post by roelforg on 2012-05-26
> **AmaterasuEye said:**
> how can i do it brother roelforg cuz im new to ubuntu???

Try to install a driver and when it errors out: open a terminal and run:
```

cat /var/log/jockey.log

```
And post the output

---

### Post by AmaterasuEye on 2012-05-26
:

---

### Post by AmaterasuEye on 2012-05-26
!

---

### Post by AmaterasuEye on 2012-05-26
part 3


ree, disabled] USB HID Boot Protocol mouse driver)
2012-05-26 12:13:06,481 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'acpi:DLL0504:SYN0600:SYN0002:PNP0F13:')
2012-05-26 12:13:06,481 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-26 12:13:06,482 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-26 12:13:06,482 DEBUG: got handler kmod:evbug([KernelModuleHandler, free, disabled] Input driver event debug module)
2012-05-26 12:13:06,482 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-05-26 12:13:06,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd00000504bc0Csc05i00')
2012-05-26 12:13:06,491 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-05-26 12:13:06,499 DEBUG: got handler kmod:i2c_i801([KernelModuleHandler, free, disabled] I801 SMBus driver)
2012-05-26 12:13:06,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'usb:v0A5Cp21BCd0761dcE0dsc01dp01icFEisc01ip01')
2012-05-26 12:13:06,501 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-05-26 12:13:06,501 DEBUG: got handler kmod:btusb([KernelModuleHandler, free, enabled] Generic Bluetooth USB driver ver 0.6)
2012-05-26 12:13:06,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'wmi:77BD0728-2E34-478C-B625-67F02A7E4897')
2012-05-26 12:13:06,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd00000504bc01sc06i01')
2012-05-26 12:13:06,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001028sd00000012bc02sc80i00')
2012-05-26 12:13:06,547 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2012-05-26 12:13:06,623 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-26 12:13:06,547 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-05-26 12:13:06,699 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-26 12:13:06,624 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-05-26 12:13:06,699 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2012-05-26 12:13:06,707 DEBUG: got handler kmod:brcmsmac([KernelModuleHandler, free, disabled] Broadcom 802.11n wireless LAN driver.)
2012-05-26 12:13:06,707 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2012-05-26 12:13:06,712 DEBUG: got handler kmod:bcma([KernelModuleHandler, free, disabled] Broadcom's specific AMBA driver)
2012-05-26 12:13:06,713 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2012-05-26 12:13:06,790 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-26 12:13:06,713 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-05-26 12:13:06,866 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-26 12:13:06,791 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-05-26 12:13:06,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-26 12:13:06,869 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-05-26 12:13:06,869 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-26 12:13:06,869 DEBUG: got handler kmod:evbug([KernelModuleHandler, free, disabled] Input driver event debug module)
2012-05-26 12:13:06,870 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-26 12:13:06,871 DEBUG: got handler kmod:mac_hid([KernelModuleHandler, free, enabled] mac_hid)
2012-05-26 12:13:06,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2012-05-26 12:13:06,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'usb:v0A5Cp21BCd0761dcE0dsc01dp01icE0isc01ip01')
2012-05-26 12:13:06,872 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-05-26 12:13:06,872 DEBUG: got handler kmod:btusb([KernelModuleHandler, free, enabled] Generic Bluetooth USB driver ver 0.6)
2012-05-26 12:13:06,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2012-05-26 12:13:06,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'platform:dcdbas')
2012-05-26 12:13:06,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-26 12:13:06,884 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-05-26 12:13:06,891 DEBUG: got handler kmod:serio_raw([KernelModuleHandler, free, enabled] Raw serio driver)
2012-05-26 12:13:06,891 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-05-26 12:13:06,898 DEBUG: got handler kmod:psmouse([KernelModuleHandler, free, enabled] PS/2 mouse driver)
2012-05-26 12:13:06,898 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-26 12:13:06,899 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-26 12:13:06,899 DEBUG: got handler kmod:evbug([KernelModuleHandler, free, disabled] Input driver event debug module)
2012-05-26 12:13:06,899 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd00000504bc06sc01i00')
2012-05-26 12:13:06,908 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-05-26 12:13:06,917 DEBUG: got handler kmod:iTCO_wdt([KernelModuleHandler, free, disabled] Intel TCO WatchDog Timer Driver)
2012-05-26 12:13:06,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'input:b0011v0002p0008e7326-e0,1,3,k110,111,112,145,14A,14D,14E,14F,ra0,1,18,2F,35,36,39,mlsfw')
2012-05-26 12:13:06,918 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-26 12:13:06,918 DEBUG: got handler kmod:evbug([KernelModuleHandler, free, disabled] Input driver event debug module)
2012-05-26 12:13:06,919 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-26 12:13:06,927 DEBUG: got handler kmod:joydev([KernelModuleHandler, free, enabled] Joystick device interfaces)
2012-05-26 12:13:06,928 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-26 12:13:06,928 DEBUG: got handler kmod:joydev([KernelModuleHandler, free, enabled] Joystick device interfaces)
2012-05-26 12:13:06,928 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-26 12:13:06,929 DEBUG: got handler kmod:joydev([KernelModuleHandler, free, enabled] Joystick device interfaces)
2012-05-26 12:13:06,929 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-26 12:13:06,929 DEBUG: got handler kmod:mac_hid([KernelModuleHandler, free, enabled] mac_hid)
2012-05-26 12:13:06,930 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7248d0c> about HardwareID('modalias', 'input:b0003v0BDAp58C0e1407-e0,1,kD4,ramlsfw')
2012-05-26 12:13:06,930 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-26 12:13:06,930 DEBUG: got handler kmod:evbug([KernelModuleHandler, free, disabled] Input driver event debug module)

---

### Post by AmaterasuEye on 2012-05-26
the output is to long and the site do not support him 


this is the link to my output, check it pleaz it's virus free:

[http://www.mediafire.com/?3pfn65524c8xtkx](http://www.mediafire.com/?3pfn65524c8xtkx)

---

### Post by mörgæs on 2012-05-26
Next time please use a more informative thread title.

---

