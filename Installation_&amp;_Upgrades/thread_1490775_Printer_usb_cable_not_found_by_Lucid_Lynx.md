---
title: "Printer usb cable not found by Lucid Lynx"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by cornelis spronk on 2010-05-22
I have upgraded from 9.04 to 10.04.  9.04 found my usb connected printer ( LaserJet 6MP) with no problems.  But 10.04 will not find the usb port to which my printer is connected.

I have searched for a solution on the forum, and others seem to have a similar problem, but not recognized it.  For some it seemed to have self corrected, but I am having no such luck.

I have downloaded **hplip** from

[http://hplip.sf.net/](http://hplip.sf.net/)

Following their instructions, I have run "hp-setup" in Terminal.  This gives the following output:

```
cs@cs-desktop:~$ hp-setup

HP Linux Imaging and Printing System (ver. 3.10.5)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb

```

After disconnecting and reconnecting the printer cable, I used the command "dmseg| tail"

Terminal output:

```
s@cs-desktop:~$ dmesg | tail
[  263.646972] Buffer I/O error on device fd0, logical block 0
[  301.759023] end_request: I/O error, dev fd0, sector 0
[  301.759033] Buffer I/O error on device fd0, logical block 0
[  339.871189] end_request: I/O error, dev fd0, sector 0
[  339.871199] Buffer I/O error on device fd0, logical block 0
[  349.600055] usb 2-1: USB disconnect, address 2
[  349.600258] usblp0: removed
[  361.712024] usb 2-1: new full speed USB device using uhci_hcd and address 3
[  361.869251] usb 2-1: configuration #1 chosen from 1 choice
[  361.884062] usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x050D pid 0x0002
```

I interpret this to mean that the printer is seen from this command.  Yet when I do the "lsusb" command, I get this output:

```
s@cs-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 050d:0002 Belkin Components 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

This to me indicates that the printer is not seen by the "lsusb" command.

I hope this might clarify the problem, but it does not solve it.  I would like to get my printer printing.

I am trying to get hold of an older parallel Centronics printer cable with a DB25 at the other end to see if I can get the printer working with it.  Have others done this with success?

---

### Post by davidmohammed on 2010-05-22
you'll notice that lsusb is infact finding the "printer" - its named "belkin" - it has the same id (050d) as in your dmesg trace.

However - I've never heard of such a device - so, like you - confused.

Maybe your printer has been blacklist for some reason - can't think why though.  Sorry for not being more helpful.

---

### Post by davidmohammed on 2010-05-22
ok now understand - you are using some sort of usb to parallel converter - correct?

The Laserjet 6MP driver is installed by default in lucid - what happens if you add the driver manually via administration - printing?

---

### Post by Sef on 2010-05-22
> I have upgraded from 9.04 to 10.04.

If you have upgraded directly from 9.04 to 10.04 that would be the reason for the problems that you are having now.  The [proper way to upgrade]("https://help.ubuntu.com/community/UpgradeNotes") is to the next distro: 9.04 -> 9.10 -> 10.04.  Note: LTS to LTS upgrades are proper.

---

### Post by cornelis spronk on 2010-05-24
Thanks to all that replied.

To clarify--I did a fresh installation of 10.04 from an .iso disk I burned.  The installation seemed to go without a problem.  Everything else works fine.

About 8 weeks ago I did a fresh install of the 10.04 Beta version.  I was pleased with it, as everything worked fine, except the printing. I assumed that it would be fixed by April 29, the official release.  I went back to a fresh install of 9.04, and the printer worked fine.

I have several times done a fresh install of 9.10, but it always gave me a problem with stuttering sound at all positions of the volume levels.   This I could not tolerate, as I like to listen to BBC iPlayer.  The 10.04 stutters at some points of the volume levels, but with a little fiddling, the stuttering can be controlled.

The cable I am using has a Centronics plug at the printer end and a usb plug at the motherboard end.

I did the **System-->Administration-->Printing** and tried various options in the pop up window. The options are: Parallel, serial, and network printers.  There is no usb choice. I cannot remember what choice I made when using 9.04.

---

### Post by cornelis spronk on 2010-05-24
Just after I posted, I was contemplating post #2.  I then tried unplugging all the usb cables and reconnecting them one at a time, and I discovered that the cable connected to the printer shows up as "Belkin components".  

I am surprised at this, as I am unaware that the cable contains any electronics.

If there is electronics in the cable, does this cable not work as a regular serial port connection?

---

### Post by davidmohammed on 2010-05-24
this [thread]("http://ubuntuforums.org/showpost.php?p=8618480&postcount=15") sounds like your situation - does it resolve your problem?

---

### Post by cornelis spronk on 2010-05-24
Excellent!  It works!!  

Thanks.

---

### Post by davidmohammed on 2010-05-24
... good news - dont forget to mark this thread as solved

---

### Post by cdw on 2010-05-24
Trying to install brother printer via usb on Lynx.

System->Admin->Printing brings up a window: Printing-local host in which all "new" items are greyed out: no printers are recognized automatically.

Any hints as to how to get the system to "see" my printer?  
it is seen by lsbusb:

lsusb
Bus 006 Device 002: ID 046d:c526 Logitech, Inc. MX Revolution Cordless Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04b8:0110 Seiko Epson Corp. Perfection 1650
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 04f3:0a11 Elan Microelectronics Corp. 
Bus 001 Device 006: ID 0566:3108 Monterey International Corp. 
Bus 001 Device 005: ID 0566:3021 Monterey International Corp. 
Bus 001 Device 002: ID 04f9:0039 Brother Industries, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by davidmohammed on 2010-05-24
> **cdw said:**
> Trying to install brother printer via usb on Lynx.

System->Admin->Printing brings up a window: Printing-local host in which all "new" items are greyed out: no printers are recognized automatically.

Any hints as to how to get the system to "see" my printer?  
it is seen by lsbusb:

lsusb
Bus 006 Device 002: ID 046d:c526 Logitech, Inc. MX Revolution Cordless Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04b8:0110 Seiko Epson Corp. Perfection 1650
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 04f3:0a11 Elan Microelectronics Corp. 
Bus 001 Device 006: ID 0566:3108 Monterey International Corp. 
Bus 001 Device 005: ID 0566:3021 Monterey International Corp. 
Bus 001 Device 002: ID 04f9:0039 Brother Industries, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

... please can you start a new thread...

---

### Post by cornelis spronk on 2010-05-24
This is a the step by step method I used on Ubuntu 10.04 which is a little different from the steps in the thread that David identified in a previous post.  I tried to make it simple, so that Newbies can follow it.

1. On top line click through **System-->Administration-->Printing**
2. A **'Printing - localhost'** box shows up.  Click in **'Add'**.  A **'New Printer'** box shows up. Leave the choice on **'LPT #1'** and click on **'Forward'**.
3. Select your printer driver from the database by scrolling down through the boxes.  The database is large and your printer most likely will be there.  After making your choices, step forward till you get the the **'Describe Printer'** box.  Then click the **'Apply'** button.
4. A box shows up asking you to **'Print a test page'**.  Choose **'No'** at this time.  This is the most important step, as Ubuntu will not find your usb connection until you do the next step.
5. Go back to the **'Printing - localhost'** box and **right-click** on the printer icon you have selected in step 3.  Then choose **'Properties'** and new box will appear showing Printer Settings.  In this box the Device URI code must be modified.
6. Device URI code shows up as **'parallel:/dev/lp0'**.  Click the **'Change'** button.  Edit the Device URI to become **'parallel:/dev/usb/lp0'**.  Click the **'Apply'** button.  Now Ubuntu 10.04 will find your parallel connected printer on a USB port. 
7. Now click the **'Print Test Page'** button.  Your printer should go into action.  

If it now prints, you are done.  

Good Luck!  It's all a learning experience.

---

### Post by bra|10n on 2010-05-26
Well I followed the steps in the post immediately above this one one and managed to list my printer as HP-Deskjet-f4100. I have changed **'parallel:/dev/lp0'** to **'parallel:/dev/usb/lp0' **and restarted but printing of a test page says printer not connected. I have uninstalled/reinstalled hplib & hpijs without success either. As others have done I post the following ```
bra10n@bra10n-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bra10n@bra10n-desktop:~$ 

``````
bra10n@bra10n-desktop:~$ dmesg | grep -i usb
[    0.112197] usbcore: registered new interface driver usbfs
[    0.112217] usbcore: registered new interface driver hub
[    0.112251] usbcore: registered new device driver usb
[    0.259083] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.259183] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.287980] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.288135] usb usb1: configuration #1 chosen from 1 choice
[    0.288176] hub 1-0:1.0: USB hub found
[    0.288274] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.288297] uhci_hcd: USB Universal Host Controller Interface driver
[    0.288417] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.288562] usb usb2: configuration #1 chosen from 1 choice
[    0.288598] hub 2-0:1.0: USB hub found
[    0.288724] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.288854] usb usb3: configuration #1 chosen from 1 choice
[    0.288891] hub 3-0:1.0: USB hub found
[    0.289007] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.289156] usb usb4: configuration #1 chosen from 1 choice
[    0.289192] hub 4-0:1.0: USB hub found
[    0.289327] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.289472] usb usb5: configuration #1 chosen from 1 choice
[    0.289509] hub 5-0:1.0: USB hub found
bra10n@bra10n-desktop:~$ 

