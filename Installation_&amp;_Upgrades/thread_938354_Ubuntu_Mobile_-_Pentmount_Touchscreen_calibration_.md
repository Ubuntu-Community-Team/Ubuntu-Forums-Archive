---
title: "Ubuntu Mobile - Pentmount Touchscreen calibration issue..."
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by Badcam on 2008-10-04
I have a Kohjinsha SH8 and it uses Penmount Touchscreen 6000 USB drivers. I have installed the driver from Penmount.com and all seems to have worked well, except that when I run the Calibration programme, it starts, and I'm asked to choose the number of calibration points, but as soon as I go into the screen where you have to point and hold to calibrate, it won't proceed. The Calibration programme recognises that I'm pressing the correct spot and the word "holding" appears, but then when I expect that it will then say acknowledge that "hold", nothing happens. It wont "save" the calibration point and move to the next screen location, ready for me to point at the next calibration spot. Am I clear as mud?

Can anyone help?

If it helps, I notice there's nothing in my Xorg file, or very little anyway:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I have since added this which I copied from thread 517816 Ubuntu Fiesty on Kohjinsha SH6KB04A, but it's made no difference at all:

Section "InputDevice"
	Identifier	"PenMount"
	Driver		"penmount"
	Option		"Device"	""
	Option		"Protocol"	"PM6000USB"
	Option		"Baudrate"	"19200"
	Option		"ADBit"		"10"
	Option		"PMode"		"1"
	Option		"ConfigFilePath"	"/etc"
	Option		"Button2"	"1"	#  1=right button / 0=middle button
	Option		"PenDownMode"	"0"	#  0=stream mode, 1=point mode
	Option		"HoldTime"	"400000"	#  how long ms to launch the 2nd button
	Option		"ScreenScale"	"0"	#  screen scale enable/disable
	Option		"LockWindowRange"	"32"	#  range for press and hold
	Option		"CalibHoldTime"	"1500000"	#  hold time for calibration
	Option		"XMinOffset"	"10"	#  edge compensation for xmin
	Option		"XMaxOffset"	"10"	#  edge compensation for xmax
	Option		"YMinOffset"	"10"	#  edge compensation for ymin
	Option		"YMaxOffset"	"10"	#  edge compensation for ymax
	Option		"StdXMin"	"10"	#  standard calibration
	Option		"StdXMax"	"1000"	                       
	Option		"StdYMin"	"10"	                       
	Option		"StdYMax"	"1000"	                       
	Option		"DebugLevel"	"0"	#  debug
	Option		"Beep"		"0"		#  0 = slience, 1 = beeper enabled
	Option		"PressVol"	"100"	#  0 = slience
	Option		"PressPitch"	"880"	#  freq. (Hz)
	Option		"PressDur"	"15"	#  duration (1~255)
	Option		"ReleaseVol"	"0"	#  0 = slience
	Option		"ReleasePitch"	"1200"	#  freq. (Hz)
	Option		"ReleaseDur"	"10"	#  duration (1~255)
EndSection

I know stuff all about Linux by the way. I really want to move away from Windows and this Ubuntu Mobile distro is looking really nice.:D

---

### Post by Shiron on 2008-10-10
I have the same problem with a Gigabyte M912, which also uses the PenMount 6000 USB touchscreen. I have also installed the drivers from penmount.com for Ubuntu 8.04 (version 2.2). The touchscreen is detected as a mouse and can't be calibrated, because the penmount driver is not loaded. 
I've tried various setting in the xorg.conf and now the driver loads but xserver does't start correctly anymore, there is some screen flickering and it shows some strange distorted images as if the graphiccard had a defect. But when I comment the line
InputDevice    "Penmount" "AlwaysCore"
it starts just fine.
Here is my current xorg.conf, please tell me if you need any additional info and sorry for my rather bad English.

