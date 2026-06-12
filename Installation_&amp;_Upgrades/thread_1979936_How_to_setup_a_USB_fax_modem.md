---
title: "How to setup a USB fax modem?"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2012-05-14
How to setup a USB fax modem?

---

### Post by lkraemer on 2012-05-15
**DETECT THE DEVICE - USB:**
Open a Linux Terminal window and copy/paste the following commands with the USB to Serial Adapter unplugged
from a USB port.
```

dmesg | tail
lsusb

```
My Results were:
> 
larry@ubuntu:~$ dmesg | tail
[10797.964432] domain 0: span 03
[10797.964434] groups: 01 02
[10797.964436] domain 1: span 03
[10797.964438] groups: 03
[10797.964440] CPU1 attaching sched-domain:
[10797.964441] domain 0: span 03
[10797.964443] groups: 02 01
[10797.964446] domain 1: span 03
[10797.964447] groups: 03
[12071.044928] usb 6-1: USB disconnect, address 3

larry@ubuntu:~$ lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Then plug in the USB-Serial Port adapter to one of your USB ports. (REMEMBER to ALWAYS use this same port when
using your USB Device) Wait for about 15 seconds, then cut and paste the following command in your Linux Terminal Window:
```

dmesg | tail
lsusb

```
My results were:
> 
larry@ubuntu:~$ dmesg | tail
[10797.964440] CPU1 attaching sched-domain:
[10797.964441] domain 0: span 03
[10797.964443] groups: 02 01
[10797.964446] domain 1: span 03
[10797.964447] groups: 03
[12071.044928] usb 6-1: USB disconnect, address 3
[12091.200574] usb 6-1: new full speed USB device using uhci_hcd and address 4
[12091.358706] usb 6-1: configuration #1 chosen from 1 choice
[12091.363887] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: This device cannot do calls on its own. It is no modem.
[12091.363914] cdc_acm 6-1:1.0: ttyACM0: USB ACM device

My device is /dev/ttyACM0

larry@ubuntu:~$ lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 003: ID 058f:9720 Alcor Micro Corp. USB-Serial Adapter
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Now, copy/paste your information with the following command in your Linux Terminal Window:
```

lsusb -v -d 058f:9720

```
My results were:
> 
Bus 006 Device 003: ID 058f:9720 Alcor Micro Corp. USB-Serial Adapter
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 1.10
bDeviceClass 2 Communications
bDeviceSubClass 0
bDeviceProtocol 0
bMaxPacketSize0 8
idVendor 0x058f Alcor Micro Corp.
idProduct 0x9720 USB-Serial Adapter
bcdDevice 0.00


**DOWNLOAD:**
Install wdvial so you can use it to locate the Modem.  You will have
to configure wvdial.  Those details are later in this posting......

**DIALOUT GROUP:**
You need to be a member of "dialout".  You can use this command in a Terminal Window to see
if you are already a member.
```

groups

```
My results were:
> 
larry@debian:~$ groups
larry dialout cdrom floppy sudo audio dip video plugdev netdev bluetooth scanner vboxusers
larry@debian:~$

I can add my loginname with:
```

useradd &#8211;G dialout loginname

```

**LINKING the COMM PORT: SYMBOLIC vs HARD:**

