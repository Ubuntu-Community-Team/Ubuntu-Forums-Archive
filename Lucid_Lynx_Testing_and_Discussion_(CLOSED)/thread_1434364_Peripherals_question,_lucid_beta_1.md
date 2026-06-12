---
title: "Peripherals question, lucid beta 1"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by techno-mole on 2010-03-20
Hello.

I decided to install the beta of lucid, I did use the upgrade feature first, worked well (actually it's the only time the upgrade worked for me in 2/3 years of using ubuntu) but there were issues so went for a fresh install.

anyway I use a usb trackball mouse, and also a genius graphics tablet, I have some questions regarding these 2 devices.

! - firstly in order to get my track ball working in a useful way I have to mess around with a fdi file, basically it's a 4 button trackball mouse -[one of these]("http://www.logitech.com/index.cfm/mice_pointers/trackballs/devices/4680&cl=us,en")

I have in the past used an fdi file to turn the small button on the left of it to work as a scroll button, you hold the button down and you can scroll, the button also works as a back button if pressed quickly.

however I can't get it to work in lucid beta 1, I'm not expecting magic from a beta, but I am wondering if I will have to do things differently if I use lucid ?

here are the steps I usually use to get the scroll button (this has worked in the last 2 releases of ubuntu)

the fdi file, this file I have to put into the  /etc/hal/fdi/policy folder

the contents of the fdi file are below - 
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" string="Logitech USB Trackball">
      <merge key="input.x11_options.ButtonMapping" type="string">1 8 3 2 9</merge>
      <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
      <merge key="input.x11_options.EmulateWheelButton" type="string">8</merge>
      <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
    </match>
  </device>
</deviceinfo>
```

and then I have to run this command, I normally just add the whole line to the start up applications.
```
xinput set-button-map "Logitech USB Trackball" 1 9 3 4 5 6 7 8 2
```

I have tried this with the beta, but I can't get the scroll feature to work, if I run the command in terminal I get the following error - 
```
unable to find device Logitech USB Trackball

```

This is a little odd because if I run - lsusb (it's a usb mouse) I get the following - 
```
Bus 004 Device 003: ID 062a:0000 Creative Labs Optical mouse
Bus 004 Device 002: ID 5543:0005 UC-Logic Technology Corp. Genius MousePen 8x6 Tablet
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 045e:0287 Microsoft Corp. 
Bus 003 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 003 Device 002: ID 045e:0286 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 004: ID 0d49:7410 Maxtor Mobile Hard Disk Drive (1TB)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root 
```

okay so the system sees the mouse (I know this because I'm using the mouse now)

if I run this in a terminal - cat /proc/bus/input/devices
I get the following - 

```
I: Bus=0003 Vendor=046d Product=c408 Version=0110
N: Name="Logitech USB Trackball"
P: Phys=usb-0000:00:02.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2:1.0/input/input7
U: Uniq=
H: Handlers=mouse3 event7 
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=3
B: MSC=10

```

does this mean that the system sees the mouse as a " Logitech USB Trackball " ? if so why when I run the xinput command in a terminal does it say it can't find the device (see above for error)

also here is the output from running "xinput list" in terminal - 

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; "Logitech USB Trackball"                	id=8	[slave  pointer  (2)]
&#9116;   &#8627; "UC-LOGIC Tablet WP8060U"               	id=9	[slave  pointer  (2)]
&#9116;   &#8627; "HID 062a:0000"                         	id=10	[slave  pointer  (2)]
&#9116;   &#8627; "Macintosh mouse button emulation"      	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; "Power Button"                          	id=6	[slave  keyboard (3)]
    &#8627; "Power Button"                          	id=7	[slave  keyboard (3)]
    &#8627; "AT Translated Set 2 keyboard"          	id=11	[slave  keyboard (3)]

```

2 - as you can see by the output of lsusb I use a graphics tablet, to get this to work I use the wizard pen driver, here is a link to the How to I did for genius graphics tablets - [linkage]("http://ubuntuforums.org/showpost.php?p=8515936&postcount=1")
as you can see this also shows that I need an fdi file in the same place as the mouse fdi file, so I was wondering if my graphics tablet is going to work under lucid ? 

these may not be super important in terms of getting lucid right, but for me (and others that use trackballs/graphics tablets) this may cause concerns.

Thanks in advance for any advice/help

---

### Post by techno-mole on 2010-03-21
*bump*

no one fancy a punt at this ?
 Ive been messing around with various things, but as yet I haven't been able to get it to work as it did on karmic or jaunty (the mouse that is, haven't gone near the graphics tablet yet)

I have even taken out all other usb devices and tried re-installing to see what happened, needless to say I am no further along, one thing I don't understand is that the mouse is a logitech trackman marble 4 button mouse, but the system seems to see it as a variety of different things, which is puzzling.

for example running lsusb gives the following - 