```

Section "Device"
	Identifier	"Intel0"
	Driver "intel"
	VendorName "Intel Corporation"
	BoardName "Mobile 945GME Express Integrated Graphics Controller"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	VendorName	"Gigabyte"
	ModelName	"M912M"
	Modeline	"800x480" 29.58 800 816 896 992 480 481 484 497 -HSync +Vsync #60hz
	Modeline "1024x600" 48.96 1024 1064 1168 1312 600 601 604 622 -Hsync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Intel0"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
EndSection

Section "InputDevice"
	Identifier	"PenMount"
	Driver		"penmount"
	Option		"Device"	"/dev/input/touchscreen"
	Option		"Protocol"	"PM6000USB"
	Option		"Baudrate"	"19200"
	Option		"ADBit"		"10"
	Option		"PMode"		"1"
	Option		"ConfigFilePath"	"/etc"
	Option		"Button2"	"1"	#  1=right button / 0=middle button
	Option		"PenDownMode"	"0"	#  0=stream mode, 1=point mode
	Option		"HoldTime"	"700000"	#  how long ms to launch the 2nd button
	Option		"ScreenScale"	"0"	#  screen scale enable/disable
	Option		"LockWindowRange"	"32"	#  range for press and hold
	Option		"CalibHoldTime"	"1500000"	#  hold time for calibration
	Option		"XMinOffset"	"10"	#  edge compensation for xmin
	Option		"XMaxOffset"	"10"	#  edge compensation for xmax
	Option		"YMinOffset"	"10"	#  edge compensation for ymin
	Option		"YMaxOffset"	"10"	#  edge compensation for ymax
	Option		"StdXMin"	"10"	#  standard calibration
	Option		"StdXMax"	"1000"	                       
	Option		"StdYMin"	"10"	                       
	Option		"StdYMax"	"1000"	                       
	Option		"DebugLevel"	"0"	#  debug
	Option		"Beep"		"0"		#  0 = slience, 1 = beeper enabled
	Option		"PressVol"	"100"	#  0 = slience
	Option		"PressPitch"	"880"	#  freq. (Hz)
	Option		"PressDur"	"15"	#  duration (1~255)
	Option		"ReleaseVol"	"0"	#  0 = slience
	Option		"ReleasePitch"	"1200"	#  freq. (Hz)
	Option		"ReleaseDur"	"10"	#  duration (1~255)
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen "Default Screen"
	InputDevice "Generic Keyboard" "CoreKeyboard"
	InputDevice    "Penmount" "AlwaysCore"
EndSection
```

---

### Post by monti on 2008-10-30
I have the Kohjinsha SH6 with PM6000 and Ubuntu 8.10 -- and the exact same problems as you guys.  The touch screen works, but needs calibration.  Have you had any luck figuring it out?

---

### Post by Badcam on 2008-10-30
So far no success. I sent a missive to penmount, who advised:

"Dear Sir,

Thank you for your email.
Currently PenMount driver for Ubuntu8.10 still under development,
we will update it on our website when it is ready,
Thank you.

Best regards."

I've installed Ubuntu 8.04 on the laptop as well, and the calibration worked well. I'm going copy the Penmount xorg.conf over to Ubunutu-mobile this weekend, just to see if it works. I'll let you know the results.

---

### Post by Shiruban on 2008-11-04
I have also a kohjinsha SH8 with penmount and intrepid mobile.
So far I still run with the mouse driver instead of the penmount as it works better. I will explain my different results :

_out of the box _: the dirver use is the mouse driver : bad calibration cannot reach the edge but working

_install xserver-xorg-input-penmount_ : a simple apt-get and you have it but to make the touchscreen use the driver I created a fdi file to say to hal to use it, and it worked. Here is my fdi file: /etc/hal/fdi/policy/10-penmount.fdi
```
<?xml version="1.0" encoding ="UTF-8"?><!-- -*- SGML -*-->
<deviceinfo version="0.2">

        <device>
                <match key="input.product" contains="DIALOGUE INC PenMount USB">
        <merge key="input.x11_driver" type="string">penmount</merge>
	<merge key="input.x11-options.AlwaysCore" type="bool">false</merge>
                </match>
        </device>

</deviceinfo>

```

and now the revelant part of a lshal :
```
udi = '/org/freedesktop/Hal/devices/usb_device_14e1_6000_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3'  (string)
  info.product = 'PenMount USB'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_14e1_6000_noserial'  (string)
  info.vendor = 'DIALOGUE INC'  (string)
  linux.device_file = '/dev/bus/usb/005/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2'  (string)
  usb_device.bus_number = 5  (0x5)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration = 'full speed'  (string)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 42164  (0xa4b4)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2'  (string)
  usb_device.max_power = 500  (0x1f4)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'PenMount USB'  (string)
  usb_device.product_id = 24576  (0x6000)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'DIALOGUE INC'  (string)
  usb_device.vendor_id = 5345  (0x14e1)  (int)
  usb_device.version = 1.0 (1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_14e1_6000_noserial_if0'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_14e1_6000_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_14e1_6000_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0'  (string)
  usb.bus_number = 5  (0x5)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration = 'full speed'  (string)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 42164  (0xa4b4)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.description = 'EndPoint1 Interrupt Pipe'  (string)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0'  (string)
  usb.max_power = 500  (0x1f4)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 24576  (0x6000)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'DIALOGUE INC'  (string)
  usb.vendor_id = 5345  (0x14e1)  (int)
  usb.version = 1.0 (1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_14e1_6000_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_14e1_6000_noserial_if0'  (string)
  info.product = 'DIALOGUE INC PenMount USB'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_14e1_6000_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event2'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_14e1_6000_noserial_if0'  (string)
  input.product = 'DIALOGUE INC PenMount USB'  (string)
  input.x11-options.AlwaysCore = false  (bool)
  [COLOR="Red"]input.x11_driver = 'penmount'  (string)[/COLOR]
  linux.device_file = '/dev/input/event2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input2/event2'  (string)
```
Results : when you touch the screen, the mouse jump everywhere, not usable. In the lshal it shows that it use the driver penmount, so not so bad, but calibration crash (gCalib bin from the website driver) even with a killall compiz.real