```This is a clean install of 10.04 which correctly detected my printer prior to installing any updates...
Cups has been restarted also. Any suggestions?

Found the following in xsession-errors if it helps diagnosis...

Caught non-fatal exception.  Traceback:
File "/usr/share/system-config-printer/system-config-printer.py", line 2019, in setDataButtonState
    self.printer.enabled and
AttributeError: 'NoneType' object has no attribute 'enabled'
Continuing anyway..
Caught non-fatal exception.  Traceback:
File "/usr/share/system-config-printer/system-config-printer.py", line 2019, in setDataButtonState
    self.printer.enabled and
AttributeError: 'NoneType' object has no attribute 'enabled'
Continuing anyway..

---

### Post by dino99 on 2010-05-26
sudo update-pciids && update-usbids 

search pmount and usbmount into synaptic, remove/purge the package then reinstall 

goto: system prefs "prefered apps at startup" or so, and check printer


and reboot

---

### Post by bra|10n on 2010-05-26
pmount and usbmount weren't installed so I installed them...

```
bra10n@bra10n-desktop:~$ sudo update-pciids && update-usbids
[sudo] password for bra10n: 
Downloaded daily snapshot dated     2010-05-10 03:15:02
touch: cannot touch `/var/lib/usbutils/usb.ids': Permission denied
/var/lib/usbutils/usb.ids is read-only, exiting.
```

