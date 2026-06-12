---
title: "How to use xinput to change device for mouse"
date: 2009-12-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sethhikari on 2009-12-19
I am using lucid and I have a device that takes controll of my mouse when I plug it in. I don't want this to happen so I can just use it as a joystick. How do I use xinput to change the current mouse.

I looked in google but they all have to do with the hal witch is not in lucid anymore?

---

### Post by hugmenot on 2009-12-20
Run ```
udevadm monitor
```and plug you device.

It probably gets assigned to be driven by input-evdev, which you don&#8217;t want?
You haven&#8217;t been very clear.

A custom udev rule in /etc/udev/rules.d/ can probably prevent that.

---

### Post by sethhikari on 2009-12-21
```
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[1261375780.132855] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5 (usb)
KERNEL[1261375780.135741] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0 (usb)
KERNEL[1261375780.135881] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/0003:054C:0268.0005 (hid)
UDEV  [1261375780.137013] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5 (usb)
UDEV  [1261375780.137088] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0 (usb)
UDEV  [1261375780.137475] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/0003:054C:0268.0005 (hid)
KERNEL[1261375780.228994] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input8 (input)
KERNEL[1261375780.229037] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input8/event7 (input)
KERNEL[1261375780.229061] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input8/js0 (input)
KERNEL[1261375780.229084] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/usb/hiddev1 (usb)
KERNEL[1261375780.229105] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/0003:054C:0268.0005/hidraw/hidraw3 (hidraw)
UDEV  [1261375780.229976] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/usb/hiddev1 (usb)
UDEV  [1261375780.230298] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/0003:054C:0268.0005/hidraw/hidraw3 (hidraw)
UDEV  [1261375780.232251] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input8 (input)
UDEV  [1261375780.241262] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input8/js0 (input)
UDEV  [1261375780.241570] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input8/event7 (input)
KERNEL[1261375795.889991] remove   /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input8/event7 (input)
UDEV  [1261375795.893044] remove   /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input8/event7 (input)
```

I would like my ps3 controller to not be configured as a mouse but as a regular joystick input device.

---

### Post by sethhikari on 2009-12-21
Im not to sure how to go about writing the rule

---

### Post by hugmenot on 2009-12-21
Can you run that again with --property?

```
udevadm monitor --property
```

And then copy the DEVPATH and run this

```
udevadm test --action=add /devices/.../input/inputN
```

I want to figure out if a bug should be filed against xserver-xorg-input-evdev or not.
I&#8217;m not sure what&#8217;s going on.

---

