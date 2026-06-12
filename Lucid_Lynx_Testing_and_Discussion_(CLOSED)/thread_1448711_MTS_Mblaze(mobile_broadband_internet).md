---
title: "MTS Mblaze(mobile broadband internet)"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ubun2warrior on 2010-04-07
Does MTS Mblaze(mobile broadband internet) work on lucid lynx ?? Someone please help ?

---

### Post by uRock on 2010-04-07
That was fast, they beat me to it. You should get better help here.:)

---

### Post by lisati on 2010-04-07
Moved to new thread

---

### Post by vishalrao on 2010-04-07
@ubun2warrior: do you have the device already? or planning to buy? from the pictures it looks like one of the known working devices similar to reliance's ones so should work either out of the box or after installing the usb-modeswitch (and related usb-modeswitch-data) package...

does google search not show up anything?

---

### Post by ubun2warrior on 2010-04-07
The device is a ZTE one and Ubuntu is not able to recognize the device. I have tried wvdial, gnome ppp also, but nothing works. I don't know much command line . The device  uses the following details: Username: [email]internet@internet.mtsindia.in[/email]
Password: MTS
Phone:      #777

I have already purchased the modem so guide me with this one please

---

### Post by vishalrao on 2010-04-07
Can you post the output of "lsusb" both before and after pluggnig in the device?

Also, does it "mount" a storage point with files in it? If so, you need to try the usb-modeswitch package or simply unmount it then run the modem setup (mobile broadband tab) via network manager...

---

### Post by ubun2warrior on 2010-04-12
Hi

This is the output of lsusb:
  	 	 	 	 	 	  Before Connecting
 Bus 002 Device 002: ID 1241:1503 Belkin Keyboard 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 

 After Connecting:
 Bus 002 Device 004: ID 19d2:fff1 ONDA Communication S.p.A.  
 Bus 002 Device 002: ID 1241:1503 Belkin Keyboard 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by GeorgeVita on 2010-04-13
Hi **ubun2warrior**, please try the following procedure:

>>> UPDATE your ubuntu using any other method (ethernet, wifi)

- boot without modem, **wait** for the system to load
- open a terminal window and try: **sudo dmesg -c**
this will show all system activity till then and will 'clear' this log. Next **dmesg** (without -c) will show only 'new' activity
- check kernel version (from terminal): **uname -a**
- attach modem
- **wait** 30-40 seconds
- from terminal: **dmesg**
- from terminal: **lsusb**
- from terminal: **ls /dev/ttyU***)

Post output of above commands EXCEPT from first 'sudo dmesg -c' as this is huge and without data for your modem!

Regards,
George

---

### Post by ubun2warrior on 2010-04-15
Hi GeorgeVita

These are the following outputs you asked for
dmesg output:-

[  393.268023] usb 4-1: new full speed USB device using uhci_hcd and address 2
[  393.432529] usb 4-1: configuration #1 chosen from 1 choice
[  393.508828] Initializing USB Mass Storage driver...
[  393.509999] scsi2 : SCSI emulation for USB Mass Storage devices
[  393.510245] usb-storage: device found at 2
[  393.510248] usb-storage: waiting for device to settle before scanning
[  393.510260] usbcore: registered new interface driver usb-storage
[  393.510265] USB Mass Storage support registered.
[  393.694391] usb 4-1: usbfs: USBDEVFS_CONTROL failed cmd usb_modeswitch rqt 128 rq 6 len 255 ret -71
[  393.695410] usb 4-1: usbfs: USBDEVFS_CONTROL failed cmd usb_modeswitch rqt 128 rq 6 len 255 ret -71
[  393.696526] usb 4-1: usbfs: USBDEVFS_CONTROL failed cmd usb_modeswitch rqt 128 rq 6 len 255 ret -71
[  393.744076] usb 4-1: USB disconnect, address 2
[  395.224035] usb 4-1: new full speed USB device using uhci_hcd and address 3
[  395.370019] usb 4-1: config 1 has an invalid interface number: 5 but max is 4
[  395.370024] usb 4-1: config 1 has no interface number 4
[  395.388531] usb 4-1: configuration #1 chosen from 1 choice
[  395.429193] scsi3 : SCSI emulation for USB Mass Storage devices
[  395.431036] usb-storage: device found at 3
[  395.431040] usb-storage: waiting for device to settle before scanning
[  400.429192] usb-storage: device scan complete
[  400.432176] scsi 3:0:0:0: Direct-Access     ZTE      USB Storage FFF1 2.31 PQ: 0 ANSI: 2
[  400.439480] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[  400.439583] sd 3:0:0:0: Attached scsi generic sg1 type 0

lsusb output:-

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 19d2:fff1  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ls /dev/ttyU* output:-
ls: cannot access /dev/ttyU*: No such file or directory

Regards

---

### Post by GeorgeVita on 2010-04-15
> **ubun2warrior said:**
> ...
[  395.429193] scsi3 : SCSI emulation for USB Mass Storage devices
[  395.431036] usb-storage: device found at 3
[  395.431040] usb-storage: waiting for device to settle before scanning
[  400.429192] usb-storage: device scan complete
[  400.432176] scsi 3:0:0:0: Direct-Access     **ZTE      USB Storage** FFF1 2.31 PQ: 0 ANSI: 2
[  400.439480] sd 3:0:0:0: [**sdb**] Attached SCSI removable disk
[  400.439583] sd 3:0:0:0: Attached scsi generic sg1 type 0

