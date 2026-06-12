---
title: "usbserial pl2303 with connected epson tt88iii printer, troubleshoot printing issue"
date: 2013-03-25
forum: Installation &amp; Upgrades
---

### Post by evias on 2013-03-25
Hello everyone!

this post concerns an EPSON TM-T88III printer which I am not able to print on. The connection works upon a usbserial interface using the PL2303 serial port driver (as shows the lsusb output posted below in the environment details). 

configured with cups' web interface and Linux Dotmatrix Foomatic/epson driver, i manage to get a beep on the serial connector at the other end of my usb adapter.
[LIST]
[*]from this i am able to tell that data is sent through the usbserial adapter but kind of gets stuck at the door of the printer if i may metaphorize..
[LIST]
[*]More details.. I get multiple beeps of different lengths on the connector when printing a self test page, which on such a ticket printer results in printing [A-Za-z0-9] and some crappy characters mixed multiple times.. (ticket length of approximately 200 dollar in a food market [=long])
[/LIST]
[/LIST]

I have tried many tutorials and researched through web, i must have clicked and flown over at least a hundred threads in the last two days .. all this kind of helped me a lot as saturday i didn't know anything about /dev/ttyUSB0 and now I know it is used in cups' URI thus means it should represent my printer's "display" .. though a simple 'echo "HELLO\x0D" > /dev/ttyUSB0' gives me not even the beep. 
 
This post might get a little long as my problem is pretty complex and I have fixed myself up to one last problem: [B]PRINTING
[/B]I mean... I HEAR MY DATA! this is really frustrating as I kind of realize something is blocking on the printer's side. 
**Though**, the printer has been tested in my presence on a cash drawer and works perfectly with a serial to ethernet cable which plugs into the cash drawer touch screen. 
I am using a serial to usb as I developed an application and basically want to print browser contents to this ticket printer. 

There seems to be a lot of people researching about my single printer model "**TM-T88iii**" though no one seems to have the real answer to it ..
I have also tried a pySerial implementation, a C++ serial printer application but no printing and, when i coded or compiled from the web, **no beep**.
Beep happens when printing using cups, such as *web browser print* or *test page print. *

I tried installing multiple drivers from Epson, first of course the TM-T88iii driver they provide on the Epson website.
I have also downloaded and successfully installed the POSMicro Linux drivers for TMT through cups, though nothing happened doing this.

What else ..

I am able to print a self test page from the ticket printer buttons (power off > power on + FEED) and get the settings that should be set such as baudrate, stopbits, etc. (i will post all details underneath the problem)

on the cups interface:
[LIST]
[*]Manage Printers > add printer
[*]When configuring the printer, options are set automatically, such as baud rate etc. and most of them correspond (but probably are defaulted to..) to the printer's settings values.
[*]As soon as the printer is added, i am able to produce that beep i am so glad to hear (as it means the adapter kind of works.. [and i have the insurance that the printer works as well; maybe, though, i will have to find another communication setting..])
[*]I have tested multiple combinations of drivers / printer options but none could print out to my ticket printer, i have also tried using several drivers from the web such as the PPD files provided directly from the EPSON support website for my printer.
[/LIST]