**DEPENDING ON WHAT YOUR USB DEVICE IS DETECTED AS-----THIS SECTION MAY NOT BE NEEDED!**
You may want to skip this and see if pon & wvdial detect the Modem..........................
To locate the possible COMM PORTS in Ubuntu, copy and paste the following commands with the USB to RS-232C Adapter plugged in.:
```

ls -l /dev/ttyS*
ls -l /dev/ttyU*

```
Notice that ttyS0 through ttyS3 are detected as shown. You may have /dev/ttyUSB0 if it was properly detected.
Mine was NOT, because it was a Sabrent SBT-USC1M USB to Serial Converter..
```

crw-rw---- 1 root dialout 4, 64 2009-11-27 15:26 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-11-27 15:26 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-11-27 15:26 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-11-27 15:26 /dev/ttyS3

```
I couldn't make a symbolic link work, so I decided to create a hard link, replacing /dev/ttyS3.
First remove /dev/ttyS3.
```

sudo rm /dev/ttyS3
sudo ln /dev/ttyACM0 /dev/ttyS3

```
Running the command again:
```

ls -l /dev/ttyS*

```
gives:
```

crw-rw---- 1 root dialout 4, 64 2010-11-10 11:59 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2010-11-10 11:59 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2010-11-10 11:59 /dev/ttyS2
crw-rw---- 2 root dialout 166, 0 2010-11-10 12:59 /dev/ttyS3

```
If you don't have rw priviledges remove /dev/ttyS3 and create it again.

You can determine the Baud rate of the Port:
```

stty -F /dev/ttyS3 -a

```
and to change it to 9600:
```

stty -F /dev/ttyS3 9600
stty -F /dev/ttyS3 -a

```
If you connect to a modem for testing you can transmit out an "ATZ" causing the Modem to flash the lights and reset with:
```

echo ATZ > /dev/ttyS3

```
Which proves characters routed to /dev/ttyS3 get sent to /dev/ttyACM0, the USB to Serial Converter.


**SETUP of PAP/CHAP-SECRETS File:**
You will need to set up the pap-secrets and/or chap-secrets file by running the following in the Terminal Window:
```

sudo pppconfig

```
You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically you just answer the questions
that are presented. You can delete a configurations and start over if
you need to from the menu selections.

For more information try:
```

man pppd
man pppconfig

```
The pap-secrets at /etc/ppp/pap-secrets file contains:
(NOTE: File Format for 10.04)
```

# Every regular user can use PPP and has to use passwords from /etc/passwd
*       hostname        ""      *

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest   hostname        "*"     -
master  hostname        "*"     -
root    hostname        "*"     -
support hostname        "*"     -
stats   hostname        "*"     -

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.
#       *       password
"yourusername@yourisp.net" provider "yourpassword"

```
ASSUME:
your loging name is GeraldJones
your password is MyPassWord

Your last section of the pap-secrets file should be:
```

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password
"GeraldJones" provider "MyPassWord"

```

If you named provider something different, then just substitute that for the provider in pon and poff.
Let's assume showmenet

Original ISP named provider
To connect use the first command. To Disconnect use the second command.
```

pon provider
poff provider

```
Modified ISP named showmenet
```

pon showmenet
poff showmenet

```
This should get you connected. You then need to open your Browser, and make sure OFFLINE is not checked.
It is in the Top Left selection under FILE:

You should be able to browse, and surf. Now disconnect and setup wvdial.


When pppconfig is setup, try running wvdialconf to detect the Modem.
```

sudo wvdialconf /etc/wvdial.conf

```
You should get a configuration file like this at /etc/wvdial.conf (you may need to add/change a few things...)

wvdial.conf contains:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
; /dev/??? may be different
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```
Now go back and try wvdial. It should now work.
Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```
You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
REMEMBER after wvdial dials, you can pick up a handset and monitor the
activity by listening to what is going on with the communications.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny characters)
and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN...) You may have to uncheck the box
marked OFFLINE when you open your browser to make it online. Surf,
then terminate the open session with CNTL C in the open terminal window
where you initiated wvdial.

Now that it works set up Gnome-PPP. From now on, you can just click on Gnome-PPP and run it from the GUI.