```
Bus 004 Device 003: ID 1004:6018 LG Electronics, Inc. 
Bus 004 Device 002: ID 5543:0005 UC-Logic Technology Corp. Genius MousePen 8x6 Tablet
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 045e:0287 Microsoft Corp. 
[COLOR="Red"]Bus 003 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)[/COLOR]
Bus 003 Device 002: ID 045e:0286 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 005: ID 0d49:7410 Maxtor Mobile Hard Disk Drive (1TB)
Bus 001 Device 004: ID 07ca:a815 AVerMedia Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

and xinput list gives the following - 

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
[COLOR="Red"]&#9116;   &#8627; "Logitech USB Trackball"                	id=8	[slave  pointer  (2)][/COLOR]
&#9116;   &#8627; "UC-LOGIC Tablet WP8060U"               	id=11	[slave  pointer  (2)]
&#9116;   &#8627; "Macintosh mouse button emulation"      	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; "Power Button"                          	id=6	[slave  keyboard (3)]
    &#8627; "Power Button"                          	id=7	[slave  keyboard (3)]
    &#8627; "AVerMedia A815"                        	id=9	[slave  keyboard (3)]
    &#8627; "IR-receiver inside an USB DVB receiver"	id=10	[slave  keyboard (3)]
    &#8627; "AT Translated Set 2 keyboard"          	id=12	[slave  keyboard (3)]

```

and running - cat /proc/bus/input/devices gives the following - 

```
I: Bus=0003 Vendor=046d Product=c408 Version=0110
N: Name="Logitech USB Trackball"
P: Phys=usb-0000:00:02.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2:1.0/input/input6
U: Uniq=
H: Handlers=mouse2 event6 
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=3
B: MSC=10

```

and finally running - lshal gives the following - 

```
udi = '/org/freedesktop/Hal/devices/usb_device_46d_c408_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c408_noserial_if0'  (string)
  info.product = 'Logitech USB Trackball'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c408_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event6'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_46d_c408_noserial_if0'  (string)
  input.product = 'Logitech USB Trackball'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2:1.0/input/input6/event6'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_45e_286_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_02_0'  (string)
  info.product = 'Unknown (0x0286)'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_45e_286_noserial'  (string)

```

I have to admit I in no way have any idea what this all means (well perhaps on a very rudimentary level) and I could just use a normal mouse, but the trackball comes in handy as I have issues with my hands and wrists (both have been operated on, and not really improved) the trackball is much better in terms of movement, and after a while of using a normal mouse I get a fair amount of pain, but not with the trackball, which is why I use one.

I know I can enable scrolling through firefox's preferences, but I also use it when looking through my files, and for scrolling in apps like bluefish when I'm looking through css files etc, so it is an almost essential bit of kit for me anyway, which is why I mentioned it.
As for the graphics tablet, well I take a shed load of pictures (kind of into photography and digital image editing) and it's a good bit of kit, also works really well with apps like Mypaint (which is great by the way)

So any help or advice would be appreciated.

cheers.

One last thing whats is this for in the xinput list ? ```
"Macintosh mouse button emulation"  
```

Many thanks

---

### Post by ridgeland on 2010-03-21
Same boat --- no answer yet.

I compared lshal between Ubuntu 9.04 where my Kinsington trackball works as a scroll wheel and Ubuntu 10.04 beta1 where it does not work.  Both have a mouse section for
```
udi = '/org/freedesktop/Hal/devices/usb_device_47d_1022_noserial_if0_logicaldev_input'

```
Both show the settings I put in /etc/hal/fdi/policy/
 I see the following are in the 9.04 working version for the mouse but not in the 10.4b1 version:

```
  access_control.file = '/dev/input/event4'  (string)
  access_control.type = 'mouse'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
```
Also the following line is different between the two
```
info.capabilities = {'input', 'input.mouse', 'access_control'} (string list)
```
In 10.4b1 the 'access_control' flag is missing.

I don't know any what and why so I'll start learning more.

Please post if you solve it or launch/find a bug report.

---

### Post by techno-mole on 2010-03-21
okay, now that's odd, I posted a solution to the problem I had, and also marked the thread as solved, so why didn't my post show up ?

Anyway, I'll try again, I spent some time fiddling around with various configurations, and had no luck, so I decided to search in synaptic for an app (didn't really know what I was looking for) I installed mouseemu, but for some reason this disabled my keybaord, no idea why.

I cam across this [[COLOR="Red"]app[/COLOR]]("http://live.gnome.org/GPointingDeviceSettings") (it's in the repo's, but I think there is a later version) I'm using the repo version though.
it works a treat for me, easy to configure and picked up the mouse first time, very simple to configure and so far it's working a load better than the way I used to do things, so you could always give it a go and see what happens.

Hope it helps, now all I need to do is test my graphics tablet, should be fun :-)

cheers

---

### Post by ridgeland on 2010-03-21
Thanks techno-mole.
GPointingDeviceSettings works for my Kensington trackball too!
Now I just have to play with the settings.
I was going down the path of search udev rules from this post:
[http://ubuntuforums.org/showthread.php?t=1434325]("http://ubuntuforums.org/showthread.php?t=1434325")
That may be a start it's about a touch pad.

---

### Post by techno-mole on 2010-03-21
no problem, I'm happy you found it useful, I must admit I didn't think it was going to work as well as it did (and still is) I even have side scrolling, which I never had messing around with fdi files.

cheers.

---

