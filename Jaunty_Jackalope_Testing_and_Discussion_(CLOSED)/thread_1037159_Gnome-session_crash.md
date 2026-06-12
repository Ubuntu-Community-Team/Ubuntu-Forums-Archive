---
title: "Gnome-session crash"
date: 2009-01-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by plun on 2009-01-11
Well.. this was a challenge

LXDE works but gnome hangs

From SSH and xsession-errors

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[3497]: WARNING: No required applications specified
GNOME_KEYRING_SOCKET=/tmp/keyring-dUhXHc/socket
SSH_AUTH_SOCK=/tmp/keyring-dUhXHc/ssh
Checking for Xgl: not present.
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
Window manager warning: "(null)" found in configuration database is not a valid value for m$
Window manager warning: Could not parse font description "(null)" from GConf key /apps/meta$
Window manager warning: 0 stored in GConf key /desktop/gnome/peripherals/mouse/cursor_size $
Window manager warning: Failed to read saved session file /home/plun/.config/metacity/sessi$

** (gnome-volume-control-applet:3708): WARNING **: Connection failed
gnome-session[3497]: WARNING: Application 'gnome-volume-control-applet.desktop' failed to r$
Failed to play sound: Not available
gnome-session[3497]: WARNING: Application 'libcanberra-login-sound.desktop' failed to regis$
No value set for `/desktop/gnome/applications/at/visual/exec'


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed a$

Initialising tracker...
starting HAL detection for ac adaptors...none found
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root priviliges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
Throttle level is 0
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in $
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privi$
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate P$

Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed a$

Initialising tracker...
starting HAL detection for ac adaptors...none found
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root priviliges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
Throttle level is 0
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in $
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privi$
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate P$

** (nm-applet:3734): WARNING **: No connections defined
evolution-alarm-notify-Message: Setting timeout for 15829 1231718400 1231702571
evolution-alarm-notify-Message:  Mon Jan 12 01:00:00 2009

evolution-alarm-notify-Message:  Sun Jan 11 20:36:11 2009

/var/crash/python-numpy
update-gconf-defaults



```


/var/crash/python-numpy   :confused:


and my PC still freezes without any dirty drivers...

---

### Post by LordVeovis on 2009-01-11
> **plun said:**
> Well.. this was a challenge

LXDE works but gnome hangs

From SSH and xsession-errors

...

/var/crash/python-numpy   :confused:


and my PC still freezes without any dirty drivers...

How did you get this to happen?  What can I do to try to reproduce?  Or are you not sure why it did this?

---

### Post by plun on 2009-01-11
> **LordVeovis said:**
> How did you get this to happen?  What can I do to try to reproduce?  Or are you not sure why it did this?

Well.. this is a brand new clean install but ubuntu-desktop is so broken so apport blocks and the config brakes because of too many errors

Manage to repair it this time but the login brakes...  I can see it with a remote ssh-login.


Never heard of this package
[http://packages.ubuntu.com/jaunty/python-numpy](http://packages.ubuntu.com/jaunty/python-numpy)

Going to try a reinstall.

---

### Post by autocrosser on 2009-01-11
Ya--sounds real broken---Last one I did was a Intrepid>Jaunty & it went well---that's the one I EXT4'd & am using now.....

Think I'll wait until the next alpha to reinstall on my other install--really want a total clean ETX4 to test with.....

---

### Post by plun on 2009-01-11
Well... I also got the big freeze... no dirty drivers.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/316152](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/316152)


But the MS Sound System maybe...:twisted:


I installed kerneloops directly with this install....

---

### Post by plun on 2009-01-11
Huh....  


> root@plun:/usr/src/linux# make xconfig
  HOSTCXX scripts/kconfig/qconf.o
**g++: Internal error: Segmentation fault (program cc1plus)**
Please submit a full bug report.
See <file:///usr/share/doc/gcc-4.3/README.Bugs> for instructions.
make[1]: *** [scripts/kconfig/qconf.o] Error 1
make: *** [xconfig] Error 2

---

### Post by autocrosser on 2009-01-11
???????????:mad::mad:

Looks like nuke it time.........

---

