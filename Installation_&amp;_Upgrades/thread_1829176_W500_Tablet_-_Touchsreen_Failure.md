---
title: "W500 Tablet - Touchsreen Failure"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by J_dillinger on 2011-08-20
**Mouse buttons fail on tablet after 2 or 3 clicks.**

I have been attempting to install Ubuntu 10.04, 10.10, 11.04 or Fedora core 16 on an Acer W500 Tablet.  Everything works great with a little tweaking, but the mouse fails after two or three clicks.  The cursor will continue to move, but the buttons stop functioning.  During the installation phase, I have been using a USB keyboard and mouse (IR) which work also, until use the touchscreen.  After several different installation here is the configuration that work the best...


Install the ati Nvidia driver: ati-driver-installer-11-7-x86.x86_64 
I have used several versions of the driver and it is easy to find on google.  The Ubuntu forums documentation will also describe in detail how to make the .bin file into a .deb for installation.

Here is the configuration for the touchscreen.

lsusb
Bus 005 Device 002: ID 0eef:7302 D-WAV Scientific Co., Ltd 

xinput --list

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]

&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]

&#9116;   &#8627; HID 0a5c:4503                           	id=10	[slave  pointer  (2)]

&#9116;   &#8627; Logitech USB Receiver                   	id=11	[slave  pointer  (2)]

&#9116;   &#8627; Logitech USB Receiver                   	id=12	[slave  pointer  (2)]

&#9116;   &#8627; eGalax Inc. USB TouchController         	id=14	[slave  pointer  (2)]

&#9116;   &#8627; Macintosh mouse button emulation        	id=18	[slave  pointer  (2)]

&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]

    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]

    &#8627; Power Button                            	id=6	[slave  keyboard (3)]

    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]

    &#8627; Power Button                            	id=8	[slave  keyboard (3)]

    &#8627; HID 0a5c:4502                           	id=9	[slave  keyboard (3)]

    &#8627; CHICONY USB NetVista Full Width Keyboard	id=13	[slave  keyboard (3)]

    &#8627; 1.3M Rear                               	id=15	[slave  keyboard (3)]

    &#8627; 1.3M Front                              	id=16	[slave  keyboard (3)]

    &#8627; AT Translated Set 2 keyboard            	id=17	[slave  keyboard (3)]


Calibrating EVDEV driver for "eGalax Inc. USB TouchController" id=14

	current calibration values (from XInput): min_x=0, max_x=32767 and min_y=0, max_y=32767



Doing dynamic recalibration:

	Setting new calibration data: -17, 32681, -86, 32708





--> Making the calibration permanent <--

  Install the 'xinput' tool and copy the command(s) below in a script that starts with your X session

    xinput set-int-prop "eGalax Inc. USB TouchController" "Evdev Axis Calibration" 32 -17 32681 -86 32708


**What can I do to keep the mouse buttons from failing?**

---

