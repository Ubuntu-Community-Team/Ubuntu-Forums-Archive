---
title: "Waltop tablet stop work in Lucid"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by oberonking on 2010-03-31
Hi, I have a Genius F509 tablet, in Jaunty/Karmic with Hal the talbet work fine.
I have a test PC where I test new releases.. I put Lucid beta1 there and when I try to make work the tablet... guess what? yes, are dead 
Now Hal are gone, so, how to manage tablets right now??
In Xorg.log it appear, also in lshal... but the tablet are dead.

**lshal**
```
udi = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial'
  info.linux.driver = 'usb' (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_0b_0' (string)
  info.product = ' Tablet' (string)
  info.subsystem = 'usb_device' (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial' (string)
  info.vendor = 'Waltop International Corp.' (string)
  linux.device_file = '/dev/bus/usb/002/003' (string)
  linux.hotplug_type = 2 (0x2) (int)
  linux.subsystem = 'usb' (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-4' (string)
  usb_device.bus_number = 2 (0x2) (int)
  usb_device.can_wake_up = false (bool)
  usb_device.configuration_value = 1 (0x1) (int)
  usb_device.device_class = 0 (0x0) (int)
  usb_device.device_protocol = 0 (0x0) (int)
  usb_device.device_revision_bcd = 257 (0x101) (int)
  usb_device.device_subclass = 0 (0x0) (int)
  usb_device.is_self_powered = false (bool)
  usb_device.linux.device_number = 3 (0x3) (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-4' (string)
  usb_device.max_power = 100 (0x64) (int)
  usb_device.num_configurations = 1 (0x1) (int)
  usb_device.num_interfaces = 1 (0x1) (int)
  usb_device.num_ports = 0 (0x0) (int)
  usb_device.product = ' Tablet' (string)
  usb_device.product_id = 56 (0x38) (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Waltop International Corp.' (string)
  usb_device.vendor_id = 5935 (0x172f) (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial_if0'
  info.linux.driver = 'usbhid' (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial' (string)
  info.product = 'USB HID Interface' (string)
  info.subsystem = 'usb' (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial_if0' (string)
  linux.hotplug_type = 2 (0x2) (int)
  linux.subsystem = 'usb' (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0' (string)
  usb.bus_number = 2 (0x2) (int)
  usb.can_wake_up = false (bool)
  usb.configuration_value = 1 (0x1) (int)
  usb.device_class = 0 (0x0) (int)
  usb.device_protocol = 0 (0x0) (int)
  usb.device_revision_bcd = 257 (0x101) (int)
  usb.device_subclass = 0 (0x0) (int)
  usb.interface.class = 3 (0x3) (int)
  usb.interface.number = 0 (0x0) (int)
  usb.interface.protocol = 0 (0x0) (int)
  usb.interface.subclass = 0 (0x0) (int)
  usb.is_self_powered = false (bool)
  usb.linux.device_number = 3 (0x3) (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0' (string)
  usb.max_power = 100 (0x64) (int)
  usb.num_configurations = 1 (0x1) (int)
  usb.num_interfaces = 1 (0x1) (int)
  usb.num_ports = 0 (0x0) (int)
  usb.product = 'USB HID Interface' (string)
  usb.product_id = 56 (0x38) (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Waltop International Corp.' (string)
  usb.vendor_id = 5935 (0x172f) (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.mouse', 'input.tablet'} (string list)
  info.category = 'input' (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial_if0' (string)
  info.product = 'stylus' (string)
  info.subsystem = 'input' (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial_if0_logicaldev_input' (string)
  input.device = '/dev/input/event5' (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_172f_38_noserial_if0' (string)
  input.product = ' WALTOP Tablet' (string)
  input.x11_driver = 'wacom' (string)
  input.x11_options.BottomX = '17679' (string)
  input.x11_options.BottomY = '10686' (string)
  input.x11_options.TopX = '21' (string)
  input.x11_options.TopY = '21' (string)
  input.x11_options.Type = 'stylus' (string)
  linux.device_file = '/dev/input/event5' (string)
  linux.hotplug_type = 2 (0x2) (int)
  linux.subsystem = 'input' (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0/input/input5/event5' (string)
```

