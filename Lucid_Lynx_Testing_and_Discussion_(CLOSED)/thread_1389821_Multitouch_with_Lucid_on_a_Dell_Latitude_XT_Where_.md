---
title: "Multitouch with Lucid on a Dell Latitude XT: Where to Start?"
date: 2010-01-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Ubuntiac on 2010-01-24
Hi there,

I'd like to get multitouch working on my Dell Latitude XT running Lucid. Trouble is that the gazillion howto guides all seem to be for older versions of ubuntu (Jaunty / Karmic), and they all seem to say that later versions will make much of what they say irrelevant.

That leaves me unsure whether to use an .fdi or xorg.conf, whether to compile a patched kernel or use the latest one in Lucid etc. etc. Any help, even just a pointer to a relevant, *up to date* tutorial would be awesome!

Thanks!



--------------------------------------
Tech specs:

I have xserver-xorg-input-wacom installed

uname -r
```
2.6.32-11-generic
```

xsetwacom list
```
stylus           STYLUS
eraser           ERASER
touch            TOUCH
"HID 1b96:0001" eraser ERASER
"HID 1b96:0001" touch TOUCH
"HID 1b96:0001"  STYLUS

```

xorg.conf
```
Section "ServerLayout"                                                                                                                  
         Identifier     "Default Layout"                                                                                                
         Screen         "Default Screen" 0 0                                                                                            
         InputDevice    "Synaptics Touchpad"                                                                                            
         InputDevice    "stylus"                                                                                                        
         InputDevice    "eraser"                                                                                                        
         InputDevice    "touch"                                                                                                         
EndSection

Section "Screen"
         Identifier  "Default Screen"
EndSection


Section "InputDevice"
         Identifier  "Synaptics Touchpad"
         Driver      "synaptics"
         Option      "Device" "/dev/input/mouse4"
         Option      "Protocol" "auto"
         Option      "HorizEdgeScroll" "0"
         Option      "SHMConfig" "on"
EndSection

 # This section is for the TabletPC that supports touch
Section "InputDevice"
         Identifier  "touch"
         Driver      "wacom"
         Option      "Mode" "Absolute"
         Option      "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
         Option      "Type" "touch"
         Option      "TopX" "0"
         Option      "TopY" "0"
         Option      "BottomX" "9600"
         Option      "BottomY" "7200"
         Option      "Touch"             "on"
         Option      "Supress"   "0"
EndSection

Section "InputDevice"
         Identifier  "stylus"
         Driver      "wacom"
         Option      "Mode" "Absolute"
         Option      "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
         Option      "Type" "stylus"
         Option      "Touch"     "on"
         Option      "Button1" "1"
         Option      "Button2" "3"
         Option      "Button3" "2"
EndSection

Section "InputDevice"
         Identifier  "eraser"
         Driver      "wacom"
         Option      "Mode" "Absolute"
         Option      "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
         Option      "Type" "eraser"
         Option      "Button1" "2"
         Option      "Button9" "0"
EndSection

```

