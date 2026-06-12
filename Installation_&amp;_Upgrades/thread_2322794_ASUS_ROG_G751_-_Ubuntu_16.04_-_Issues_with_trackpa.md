---
title: "ASUS ROG G751 - Ubuntu 16.04 - Issues with trackpad"
date: 2016-04-30
forum: Installation &amp; Upgrades
---

### Post by jvilla1983 on 2016-04-30
Hi all!

I have an ASUS ROG G751 that most functionality worked with the trackpad on 15.10. Upon upgrading to 16.04, I'm having some issues.. 

Here's the issue: 

The trackpad works, but the mouse buttons do not, this is unless I touch and hold the trackpad then click. Which when doing this, only the left click works and not the right. Tapping twice on the trackpad does allow me to double click, but is rather annoying to do. 

Are there any ideas? Were there any significant changes with the drivers? 

Thanks!

---

### Post by jvilla1983 on 2016-04-30
Another, very weird thing I discovered. if I multitouch two fingers on the trackpad, then left click I'm able to get the functionality of the right click. lol.. Very weird.

---

### Post by jvilla1983 on 2016-04-30
Here is my output from xinput.. 

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Sunrex/JME Ghost Key Elimiantion Keyboard	id=10	[slave  pointer  (2)]
&#9116;   &#8627; ASUS Tech Inc. ASUS HID Device          	id=12	[slave  pointer  (2)]
&#9116;   &#8627; ASUS Tech Inc. ASUS HID Device          	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Elan Touchpad                           	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sunrex/JME Ghost Key Elimiantion Keyboard	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                    	id=11	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=15	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=16	[slave  keyboard (3)]

---