### Post by sethhikari on 2009-12-23
udevadm monitor --property
```
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[1261595909.630635] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-5
SUBSYSTEM=usb
DEVNAME=bus/usb/004/004
DEVTYPE=usb_device
PRODUCT=54c/268/100
TYPE=0/0/0
BUSNUM=004
DEVNUM=004
SEQNUM=2003
MAJOR=189
MINOR=387

KERNEL[1261595909.633551] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0
SUBSYSTEM=usb
DEVTYPE=usb_interface
PRODUCT=54c/268/100
TYPE=0/0/0
INTERFACE=3/0/0
MODALIAS=usb:v054Cp0268d0100dc00dsc00dp00ic03isc00ip00
SEQNUM=2004

KERNEL[1261595909.633728] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/0003:054C:0268.0007 (hid)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/0003:054C:0268.0007
SUBSYSTEM=hid
HID_ID=0003:0000054C:00000268
HID_NAME=Sony PLAYSTATION(R)3 Controller
HID_PHYS=usb-0000:00:04.0-5/input0
DRIVER=sony
MODALIAS=hid:b0003v0000054Cp00000268
SEQNUM=2005

UDEV  [1261595909.635324] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-5
SUBSYSTEM=usb
DEVNAME=/dev/bus/usb/004/004
DEVTYPE=usb_device
PRODUCT=54c/268/100
TYPE=0/0/0
BUSNUM=004
DEVNUM=004
SEQNUM=2003
ID_VENDOR=Sony
ID_VENDOR_ENC=Sony
ID_VENDOR_ID=054c
ID_MODEL=PLAYSTATION_R_3_Controller
ID_MODEL_ENC=PLAYSTATION\x28R\x293\x20Controller
ID_MODEL_ID=0268
ID_REVISION=0100
ID_SERIAL=Sony_PLAYSTATION_R_3_Controller
ID_BUS=usb
ID_USB_INTERFACES=:030000:
MAJOR=189
MINOR=387
DEVLINKS=/dev/char/189:387

UDEV  [1261595909.635446] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0
SUBSYSTEM=usb
DEVTYPE=usb_interface
PRODUCT=54c/268/100
TYPE=0/0/0
INTERFACE=3/0/0
MODALIAS=usb:v054Cp0268d0100dc00dsc00dp00ic03isc00ip00
SEQNUM=2004

UDEV  [1261595909.635509] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/0003:054C:0268.0007 (hid)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/0003:054C:0268.0007
SUBSYSTEM=hid
HID_ID=0003:0000054C:00000268
HID_NAME=Sony PLAYSTATION(R)3 Controller
HID_PHYS=usb-0000:00:04.0-5/input0
DRIVER=sony
MODALIAS=hid:b0003v0000054Cp00000268
SEQNUM=2005

KERNEL[1261595909.726806] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input10 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input10
SUBSYSTEM=input
PRODUCT=3/54c/268/111
NAME="Sony PLAYSTATION(R)3 Controller"
PHYS="usb-0000:00:04.0-5/input0"
UNIQ=""
EV==1b
KEY==7ffff00000000 0 0 0 0
ABS==ffffff0000000027
MSC==10
MODALIAS=input:b0003v054Cp0268e0111-e0,1,3,4,k120,121,122,123,124,125,126,127,128,129,12A,12B,12C,12D,12E,12F,130,131,132,ra0,1,2,5,28,29,2A,2B,2C,2D,2E,2F,30,31,32,33,34,35,36,37,38,39,3A,3B,3C,3D,3E,m4,lsfw
SEQNUM=2006

KERNEL[1261595909.726905] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input10/event6 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input10/event6
SUBSYSTEM=input
DEVNAME=input/event6
SEQNUM=2007
MAJOR=13
MINOR=70

KERNEL[1261595909.726959] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input10/js0 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input10/js0
SUBSYSTEM=input
DEVNAME=input/js0
SEQNUM=2008
MAJOR=13
MINOR=0

KERNEL[1261595909.727009] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/usb/hiddev1 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/usb/hiddev1
SUBSYSTEM=usb
DEVNAME=usb/hiddev1
SEQNUM=2009
MAJOR=180
MINOR=97

KERNEL[1261595909.727059] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/0003:054C:0268.0007/hidraw/hidraw3 (hidraw)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/0003:054C:0268.0007/hidraw/hidraw3
SUBSYSTEM=hidraw
DEVNAME=hidraw3
SEQNUM=2010
MAJOR=252
MINOR=3

UDEV  [1261595909.727791] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/usb/hiddev1 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/usb/hiddev1
SUBSYSTEM=usb
DEVNAME=/dev/usb/hiddev1
SEQNUM=2009
MAJOR=180
MINOR=97
DEVLINKS=/dev/char/180:97

UDEV  [1261595909.728084] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/0003:054C:0268.0007/hidraw/hidraw3 (hidraw)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/0003:054C:0268.0007/hidraw/hidraw3
SUBSYSTEM=hidraw
DEVNAME=/dev/hidraw3
SEQNUM=2010
MAJOR=252
MINOR=3
DEVLINKS=/dev/char/252:3

UDEV  [1261595909.730101] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input10 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input10
SUBSYSTEM=input
PRODUCT=3/54c/268/111
NAME="Sony PLAYSTATION(R)3 Controller"
PHYS="usb-0000:00:04.0-5/input0"
UNIQ=""
EV==1b
KEY==7ffff00000000 0 0 0 0
ABS==ffffff0000000027
MSC==10
MODALIAS=input:b0003v054Cp0268e0111-e0,1,3,4,k120,121,122,123,124,125,126,127,128,129,12A,12B,12C,12D,12E,12F,130,131,132,ra0,1,2,5,28,29,2A,2B,2C,2D,2E,2F,30,31,32,33,34,35,36,37,38,39,3A,3B,3C,3D,3E,m4,lsfw
SEQNUM=2006

UDEV  [1261595909.738976] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input10/js0 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input10/js0
SUBSYSTEM=input
DEVNAME=/dev/input/js0
SEQNUM=2008
ID_INPUT=1
ID_INPUT_JOYSTICK=1
ID_VENDOR=Sony
ID_VENDOR_ENC=Sony
ID_VENDOR_ID=054c
ID_MODEL=PLAYSTATION_R_3_Controller
ID_MODEL_ENC=PLAYSTATION\x28R\x293\x20Controller
ID_MODEL_ID=0268
ID_REVISION=0100
ID_SERIAL=Sony_PLAYSTATION_R_3_Controller
ID_TYPE=hid
ID_BUS=usb
ID_USB_INTERFACES=:030000:
ID_USB_INTERFACE_NUM=00
ID_USB_DRIVER=usbhid
ID_PATH=pci-0000:00:04.0-usb-0:5:1.0
ACL_MANAGE=1
MAJOR=13
MINOR=0
DEVLINKS=/dev/char/13:0 /dev/input/by-id/usb-Sony_PLAYSTATION_R_3_Controller-joystick /dev/input/by-path/pci-0000:00:04.0-usb-0:5:1.0-joystick

UDEV  [1261595909.739136] add      /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input10/event6 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input10/event6
SUBSYSTEM=input
DEVNAME=/dev/input/event6
SEQNUM=2007
ID_INPUT=1
ID_INPUT_JOYSTICK=1
ID_VENDOR=Sony
ID_VENDOR_ENC=Sony
ID_VENDOR_ID=054c
ID_MODEL=PLAYSTATION_R_3_Controller
ID_MODEL_ENC=PLAYSTATION\x28R\x293\x20Controller
ID_MODEL_ID=0268
ID_REVISION=0100
ID_SERIAL=Sony_PLAYSTATION_R_3_Controller
ID_TYPE=hid
ID_BUS=usb
ID_USB_INTERFACES=:030000:
ID_USB_INTERFACE_NUM=00
ID_USB_DRIVER=usbhid
ID_PATH=pci-0000:00:04.0-usb-0:5:1.0
x11_driver=evdev
ACL_MANAGE=1
MAJOR=13
MINOR=70
DEVLINKS=/dev/char/13:70 /dev/input/by-id/usb-Sony_PLAYSTATION_R_3_Controller-event-joystick /dev/input/by-path/pci-0000:00:04.0-usb-0:5:1.0-event-joystick
```

