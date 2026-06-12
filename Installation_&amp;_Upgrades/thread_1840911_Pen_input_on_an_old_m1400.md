---
title: "Pen input on an old m1400"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by pgcudahy on 2011-09-08
Hey, I've been having trouble trying to get the pen recognized on my fresh install of 11.04 on an old motion computing m1400.  There are a few old support threads that talk about using the wacom-tools package which doesn't seem to be in the distro anymore and directly editing xorg.conf which seems seems to not even exist anymore. Anyone have any luck getting the pen input to work on one of these old tablet PCs?
Patrick

---

### Post by Favux on 2011-09-08
Hi Patrick,

Natty has made some changes to the serial stack which confuses things some but it should be working out of the box.  Check that xf86-input-wacom is installed -  Ubuntu package xserver-xorg-input-wacom.

Let's try to find out what serial port it is on:
```
dmesg | grep ttyS
or
sudo dmesg | grep ttyS
```
Also what is the output of?
```
xinput list
```

---

### Post by pgcudahy on 2011-09-08
```
patrick@DisplayBox:~$ dmesg | grep ttyS
[    0.136090] 00:11: ttyS4 at I/O 0x238 (irq = 4) is a 16550A
patrick@DisplayBox:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Mouse                      	id=6	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; DELL DELL USB Keyboard                  	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=8	[slave  keyboard (3)]

```

---

### Post by Favux on 2011-09-08
Alright it isn't showing up in *xinput list* and that's why it isn't working  It appears to be on the ttyS4 port.  Let's confirm that.  What is the output of?
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS4)
```
We're looking for an ID that says WACf*.

---

### Post by pgcudahy on 2011-09-09
Don't see WACf...

```
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pnp0/00:11/tty/ttyS4':
    KERNEL=="ttyS4"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pnp0/00:11':
    KERNELS=="00:11"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"
    ATTRS{id}=="PNP0501"

  looking at parent device '/devices/pnp0':
    KERNELS=="pnp0"
    SUBSYSTEMS==""
    DRIVERS==""

```

---

### Post by pgcudahy on 2011-09-09
This seems like it's going to take a bunch of work. I've seen reports of the m1400 working out of the box with 10.04 so I'm going to try that first. Thanks for your help.

---

### Post by pgcudahy on 2011-09-09
Well can't even get the 10.04 disk to boot so maybe I am stuck trying to figure out 11.04

---

### Post by Favux on 2011-09-09
Ouch.

Well:
>  ATTRS{id}=="PNP0501"

has me confused.  "PNP0501" is associated with legacy Wacom serial graphics tablets not tablet PCs which are serial ISDV4 and should have a WACf* product ID.  Since starting with Lucid (10.04) and the change to the xf86-input-wacom X driver only the ISDV4 serial tablets (i.e. tablet PCs) are supported.  Which I suppose could explain why it isn't working.

I'm just not sure I believe it.  There are non-ISDV4 tablet PCs/slates?  I have to look at that a little bit more.  Can you post your Xorg.0.log in /var/log?  You can compress it with right click Create Archive and attach it with Manage Attachments below.

If that is really true we may be able to get it working with one of the new wacom_serial.ko's.  It would be a protocol 4 I suppose.  In which case you are in luck:  [http://ubuntuforums.org/showthread.php?t=1780154](http://ubuntuforums.org/showthread.php?t=1780154)

---

### Post by pgcudahy on 2011-09-09
Thanks for your amazing help

---

### Post by Favux on 2011-09-09
No sign of the Wacom digitizer in the Xorg.0.log.  You have the Wacom X driver xf86-input-wacom installed correct?  Ubuntu calls the package xserver-xorg-input-wacom.  If Synaptic Package Manager says it is not installed install it.

Confusion continues.  I can't find anything where a WACf* for the Motion 1400 is actually identified.  No .fdi or .conf file with it for a match.  But what I do see is in the xorg.conf file:
```
Option "ForceDevice" "ISDV4"
```
But then why aren't we seeing WACf?  Are we on the wrong port?  Seeing "PNP0501" sort of argues against that.  Confusion.

Try:
```

setserial -g /dev/ttyS4
or
sudo setserial -g /dev/ttyS4
```
There were just 4 serial ports available, ttyS0 to ttyS3.  Now with Natty there are like 32:
```
ls /dev/ttyS*
```
And devices that always used to be on ttyS0 (like the Motion 1400's Wacom digitizer) now seem to be on ttyS4.  I'm not real excited about checking the others since S4 seems most likely.

Could it just be as easy as adding "PNP0501" to the serial snippet in 50-wacom.conf?

---

### Post by Favux on 2011-09-09
Heck you might as well try that too.

In /usr/share/X11/xorg.conf.d the 50-wacom.conf should look something like:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
#	Option "ForceDevice" "ISDV4"  # deprecated starting with
#        xf86-input-wacom-0.10.8
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection
```
Try changing the second serial snippet from:
```
Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection
```
to
```
Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "PNP0501|WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection
```
using:
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf
```
Cross your fingers and reboot.

---

### Post by pgcudahy on 2011-09-09
Sorry no luck with that.
Patrick

---

### Post by pgcudahy on 2011-09-09
For what it's worth:
$ setserial -g /dev/ttyS4
/dev/ttyS4, UART: 16550A, Port: 0x0238, IRQ: 4

---

### Post by Favux on 2011-09-09
No, why would it be easy?  :)

Well post the outputs of those setserial commands if there are any.


You have a stylus, eraser, and two side buttons on the stylus, correct?

---

### Post by Favux on 2011-09-09
Alright.  The dmesg and setserial are in agreement.  So if it is on S4 there doesn't appear to be a problem with S4.

So let's try a xorg.conf.  I'll post one tomorrow.

---

### Post by pgcudahy on 2011-09-09
Thanks again. I also tried installing and patching inputattach but that doesn't seem to work either...

---

### Post by Favux on 2011-09-09
Sure.
> I also tried installing and patching inputattach but that doesn't seem to work either... 
Well that argues it is ISDV4.  I'd feel better if we saw an ISDV4 product ID though.  Good you checked that out.

OK, this assumes your xorg.conf is empty.  If instead there is something in it, probably to do with your Intel integrated video chipset, please post it.  You'll still add the Wacom sections but we'll need to change the "ServerLayout":
```
Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  Option "Device" "/dev/ttyS4"
  Option "Type" "stylus"
  Option "Button2" "3"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  Option "Device" "/dev/ttyS4"
  Option "Type" "eraser"
EndSection

Section "ServerLayout"
  Identifier "X.org Configured"
  InputDevice "stylus"
  InputDevice "eraser"
EndSection
```
Before you change anything if you have an xorg.conf first back it up.  Backing up and restoring xorg.conf from the command line is discussed in Old serial tablet driver part II. on "HOW TO Set Up a Wacom Serial Tablet".

Use:
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by pgcudahy on 2011-09-27
Hey, I was super busy at work and didn't get to try your xorg.conf until now but it worked like a charm. Thanks so much for your patience and detailed help.

---

