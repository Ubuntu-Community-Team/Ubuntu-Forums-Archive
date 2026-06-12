---
title: "Neither Simple Scan nor XSane working"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2010-05-15
I have installed Lucid about 1 hour ago. I'm testing all the bits & pieces. The scanner service is a'goner. viz:


ark@Lexington-19-Karmic:~$ simple-scan -d
** (simple-scan:12360): DEBUG: Starting Simple Scan 1.0.3, PID=12360
** (simple-scan:12360): DEBUG: Restoring window to 600x400 pixels
** (simple-scan:12360): DEBUG: sane_init () -> SANE_STATUS_GOOD
** (simple-scan:12360): DEBUG: SANE version 1.0.20
** (simple-scan:12360): DEBUG: Requesting redetection of scan devices
** (simple-scan:12360): DEBUG: Processing request
** (simple-scan:12360): DEBUG: sane_get_devices () -> SANE_STATUS_GOOD
** (simple-scan:12360): DEBUG: Device: name="brother2:bus1;dev3" vendor="Brother" model="MFC-240C" type="USB scanner"
** (simple-scan:12360): DEBUG: Requesting scan at 300 dpi from device 'brother2:bus1;dev3'
** (simple-scan:12360): DEBUG: scanner_scan ("brother2:bus1;dev3", 300, SCAN_SINGLE)
** (simple-scan:12360): DEBUG: Processing request
** (simple-scan:12360): DEBUG: sane_open ("brother2:bus1;dev3") -> SANE_STATUS_INVAL

** (simple-scan:12360): WARNING **: Unable to get open device: Invalid argument
** (simple-scan:12360): DEBUG: Stopping scan thread
** (simple-scan:12360): DEBUG: Processing request
** (simple-scan:12360): DEBUG: sane_exit ()
mark@Lexington-19-Karmic:~$ scanimage -L
device `brother2:bus1;dev3' is a Brother MFC-240C USB scanner

============= 15 minutes after this post above =============

I found a way to get XSane to work at:

[http://ubuntuforums.org/archive/index.php/t-166944.html](http://ubuntuforums.org/archive/index.php/t-166944.html)

sudo chmod a+w /dev/bus/usb/002/002

I'm still researching the Simple Scan prob.

======================
The Next Day:

rerunning the chmod a+w command on ALL usb buses (001 and 002), now does not work, unlike yesterday. Go Figure!!!

=================

15 minutes after the Next Day: post.

I have found a partial solution. I quote post #5 in full:

[Re: HOWTO: Make HP Scanjet 4370 work]("http://ubuntuforums.org/showthread.php?t=410398")

In the meantime I made an upgrade of my box to kubuntu 7.10 and unfortunately lost my scanner configuration. I installed sane, xsane, hp3900-xxx(version 0.9) again I had the same problem as I had before when starting to get xsane running.

I got the following message in response to the command: scanimage -T

scanimage: open of device hp3900:libusb:005:003 failed: Access to resource has been denied

or by using xsane (response is in German, sorry):

Fehler beim Öffnen des Geräts 'hp3900:libusb:005:003': Zugang zum Gerät verweigert.

Reason for all this time consuming research work was very simple:

the usb device 005:003 did not have the right write permission - that is what to have to be changed!

the command ls -lR /dev/bus/usb/005/003 gives the following response:

0 crw-rw-r-- 1 root root 189, 514 2007-11-24 19:54 003

where we can see that there is no write permission set to others to this particular device (see the numbers in the above mentioned scanimage response, which directly gives us the needed infos to go further)

after changing this with:

sudo chmod 666 /dev/bus/usb/005/003 we can check it again

0 crw-rw-rw- 1 root root 189, 514 2007-11-24 19:54 003

...and voila - scanimage -L works and the scanner can be started with xsane properly without complaining. I hope it helps others too...

--------------

This works for one session ONLY! However it allows both XSane and Simple Scan to operate correctly, as far as I can tell. I had to open a terminal and lsusb 

Will someone reading this tell me how to make the chmod 666 persistent, please.

---

### Post by Mark_in_Hollywood on 2010-05-24
from the Brother Website that solved my scanner problems:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

Ubuntu 9.10, 10.04
1. Open "/lib/udev/rules.d/40-libsane.rules" file.
2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


The lines to be added---------------------------

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

---

### Post by Jolicoeur on 2011-09-23
> **Mark_in_Hollywood said:**
> from the Brother Website that solved my scanner problems:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

Ubuntu 9.10, 10.04
1. Open "/lib/udev/rules.d/40-libsane.rules" file.
2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


The lines to be added---------------------------

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

I know I should know this but how do I open up "/lib/udev/rules.d/40-libsane.rules" ? thanks also, do I need to download the drivers first?

---

### Post by F W Adams on 2012-02-07
I'm also got a similar problem. I'm using an HP4370, it's supported by xsane and has been working for years without any problem. Now I've come to use it again and its started replying "No devices found". It seems consistent and unplugging the usb, trying different usb, re-starting have no effect.

Also tried reading other threads and trying other things, reloading the driver. Have not succeeded in changing the symptoms in any way. Now I'm stuck.

sane-find-scanner is giving, together with the usual remarks
"found USB scanner (vendor=0x0543, product=0x0001, chip=RTS8822?) at libusb:001:004"

simple-scan -d -> "No scanners detected"

xsane -> "no devices available"

any ideas - thanks

---