lsusb -v   (n-trig section only)
```
Bus 003 Device 002: ID 1b96:0001 N-Trig Duosense Transparent Electromagnetic Digitizer
Device Descriptor:                                                                    
  bLength                18                                                           
  bDescriptorType         1                                                           
  bcdUSB               1.10                                                           
  bDeviceClass            0 (Defined at Interface level)                              
  bDeviceSubClass         0                                                           
  bDeviceProtocol         0                                                           
  bMaxPacketSize0        64                                                           
  idVendor           0x1b96 N-Trig                                                    
  idProduct          0x0001 Duosense Transparent Electromagnetic Digitizer            
  bcdDevice            0.00                                                           
  iManufacturer           0                                                           
  iProduct                0                                                           
  iSerial                 0                                                           
  bNumConfigurations      1                                                           
  Configuration Descriptor:                                                           
    bLength                 9                                                         
    bDescriptorType         2                                                         
    wTotalLength           95                                                         
    bNumInterfaces          3                                                         
    bConfigurationValue     1                                                         
    iConfiguration          0                                                         
    bmAttributes         0xe0                                                         
      Self Powered                                                                    
      Remote Wakeup                                                                   
    MaxPower              500mA                                                       
    Interface Descriptor:                                                             
      bLength                 9                                                       
      bDescriptorType         4                                                       
      bInterfaceNumber        0                                                       
      bAlternateSetting       0                                                       
      bNumEndpoints           1                                                       
      bInterfaceClass         3 Human Interface Device                                
      bInterfaceSubClass      1 Boot Interface Subclass                               
      bInterfaceProtocol      2 Mouse                                                 
      iInterface              0                                                       
        HID Device Descriptor:                                                        
          bLength                 9                                                   
          bDescriptorType        33                                                   
          bcdHID               1.10                                                   
          bCountryCode            0 Not supported                                     
          bNumDescriptors         1                                                   
          bDescriptorType        34 Report                                            
          wDescriptorLength     161                                                   
         Report Descriptors:                                                          
           ** UNAVAILABLE **                                                          
      Endpoint Descriptor:                                                            
        bLength                 7                                                     
        bDescriptorType         5                                                     
        bEndpointAddress     0x81  EP 1 IN                                            
        bmAttributes            3                                                     
          Transfer Type            Interrupt                                          
          Synch Type               None                                               
          Usage Type               Data                                               
        wMaxPacketSize     0x0010  1x 16 bytes                                        
        bInterval               1                                                     
    Interface Descriptor:                                                             
      bLength                 9                                                       
      bDescriptorType         4                                                       
      bInterfaceNumber        1                                                       
      bAlternateSetting       0                                                       
      bNumEndpoints           1                                                       
      bInterfaceClass         3 Human Interface Device                                
      bInterfaceSubClass      1 Boot Interface Subclass                               
      bInterfaceProtocol      2 Mouse                                                 
      iInterface              0                                                       
        HID Device Descriptor:                                                        
          bLength                 9                                                   
          bDescriptorType        33                                                   
          bcdHID               1.10                                                   
          bCountryCode            0 Not supported                                     
          bNumDescriptors         1                                                   
          bDescriptorType        34 Report                                            
          wDescriptorLength     161                                                   
         Report Descriptors:                                                          
           ** UNAVAILABLE **                                                          
      Endpoint Descriptor:                                                            
        bLength                 7                                                     
        bDescriptorType         5                                                     
        bEndpointAddress     0x82  EP 2 IN                                            
        bmAttributes            3                                                     
          Transfer Type            Interrupt                                          
          Synch Type               None                                               
          Usage Type               Data                                               
        wMaxPacketSize     0x0010  1x 16 bytes                                        
        bInterval               1                                                     
    Interface Descriptor:                                                             
      bLength                 9                                                       
      bDescriptorType         4                                                       
      bInterfaceNumber        2                                                       
      bAlternateSetting       0                                                       
      bNumEndpoints           1                                                       
      bInterfaceClass         0 (Defined at Interface level)                          
      bInterfaceSubClass      0                                                       
      bInterfaceProtocol      0                                                       
      iInterface              0                                                       
      Endpoint Descriptor:                                                            
        bLength                 7                                                     
        bDescriptorType         5                                                     
        bEndpointAddress     0x83  EP 3 IN                                            
        bmAttributes            2                                                     
          Transfer Type            Bulk                                               
          Synch Type               None                                               
          Usage Type               Data                                               
        wMaxPacketSize     0x0040  1x 64 bytes                                        
        bInterval               0                                                     
        ** UNRECOGNIZED:  14 ff 42 49 53 54 00 01 01 01 10 00 00 00 00 00 01 03 02 02 
Device Status:     0x0000                                                             
  (Bus Powered)                                                               
```