[http://ubuntuforums.org/showthread.php?t=1720726&highlight=pppconfig](http://ubuntuforums.org/showthread.php?t=1720726&highlight=pppconfig)
[http://ubuntuforums.org/showthread.php?t=1614599&highlight=pppconfig](http://ubuntuforums.org/showthread.php?t=1614599&highlight=pppconfig)


lk

---

### Post by ELMIT on 2012-05-21
I still could not make it :-k

I realized that the modem is only recognized when the phone line is also attached.

lsusb includes the modem:
> Bus 001 Device 009: ID 0572:1329 Conexant Systems (Rockwell), Inc.

lsusb -v -d 0572:1329 shows:

> Bus 001 Device 009: ID 0572:1329 Conexant Systems (Rockwell), Inc. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0572 Conexant Systems (Rockwell), Inc.
  idProduct          0x1329 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           73
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval             128
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      CDC Header:
        bcdCDC               1.10
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          1
      CDC ACM:
        bmCapabilities       0x07
          sends break
          line coding and serial state
          get/set/clear comm features
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      Country Selection:
        iCountryCodeRelDate        4 (??)
        wCountryCode          0x4803
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           96
    bNumInterfaces          3
    bConfigurationValue     2
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval             128
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
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
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      CDC Header:
        bcdCDC               1.10
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          1
      CDC ACM:
        bmCapabilities       0x07
          sends break
          line coding and serial state
          get/set/clear comm features
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      Country Selection:
        iCountryCodeRelDate        4 (??)
        wCountryCode          0x4803


disconnect of modem and reconnect gives me in dmesg:
> [34330.058224] cdc_acm 1-3.5.5:1.0: ttyACM0: USB ACM device
[34330.059553] usbcore: registered new interface driver cdc_acm
[34330.059560] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters


sudo stty -F /dev/ttyACM0 -a
> speed 9600 baud; rows 0; columns 0; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>;
eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;
werase = ^W; lnext = ^V; flush = ^O; min = 1; time = 0;
-parenb -parodd cs8 hupcl -cstopb cread clocal -crtscts
-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon -ixoff
-iuclc -ixany -imaxbel -iutf8
opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
isig icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt
echoctl echoke

sudo echo ATZ > /dev/ttyACM0
> bash: /dev/ttyACM0: Permission denied

Then I downloaded from linuxant the dgcmodem_1.13_i386.deb and tried to install it. Ubuntu Software Center opens and I get the install prompt. However, after showing the installation bar it still says [Install] - No error, nothing, ... 


I want to use efax-gtk to send / receive faxes.

How can I continue to get a fax working?

---

### Post by lkraemer on 2012-05-22
OK, you're off to a good start, so far.  Don't worry about the error for sending reset to the Modem.

From the linuxant site you need to follow their directions:
[http://www.linuxant.com/drivers/dgc/install.php](http://www.linuxant.com/drivers/dgc/install.php)

> 
METHOD B: DEBIAN PACKAGE (*.deb)
If you have obtained the driver package in DEBIAN format:

1. install the package with "dpkg -i dgcmodem_{version}_{arch}.deb", if apt-get or some other tool hasn't already done it for you.

2. if necessary, run "dgcconfig" to complete the installation, or to change your modem's configuration. 


So, open a Terminal Window and do:
```

cd ~
cd /path/to/downloaded/deb/file
dpkg -i dgcmodem_1.13_i386.deb

```
That should get it installed. 

Do the following sections - ONLY:
DIALOUT GROUP:
SETUP of PAP/CHAP-SECRETS File:

When you get to the testing section with pon & poff try those commands.


Do you have wvdial installed? 
Open a Terminal Window and type the following commands:
```

which wvdial
sudo wvdialconf /etc/wvdial.conf

```
Post the output of the commands.


lk

---

### Post by ELMIT on 2012-05-23
I installed essentials first!

root@ronald-Desktop:/home/ronald/Downloads# dpkg -i dgcmodem_1.13_i386.deb 
(Reading database ... 239374 files and directories currently installed.)
Preparing to replace dgcmodem:i386 1.13 (using dgcmodem_1.13_i386.deb) ...
Unpacking replacement dgcmodem:i386 ...
Setting up dgcmodem:i386 (1.13) ...
Conexant DGC USB modem driver, version 1.13

If you need assistance or more information, please go to:
	[http://www.linuxant.com/](http://www.linuxant.com/)

When reporting a problem for the first time, please send
us the file generated by "dgcconfig --dumpdiag".

No pre-built modules for: Ubuntu-12.04 linux-3.2.0-24-generic x86_64-SMP

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Building modules for kernel 3.2.0-24-generic, using source directory
/lib/modules/3.2.0-24-generic/build. Please wait...

ERROR: Module build failed!
Please examine the log file "/tmp/dgcconfig-buildlog.txt" to determine why.


> (cd /lib/modules/3.2.0-24-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.2.0-24-generic/build" "M=/usr/lib/dgcmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/3.2.0-24-generic/build/.tmp_versions/dgcusbdcp.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/3.2.0-24-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.2.0-24-generic/build" "M=/usr/lib/dgcmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
  CC [M]  /usr/lib/dgcmodem/modules/mod_dgcusbdcp.o
/usr/lib/dgcmodem/modules/mod_dgcusbdcp.c: In function 'dgcUsbWrite':
/usr/lib/dgcmodem/modules/mod_dgcusbdcp.c:173:2: warning: format '%d' expects argument of type 'int', but argument 5 has type 'size_t' [-Wformat]
/usr/lib/dgcmodem/modules/mod_dgcusbdcp.c: At top level:
/usr/lib/dgcmodem/modules/mod_dgcusbdcp.c:263:36: error: 'SPIN_LOCK_UNLOCKED' undeclared here (not in a function)
make[2]: *** [/usr/lib/dgcmodem/modules/mod_dgcusbdcp.o] Error 1
make[1]: *** [_module_/usr/lib/dgcmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
make: *** [all] Error 2




root@ronald-Desktop:~# which wvdial
/usr/bin/wvdial
root@ronald-Desktop:~# sudo wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   S4   S5   S6   S7   S8   
Modem Port Scan<*1>: S9   S10  S11  S12  S13  S14  S15  S16  
Modem Port Scan<*1>: S17  S18  S19  S20  S21  S22  S23  S24  
Modem Port Scan<*1>: S25  S26  S27  S28  S29  S30  S31  


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://alumnit.ca/wiki/?WvDial](http://alumnit.ca/wiki/?WvDial)

---

### Post by lkraemer on 2012-05-23
It looks like you are going to need to contact the folks at linuxant and
give them the errors found in the log file "/tmp/dgcconfig-buildlog.txt"
to be able to get the driver compiled.

You installed build-essential, but did you also install the Linux-headers for your current system?

**Prerequisites:**
Typically you need to install build-essential, and the headers for the
kernel you are running, if you are going to compile code.
```

uname -r

```
will tell you the kernel you are currently running.
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
will install the software needed to compile your code.


lk

---

### Post by ELMIT on 2012-06-02
I did not receive an answer from linuxant, ...

headers and essential is installed.

I found on the Internet that SPIN_LOCK_UNLOCKED should not be used anymore, ... 

... seems I bought a useless device, ...

---

### Post by kidoruigenso on 2012-09-07
There is a solution to the SPIN_LOCK_UNLOCKED problem, see
[http://ubuntuforums.org/showthread.php?t=1939787&page=5](http://ubuntuforums.org/showthread.php?t=1939787&page=5)
and
[http://ubuntuforums.org/showthread.php?t=1942869](http://ubuntuforums.org/showthread.php?t=1942869).

This is thanks to "Computator" of the UbuntuForums (apparently Derek Neely) who created a patch that allows the Linuxant USB modem driver to work with the latest kernels like you find in Ubuntu 12.04 that do not recognize SPIN_LOCK_UNLOCKED.

On my system, with a fresh install of Ubuntu 12.04 and a ZOOM Model 3095 external USB mini external modem, the solution worked.

---

