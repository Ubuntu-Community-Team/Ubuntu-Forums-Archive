---
title: "Gusty Bluetooth not working"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by nedmas on 2007-10-24
Hi i upgrade to gusty, and now i can't get the bluetooth to work properly.
I can successfully pair my phone nd computer however when it comes to establishing a connection or using a service i get all sorts of errors.

E.g when i use the Gnome Bluetooth Applet to browse->then connect i get told that "obex://[00:1c:a4c2:84:90]" is not a valid location. However hcitool says that it is the correct address for my phone!

I would appreciate any help or suggestions anyone has.
Thanx

---

### Post by SwiftNano on 2007-11-09
Hi,

I have the same problem and have not yet found a fix however I have found a article about a mouse connection problem which might be relevant but haven't had time to test. [Link]("http://ubuntuforums.org/showthread.php?t=582186") This artical suggest permission problems.

I also have an additional problem where my usb dongle is not recognised unless I restart Bluetooth.
i.e. sudo /etc/init.d/bluetooth restart
Has anyone else had this problem as I would like the device to be detected when ubuntu starts or when I plug the dongle in.

Any help is appreciated 

Thanks#

Swift

---

### Post by Spoker on 2007-12-01
Hello,
another post led me (I had the same problem) to the solution:

```
sudo apt-get install gnome-vfs-obexftp
```

---