_driver from penmount websites_.
I installed the driver from the website, kept the fdi, reboot it was still same results : jumping everywhere. I tried a calibration : big X crash, i fixed it in recovery mode by reinstalling the xserver-xorg-input-penmount . 
I try to pass an option AlwaysCore through the fdi but it didn't work : I let it in the file to show how to pass boolean option... you can remove it. 
 
to restore everything just rename your fdi file, restart hal and X.

Next thing i will try is to pass all calibration that was in xorg through the fdi file using the penmount driver from the repository.

some useful references : 
[https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/261873]("https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/261873")
[https://wiki.ubuntu.com/X/Config]("https://wiki.ubuntu.com/X/Config")

perhaps we may have to wait after penmount staff, last time (for hardy they were not so long 2 to 3 months (ok compare to a new release every 6 months it is long)... I will submit a bug anyway : hal doesn't detect well the penmount touchscreen and the driver is broken!


some other problem i got with kohjinsha and intrepid (mobile edition)
[INDENT]suspend doesn't work  : starting to work on it, this is a big regression from hardy![/INDENT]
[INDENT]cellwriter doesn't fit in the screen (this is specific to the mobile edition[/INDENT]
[INDENT]the integrated mic does not work. I will definetevely contact the alsa people, because it is too boring to have to take an external mic always with me...[/INDENT]

more later, I hope...

---

### Post by Badcam on 2008-11-04
> **Shiruban said:**
> 
some other problem i got with kohjinsha and intrepid (mobile edition)
[INDENT]suspend doesn't work  : starting to work on it, this is a big regression from hardy![/INDENT]
[INDENT]cellwriter doesn't fit in the screen (this is specific to the mobile edition[/INDENT]
[INDENT]the integrated mic does not work. I will definetevely contact the alsa people, because it is too boring to have to take an external mic always with me...[/INDENT]

more later, I hope...

Likewise, suspend (nor hibernate if I recall correctly) and the mic don't work for me. I'd like to get Skype working as well. Also, there are quite a few windows that don't fit in the Kohji screen area as well. For some, you have to touch the screen, it moves upwards, touch it again at the same location and then the item I wanted to select originally then activates.

It has great promise though.

---

### Post by Shiruban on 2008-11-04
you're right nor hibernate...
Big problem for a mobile device
I will try to debug this.

cheers

---

### Post by charlie763 on 2008-11-06
Any updates?

---

### Post by remy_cook on 2008-11-19
Hi all,
 I have a Kohjinsha laptop. And penmount drivers worked for me on hardy8.04.1. But as and when I goes to lower right corner of the screen there appears some distance between my pointer and touch pen.
 Another serious problem is that when I rotate screen using "xrandr", the screen doesn't get fit automatically to new resolution(1024x600 -> 600x1024). And remaining part of desktop comes below the first part. Also mouce and touchpen doesn't get updated according to new screen. And moves in wrong direction.
So is there any way to fix it? 

The previous documentation at [http://ubuntuforums.org/archive/index.php/t-517816.html](http://ubuntuforums.org/archive/index.php/t-517816.html) helped me a lot. But still have these problems so please help me. 

Thanks in advance...

---

### Post by monti on 2008-11-19
I have reported the Kohjinsha hibernate issue here as well: 

- [http://ubuntuforums.org/showthread.php?p=6209848](http://ubuntuforums.org/showthread.php?p=6209848)
- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290019](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290019)

Discuss the hibernate issues there instead :)

---

### Post by Shiruban on 2008-11-19
@remy_cook
Does not running gCalib fix your issue of lower right corner. When I was under Hardy after calibration the screen was accesible everywhere. Of course you installed the driver from te penmount website, no?
For the xrandr problem, I couldn't find any way to fix this. Well I didn't have the problem of resolution (I only did xrandr -o right) but the synaptics and touch screen yes. When I mailed this problem to penmount they told me they were working on it, but nothing came. Moreover I think it is much a problem of xorg/xrandr as wacom tablet, synaptics all have this problem...

@monti
I didn't have much time to work on the suspend problem now,  writing my doctor thesis, but I will confirm your bug as soon as possible.

---

### Post by remy_cook on 2008-11-21
[COLOR="DarkGreen"]@remy_cook
Does not running gCalib fix your issue of lower right corner. When I was under Hardy after calibration the screen was accesible everywhere. Of course you installed the driver from te penmount website, no?

[COLOR="DarkRed"]yes as you all suggested in the kohjinsha's 517816 thread.[/COLOR]

For the xrandr problem, I couldn't find any way to fix this. Well I didn't have the problem of resolution (I only did xrandr -o right) but the synaptics and touch screen yes.

[COLOR="DarkRed"]ok. I will test it again on fresh installation.[/COLOR]

 When I mailed this problem to penmount they told me they were working on it, but nothing came. Moreover I think it is much a problem of xorg/xrandr as wacom tablet, synaptics all have this problem...

[COLOR="DarkRed"]Thanks.[/COLOR]

@monti
I didn't have much time to work on the suspend problem now, writing my doctor thesis, but I will confirm your bug as soon as possible.[/COLOR]

---