Xorg.0.log (wacom / n-trig sections)
```
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 0.10.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0




(**) Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
(**) stylus: always reports core events
(**) Option "Mode" "Absolute"
(**) Option "Touch" "on"
(**) Option "Button1" "1"
(**) Option "Button2" "3"
(**) Option "Button3" "2"
(II) XINPUT: Adding extended input device "stylus" (type: STYLUS)
(--) stylus: using pressure threshold of 15 for button 1
(--) stylus: Wacom Unknown USB tablet speed=38400 maxX=9600 maxY=7200 maxZ=256 resX=1016 resY=1016  tilt=enabled
(--) stylus: top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=1016 resol Y=1016
(**) Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
(**) eraser: always reports core events
(**) Option "Mode" "Absolute"
(**) Option "Button1" "2"
(**) Option "Button9" "0"
(II) XINPUT: Adding extended input device "eraser" (type: ERASER)
(--) eraser: top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=1016 resol Y=1016
(**) Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
(**) touch: always reports core events
(**) Option "Mode" "Absolute"
(**) Option "TopX" "0"
(**) Option "TopY" "0"
(**) Option "BottomX" "9600"
(**) Option "BottomY" "7200"
(**) Option "Touch" "on"
(II) XINPUT: Adding extended input device "touch" (type: TOUCH)
(--) touch: top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=1016 resol Y=1016



(II) config/udev: Adding input device "HID 1b96:0001" (/dev/input/event7)
(**) Option "Device" "/dev/input/event7"
(II) "HID 1b96:0001": type not specified, assuming 'stylus'.
(II) "HID 1b96:0001": other types will be automatically added.
(WW) "HID 1b96:0001": device file already in use by stylus. Ignoring.
(II) UnloadModule: "wacom"
(EE) PreInit returned NULL for ""HID 1b96:0001""
(II) config/udev: Adding input device "HID 1b96:0001" (/dev/input/event8)
(**) Option "Device" "/dev/input/event8"
(II) "HID 1b96:0001": type not specified, assuming 'stylus'.
(II) "HID 1b96:0001": other types will be automatically added.
(**) "HID 1b96:0001": always reports core events
(II) "HID 1b96:0001": hotplugging dependent devices.
(**) Option "Device" "/dev/input/event8"
(**) "HID 1b96:0001" eraser: always reports core events
(II) XINPUT: Adding extended input device ""HID 1b96:0001" eraser" (type: ERASER)
(--) "HID 1b96:0001" eraser: using pressure threshold of 15 for button 1
(--) "HID 1b96:0001" eraser: Wacom Unknown USB tablet speed=38400 maxX=9600 maxY=7200 maxZ=256 resX=1016 resY=1016  tilt=enabled
(--) "HID 1b96:0001" eraser: top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=1016 resol Y=1016
(**) Option "Device" "/dev/input/event8"
(**) "HID 1b96:0001" touch: always reports core events
(II) XINPUT: Adding extended input device ""HID 1b96:0001" touch" (type: TOUCH)
(--) "HID 1b96:0001" touch: top X=0 top Y=0 bottom X=1024 bottom Y=1024 resol X=1016 resol Y=1016
(II) "HID 1b96:0001": hotplugging completed.
(II) XINPUT: Adding extended input device ""HID 1b96:0001"" (type: STYLUS)
(--) "HID 1b96:0001": top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=1016 resol Y=1016

```

---

### Post by Ayuthia on 2010-01-24
As far as I know, there isn't anything out there that has the multitouch working quite right for the N-Trig device in Lucid.  The best to start is with this [link]("http://lii-enac.fr/en/projects/shareit/xorg.html").  It is the closest to getting it to work.  You will need to use the evdev driver.  I have tried it out and had to make modifications to Benjamin's evdev driver.  The hid-ntrig.ko module also needs to be modified to help make it work too because the Wacom driver uses a BTN_TOOL_DOUBLETAP for touch and the evdev driver uses BTN_TOUCH.  There are also some ordering changes that I had to make so that the driver will be able to see the device as a multitouch device.

At this point, I have been able to send the two fingers with the Win 7 firmware, but I have not gotten the two fingers to report at the same time properly.  I am able to use the mouse and finger as two different pointers at the same time though.

I have not had a chance to look at the new Wacom driver that is going to be used in Lucid.

---

### Post by overdrank on 2010-01-24
Moved to Lucid Lynx Testing and Discussion

---

### Post by Ubuntiac on 2010-01-24
> **Ayuthia said:**
> As far as I know, there isn't anything out there that has the multitouch working quite right for the N-Trig device in Lucid.

Funny thing is that a fresh install of Kubuntu Lucid Alpha 2 had touch working as a mouse and single touch out of the box. I updated and... it died.

Right now, I'd settle for single touch, though obviously multitouch working would be awesome! :D

---