^Cseth@Twilight-Linux:~$ udevadm test --```
action=add/devices/pci0000:00/0000:00:04/usb4/4-5/4-5:1.0/input/input10/event6
run_command: calling: test
udevadm_test: version 149
syspath parameter missing
```

---

### Post by hugmenot on 2009-12-24
You missed a space. Try this:

```
udevadm test --action=add  /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input10/event6
```

---

### Post by sethhikari on 2009-12-24
Oh duh my bad

```
udevadm test --action=add  /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input10/event6
run_command: calling: test
udevadm_test: version 149
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

parse_file: reading '/lib/udev/rules.d/40-gnupg.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-hplip.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-ia64.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-infiniband.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-isdn.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-libgphoto2-2.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-libpisock9.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-libsane.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-pilot-links.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-ppc.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-xserver-xorg-video-intel.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-zaptel.rules' as rules file
parse_file: reading '/lib/udev/rules.d/45-fuse.rules' as rules file
parse_file: reading '/lib/udev/rules.d/45-libmtp8.rules' as rules file
parse_file: reading '/lib/udev/rules.d/50-firmware.rules' as rules file
parse_file: reading '/lib/udev/rules.d/50-udev-default.rules' as rules file
parse_file: reading '/lib/udev/rules.d/56-hpmud_support.rules' as rules file
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/56-hpmud_support.rules:10
parse_file: reading '/lib/udev/rules.d/60-cdrom_id.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-alsa.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-input.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-serial.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage-tape.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-v4l.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-gnome-bluetooth-rfkill.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-mobile-action.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-option-modem-modeswitch.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-persistent-storage-edd.rules' as rules file
parse_file: reading '/lib/udev/rules.d/64-device-mapper.rules' as rules file
parse_file: reading '/lib/udev/rules.d/64-xorg-xkb.rules' as rules file
parse_file: reading '/lib/udev/rules.d/65-dmsetup.rules' as rules file
parse_file: reading '/lib/udev/rules.d/65-xorg-evdev.rules' as rules file
parse_file: reading '/lib/udev/rules.d/66-xorg-synaptics.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-acl.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-hid2hci.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-cd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-net.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-printers.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-cd-aliases-generator.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-net-description.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-persistent-net-generator.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-tty-description.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-ericsson-mbm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-zte-port-types.rules' as rules file
parse_file: reading '/lib/udev/rules.d/78-graphics-card.rules' as rules file
parse_file: reading '/lib/udev/rules.d/78-sound-card.rules' as rules file
parse_file: reading '/lib/udev/rules.d/79-fstab_import.rules' as rules file
parse_file: reading '/lib/udev/rules.d/80-alsa.rules' as rules file
parse_file: reading '/lib/udev/rules.d/80-drivers.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-brltty.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-hdparm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-hplj10xx.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-pcmcia.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-regulatory.rules' as rules file
parse_file: reading '/lib/udev/rules.d/90-pulseaudio.rules' as rules file
parse_file: reading '/lib/udev/rules.d/90-usb-media-players.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-disks.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-battery-recall-dell.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-battery-recall-fujitsu.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-battery-recall-gateway.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-battery-recall-ibm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-battery-recall-lenovo.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-battery-recall-toshiba.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-csr.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-hid.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-devkit-power-wup.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-keymap.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-udev-late.rules' as rules file
parse_file: reading '/lib/udev/rules.d/97-bluetooth.rules' as rules file
udev_rules_new: rules use 189072 bytes tokens (15756 * 12 bytes), 28497 bytes buffer
udev_rules_new: temporary index used 49380 bytes (2469 * 20 bytes)
unable to open device '/sys/devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input10/event6'
```

---

### Post by hugmenot on 2009-12-25
Err ...

Actually the path changes every time you boot, or plug in that thing. So you have to copy and paste the device path every time.

[Just do this again]("http://ubuntuforums.org/showpost.php?p=8535316&postcount=5")

---