As i tell you, i tried installing the printer a billion times using cups' [i must say handy] web interface, though all settings failed, no setting printed anything, and the best i got is sound on the serial port. now.. maybe there is a data encoding standard i don't get which makes data receival fail, maybe [*i just read 'Buffer capacity: 4K bytes' but don't know what i could do about that] *my data is sent in the wrong way (sending tickets as ASCII and simple "HELLO\x0D" and "HELLO" files tried as well..).

I am out of ideas right now and probably will edit my post with more facts and analyses i have done...

Here is more about my environment and settings:
```

epsontmt printer configuration on cups' web interface :
-------------------------------------------------------------

[TABLE]
[TR]
[TH]Description:[/TH]
[TD]ticket[/TD]
[/TR]
[TR]
[TH]Location:[/TH]
[TD]cuisine[/TD]
[/TR]
[TR]
[TH]Driver:[/TH]
[TD]Epson Dot Matrix Foomatic/epson (grayscale, 2-sided printing)[/TD]
[/TR]
[TR]
[TH]Connection:[/TH]
[TD]serial:/dev/ttyUSB0?baud=9600+bits=8+parity=none+flow=soft[/TD]
[/TR]
[TR]
[TH]Defaults:[/TH]
[TD]job-sheets=none, none media=na_letter_8.5x11in sides=one-sided[/TD]
[/TR]
[/TABLE]

```

```

***$ uname -a***
Linux greg-laptop 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:20:06 UTC 2013 i686 i686 i686 GNU/Linux

```

```

***$ lsusb***
Bus 001 Device 003: ID 04f2:b083 Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 006 Device 013: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Here is the output of "***cat /var/log/cups/error_log***" :
*[too long, would massacre post readability..*][URL="http://pastebin.com/ELRxsNEa"]
http://pastebin.com/ELRxsNEa[/URL]


```

***$ modprobe -l | grep usbserial***
kernel/drivers/usb/serial/usbserial.ko
***$ modprobe -l | grep pl2303***
kernel/drivers/usb/serial/pl2303.ko


```

```

***$ ll /dev/ttyUSB****
crw-rw---- 1 root dialout 188, 0 Mar 25 23:53 /dev/ttyUSB0

```

i also tried things with minicom, and installed libgnomeprint, nothing to do with it ... with minicom i must assume i am not able to understand which part of the program i could possibly use to test my printer here.. 

NO /dev/usb/ available, nor /dev/lp0, guess this has to do with the cups updates as mention multiple forum threads. Though, many people seem to tell 'echo "hello" > /dev/ttyUSB0' should have the exact same effect, which i cannot achieve to produce ..  

i found one more thing referencing the adapter ..

```

***$ ll /dev/serial/by-id/***
total 0
drwxr-xr-x 2 root root 60 Mar 25 21:45 ./
drwxr-xr-x 4 root root 80 Mar 25 21:45 ../
lrwxrwxrwx 1 root root 13 Mar 25 21:45 usb-Prolific_Technology_Inc._USB-Serial_Controller-if00-port0 -> ../../ttyUSB0

```

Didn't find anything about the printer except after adding it through the cups interface

```

***$ lpstat -p -d epsontmt***
*printer epsontmt is idle.  enabled since Tue 26 Mar 2013 12:04:26 AM CET*
printer MFC-235C disabled since Sun 24 Mar 2013 03:54:50 PM CET -
    Unplugged or turned off
system default destination: epsontmt

```

Ok got more interesting data:
[LIST]
[*]on the cups web interface in the manage printers part of my epsontmt printer i can choose to "Clean Print Heads" which results in a stopped job (automatic) with an error message of "_invalid printer command 'Clean'_"  This i all get from the cups web interface
[*]using the same menu i may "Print Self Test Page" which results only in [*a eureka feeling-like*] **beep **and "printer job completed" message on the cups web interface (no printing occured, i got all notifications from cups though on my system.. "Printing Self Test Page" "Print Completed" ...)
[*]same menu again "Print Test Page" which results in a much **longer beep** [*heart stopped beating long*] (job started at  *12:15:49 *and finished at *12:16:39 ***beeps almost a minute**)
[/LIST]

Even More Data late late in the evening:
[LIST]
[*]when i unplug my printer, then print something, i get a Held job with message "_unable to open serial port: No such file or directory_" from the cups web interface
[*]when i plug it back in i am now able to "Release the job" on the cups interface and that gives me a gnome notification with "Print error: epsontmt connecting-to-device" and after the held job is release, the test page is sent back to the printer again (now it works and i get the beep again as the pritner is connected
[*]***interesting bottom fact: when i turn off the printer but leave it connected through usb; i get no beep. When i turn it back on, the serial connector starts beeping again. Isn't it obvious that my printer is recognized but ignoring my data ? Somehow i have a feeling of data problem, maybe i send to big data blocks ? how could i change that ?***
[/LIST]


Might have gotten a bit unorganized, though all my problem is listed in here now, **PLEASE**; really, ***PLEASE*** someone share his / her knowledge and help me** troubleshoot** that ..

i'm out of power now ^^ 
peace

---

### Post by pdc on 2013-03-25
this thread

[http://ubuntuforums.org/showthread.php?t=1444715](http://ubuntuforums.org/showthread.php?t=1444715) 

contained more questions than answers but it did suggest one look at linux OPOS/JPOS software

that sort of shows up some google responses: IBM support the Suse linux as SLED in this link [http://www-01.ibm.com/support/docview.wss?uid=pos1R1003632](http://www-01.ibm.com/support/docview.wss?uid=pos1R1003632)

I don't know where you will find some experts to help you on this ......I suspect in places like IBM

I can only find an Epson driver for the newer 88iv as opposed to your 88iii

[http://download.epson-biz.com/modules/pos/index.php?page=prod&pcat=3&scat=32&pid=30](http://download.epson-biz.com/modules/pos/index.php?page=prod&pcat=3&scat=32&pid=30)

---

### Post by evias on 2013-03-25
thanks for the reply at first .. 

yup you hit the same download place i did.. i tried 4 different epson downloads (not to mention the tests using windows XP and 7), none would print anything, nor send data (as of my latest superpower of **hearing** data flow across serial cables... seriously i know it's normal, i'm just really frustrated the data won't print with any driver xD)

so .. yeah i'm gonna give a look at this **opos/jpos** software, read that too but didn't investigate deeper, seemed a bit complicated at first regard, and i forgot about it now so good point mentioning it .. checking that right away and i'll update the post with more input .. looks like a sleepless night for me!

again thanks for the post, searching the web can be a real pain, i start questioning my keyword search abilities after a while, hitting all the same doors .. so people help is welcome

bye

---

### Post by evias on 2013-03-25
seems like there is not a lot of ubuntu support on this side of the door .. trying to find something but only found windows drivers which had already downloaded and installed previously (APD 4.54 ; TMUSB) and found a linux application "turboprint" which does not list my Epson model in the Epson printer list. 

more updates on cups interface: only the "**Epson Dot Matrix Foomatic/epson** " gives me any response at all (**beep**) as all other drivers finalize the process by shouting an error message i may have mentioned in the original thread post. 

again i'm stuck .. tried "locate *.ppd" after installing turboprint, it wasn't a lucky day i guess ..

using the pos.epson.com website i also installed "**tmportconfig**" and "**tmpcsconfig**", though i have no idea how to use those and am searching the web .. first search "tmportconfig", all the google results are coming from the epson download website... today i must really be cursed !

Oh... found some input in the tmt-cups implementation downloaded on the epson website, here is more data for you to know; i investigate further..

```

***$ dpkg-query -l libusb-1.0-0***
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version               Architecture          Description
+++-=================================-=====================-=====================-========================================================================
ii  libusb-1.0-0:i386                 2:1.0.12-2            i386                  userspace USB programming library
[I][B]
$ dpkg-query -l cups[/B][/I]
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version               Architecture          Description
+++-=================================-=====================-=====================-========================================================================
ii  cups                              1.6.1-0ubuntu11.3     i386                  Common UNIX Printing System(tm) - server

```

hope this helps you help me .. 

thanks in advance

---

### Post by evias on 2013-03-26
still browsing the web ... i will go on pasting interesting data which might help **you** (me) understanding the issue or recognizing, etc..

```

***$ cat /proc/tty/drivers*** /dev/tty             /dev/tty        5       0 system:/dev/tty
/dev/console         /dev/console    5       1 system:console
/dev/ptmx            /dev/ptmx       5       2 system
/dev/vc/0            /dev/vc/0       4       0 system:vtmaster
rfcomm               /dev/rfcomm   216 0-255 serial
usbserial            /dev/ttyUSB   188 0-253 serial
ttyprintk            /dev/ttyprintk   5       3 console
serial               /dev/ttyS       4 64-111 serial
pty_slave            /dev/pts      136 0-1048575 pty:slave
pty_master           /dev/ptm      128 0-1048575 pty:master
unknown              /dev/tty        4 1-63 console

```

i see /dev/ttyUSB uses usbserial driver, isn't that what it should? i think it is.. next..

```

***$ setserial /dev/ttyUSB0***
/dev/ttyUSB0, UART: 16654, Port: 0x0000, IRQ: 0
***$ lsmod | grep serial***
usbserial              36684  1 pl2303
***$ setserial -G /dev/ttyUSB0 ***
/dev/ttyUSB0 uart 16654 port 0x0000 irq 0 baud_base 460800 spd_normal
***$ sudo ls /proc/tty/driver/***
serial    usbserial




```

```

***$ setserial -a /dev/ttyUSB0 ***
/dev/ttyUSB0, Line 0, UART: 16654, Port: 0x0000, IRQ: 0
    Baud_base: 460800, close_delay: 0, divisor: 0
    closing_wait: infinite
    Flags: spd_normal

```

for the last one i assume baud_base must be updated here but i also discover UART 16654, which, as i read on a forum [http://forums.fedoraforum.org/archive/index.php/t-249170.html](http://forums.fedoraforum.org/archive/index.php/t-249170.html) , means that the serial connection is recognized entirely.

so now, after this **setserial **command execution i am able to produce a [*the wonderful*] **beep **from a simple 
```

echo "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789" > /dev/ttyUSB0

```

i had only tested with "HELLO", which was a really small data size and resulted in a very low **beep** i didn't even notice .. So now basically i produce this **data-transfer** by command line command execution directly. Though the printer does not happen [*yet?*]

digging..
```

***$ ll /sys/class/tty/ttyUSB0/device/driver/***
total 0
drwxr-xr-x 2 root root    0 Mar 26 05:15 ./
drwxr-xr-x 4 root root    0 Mar 26 05:15 ../
--w------- 1 root root 4096 Mar 26 05:51 bind
lrwxrwxrwx 1 root root    0 Mar 26 05:51 module -> ../../../../module/pl2303/
-rw-r--r-- 1 root root 4096 Mar 26 05:51 new_id
lrwxrwxrwx 1 root root    0 Mar 26 05:51 ttyUSB0 -> ../../../../devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/ttyUSB0/
--w------- 1 root root 4096 Mar 26 05:15 uevent
--w------- 1 root root 4096 Mar 26 05:51 unbind

```

```

***$ stty -a -F /dev/ttyUSB0 ***
speed 9600 baud; rows 0; columns 0; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>; eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;
werase = ^W; lnext = ^V; flush = ^O; min = 1; time = 0;
-parenb -parodd cs8 hupcl -cstopb cread clocal -crtscts
-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon -ixoff -iuclc -ixany -imaxbel -iutf8
opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
isig icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt echoctl echoke

```

---

### Post by evias on 2013-03-26
even more ..

```

**$ udevadm info --query=all --name=/dev/ttyUSB0 **
P: /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/ttyUSB0/tty/ttyUSB0
N: ttyUSB0
S: serial/by-id/usb-Prolific_Technology_Inc._USB-Serial_Controller-if00-port0
S: serial/by-path/pci-0000:00:1d.2-usb-0:2:1.0-port0
E: DEVLINKS=/dev/serial/by-id/usb-Prolific_Technology_Inc._USB-Serial_Controller-if00-port0 /dev/serial/by-path/pci-0000:00:1d.2-usb-0:2:1.0-port0
E: DEVNAME=/dev/ttyUSB0
E: DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/ttyUSB0/tty/ttyUSB0
E: ID_BUS=usb
E: ID_MM_CANDIDATE=1
E: ID_MODEL=USB-Serial_Controller
E: ID_MODEL_ENC=USB-Serial\x20Controller
E: ID_MODEL_FROM_DATABASE=PL2303 Serial Port
E: ID_MODEL_ID=2303
E: ID_PATH=pci-0000:00:1d.2-usb-0:2:1.0
E: ID_PATH_TAG=pci-0000_00_1d_2-usb-0_2_1_0
E: ID_REVISION=0300
E: ID_SERIAL=Prolific_Technology_Inc._USB-Serial_Controller
E: ID_TYPE=generic
E: ID_USB_DRIVER=pl2303
E: ID_USB_INTERFACES=:ff0000:
E: ID_USB_INTERFACE_NUM=00
E: ID_VENDOR=Prolific_Technology_Inc.
E: ID_VENDOR_ENC=Prolific\x20Technology\x20Inc.
E: ID_VENDOR_FROM_DATABASE=Prolific Technology, Inc.
E: ID_VENDOR_ID=067b
E: MAJOR=188
E: MINOR=0
E: SUBSYSTEM=tty
E: UDEV_LOG=3
E: USEC_INITIALIZED=2627554295

```

---

### Post by evias on 2013-03-26
okay okay, getting closer to the point [*kind of*] .. analysing cups/error_log when printing from the browser gives me this block of lines :

```

(*send print request from web browser*)
***$ cat /var/log/cups/error_log | wc -l***
723

```

723 lines i am now analysing ...

```

***$ cat /var/log/cups/error_log | grep Job\ 88***
I [26/Mar/2013:13:15:21 +0100] [Job 88] Adding start banner page "none".
I [26/Mar/2013:13:15:21 +0100] [Job 88] Adding end banner page "none".
I [26/Mar/2013:13:15:21 +0100] [Job 88] File of type [COLOR=#ff0000]***application/pdf***[/COLOR] queued by "greg".
D [26/Mar/2013:13:15:21 +0100] [Job 88] hold_until=0
I [26/Mar/2013:13:15:21 +0100] [Job 88] Queued on "epsontmt" by "greg".
D [26/Mar/2013:13:15:21 +0100] [Job 88] time-at-processing=1364300121
D [26/Mar/2013:13:15:21 +0100] [Job 88] job-sheets=none,none
D [26/Mar/2013:13:15:21 +0100] [Job 88] argv[0]="epsontmt"
D [26/Mar/2013:13:15:21 +0100] [Job 88] argv[1]="88"
D [26/Mar/2013:13:15:21 +0100] [Job 88] argv[2]="greg"
D [26/Mar/2013:13:15:21 +0100] [Job 88] argv[3]="Pizzeria Da Antonio - Back Office"
D [26/Mar/2013:13:15:21 +0100] [Job 88] argv[4]="1"
D [26/Mar/2013:13:15:21 +0100] [Job 88] argv[5]="PageSize=Letter number-up=1 Resolution=60x216dpi job-uuid=urn:uuid:d1502cd1-8539-3da1-6bc6-84b4d2b4af6f job-originating-host-name=localhost time-at-creation=1364300121 time-at-processing=1364300121"
D [26/Mar/2013:13:15:21 +0100] [Job 88] argv[6]="***/var/spool/cups/d00088-001***"

```

"***application/pdf***" surely is not the one i want to use, i guess i should probably use something like "***text/plain***" at a first to fix the printing issue, though i don't know how to tell chrome to print with another file type .. any idea on that path ?

second bolded is the cups spooler file created for printing, the content of this file is not relevant as not human readable. I have also tried "***rm -f /var/spool/cups/d****" with no success.

cups environment configuration logged at print time:
```

D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[8]="HOME=/var/spool/cups/tmp"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[10]="SERVER_ADMIN=root@greg-laptop"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[11]="SOFTWARE=CUPS/1.6.1"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[13]="USER=root"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[14]="CUPS_MAX_MESSAGE=2047"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[17]="IPP_PORT=631"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[18]="CHARSET=utf-8"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[19]="LANG=en_US.UTF-8"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[20]="PPD=/etc/cups/ppd/epsontmt.ppd"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[21]="RIP_MAX_CACHE=128m"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[22]="CONTENT_TYPE=***application/pdf***"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[23]="DEVICE_URI=***serial:/dev/ttyUSB0?baud=9600+bits=8+parity=none+flow=soft***"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[24]="PRINTER_INFO=ticket"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[25]="PRINTER_LOCATION=cuisine"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[26]="PRINTER=epsontmt"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[27]="PRINTER_STATE_REASONS=none"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[28]="CUPS_FILETYPE=document"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[29]="FINAL_CONTENT_TYPE=printer/epsontmt"
D [26/Mar/2013:13:15:21 +0100] [Job 88] envp[30]="AUTH_I****"

```

the file description:
```

D [26/Mar/2013:13:15:21 +0100] [Job 88] ================================================
D [26/Mar/2013:13:15:21 +0100] [Job 88] File: <STDIN>
D [26/Mar/2013:13:15:21 +0100] [Job 88] ================================================
D [26/Mar/2013:13:15:21 +0100] [Job 88] Filetype: ***PDF***
D [26/Mar/2013:13:15:21 +0100] [Job 88] Storing temporary files in /var/spool/cups/tmp
D [26/Mar/2013:13:15:21 +0100] [Job 88] STATE: -connecting-to-device
D [26/Mar/2013:13:15:21 +0100] [Job 88] PID 7978 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [26/Mar/2013:13:15:21 +0100] [Job 88] File contains 1 pages
D [26/Mar/2013:13:15:21 +0100] [Job 88] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -dNOINTERPOLATE -sDEVICE=epson -r60x216 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-   /var/spool/cups/tmp/foomatic-mqh4we 
D [26/Mar/2013:13:15:21 +0100] [Job 88] Starting process "kid3" (generation 1)
D [26/Mar/2013:13:15:21 +0100] [Job 88] Starting process "kid4" (generation 2)
D [26/Mar/2013:13:15:21 +0100] [Job 88] Starting process "renderer" (generation 2)
D [26/Mar/2013:13:15:21 +0100] [Job 88] JCL: %-12345X@PJL
D [26/Mar/2013:13:15:21 +0100] [Job 88] <job data> 
D [26/Mar/2013:13:15:21 +0100] [Job 88] Wrote 96 bytes.
D [26/Mar/2013:13:15:21 +0100] [Job 88] Wrote 96 bytes.
D [26/Mar/2013:13:15:21 +0100] [Job 88] Wrote 96 bytes.
D [26/Mar/2013:13:15:21 +0100] [Job 88] Wrote 96 bytes.
D [26/Mar/2013:13:15:21 +0100] [Job 88] Wrote 96 bytes.
D [26/Mar/2013:13:15:21 +0100] [Job 88] renderer exited with status 0
D [26/Mar/2013:13:15:21 +0100] [Job 88] kid4 exited with status 0
D [26/Mar/2013:13:15:21 +0100] [Job 88] kid3 finished
D [26/Mar/2013:13:15:21 +0100] [Job 88] Kid3 exit status: 0
D [26/Mar/2013:13:15:21 +0100] [Job 88] Closing foomatic-rip.
D [26/Mar/2013:13:15:21 +0100] [Job 88] PID 7979 (/usr/lib/cups/filter/foomatic-rip) exited with no errors.
D [26/Mar/2013:13:15:21 +0100] [Job 88] Wrote 96 bytes.
D [26/Mar/2013:13:15:21 +0100] [Job 88] Wrote 96 bytes.D [26/Mar/2013:13:15:21 +0100] [Job 88] Wrote 96 bytes.
D [26/Mar/2013:13:15:21 +0100] [Job 88] Wrote 96 bytes.
D [26/Mar/2013:13:15:21 +0100] [Job 88] Wrote 96 bytes.
D [26/Mar/2013:13:15:21 +0100] [Job 88] Wrote 96 bytes.
D [26/Mar/2013:13:15:21 +0100] [Job 88] Wrote 96 bytes.
D [26/Mar/2013:13:15:21 +0100] [Job 88] Wrote 96 bytes.
D [26/Mar/2013:13:15:21 +0100] [Job 88] Wrote 96 bytes.....
....
D [26/Mar/2013:13:15:30 +0100] [Job 88] PID 7980 (/usr/lib/cups/backend/serial) exited with no errors.
D [26/Mar/2013:13:15:30 +0100] [Job 88] time-at-completed=1364300130
I [26/Mar/2013:13:15:30 +0100] [Job 88] Job completed.
D [26/Mar/2013:13:16:51 +0100] [Job 88] Unloading...

```

now for issuing print jobs i use lp which is more convenient than printing from web browser but results in exactly the same... 
```

[I][B]$ lp -d epsontmt -o fitplot -o blackplot -o media=Custom.612x792 -o source=DocFeedCut -o cpi=9 /home/greg/txtfile
[/B][/I]
OR

***$ cat /home/greg/txtfile | lp -d epsontmt -o fitplot -o blackplot -o media=Custom.612x792 -o source=DocFeedCut -o cpi=9***

```

i have tried using none of these options; using some of them, etc.. couldn't find a working configuration, ***beep happens ***as long as the text is .. (if i send a simple "A", the beep is merely audible .. if i send the whole alphanumerical character set, it is recognizable...) but [COLOR=#ff0000]_**still no printing**_[/COLOR]

---