**Xorg.log**
```
(II) config/udev: Adding input device WALTOP Tablet (/dev/input/event5)
(**) WALTOP Tablet : Applying InputClass "evdev pointer catchall"
(**) WALTOP Tablet : Applying InputClass "evdev tablet catchall"
(**) WALTOP Tablet : Applying InputClass "Wacom class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
 compiled for 1.7.6, module version = 0.10.5
 Module class: X.Org XInput Driver
 ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event5"
(II) WALTOP Tablet : type not specified, assuming 'stylus'.
(II) WALTOP Tablet : other types will be automatically added.
(**) WALTOP Tablet : always reports core events
(II) WALTOP Tablet : hotplugging dependent devices.
(**) Option "Device" "/dev/input/event5"
(**) WALTOP Tablet eraser: always reports core events
(II) XINPUT: Adding extended input device " WALTOP Tablet eraser" (type: ERASER)
(--) WALTOP Tablet eraser: using pressure threshold of 61 for button 1
(--) WALTOP Tablet eraser: Wacom Unknown USB tablet speed=38400 maxX=17920 maxY=10752 maxZ=1023 resX=1016 resY=1016 tilt=enabled
(--) WALTOP Tablet eraser: top X=0 top Y=0 bottom X=17920 bottom Y=10752 resol X=1016 resol Y=1016
(II) WALTOP Tablet : hotplugging completed.
(II) XINPUT: Adding extended input device " WALTOP Tablet " (type: STYLUS)
(--) WALTOP Tablet : top X=0 top Y=0 bottom X=17920 bottom Y=10752 resol X=1016 resol Y=1016
(II) config/udev: Adding input device WALTOP Tablet (/dev/input/mouse2)
```

[b]lsusb]
```
Bus 002 Device 003: ID 172f:0038 Waltop International Corp.
```

**xinput**
```
mato@R2-D2:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Genius Optical Mouse                    	id=8	[slave  pointer  (2)]
&#9116;   &#8627;          WALTOP             Tablet      	id=10	[slave  pointer  (2)]
&#9116;   &#8627;          WALTOP             Tablet     eraser	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
mato@R2-D2:~$ 
```

**xsetwacom**
```
mato@R2-D2:~$ xsetwacom --list -v
... Display is '(null)'.
... 'list' requested.
... Found device 'Virtual core XTEST pointer' (4).
... Found device 'Virtual core XTEST keyboard' (5).
... Found device 'Power Button' (6).
... Found device 'Power Button' (7).
... Found device 'Genius Optical Mouse' (8).
... Found device '         WALTOP             Tablet    ' (10).
         WALTOP             Tablet     STYLUS    
... Found device '         WALTOP             Tablet     eraser' (9).
         WALTOP             Tablet     eraser ERASER    
... Found device 'AT Translated Set 2 keyboard' (11).
... Found device 'Macintosh mouse button emulation' (12).
mato@R2-D2:~$
```

Well.... I need it, so, if that don't have fix.... I can't use Lucid when become released

Any idea??? someone?? thanks in advance.....

---

### Post by oberonking on 2010-04-01
Bump!!!

---

### Post by oberonking on 2010-04-02
2nd Bump

---

### Post by NCLI on 2010-04-02
[Report a bug]("https://help.ubuntu.com/community/ReportingBugs") ;)

---

### Post by oberonking on 2010-04-03
> **NCLI said:**
> [Report a bug]("https://help.ubuntu.com/community/ReportingBugs") ;)

Yes, I know....... there's somes

But, I ask for the metod to make it work without Hal... 
If I uninstall xserver-xorg-input-wacom the tablet began to work like a mouse... but there's no way (that I know) to configure it.
wacom.fdi not work anymore and with xsetwacom either. 
With xserver-xorg-input-wacom the tablet comes to dead state

If someone know how to make work tablets without Hal... please advice

---

### Post by mcoleman44 on 2010-04-03
```
sudo apt-get install git-core

cd ./Desktop

git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom

sudo apt-get build-dep xf86-input-wacom

cd xf86-input-wacom

./autogen.sh --prefix=/usr

make

sudo make install
```This should get things working.

You need to configure it using an xorg.conf by the way.

---

### Post by oberonking on 2010-04-03
> **mcoleman44 said:**
> ```
sudo apt-get install git-core

cd ./Desktop

git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom

sudo apt-get build-dep xf86-input-wacom

cd xf86-input-wacom

./autogen.sh --prefix=/usr

make

sudo make install
```This should get things working.

You need to configure it using an xorg.conf by the way.

I already try it with no luck.... thanks any way... ;)
The tablet use the udev....
I change The xorg.conf like this:

```
Section "InputDevice"
	Identifier 	"stylus"
        Driver 		"wacom"
        Option 		"Device"	"/dev/input/event5"
        Option  	"Type"		"stylus"
	Option 		"Mode" 		"Relative"
	Option  	"USB"           "on"
	Option 		"TopX" 		"21"
	Option 		"TopY" 		"21"
	Option 		"BottomX"	"17679"
	Option 		"BottomX" 	"10686"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
                Depth     24
                Modes     "1280x1024"
        EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "stylus"  "SendCoreEvents"
EndSection
```

