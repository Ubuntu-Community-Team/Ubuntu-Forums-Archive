---
title: "/proc/bus/usb Missing"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by gdesilva on 2010-03-17
Hi, 

I had Ubuntu Desktop 9.10 installed successfully and had Plextor USB capture device working properly.

I recently upgraded to Ubuntu Studio 9.10 and now find that I can no longer use Plextor device as it requires usbfs mounted on /proc/bus/usb. When I checked I found that /proc/bus/usb directory has disappeared and hence the usbfs mount fails. I have no problems with other USB devices however.

Any suggestions will be greatly appreciated.

Did a bit more checking....the problem started with the 2.6.31.20-generic-pae upgrade. When I boot into 2.6.31.19-generic-pae the /proc/bus/usb directory appears!

---

### Post by sbrendtro on 2010-03-18
The folder /proc/bus/usb is part of usbfs.  Because of conflicts with udev, newer Ubuntu kernels come with usbfs disabled.  Your basic options are:

1.  Use an older kernel (2.6.31.17 or 2.6.31.18 for instance).
2.  Compile your own kernel with usbfs enabled (not going to go into how you do that exactly, as the info is available simply by searching Google for "ubuntu compile kernel usbfs").

Hope that helps!
Steve

---

### Post by gdesilva on 2010-03-18
Thanks for the response Steve, I will give it a try.

---

### Post by gdesilva on 2010-03-19
It appears that the same problem has occurred with earlier versions of the 64bit OS. As Steve mentioned with later versions of kernel /proc/bus/usb will not be available. However, a workaround of sorts for this has been already found [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507824](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507824) 

The solution is as follows;

[COLOR=Red]It is not a long term solution, but I found another solution, for getting /proc/bus/usb back again and no need for usbfs.

First I put my user to sudoers for /bin/mount and /bin/umount
Then I changed my scanner script to do the magic.

Before running my scanner the script will do:
sudo mount --bind /dev/bus /proc/bus

while on exit of the script it fires the command:
sudo umount -l /proc/bus

mount --bind /dev/bus /proc/bus or
mount --bind /dev/bus/usb /proc/bus/usb
will make /proc/bus/usb accessible /proc/bus/usb for some hardware (although this will cause the other directories under /proc/bus to be hidden). So you should umount again, after use.
[COLOR=Black]
It is a reasonable workaroud and worked fine for me. Just should make sure to unmount after using the device otherwise /proc/bus/pci and /proc/bus/input etc gets hidden![/COLOR]
[/COLOR]

---

