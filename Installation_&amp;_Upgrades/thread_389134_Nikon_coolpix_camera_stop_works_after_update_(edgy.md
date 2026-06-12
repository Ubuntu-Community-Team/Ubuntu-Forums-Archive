---
title: "Nikon coolpix camera stop works after update (edgy)"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by larini on 2007-03-20
My digital camera stop to work after an update from version 2.2.1 to 2.3.0 of libgphoto2
Can anyone have the solution other than lock 2.2.1 version?
Thanks,

follow the error:

paulo@Amd64:~$ sudo env LANG=C gphoto2 --debug --camera="Nikon Coolpix 880" --port=usb: -P
0.000015 main(2): ALWAYS INCLUDE THE FOLLOWING LINES WHEN SENDING DEBUG MESSAGES TO THE MAILING LIST:
0.000241 main(2): gphoto2 2.2.0
0.000389 main(2): gphoto2 has been compiled with the following options:
0.000535 main(2):  + gcc (C compiler used)
0.000679 main(2):  + popt (for handling command-line parameters)
0.000821 main(2):  + exif (for displaying EXIF information)
0.000962 main(2):  + cdk (for accessing configuration options)
0.001104 main(2):  + no aa (for displaying live previews)
0.001246 main(2):  + jpeg (for displaying live previews in JPEG format)
0.001388 main(2):  + readline (for easy navigation in the shell)
0.001530 main(2): libgphoto2 2.3.0
0.001677 main(2): libgphoto2 has been compiled with the following options:
0.001819 main(2):  + gcc (C compiler used)
0.001960 main(2):  + no ltdl (for portable loading of camlibs)
0.002102 main(2):  + EXIF (for special handling of EXIF files)
0.002245 main(2): libgphoto2_port 0.7.0
0.002388 main(2): libgphoto2_port has been compiled with the following options:
0.002537 main(2):  + gcc (C compiler used)
0.002678 main(2):  + no ltdl (for portable loading of camlibs)
0.002819 main(2):  + USB (libusb, for USB cameras)
0.002960 main(2):  + serial (for serial cameras)
0.003101 main(2):  + no resmgr (serial port access and locking)
0.003243 main(2):  + no baudboy (serial port locking)
0.003384 main(2):  + no ttylock (serial port locking)
0.003525 main(2):  + no lockdev (serial port locking)
0.003689 main(2): Processing 'model' option ('Nikon Coolpix 880')...
0.003957 gphoto2-camera(2): Setting abilities ('Nikon CoolPix 880')...
0.004112 setting/gphoto2-setting.c(2): Creating $HOME/.gphoto
0.004374 setting/gphoto2-setting.c(2): Loading settings from file "/home/paulo/.gphoto/settings"
0.004556 gphoto2-setting(2): Setting key 'model' to value 'Nikon CoolPix 880' (gphoto2)
0.004710 gphoto2-setting(2): Saving 2 setting(s) to file "/home/paulo/.gphoto/settings"
0.005022 main(2): Processing 'port' option ('usb:')...
0.005191 gphoto2-port-info-list(2): Using ltdl to load io-drivers from '/usr/lib/libgphoto2_port/0.7.0'...
0.005398 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.7.0/disk'.
0.010300 gphoto2-port/disk(2): found 7 volumes
0.022072 gphoto2-port-info-list(2): Loaded 'Media 'Volume (ext3)'' ('disk:/') from '/usr/lib/libgphoto2_port/0.7.0/disk'.
0.026506 gphoto2-port-info-list(2): Loaded 'Media 'Volume (ext3)'' ('disk:/media/dados') from '/usr/lib/libgphoto2_port/0.7.0/disk'.
0.026532 gphoto2-port-info-list(2): Loaded '' ('^disk:') from '/usr/lib/libgphoto2_port/0.7.0/disk'.
0.026553 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.7.0/ptpip'.
0.026892 gphoto2-port-info-list(2): Loaded 'PTP/IP Connection' ('ptpip:') from '/usr/lib/libgphoto2_port/0.7.0/ptpip'.
0.026915 gphoto2-port-info-list(2): Loaded '' ('^ptpip') from '/usr/lib/libgphoto2_port/0.7.0/ptpip'.
0.026935 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.027104 gphoto2-port-serial(2): Trying to lock '/dev/ttyS0'...
0.027302 gphoto2-port-serial(2): Trying to lock '/dev/ttyS1'...
0.027358 gphoto2-port-serial(2): Trying to lock '/dev/ttyS2'...
0.027408 gphoto2-port-serial(2): Trying to lock '/dev/ttyS3'...
0.027620 gphoto2-port-info-list(2): Loaded 'Serial Port 0' ('serial:/dev/ttyS0') from '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.027642 gphoto2-port-info-list(2): Loaded 'Serial Port 1' ('serial:/dev/ttyS1') from '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.027661 gphoto2-port-info-list(2): Loaded 'Serial Port 2' ('serial:/dev/ttyS2') from '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.027681 gphoto2-port-info-list(2): Loaded 'Serial Port 3' ('serial:/dev/ttyS3') from '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.027700 gphoto2-port-info-list(2): Loaded '' ('^serial') from '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.027719 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.7.0/usb'.
0.028508 gphoto2-port-info-list(2): Loaded 'Universal Serial Bus' ('usb:') from '/usr/lib/libgphoto2_port/0.7.0/usb'.
0.028533 gphoto2-port-info-list(2): Loaded '' ('^usb:') from '/usr/lib/libgphoto2_port/0.7.0/usb'.
0.028557 gphoto2-port-info-list(2): Counting entries (12 available)...
0.028576 gphoto2-port-info-list(2): 8 regular entries available.
0.028595 gphoto2-port-info-list(2): Looking for path 'usb:' (12 entries available)...
0.028615 gphoto2-port-info-list(2): Getting info of entry 7 (12 available)...
0.028641 gphoto2-camera(2): Setting port info for port 'Universal Serial Bus' at 'usb:'...
0.029250 gphoto2-port(2): Setting timeout to 5000 millisecond(s)...
0.029274 gphoto2-port(2): Setting settings...
0.029292 gphoto2-setting(2): Setting key 'port' to value 'usb:' (gphoto2)
0.029313 gphoto2-setting(2): Saving 2 setting(s) to file "/home/paulo/.gphoto/settings"
0.030194 gphoto2-camera(2): Listing files in '/'...
0.030220 gphoto2-camera(2): Initializing camera...
0.030267 gphoto2-port-usb(1): Looking for USB device (vendor 0x4b0, product 0x103)... found.
0.030293 gphoto2-port-usb(1): Detected defaults: config 1, interface 0, altsetting 0, inep 83, outep 04, intep ffffffff, class ff, subclass ff
0.030314 gphoto2-camera(2): Loading '/usr/lib/libgphoto2/2.3.0/sierra'...
0.030649 gphoto2-port(2): Opening USB port...
0.030787 gphoto2-port(0): Could not query kernel driver of device.
0.030903 gphoto2-port(2): Setting settings...
0.041963 gphoto2-port(0): Could not set config 0/1 (Broken pipe)
0.042141 sierra/sierra.c(2): Operation failed (-37)!
0.042305 gphoto2-port(2): Closing port...
0.042489 gphoto2-port(0): Could not release interface 0 (Invalid argument).
0.042693 context(0): An error occurred in the io-library ('Error updating the port settings'): Could not release interface 0 (Invalid argument).

*** Error ***              
An error occurred in the io-library ('Error updating the port settings'): Could not release interface 0 (Invalid argument).
*** Error (-37: 'Error updating the port settings') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug --camera=Nikon Coolpix 880 --port=usb: -P

Please make sure there is sufficient quoting around the arguments.

0.043586 gp-camera(2): Freeing camera...
0.046552 gphoto2-port(2): Freeing port...
0.046574 gphoto2-port(2): Closing port...
0.046610 gphoto2-port(0): Could not release interface 0 (Invalid argument).
0.046719 libgphoto2/gphoto2-filesys.c(2): Clearing fscache LRU list...
0.046735 libgphoto2/gphoto2-filesys.c(2): fscache LRU list already empty
0.046749 gphoto2-filesystem(2): Internally deleting all folders from '/'...
paulo@Amd64:~$

---

