---
title: "Problem in connecting beagle board xm"
date: 2014-10-06
forum: Installation &amp; Upgrades
---

### Post by amit_2 on 2014-10-06
I need to connect beagle board to pc using usb for android development. But when i connect it doesn't get recognized by 'lsusb'. 
Whatever i have read about this, according to that it should get detected as a  ttyUSB*.  but its not shown by 'lsusb'. 
I have followed this post too..   [http://ubuntuforums.org/showthread.php?t=1325846](http://ubuntuforums.org/showthread.php?t=1325846). 
Its a 64bit linux.

Outputs are as follows-->

```
 lsmod | grep ftdi_sio
```
----> No output


```
sudo modprobe ftdi_sio
$ lsmod | grep ftdi_sio
```
output---->```
 
        ftdi_sio               48930  0 
        usbserial              45014  1 ftdi_sio
```


```
dmesg | grep -i ftdi
[19067.609686] usbcore: registered new interface driver ftdi_sio
[19067.609698] usbserial: USB Serial support registered for FTDI USB Serial Device
```

No output for ```
 lsusb | grep -i ft 
```

When i try to access using Putty with 192.168.7.2, it shows no route to the host!

---

### Post by amit_2 on 2014-10-08
Just changed the cable.. Got Serial to USB cable.

---