Hi **ubun2warrior**,
try again the procedure, check again the name of 'attached SCSI removable disk', above shown **sdb**. Eject it using the name that will appear (sdb or anything else):
```
sudo eject sdb
```
Wait some seconds, try again **dmesg** and **ls /dev/ttyU***

Post any 'better' result.
Also check the sticker on the modem's case to find the full model.

Regards,
George

---

### Post by ubun2warrior on 2010-04-16
Hi
On Ubunu 9.10 i installed USB- Modeswitch and restarted the computer. Then i went to network manager and creates new mobile broadband connection and its working(Wow!!!). 

But in Ubuntu 9.04 i tried the same thing and its not working.

 Thanks for all your help. 
Regards

---

### Post by hemant2007 on 2010-04-26
Please help 
on this issue I am facing the same problem
How can I connect to Internet via MTS MBLAZE ?

---

### Post by GeorgeVita on 2010-04-26
Hi **hemant2007**, welcome to this forum!

To use your 3g modem you need (most times) an update of ubuntu **9.10** using other connection (ethernet or wifi). After this update if you have any problem configuring your 3g post here your exact modem type (look sticker on it) to search for a solution.

To check your connection: update, boot without modem, wait for the system to fully load, attach modem, wait 30 seconds, click on network manager icon to configure (up right panel, beside volume control) 

Regards,
George

P.S. I suppose that you are using ubuntu 9.10 and not the beta/RC of Ubuntu 10.04 (if so it will help to open a new thread at [Networking & Wireless forum]("http://ubuntuforums.org/forumdisplay.php?f=336")
This is a ' Lucid Lynx Testing and Discussion' forum ...

---

### Post by alexfish on 2010-04-26
> **hemant2007 said:**
> Please help 
on this issue I am facing the same problem
How can I connect to Internet via MTS MBLAZE ?

Hi hemant2007

follow these steps

1. boot up the computer without the device,allow time for the system to settle approx 30s
2. connect the device ,give time for the device to settle
3. notice if  a device or cd or even a file appears on the desktop
4. check the Network Manager to see if you can make new connection , or if the device is recognised in the wizard , done through Mobile Broadband ADD. The box below the "create a connection for this mobile device "  may show your device . Make your connection.
5. if the box is blanked try right click with the mouse and eject the device that appeared on the desktop, goto 4

6 if the Network Manager fails to recognise the device try the usb modeswitch


[LIST]
[*][SIZE=1]Usb ModeSwitch Latest debian Package (1.1.2-1)
[/SIZE]
[*][SIZE=1]
[/SIZE]
[*][SIZE=1][http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)[Package  ]("http://packages.debian.org/sid/usb-modeswitch")[/SIZE]
[*][SIZE=1]save the file if you are having to use alternate os and internet
[/SIZE]
[*][SIZE=1]locate the file when in Ubuntu , will self install when double clicked[/SIZE]
[*][SIZE=1]Reboot the computer[/SIZE]
[*][SIZE=1]Check again with the Network Manager[/SIZE]
[/LIST]
7. if the network manager configures the device and all info is correct but fails to connect try wvdial or some prefer gnomeppp which is a front end to wvdial

some checks can be done through the terminal

to find usb device id's

Code:

lsusb

**dmesg** gives a lot of output so it is worth learning about the  grep command  and piping the output through  it. Piping is sending output from one command or program straight into  another and is done by the | . In this case the output from dmesg is  piped into the grep command which filters out all lines except those  containing modem.


Code:

dmesg | grep "modem"


will  just give you the lines including **modem**. You could also search  for lines with tty or modem by

Code:

dmesg | grep  -e "modem" -e "tty" 



that is a good start for finding a  built in modem which could be almost anywhere in the dmesg output, also will show the ports the device is using, and possibly which drivers have been loaded





**syslog:**  When you are doing initial checks it is very useful, to monitor the  main system log which is /var/log/syslog by use &#8216;tail -f  /var/log/syslog&#8217; (**in a separate  terminal**) to check real time that all the right things are  happening and what data has been transferred by the time the connection  is closed. This can also help identify what port has been allocated to a  device although the output is much more dificult to unscramble.


from a seperate terminal


Code:


tail -f /var/log/syslog


**tail** is a command  which outputs the last 10 lines of a file, with the -f option it  continues to monitor the file and keeps outputing any further additions  appended to the file in real time. 


regards 

alexfish

ADDED / pipped by GeorgeVitas/ while doing this post

also for further reading and note Sakis3g this is handy if you use "different devices" and the modeswitch resets the device IE the modeswich works with device A but can't use device B;reference Ubuntu 9.10

[http://ubuntuforums.org/showthread.php?t=1331660](http://ubuntuforums.org/showthread.php?t=1331660)

as said read before you commit

---

### Post by rajeev1204 on 2010-04-26
Here is what works for the TATA Photon device maybe it works for yours too.

But first , check if the usb device has a folder with instructions, teh photon comes with complete linux instructions (inst that great ) :)

First plug the device and let it be recognised as a  USB device, then unmount device.

Then wait 5 sec ,go to network manager icon and see if it appears there as a wireless connection.




rajeev

---