### Post by plun on 2009-01-11
> **autocrosser said:**
> ???????????:mad::mad:

Looks like nuke it time.........


Well.. maybe more "Houston we have a problem"  ):P  (Apollo ? )

---

### Post by autocrosser on 2009-01-11
(vision of WWI fighter spiraling in on fire.......)

---

### Post by plun on 2009-01-11
> **autocrosser said:**
> (vision of WWI fighter spiraling in on fire.......)

OK....:p  it was Apollo 13 [http://history.nasa.gov/SP-350/ch-13-1.html](http://history.nasa.gov/SP-350/ch-13-1.html)

The da--ed PC frooze again with the MS Sound system disconneted so it must be 1 or more "brown bags"" within the software..:tongue:

Now I for sure used the power button 20 times last week...

Good night...):P

---

### Post by ShirishAg75 on 2009-01-11
plun have subscribed to your bug. Chris has asked you to do couple of things to see if this can be narrowed down. See if you can help.

---

### Post by plun on 2009-01-12
> **ShirishAg75 said:**
> plun have subscribed to your bug. Chris has asked you to do couple of things to see if this can be narrowed down. See if you can help.

Yes... working on it,  Memtest on the run..

---

### Post by plun on 2009-01-14
Well... back in the mess....


- ld crashed

- glibc crasched, gcc errors >  segmentation fault  during a compile

---

### Post by plun on 2009-01-18
Well... took this morning and tested everything and its time for the PC store....:^o


Just crap left....

[[img]http://ubuntu-pics.de/thumb/8507/dsc00079_jSrvY8.jpg[/img]](http://ubuntu-pics.de/bild/8507/dsc00079_jSrvY8.jpg)

:tongue:

---

### Post by ronacc on 2009-01-18
been there done that .:confused:

---

### Post by plun on 2009-01-23
> **ronacc said:**
> been there done that .:confused:

Well... up and running again....:D

The da--ed postal service took time and I was stubborn and wanted an Intel 5200 CPU....  great to overclock...;)

```
plun@plun:~$ sudo dmidecode
# dmidecode 2.9
SMBIOS 2.5 present.
46 structures occupying 1412 bytes.
Table at 0x000F0000.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Phoenix Technologies, LTD
	Version: ASUS P5N73-AM ACPI BIOS Revision 0201
	Release Date: 06/11/2008
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: ASUSTeK Computer INC.
	Product Name: P5N73-AM
	Version: 2.XX    
	Serial Number: MT7087K11405673

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
	Manufacturer: Chassis Manufacture
	Type: Desktop
	Lock: Not Present
	Version: Chassis Version
	Serial Number: EVAL          
	Asset Tag: 123456789000
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000001

Handle 0x0004, DMI type 4, 40 bytes
Processor Information
	Socket Designation: Socket 775
	Type: Central Processor
	Family: Other
	Manufacturer: Intel
	ID: 76 06 01 00 FF FB EB BF
	Version: Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
	Voltage: 1.2 V
	External Clock: 200 MHz
	Max Speed: 3800 MHz
	Current Speed: 2500 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: 0x0007
	Serial Number:  
	Asset Tag:  
	Part Number:  
	Core Count: 2
	Core Enabled: 2
	Thread Count: 2
	Characteristics: None

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 64 KB
	Maximum Size: 64 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Data
	Associativity: 4-way Set-associative

```



And a nVidia chip so I could save money...:cool:, maybe a crappy MB but it was cheap...

Install 64 bit or investigate disks....:D

---

### Post by ronacc on 2009-01-23
glad to see you back ;)

---

### Post by plun on 2009-01-23
> **ronacc said:**
> glad to see you back ;)

Well...the disk was empty....  :^o

```
plun@plun:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00069b60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3648    29302528+  83  Linux
/dev/sda2           19084       19457     3004155   82  Linux swap / Solaris
/dev/sda3           13005       19083    48829567+  83  Linux
/dev/sda4            3649       13004    75152070   83  Linux

Partition table entries are not in disk order

[B]Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000[/B]

```


64bit is up and running also.... and EXT4,  just Magic..:D

Gnome login takes longer then boot...:D

nVidia 180.22 also  :popcorn:

---

