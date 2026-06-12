---
title: "New bluetooth applet (1.8)"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by olavjunior on 2008-10-08
Love the new applet and ability to add new devises. Very smooth compared to how it used to be. 

However, when I first tried the intrepid beta I was very pleased to see that it finally was possible to send files from my mobile to ubuntu initiated from the mobile! But now that feature is gone, and there ain't even options to select "accept incoming requests" ect like it used to be! Bring it back! 

Should I file a bug?

---

### Post by plun on 2008-10-08
Yup... file a bug.

bluez-network and bluez-serial seems to be complete broken.

"mission impossible" to connect to a cellphone (at least for me)

---

### Post by olavjunior on 2008-10-08
Yes, browse files works fine, but when clicking connect in preferences nothing happens. I just tried to figure out how to use Network Manager 0.7 to use my 3G phone to surf, but I guess that's no use then?

---

### Post by plun on 2008-10-08
> **olavjunior said:**
> Yes, browse files works fine, but when clicking connect in preferences nothing happens. I just tried to figure out how to use Network Manager 0.7 to use my 3G phone to surf, but I guess that's no use then?

NM 0.7 supports USB connected phones, not Blutooth, coming in next version.

You can use wvdial for that.
[https://wiki.kubuntu.org/NetworkManager/Hardware/3G/Probing](https://wiki.kubuntu.org/NetworkManager/Hardware/3G/Probing)

USB nevertheless works great with NM 0.7


I have tested with 2 different Sony Ericsson phones and no one is detected with blutooth...:confused:   Testing more....:)

**EDIT test ready....**

Lost bluez packages > reinstalled bluez..:tongue:

---

### Post by plun on 2008-10-08
Followup, bluez-network is broken

> The following packages are BROKEN:
  bluez 
The following NEW packages will be installed:
  bluez-network 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 40.7kB of archives. After unpacking 131kB will be used.
The following packages have unmet dependencies:
  bluez: Conflicts: bluez-network but 3.36-1ubuntu2 is to be installed.
The following actions will resolve these dependencies:

Remove the following packages:
bluetooth
bluez
bluez-utils



---

### Post by plun on 2008-10-10
Today it works after updates  :)

> plun@plun:~$ hcitool scan 
Scanning ...
	00:99:13:90:48:CA	Min


> 
plun@plun:~$ sdptool search --bdaddr 00:99:13:90:48:CA DUN
Searching for DUN on 00:18:13:90:48:CA ...
Service Name: Dial-up Networking
Service RecHandle: 0x10002
Service Class ID List:
  "Dialup Networking" (0x1103)
  "Generic Networking" (0x1201)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 2
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100

And so on from the probing wiki.....:)

---

### Post by _oOMOo_ on 2008-10-10
Hi plun, I don't seem to be able to pair my Sony Ericsson phone with my laptop at all with 2.6.27 - it works ok with 2.6.26

Are you still having problems or did you find a workaround?

Cheers, Jon

---

### Post by dngpng on 2008-10-10
The new bluetooth system seems fine when connecting my cellphone, but I don't know how to make it to automatically reconnect my BT mouse after reboot. For previous version I had the "HIDD_ENABLED = 1" in file /etc/default/bluetooth and it just worked, but the new version of that file doesn't contain that line, pluse there is no more hidd command in the system.

---

### Post by plun on 2008-10-10
> **_oOMOo_ said:**
> Hi plun, I don't seem to be able to pair my Sony Ericsson phone with my laptop at all with 2.6.27 - it works ok with 2.6.26

Are you still having problems or did you find a workaround?

Cheers, Jon

No you are right pairing is broken...

You can also use Blueproximity which somehow works.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=blueproximity](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=blueproximity)

USB with NM 0.7 works great.


This is the wiki and hopefully we also can nail this one....:)

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing](https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing)

Bluetooth must then be run with wvdial, no support within NM 0.7

---

### Post by dngpng on 2008-10-14
The new bluetooth system seems much different than before, anyone here who uses bluetooth mouse/kb can confirm the issue that the device doesn't get reconnect after reboot/idel like I experienced? 

It is already filed at [http://launchpad.net/bugs//249448](http://launchpad.net/bugs//249448)

---

### Post by solitaire on 2008-10-14
Have you installed "Bluetooth File sharing" program? it's different from Bluez group of software.

The Receiving files FROM mobile to Laptop did not work with Bluez alone but with the File shareing program it now works! :D

If you stick on "blue" into the quick search in Synaptic and added in all the bluetooth options not selected (there are a few!)

---

### Post by olavjunior on 2008-10-15
I've used the applet interface to add mouse  and headset, and they always get automatically connected between boots.

---

### Post by mihai.ile on 2008-10-22
so what happened to the old bluetooth applet? it had the option to start the service to recieve incomming files. Now I am unable to receive files from the mobile

How can I change to the old one? anyone filled a bug about this??

---

### Post by olavjunior on 2008-10-23
The possibility to receive files by sending from other devices is in the package "gnome-user-share". Install it and configure it in pref --> gnome-user-share

I'm having trouble with it though... What you can do to transfer a file from device to pc, is to "browse device".

---

### Post by mihai.ile on 2008-10-23
> **olavjunior said:**
> 
What you can do to transfer a file from device to pc, is to "browse device".

Wow and only if my mobile could give me access over bluetooth to the pictures, music, videos folders.... they are all empty, other folders are not.
That's why is important to be able to receive individual files sent from the mobile and not "being taken" from the mobile...

---

### Post by FuturePilot on 2008-10-23
> **mihai007 said:**
> so what happened to the old bluetooth applet? it had the option to start the service to recieve incomming files. Now I am unable to receive files from the mobile

How can I change to the old one? anyone filled a bug about this??

Try installing the "gnome-bluetooth" package. It should contain the gnome-obex-server service under Applications>Accessories>Bluetooth File Sharing

---