---

### Post by dino99 on 2010-05-26
sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a

---

### Post by bra|10n on 2010-05-26
> **dino99 said:**
> sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a

I did this then tried the previous command, with still the same error
```
bra10n@bra10n-desktop:~$ sudo update-pciids && update-usbids
[sudo] password for bra10n: 
Downloaded daily snapshot dated     2010-05-10 03:15:02
touch: cannot touch `/var/lib/usbutils/usb.ids': Permission denied
/var/lib/usbutils/usb.ids is read-only, exiting.

```If it helps xsession-errors is now clear of any printing related issues

Update: This has to be more a usb problem after finding this, yes?
bra10n@bra10n-desktop:~$ lpstat -p -d
printer HP-Deskjet-f4100 is idle.  enabled since Wed 26 May 2010 18:49:12 EST
    Printer not connected; will retry in 30 seconds...
system default destination: HP-Deskjet-f4100

---

### Post by bra|10n on 2010-05-28
> **bra|10n said:**
> I did this then tried the previous command, with still the same error
```
bra10n@bra10n-desktop:~$ sudo update-pciids && update-usbids
[sudo] password for bra10n: 
Downloaded daily snapshot dated     2010-05-10 03:15:02
touch: cannot touch `/var/lib/usbutils/usb.ids': Permission denied
/var/lib/usbutils/usb.ids is read-only, exiting.

```If it helps xsession-errors is now clear of any printing related issues

Update: This has to be more a usb problem after finding this, yes?
bra10n@bra10n-desktop:~$ lpstat -p -d
printer HP-Deskjet-f4100 is idle.  enabled since Wed 26 May 2010 18:49:12 EST
    Printer not connected; will retry in 30 seconds...
system default destination: HP-Deskjet-f4100

Indeed my problems were of a USB kind... "un seated board" ;)

---

### Post by johnfrith on 2010-08-05
> **dino99 said:**
> sudo update-pciids && update-usbids 

search pmount and usbmount into synaptic, remove/purge the package then reinstall 

goto: system prefs "prefered apps at startup" or so, and check printer


and reboot

Produced:
```
john@jf:~$ sudo update-pciids && update-usbids 
[sudo] password for john: 
Downloaded daily snapshot dated     2010-07-14 03:15:03
touch: cannot touch `/var/lib/usbutils/usb.ids': Permission denied
/var/lib/usbutils/usb.ids is read-only, exiting.
```Samsung ML4500 Parallel printer on USB port only worked under Karmic by using URI of: parallel:/dev/usb/lp0
On upgrading to Lucid, printer worked after deleting and re-installing printer in System > Printing. Than after upgrade today, system says "printer may not be connected".

```
john@jf:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 5986:0241 Acer, Inc 
Bus 002 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``````
john@jf:~$ dmesg | tail -n10
[   29.864166] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   40.412010] wlan0: no IPv6 routers present
[   54.985999] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[   91.541130] __ratelimit: 9 callbacks suppressed
[   91.541133] type=1503 audit(1281041070.652:15):  operation="open" pid=1039 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
[   91.541153] type=1503 audit(1281041070.652:16):  operation="open" pid=1039 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
[  108.031800] type=1503 audit(1281041087.139:17):  operation="open" pid=1039 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
[  108.031816] type=1503 audit(1281041087.139:18):  operation="open" pid=1039 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
[  118.430298] type=1503 audit(1281041097.539:19):  operation="open" pid=1039 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
[  118.430314] type=1503 audit(1281041097.539:20):  operation="open" pid=1039 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
```Any help appreciated. You can help the environment if you can help me figure this out, as I won't have to throw it away!

---