And the log of xorg are:

```
(II) config/udev: Adding input device          WALTOP             Tablet     (/dev/input/event5)
(**)          WALTOP             Tablet    : Applying InputClass "evdev pointer catchall"
(**)          WALTOP             Tablet    : Applying InputClass "evdev tablet catchall"
(**)          WALTOP             Tablet    : always reports core events
(**)          WALTOP             Tablet    : Device: "/dev/input/event5"
(II)          WALTOP             Tablet    : Found 9 mouse buttons
(II)          WALTOP             Tablet    : Found scroll wheel(s)
(II)          WALTOP             Tablet    : Found relative axes
(II)          WALTOP             Tablet    : Found x and y relative axes
(II)          WALTOP             Tablet    : Found absolute axes
(II)          WALTOP             Tablet    : Found x and y absolute axes
(II)          WALTOP             Tablet    : Found absolute tablet.
(II)          WALTOP             Tablet    : Configuring as tablet
(**)          WALTOP             Tablet    : YAxisMapping: buttons 4 and 5
(**)          WALTOP             Tablet    : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "         WALTOP             Tablet    " (type: TABLET)
(WW)          WALTOP             Tablet    : touchpads, tablets and touchscreens ignore relative axes.
(II)          WALTOP             Tablet    : initialized for absolute axes.
(II) config/udev: Adding input device          WALTOP             Tablet     (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
```

The wacom's module is loaded



I don't know other changes to do it...... any sugestion??

---

### Post by mcoleman44 on 2010-04-03
see if you get any results when trying this. Type this command and try using your finger or the stylus to see if you get any results 
sudo xxd /dev/hidraw1

press ctrl+c to exit the application.
if you get no response from hidraw1 try hidraw0 and hidraw2

---

### Post by oberonking on 2010-04-03
> **mcoleman44 said:**
> see if you get any results when trying this. Type this command and try using your finger or the stylus to see if you get any results 
sudo xxd /dev/hidraw1

press ctrl+c to exit the application.
if you get no response from hidraw1 try hidraw0 and hidraw2

Yes.. it start to move like a mouse and responds on buttons clicks....

---

### Post by mcoleman44 on 2010-04-03
Post the results of ls /dev/input
please

---

### Post by oberonking on 2010-04-03
At your command

```
mato@R2-D2:~$ ls /dev/input
by-id    event0  event2  event4  event6  mouse0  mouse2
by-path  event1  event3  event5  mice    mouse1
mato@R2-D2:~$ 
```

---

### Post by mcoleman44 on 2010-04-03
After taking another look at your log and xorg.conf file im thinking it may not work.

**[SIZE=3][COLOR=Red]Notice for Serial Graphics Tablet  Users[/COLOR][/SIZE]**:  This quote is from a LWP developer (2-17-10):
 	Quote:
 	 	 		 			 				If it is not an ISDv4 model, i.e., the digitizer is not embedded in  your laptop/desktop, you will have to
use an X server older than XOrg 1.7. We do not support regular serial  tablets on X server 1.7 or later. 			 		 	 	 
In other words, if this is correct, external Serial Graphics  Tablets connecting via a serial cable will not be supported on X server  1.7 (Lucid) and up.  If true **[SIZE=3]do not update to Lucid![/SIZE]**   Waiting on further clarification.

[http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1)

Im thinking this applies to you. 
I may be wrong though, someone feel free to correct me if I am.

---

### Post by oberonking on 2010-04-03
Mine is USB not Serial.
By the way... I can't compile linuxwacom it gives me errors at "make" step

```
mato@R2-D2:~/Escritorio/linuxwacom-0.8.4-4$ make
Making all in src
make[1]: se ingresa al directorio `/home/mato/Escritorio/linuxwacom-0.8.4-4/src'
Making all in .
make[2]: se ingresa al directorio `/home/mato/Escritorio/linuxwacom-0.8.4-4/src'
make[2]: No se hace nada para `all-am'.
make[2]: se sale del directorio `/home/mato/Escritorio/linuxwacom-0.8.4-4/src'
Making all in wacomxi
make[2]: se ingresa al directorio `/home/mato/Escritorio/linuxwacom-0.8.4-4/src/wacomxi'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/mato/Escritorio/linuxwacom-0.8.4-4/src/wacomxi'
Making all in util
make[2]: se ingresa al directorio `/home/mato/Escritorio/linuxwacom-0.8.4-4/src/util'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/mato/Escritorio/linuxwacom-0.8.4-4/src/util'
Making all in xdrv
make[2]: se ingresa al directorio `/home/mato/Escritorio/linuxwacom-0.8.4-4/src/xdrv'
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  -fvisibility=hidden -I/usr/include/xorg -I/usr/include/pixman-1   \
		-D_XSERVER64 -fvisibility=hidden -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o xf86Wacom.o -c ./xf86Wacom.c
