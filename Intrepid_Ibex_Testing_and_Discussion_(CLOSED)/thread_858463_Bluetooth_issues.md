---
title: "Bluetooth issues"
date: 2008-07-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MALEADt on 2008-07-13
Hi all,

Just switched to Intrepid, and next to a corrupt framebuffer & missing nvidia driver (known issues) the bluetooth stack seems to have gone awry. Neither the multisync/msynctool application nor the bluetooth file transfer panel (both OBEX based) function properly, while in both cases my phone just reports "Bluetooth connection failed".

Is somebody else suffering from this problem, or am I a lone case? If so, how the hell can I debug such a "burried" problem (can't really run a strace on the bluetooth stack).

(For the record, both syslog and kernel log stay clean on errors, and I've looked over existing bugs in launchpad's intrepid section)

---

### Post by wilbur.harvey on 2008-07-13
I notice that pand is no longer there, and I cannot connect using my T-Mobile Dash.

---

### Post by remedy on 2008-08-01
I have the same problem indeed, nc4010 HP laptop. No bluetooth at all working after upgrade to Intrepid Alpha 3. I added a bug in launchpad - see: [Bluetooth not working on Intrepid https://bugs.launchpad.net/bugs/254123]("Bluetooth not working on Intrepid https://bugs.launchpad.net/bugs/254123")

---

### Post by nystire on 2008-08-02
Slight problem with your link there...

---

### Post by peddy on 2008-10-06
Remains unfixed in Beta 1

---

### Post by anarki13 on 2008-10-08
i can confirm this as well. 

i get the error 
Method "CreateBluetoothSession" with signature "sss" on interface "org.openbox.Manager" does not exist

using Intrepid Beta 1.

---

### Post by peddy on 2008-10-10
I'm getting this from bluetooth apps:
```
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Method "ListServices" with signature "" on interface "org.bluez.Manager" doesn't exist
```

---

### Post by isecore on 2008-10-24
For what it's worth, I have this same experience. Upgraded my Hardy install to Intrepid just earlier today.

I have a Billionton (identified by Ubuntu as a Broadcom device so I guess it's a pretty generic one) USB dongle. Worked just fine in Hardy, but in Intrepid it's no go. 

This is what it's listed like in lsusb
```
Bus 003 Device 002: ID 0a5c:200a Broadcom Corp. Bluetooth dongle
```

EDIT: I discovered that if I restarted bluetooth, either through GUI or doing sudo /etc/init.d/bluetooth restart the icon would pop up. However, it seems to be only symbolically since I can't pair any devices or send/receive anything.

---

