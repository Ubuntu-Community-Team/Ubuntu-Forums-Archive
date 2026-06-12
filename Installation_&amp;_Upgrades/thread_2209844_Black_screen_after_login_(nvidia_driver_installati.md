---
title: "Black screen after login (nvidia driver installation)"
date: 2014-03-07
forum: Installation &amp; Upgrades
---

### Post by childintime on 2014-03-07
So I tried to install nvidia driver from Additional drivers, and after installation and reboot I login and my screen goes black with only mouse visible. I read some different solutions, but nothing seems to work!

What I've tried:

```
[Remove Nvidia proprietary drivers]("http://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver")[COLOR=#333333][FONT=UbuntuRegular]:[/FONT][/COLOR]sudo apt-get remove --purge nvidia*
[COLOR=#333333][FONT=UbuntuRegular]Add xorg edgers PPA for NVIDIA drivers and install nvidia-331:[/FONT][/COLOR]
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331
[COLOR=#333333][FONT=UbuntuRegular][Remove/purge bumblebee]("http://askubuntu.com/a/400010/127101") and reboot:[/FONT][/COLOR]
sudo apt-get --purge remove bumblebee [FONT=Ubuntu Mono]sudo reboot[/FONT]
```

I also tried this:

```
[COLOR=#333333][FONT=UbuntuRegular]i solved by installing Bumblebee. add the ppa to my system from the Xorg-Edgers PPA[/FONT][/COLOR]sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
[COLOR=#333333][FONT=UbuntuRegular]check which nvidia driver you already installed run this command dpkg -l | grep -i nvidia and remove it in my case i had nvidia-current .[/FONT][/COLOR]
sudo apt-get remove nvidia-current nvidia-settings
[COLOR=#333333][FONT=UbuntuRegular]then install bumblebee[/FONT][/COLOR]
[FONT=Ubuntu Mono]sudo apt-get install bumblebee-nvidia nvidia-319[/FONT]
```

And both solutions here: [http://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver](http://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver)

Which got many thumbs up, but still everytime I login I get black screen. 

How can I fix this, I am trying to fix this whole day already? My card is nvidia geforce 740M

At this point any driver will be fine for me as long as ubuntu works.

---

### Post by 23dornot23d on 2014-03-08
**This is what worked for mine using optimus and bumblebee (mine is the nvidia gt540m though )**

(ctrl + alt + f1)
stop lightdm
stop gdm
stop kdm

Often as a first check but you can rename the xorg.conf in 

cd **/etc/X11/**

**rn xorg.conf xorg.confold** 

basically moves it out of the way to give you a screen that works ........... 


Then type in **lightdm** or **gdm** or **kdm** all done from the console though

This depending on what display manager you are using and see if the standard drivers installed are working.

to put it back to what it was before rebooting
do the opposite

**rn xorg.confold xorg.conf**



> 
To set up the optimus gt540m + intel i965 ( ubuntu 14.04 testing )
not sure if the files are available for your system - but the option is here if needed for
a successful install for my own system any way .....

First for me - remove nvidia-prime and any old drivers

**sudo apt-get remove --purge nvidia***

so removed all versions of nvidia drivers ..... these can be purged .......

Then made sure to  install these files last by using synaptic package manager or you can do

[B]sudo apt-get install nvidia-331 nvidia-opencl-icd-331-updates
sudo apt-get install nvidia-opencl-icd-331-updates libcuda1-331-updates
sudo apt-get install nvidia-settings

sudo apt-get install bumblebee bumblebee-nvidia primus[/B]

After this rebooted and my system was sorted.

Also can add these ..... 

**sudo apt-get install mesa-utils mesa-utils-extra**

to do the test to see that its working ok once into a graphical desktop ......



**optirun glxgears**

  


The above is just for information as mine was a success ..... but obviously the steps should
be similar in most cases using optimus (intel and nvidia) graphics that save on laptop battery power
by switching to the least consuming graphics card .......

14.04 comes out on the 17 April by the way and is in testing at the moment - but it seems to do a
lot better at making sure people have their graphics working 
[http://ubuntuforums.org/showthread.php?t=2201790&page=2](http://ubuntuforums.org/showthread.php?t=2201790&page=2)
- but obviously release time 17th April
is the time to do the change for people unsure about correcting problems should they arise.

---

### Post by childintime on 2014-03-08
Thank you sir a lot, it worked, appreciated!

But after login, black screen still remains for like 10 seconds (it was never before) and then I get several error messages to report problem and finally desktop appears. So how do I figure out which graphics driver is best for me at this point, or the one you told me is good?


P.S. in your quote it's not openci but opencl in case someone reads..

---

### Post by 23dornot23d on 2014-03-08
Good to know it is working now .......... what are the errors you get back ..........

( also I changed the ci to cl ) in the post incase anyone else should use it .... ty

does this show anything .........

[B]grep -Fn 'NVIDIA' /var/log/Xorg.8.log

also
[/B][B]lspci | grep VGA


[/B]

---

### Post by childintime on 2014-03-08
```
mosquito@mosquito-K56CB:~$ grep -Fn 'NVIDIA' /var/log/Xorg.8.log100:[   288.972] (II) Module glx: vendor="NVIDIA Corporation"
103:[   288.972] (II) NVIDIA GLX Module  331.49  Wed Feb 12 20:17:10 PST 2014
107:[   289.334] (II) Module nvidia: vendor="NVIDIA Corporation"
121:[   289.391] (II) NVIDIA dlloader X Driver  331.49  Wed Feb 12 19:57:36 PST 2014
122:[   289.391] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
141:[   289.546] (II) NVIDIA(0): Creating default Display subsection in Screen section
143:[   289.546] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
144:[   289.546] (==) NVIDIA(0): RGB weight 888
145:[   289.546] (==) NVIDIA(0): Default visual is TrueColor
146:[   289.547] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
147:[   289.547] (**) NVIDIA(0): Option "NoLogo" "true"
148:[   289.547] (**) NVIDIA(0): Option "ProbeAllGpus" "false"
149:[   289.547] (**) NVIDIA(0): Option "UseEDID" "false"
150:[   289.547] (**) NVIDIA(0): Option "UseDisplayDevice" "none"
151:[   289.547] (**) NVIDIA(0): Enabling 2D acceleration
152:[   289.547] (**) NVIDIA(0): Ignoring EDIDs
153:[   289.547] (**) NVIDIA(0): Option "UseDisplayDevice" set to "none"; enabling NoScanout
154:[   289.547] (**) NVIDIA(0):     mode
155:[   291.238] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102)
156:[   291.239] (II) NVIDIA(0): NVIDIA GPU GeForce GT 740M (GK107) at PCI:1:0:0 (GPU-0)
157:[   291.239] (--) NVIDIA(0): Memory: 2097152 kBytes
158:[   291.239] (--) NVIDIA(0): VideoBIOS: 80.07.a0.00.11
159:[   291.239] (II) NVIDIA(0): Detected PCI Express Link width: 16X
160:[   291.239] (--) NVIDIA(0): Valid display device(s) on GeForce GT 740M at PCI:1:0:0
161:[   291.239] (--) NVIDIA(0):     none
162:[   291.239] (II) NVIDIA(0): Validated MetaModes:
163:[   291.239] (II) NVIDIA(0):     "NULL"
164:[   291.239] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
165:[   291.239] (WW) NVIDIA(0): Unable to get display device for DPI computation.
166:[   291.239] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
168:[   291.239] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
169:[   291.240] (II) NVIDIA:     access.
170:[   291.243] (II) NVIDIA(0): Setting mode "NULL"
171:[   291.243] (EE) NVIDIA(0): Failed to initiate mode change.
172:[   291.243] (EE) NVIDIA(0): Failed to complete mode change
174:[   291.280] (==) NVIDIA(0): Disabling shared memory pixmaps
175:[   291.280] (==) NVIDIA(0): Backing store disabled
176:[   291.280] (==) NVIDIA(0): Silken mouse enabled
177:[   291.280] (==) NVIDIA(0): DPMS enabled
182:[   291.281] (II) NVIDIA(0): [DRI2] Setup complete
183:[   291.281] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
254:[   372.074] (II) NVIDIA(GPU-0): Deleting GPU-0

```

```
mosquito@mosquito-K56CB:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)

```

About errors, it's just the message send report or cancel, that's all, several of those.

---

### Post by 23dornot23d on 2014-03-08
Do you just use the laptop by itself or is it connected to other monitors or to a TV through a HDMI cable.

```

149:[   289.547] (**) NVIDIA(0): Option "UseEDID" "false"
150:[   289.547] (**) NVIDIA(0): Option "UseDisplayDevice" "none"
151:[   289.547] (**) NVIDIA(0): Enabling 2D acceleration
152:[   289.547] (**) NVIDIA(0): Ignoring EDIDs
153:[   289.547] (**) NVIDIA(0): Option "UseDisplayDevice" set to "none"; enabling NoScanout
154:[   289.547] (**) NVIDIA(0):     mode

```

seems not to detect the monitor or the laptop screen

```

156:[   291.239] (II) NVIDIA(0): NVIDIA GPU GeForce GT 740M (GK107) at PCI:1:0:0 (GPU-0)
157:[   291.239] (--) NVIDIA(0): Memory: 2097152 kBytes
158:[   291.239] (--) NVIDIA(0): VideoBIOS: 80.07.a0.00.11
159:[   291.239] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[COLOR=#ff0000][B]160:[   291.239] (--) NVIDIA(0): Valid display device(s) on GeForce GT 740M at PCI:1:0:0
161:[   291.239] (--) NVIDIA(0):     none[/B][/COLOR]

```

Will search around unless someone else knows why its not picking up the screen to use
they seem to ignore the EDID but I know if the TV is plugged in at setup time the EDID
results can be odd.

```

171:[   291.243] (EE) NVIDIA(0): Failed to initiate mode change.
172:[   291.243] (EE) NVIDIA(0): Failed to complete mode change
174:[   291.280] (==) NVIDIA(0): Disabling shared memory pixmaps
175:[   291.280] (==) NVIDIA(0): Backing store disabled
176:[   291.280] (==) NVIDIA(0): Silken mouse enabled
[COLOR=#ff0000][B]177:[   291.280] (==) NVIDIA(0): DPMS enabled
182:[   291.281] (II) NVIDIA(0): [DRI2] Setup complete
183:[   291.281] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
254:[   372.074] (II) NVIDIA(GPU-0): Deleting GPU-0[/B][/COLOR]

```

DPMS
[https://wiki.archlinux.org/index.php/Display_Power_Management_Signaling](https://wiki.archlinux.org/index.php/Display_Power_Management_Signaling)

Not fully sure what it means - by setup complete - then it removes the GPU though ........

VDPAU
[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

I got my own working to some extent - but even now I wonder if its in some virtual mode
but optirun works and also compiz ............

Maybe someone else can take you further with this now ...... that understands the output from that
better than I do ....... but it seems to have failed ......... even though it reports setup complete.

---

### Post by childintime on 2014-03-08
It's just a Asus K56C laptop not connected to any other screens.

23dornot23d, thank you sir!

---

### Post by 23dornot23d on 2014-03-08
Your welcome - try playing this video back at full screen and see if there is any tearing or stuttering .........

[http://youtu.be/1ujmDrcKWo8](http://youtu.be/1ujmDrcKWo8) ( was posted in the Ubuntu+1 ) as people are saying how well

[http://youtu.be/6v2L2UGZJAM](http://youtu.be/6v2L2UGZJAM)
the graphics setups are for the new version coming.

Only other things that will push it are 3D like Blender ..... or games ...... but it all depends what you use

the laptop for ..........

---

### Post by childintime on 2014-03-09
> **23dornot23d said:**
> Your welcome - try playing this video back at full screen and see if there is any tearing or stuttering .........

[http://youtu.be/1ujmDrcKWo8](http://youtu.be/1ujmDrcKWo8) ( was posted in the Ubuntu+1 ) as people are saying how well

[http://youtu.be/6v2L2UGZJAM](http://youtu.be/6v2L2UGZJAM)
the graphics setups are for the new version coming.

Only other things that will push it are 3D like Blender ..... or games ...... but it all depends what you use

the laptop for ..........

Both videos run very well  :grin:

---

### Post by 23dornot23d on 2014-03-09
Good to know ........... that surprised me when I clicked the link to find it was the windows 8 one
as a friend is wanting to go from windows XP to 8.1 so I posted her the link ......... it must have
stayed in the clipboard ........ so I never realized at the time the wrong video had been posted.

I do like that second video though and the graphics even hold up well on my old 2 core laptop but
its got a old 9300m gs Nvidia card in it .......... that runs pretty good ..... but there is some small screen
discrepancy at times on it at full screen on the 40 inch TV .......... am quite liking the fact my optimus runs
well now though and can use the compiz and the faster rendering for Blender when I need it using optirun

But am not sure how the whole thing works ......... 

I would have liked Nvidia Prime to work properly - which basically switches over to the Nvidia for everything ........
from what I have read so far ......... then you just switch it back out of performance mode .........

But mine comes back with this error when I try to implement that .......... which is very vague ........

[IMG]http://i.minus.com/ibal849Yt5s6LU.jpg[/IMG]

Well with all these things as time goes on they all eventually iron out ..... but so far I have everything I need
on my system - hope you also are having a better experience with it all now ..........

---

### Post by childintime on 2014-03-13
The problem I am now facing is that since I deleted and recreated xorg.conf file, my mouse is working very bad, it's often clicking 2 times instead of 1 or releasing the pointed when I am holding. I tried several configurations which I found on internet but it's still the same. I am pretty sure it's due to xorg.conf because before this mouse worked good.

---

### Post by 23dornot23d on 2014-03-13
Have you tried using a different mouse .......... as sometimes the tiny switch in the mouse does wear out ...... not saying that 
this is your problem - but by either trying your mouse out on another computer or by adding a fresh one that you know works
alright will probably confirm its that drivers rather than the mouse that is at fault.

I have no problems with my mouse by the way using a similar setup ( but I have had mice stop clicking properly )

Just a thought and usually easy enough to do a quick check to confirm things ......... as mice can wear out over time

I have had 3 up to now and a few keyboards too ............ but they do get a fair amount of use.

---

### Post by childintime on 2014-03-13
Well I don't have extra mouse to try now, but considering that it started happening right after I deleted xorg.conf I am 99% sure that's the reason. Do you have any entries for your mouse in xorg.conf?

---

### Post by 23dornot23d on 2014-03-13
Just this in my xorg.conf for mouse ......... but its a Labtec I use and connected via usb ........ 3 button with a scroll wheel 


```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

```

```

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection



```

---

### Post by childintime on 2014-03-13
Hmm I've done the same but mouse is still not working correctly.

---

### Post by 23dornot23d on 2014-03-13
What do the following commands show now ..........

```


[B]sudo dmesg | grep -i mouse

sudo dmesg | grep -i usb
[/B]

```

---

### Post by childintime on 2014-03-13
```
mosquito@mosquito-K56CB:~$ sudo dmesg | grep -i mouse[sudo] password for mosquito: 
[    1.372597] mousedev: PS/2 mouse device common for all mice
[    2.364803] hid-generic 0003:22D4:2100.0003: input,hiddev0,hidraw2: USB HID v1.11 Mouse [Laview Co. Spawn_108a] on usb-0000:00:14.0-3/input0
[   21.578278] psmouse serio4: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[   22.067763] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   22.080435] psmouse serio4: elantech: Synaptics capabilities query result 0x10, 0x14, 0x0e.

```

```
mosquito@mosquito-K56CB:~$ sudo dmesg | grep -i usb
[    0.760396] ACPI: bus type USB registered
[    0.760417] usbcore: registered new interface driver usbfs
[    0.760427] usbcore: registered new interface driver hub
[    0.760463] usbcore: registered new device driver usb
[    1.322844] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.322995] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.336714] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.336745] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.336750] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.336753] usb usb1: Product: EHCI Host Controller
[    1.336759] usb usb1: Manufacturer: Linux 3.11.0-18-generic ehci_hcd
[    1.336763] usb usb1: SerialNumber: 0000:00:1a.0
[    1.337068] hub 1-0:1.0: USB hub found
[    1.337280] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.352709] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.352735] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.352739] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.352743] usb usb2: Product: EHCI Host Controller
[    1.352747] usb usb2: Manufacturer: Linux 3.11.0-18-generic ehci_hcd
[    1.352749] usb usb2: SerialNumber: 0000:00:1d.0
[    1.353039] hub 2-0:1.0: USB hub found
[    1.353129] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.353147] uhci_hcd: USB Universal Host Controller Interface driver
[    1.353313] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.353489] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.353491] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.353493] usb usb3: Product: xHCI Host Controller
[    1.353495] usb usb3: Manufacturer: Linux 3.11.0-18-generic xhci_hcd
[    1.353497] usb usb3: SerialNumber: 0000:00:14.0
[    1.353599] hub 3-0:1.0: USB hub found
[    1.353696] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.353717] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.353720] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.353722] usb usb4: Product: xHCI Host Controller
[    1.353724] usb usb4: Manufacturer: Linux 3.11.0-18-generic xhci_hcd
[    1.353725] usb usb4: SerialNumber: 0000:00:14.0
[    1.353822] hub 4-0:1.0: USB hub found
[    1.648625] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.785036] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.785060] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.785293] hub 1-1:1.0: USB hub found
[    1.896615] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.028966] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    2.028970] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.029318] hub 2-1:1.0: USB hub found
[    2.196476] usb 3-1: new low-speed USB device number 2 using xhci_hcd
[    2.231707] usb 3-1: New USB device found, idVendor=04d9, idProduct=2011
[    2.231716] usb 3-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    2.231721] usb 3-1: Product: USB Keyboard
[    2.231867] usb 3-1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.231871] usb 3-1: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.270138] usbcore: registered new interface driver usbhid
[    2.270140] usbhid: USB HID core driver
[    2.272088] input: USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input4
[    2.272176] hid-generic 0003:04D9:2011.0001: input,hidraw0: USB HID v1.10 Keyboard [USB Keyboard] on usb-0000:00:14.0-1/input0
[    2.272296] input: USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/input/input5
[    2.272414] hid-generic 0003:04D9:2011.0002: input,hidraw1: USB HID v1.10 Device [USB Keyboard] on usb-0000:00:14.0-1/input1
[    2.344450] usb 3-3: new full-speed USB device number 3 using xhci_hcd
[    2.362947] usb 3-3: New USB device found, idVendor=22d4, idProduct=2100
[    2.362950] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.362952] usb 3-3: Product: Spawn_108a
[    2.362953] usb 3-3: Manufacturer: Laview Co.
[    2.364634] input: Laview Co. Spawn_108a as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input6
[    2.364803] hid-generic 0003:22D4:2100.0003: input,hiddev0,hidraw2: USB HID v1.11 Mouse [Laview Co. Spawn_108a] on usb-0000:00:14.0-3/input0
[    2.365707] input: Laview Co. Spawn_108a as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.1/input/input7
[    2.365796] hid-generic 0003:22D4:2100.0004: input,hidraw3: USB HID v1.11 Keyboard [Laview Co. Spawn_108a] on usb-0000:00:14.0-3/input1
[    2.436508] usb 1-1.1: new full-speed USB device number 3 using ehci-pci
[    2.530364] usb 1-1.1: New USB device found, idVendor=13d3, idProduct=3362
[    2.530373] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.530379] usb 1-1.1: Product: Bluetooth USB Host Controller
[    2.530383] usb 1-1.1: Manufacturer: Atheros Communications
[    2.530387] usb 1-1.1: SerialNumber: Alaska Day 2006
[    2.600328] usb 1-1.2: new high-speed USB device number 4 using ehci-pci
[    2.794262] usb 1-1.2: New USB device found, idVendor=13d3, idProduct=5165
[    2.794265] usb 1-1.2: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    2.794266] usb 1-1.2: Product: USB Camera
[    2.794268] usb 1-1.2: Manufacturer: Azurewave
[    2.794269] usb 1-1.2: SerialNumber: NULL
[   22.288035] usbcore: registered new interface driver btusb
[   22.643021] usbcore: registered new interface driver ath3k
[   22.825258] usb 1-1.1: USB disconnect, device number 3
[   22.827154] uvcvideo: Found UVC 1.00 device USB Camera (13d3:5165)
[   22.838220] input: USB Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input11
[   22.838308] usbcore: registered new interface driver uvcvideo
[   22.838308] USB Video Class driver (1.1.1)
[   23.025963] usb 1-1.1: new full-speed USB device number 5 using ehci-pci
[   28.118675] usb 1-1.1: New USB device found, idVendor=13d3, idProduct=3362
[   28.118685] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   28.118691] usb 1-1.1: Product: Bluetooth USB Host Controller
[   28.118696] usb 1-1.1: Manufacturer: Atheros Communications
[   28.118700] usb 1-1.1: SerialNumber: Alaska Day 2006



```

---

### Post by 23dornot23d on 2014-03-13
Not sure what is going on here but the keyboard seems to get assigned twice at first  .... to input 0 and input 1

Then later on it seems to be ok .........

> 
input: USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input4
[    2.272176] [COLOR=#ff0000]**hid-generic 0003:04D9:2011.0001: input,hidraw0: USB HID v1.10 Keyboard [USB Keyboard] on usb-0000:00:14.0-1/input0**[/COLOR]
[    2.272296] input: USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/input/input5
[    2.272414] hid-generic 0003:04D9:2011.0002: input,hidraw1: USB HID v1.10 Device [COLOR=#ff0000]**[USB Keyboard] on usb-0000:00:14.0-1/input1**[/COLOR]
[    2.344450] usb 3-3: new full-speed USB device number 3 using xhci_hcd
[    2.362947] usb 3-3: New USB device found, idVendor=22d4, idProduct=2100
[    2.362950] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.362952] usb 3-3: Product: Spawn_108a
[    2.362953] usb 3-3: Manufacturer: Laview Co.
[    2.364634] input: Laview Co. Spawn_108a as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input6
[    2.364803] hid-generic 0003:22D4:2100.0003: [COLOR=#ff0000]**input,hiddev0,hidraw2: USB HID v1.11 Mouse [Laview Co. Spawn_108a] on usb-0000:00:14.0-3/input0**[/COLOR]
[    2.365707] input: Laview Co. Spawn_108a as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.1/input/input7
[    2.365796] hid-generic 0003:22D4:2100.0004: input,hidraw3: USB HID v1.11 [COLOR=#ff0000]**Keyboard [Laview Co. Spawn_108a] on usb-0000:00:14.0-3/input1**[/COLOR]



Not something I have had problems with though - and before messing about with settings - the easy options are always the first
to try out at least ........ check that the hardware is ok before changing anything .

Might just be a coincidence ... or it might be as you think - something is conflicting somewhere ......

The only real thing I know about how these things operate is that they are constantly sending signals back and forth
to see if anything has changed ...... these are controlled by something called interrupts 

[http://en.wikipedia.org/wiki/Interrupt_request](http://en.wikipedia.org/wiki/Interrupt_request)

If for instance 2 devices were using the same interrupt and confusing each other - then things could go wrong.

But how you track that down may be more difficult than plugging in another mouse to see if that sorts the problem or not.

I have had odd problems at boot up where the keyboard is not detected - and unplugging the mouse at boot as
freed the the option for the keyboard to work ......... doing a process of elimination to start with can sometimes
be more beneficial than starting to change settings - when there may be another problem.

But that is all I can say on this as its taking me to problems I have never usually encountered once into the OS.

Looking for conflicts is where I would start though .... and as I say sometimes its down to the interrupt settings
and assignments ......... and other times its down to how things are configured ..... 

I had some problems when I added a Gpen .... which is another device for pointing selecting and drawing .... this led me
to all sorts of hidden configuration files - which although were interesting - soon get very complicated in how the system works
things out .......... ( if it was me - as I say - try another mouse first ) or you can start down a long and winding road of
discovery as to how the system sets the mouse up ...........

Am out of my depth on this - so just hope that the little bit of recon we just did points someone else towards seeing
if there is something obvious going on with the set up of the mouse and keyboard.


Also just did a quick search on the touchpad not known  .......

```

psmouse serio4: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64

```

 [https://www.google.co.uk/search?client=ubuntu&channel=fs&q=psmouse+serio4:+alps:+Unknown+ALPS+touchpad:+E7%3D10+00+64,+EC%3D10+00+64+](https://www.google.co.uk/search?client=ubuntu&channel=fs&q=psmouse+serio4:+alps:+Unknown+ALPS+touchpad:+E7%3D10+00+64,+EC%3D10+00+64+)[+++22.067763]+psmouse+serio4:+elantech:+assuming+hardware+version+4&ie=utf-8&oe=utf-8&gfe_rd=cr&q=psmouse+ALPS+touchpad++psmouse+serio4%3A+elantech%3A+assuming+hardware+version+4

---

### Post by childintime on 2014-03-13
Thanks man, now I got some errors so decided to reinstall nvidia driver, and now again I get black screen in Ubuntu and cannot do anything.... It just blows my mind how complicated some things are on linux, that in whole week I cannot fix simple thing.

I tried again all your steps just like first time when it worked but now neither of those commands work:

[B]sudo apt-get install nvidia-331 nvidia-opencl-icd-331-updates
[/B][B]sudo apt-get install nvidia-opencl-icd-331-updates libcuda1-331-updates

[/B]It says those packages not found..

I can't imagine that there is no simple way to reinstall those drivers, I tried literally every solution posted on askubuntu and nothing worked.

Why those drivers do not work, why do I get the black screen everytime? :|

---

### Post by 23dornot23d on 2014-03-13
See post 2 ........ but this routiine does work as I have tried it more than once ........

purge the old nvidia drivers ........ first step .......

Install the new nvidia drivers  ........ second step ........

Install *(bumblebee bumblebee-nvidia primus) use the synaptic package manager but
do this last before rebooting ........ [B]bumblebee bumblebee-nvidia primus

Reboot .........

[/B]Hopefully you have graphics ....... if not try to remove the xorg.conf [B]

By stopping lightdm or kdm or gdm etc ........

[/B]then if need be remove the xorg.conf
****```
rm /etc/X11/xorg.conf

```start kdm or lightdm or gdm```


type in which ever display manager name it is that you use .......[B]

lightdm
[/B]

```****
and see if it anything works ........

---

### Post by childintime on 2014-03-13
Well as I said for some reason 

[B]sudo apt-get install nvidia-331 nvidia-opencl-icd-331-updates
sudo apt-get install nvidia-opencl-icd-331-updates libcuda1-331-updates
[/B]

It says cannot find package or something like this.

---

### Post by 23dornot23d on 2014-03-13
Can you go into synaptic and do a search - for them ........

I checked the repositories and they are still there ....... unless you have somehow disabled
the repository or changed your sources somehow - they should still be there.

[IMG]http://i.minus.com/ibbRYaCNlcElE2.jpg[/IMG]

I have just upgraded this version as it was out of date ...... and all went as expected using that routine above

But I am on 14.04 ..... and you are probably on 13.10 ....... so it maybe something to do with that - the new
release is not too far away now though.

[IMG]http://i.minus.com/ibhseSBhA36wIl.png[/IMG]

---

### Post by childintime on 2014-03-13
Well I don't have GUI, all I can use is command line and I tried your commands, but it says package cannot be located. I also tried another solution by completely removing nvidia files and downloading driver from site and manually installing, but still the same :(

---

### Post by 23dornot23d on 2014-03-14
```

I tried your commands, but it says package cannot be located

```

We had a graphic display working .........

We also could load in the graphics drivers - as we have done that once already to get it working.

The only thing that seemed to be not working properly was the mouse ........

__________________________________________________________________________

I am at a loss as to understand how we now have no graphics and no access to the files we used previously.

> 
 I also tried another solution by completely removing nvidia files and  downloading driver from site and manually installing, but still the same


Is there a thread I should be following that will lead me to know how you loaded in the new Nvidia Drivers manually - 
(that do not work) ....... 

_________________________________________________________________________________

But the main thing that concerns me - is why we cannot load in the drivers we previously had working.

Options ..... 

1 ...... If you boot from a live cd or dvd can you get to look at the /etc/apt/sources.list on the main drive and then post
back what is in it ..........

If for any reason there is something wrong with the (sources.list) 

( but the only things we did since the mouse was playing up was to look at the logs [COLOR=#ff0000][/COLOR]........... )
[http://en.wikipedia.org/wiki/Dmesg](http://en.wikipedia.org/wiki/Dmesg)

 Then you said you had errors and then back to a black screen - none of which could be caused by checking information out.

---

### Post by childintime on 2014-03-14
Thanks man for your support. Well I've run some commands about installing nvidia drivers without your knowledge so maybe that's what made it not work, I don't know but I am pretty sure I enter command correctly.

Either way, I tried to just remove all nvidia drivers and boot on nouveau driver and it worked ^^ I still get somehow long black waiting screen after login, like 15 seconds, several error messages, but at least it works. I think I am going to stay on this until 14.04 comes and upgrade to it.

You asked which guide I use to manually install downloaded driver: [http://askubuntu.com/questions/399153/after-apt-get-upgrade-system-always-boot-to-low-graphics-mode](http://askubuntu.com/questions/399153/after-apt-get-upgrade-system-always-boot-to-low-graphics-mode)
Apparently for others it worked, but not for me.

P.S. mouse again working good.

---

### Post by 23dornot23d on 2014-03-14
Cheers for that link - its interesting what they are saying about bumblebee ........ and the config file .......... 

Check this file as it shows what is loading and gives more information for what is being set up
/var/log/gpu-manager.log

---

### Post by childintime on 2014-03-15
Well I don't even have this file in /var/log/

---

### Post by 23dornot23d on 2014-03-15
Probably only exists in 14.04 then .......... but its giving more information as to what is detected and what is not detected ...........

So maybe the developers are having a good look at solving the problem now with Nvidia and Intel graphics working together.

No doubt they have their work cut out if Nvidia were to give 100 % support for Linux - then no doubt the drivers would be good .

( and maybe if they did that their sales would go up and optimus computer sales would go up too )

At the moment any linux user reading about optimus should steer well clear and try to buy computers that have
one dedicated graphics card in the machine - IMHO ....

Its ok having a computer that can sit in basic graphics mode all the time - but what is the point in paying extra to
have a better graphics card sat in the machine doing nothing at all other than taking up space ........... ;(

```

log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
Error: can't access /etc/force-laptop
Is laptop? yes
grep dmesg status 256
dmesg status 256 == 0? No
grep dmesg status 256
dmesg status 256 == 0? No
Is nvidia loaded? no
Was nvidia unloaded? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is intel loaded? yes
Is radeon loaded? no
Is nouveau loaded? no
Vendor/Device Id: 8086:116
BusID "PCI:0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:df4
BusID "PCI:1:0:0"
Is boot vga? no
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Is nvidia enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is nvidia available? yes
Is fglrx available? no
Is mesa available? yes
Is pxpress available? no
Is prime available? yes
Intel IGP detected
Desktop system detected
or laptop with open drivers
Discrete NVIDIA card detected
Driver not enabled or not in use
Nothing to do

```

---

### Post by jacobpaul76-q on 2014-05-30
> **23dornot23d said:**
> **This is what worked for mine using optimus and bumblebee (mine is the nvidia gt540m though )**

(ctrl + alt + f1)
stop lightdm
stop gdm
stop kdm

Often as a first check but you can rename the xorg.conf in 

cd **/etc/X11/**

**rn xorg.conf xorg.confold** 

basically moves it out of the way to give you a screen that works ........... 


Then type in **lightdm** or **gdm** or **kdm** all done from the console though

This depending on what display manager you are using and see if the standard drivers installed are working.

to put it back to what it was before rebooting
do the opposite

**rn xorg.confold xorg.conf**





The above is just for information as mine was a success ..... but obviously the steps should
be similar in most cases using optimus (intel and nvidia) graphics that save on laptop battery power
by switching to the least consuming graphics card .......

14.04 comes out on the 17 April by the way and is in testing at the moment - but it seems to do a
lot better at making sure people have their graphics working 
[http://ubuntuforums.org/showthread.php?t=2201790&page=2](http://ubuntuforums.org/showthread.php?t=2201790&page=2)
- but obviously release time 17th April
is the time to do the change for people unsure about correcting problems should they arise.

Okay, it's working.... But, it doesn't fill the whole screen

---