In file included from ./xf86Wacom.h:27,
                 from ./xf86Wacom.c:93:
/usr/include/xorg/xorg-server.h:183:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./xf86Wacom.c:93:
./../include/xdrv-config.h:9:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:159,
                 from ./xf86Wacom.c:93:
./xf86WacomDefs.h:129:1: warning: "MAX_BUTTONS" redefined
In file included from /usr/include/xorg/xf86str.h:38,
                 from /usr/include/xorg/xf86.h:46,
                 from ./xf86Wacom.h:68,
                 from ./xf86Wacom.c:93:
/usr/include/xorg/input.h:80:1: warning: this is the location of the previous definition
./xf86Wacom.c: In function &#8216;xf86WcmInitialCoordinates&#8217;:
./xf86Wacom.c:368: error: too few arguments to function &#8216;InitValuatorAxisStruct&#8217;
./xf86Wacom.c:395: error: too few arguments to function &#8216;InitValuatorAxisStruct&#8217;
./xf86Wacom.c: In function &#8216;xf86WcmRegisterX11Devices&#8217;:
./xf86Wacom.c:630: warning: passing argument 3 of &#8216;InitButtonClassDeviceStruct&#8217; from incompatible pointer type
/usr/include/xorg/input.h:290: note: expected &#8216;Atom *&#8217; but argument is of type &#8216;CARD8 *&#8217;
./xf86Wacom.c:630: error: too few arguments to function &#8216;InitButtonClassDeviceStruct&#8217;
./xf86Wacom.c:670: warning: passing argument 3 of &#8216;InitValuatorClassDeviceStruct&#8217; makes pointer from integer without a cast
/usr/include/xorg/input.h:296: note: expected &#8216;Atom *&#8217; but argument is of type &#8216;int&#8217;
./xf86Wacom.c:670: error: too few arguments to function &#8216;InitValuatorClassDeviceStruct&#8217;
./xf86Wacom.c:712: warning: implicit declaration of function &#8216;InitKeyClassDeviceStruct&#8217;
./xf86Wacom.c:720: warning: implicit declaration of function &#8216;InitKbdFeedbackClassDeviceStruct&#8217;
./xf86Wacom.c:751: error: too few arguments to function &#8216;InitValuatorAxisStruct&#8217;
./xf86Wacom.c:756: error: too few arguments to function &#8216;InitValuatorAxisStruct&#8217;
./xf86Wacom.c:757: error: too few arguments to function &#8216;InitValuatorAxisStruct&#8217;
./xf86Wacom.c:765: error: too few arguments to function &#8216;InitValuatorAxisStruct&#8217;
./xf86Wacom.c:766: error: too few arguments to function &#8216;InitValuatorAxisStruct&#8217;
./xf86Wacom.c:772: error: too few arguments to function &#8216;InitValuatorAxisStruct&#8217;
./xf86Wacom.c:773: error: too few arguments to function &#8216;InitValuatorAxisStruct&#8217;
./xf86Wacom.c:781: error: too few arguments to function &#8216;InitValuatorAxisStruct&#8217;
./xf86Wacom.c:786: error: too few arguments to function &#8216;InitValuatorAxisStruct&#8217;
./xf86Wacom.c:790: error: too few arguments to function &#8216;InitValuatorAxisStruct&#8217;
make[2]: *** [xf86Wacom.o] Error 1
make[2]: se sale del directorio `/home/mato/Escritorio/linuxwacom-0.8.4-4/src/xdrv'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/mato/Escritorio/linuxwacom-0.8.4-4/src'
make: *** [all-recursive] Error 1
```

So, I can't follow that guide

---

### Post by mcoleman44 on 2010-04-04
Try seeing what events give you a response when using the stylus.
sudo xxd /dev/input/eventx

Try events 1-6

---

### Post by oberonking on 2010-04-04
> **mcoleman44 said:**
> Try seeing what events give you a response when using the stylus.
sudo xxd /dev/input/eventx

Try events 1-6

Nothing... the tablet in lshal at least is /dev/input/event5... nothing happens.
the other are not the tablet.. event3 is keyboard and event4 mouse.

I'm out of my mind....  I think Lucid is not an option to me.

I go back to Karmic and stay there for ever.. :p

---

