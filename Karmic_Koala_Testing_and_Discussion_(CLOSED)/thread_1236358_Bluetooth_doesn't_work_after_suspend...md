---
title: "Bluetooth doesn't work after suspend.."
date: 2009-08-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lsrg on 2009-08-10
Hi everyone,
my bluetooth disappears before suspend. When I had this problem in jaunty I ran "sudo hid2hci" from a command line, but now in karmic hid2hci is in the udev rules.. 

My BT is from a Logitech Dinovo keyboard:
```
~$ lsusb
Bus 001 Device 003: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 020: ID 046d:c70c Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 004 Device 019: ID 046d:c70b Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 004 Device 018: ID 046d:0b02 Logitech, Inc. BT Mini-Receiver (HID proxy mode)
```

I don't know so much about udev rules, but I suppose that the rule in **/lib/udev/rules.d/70-hid2hci.rules** should run automatically when I plug the BT, but doesn't:

# Logitech devices
ATTR{idVendor}=="046d", ATTR{idProduct}=="c70[345abce]", RUN+="hid2hci --method logitech -v $attr{idVendor} -p $attr{idProduct} --mode hci"
ATTR{idVendor}=="046d", ATTR{idProduct}=="c71[34bc]", RUN+="hid2hci --method logitech -v $attr{idVendor} -p $attr{idProduct} --mode hci"

I have to run, every suspend or plug/unplug the BT, the command line:

```
~$ sudo /lib/udev/hid2hci --method logitech -v 046d -p c70c --mode hid

```

Where am I wrong?
How is the right form to do it?? 

Thanks.. 

lsrg

---

### Post by lsrg on 2009-10-06
hi to everyone interested...

I started to learn how udev rules work and discovered a very small bug in logitech bluetooth usb devices.

sudo vi /lib/udev/rules.d/70-hid2hci.rules

and change 
# Logitech devices (hidraw)
KERNEL=="hiddraw*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"

to 

# Logitech devices (hidraw)
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"

so much time for this small change, don't you think?

lsrg

---

