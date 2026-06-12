---
title: "USB not recognized"
date: 2022-03-07
forum: Installation &amp; Upgrades
---

### Post by lassesj on 2022-03-07
Ubuntu (dmesg) shows an error upon connecting my external USB hdd

usb usb4-port4: config error
usb 3-4: new high-speed USB device number 5 using xhci_hcd

The port is working with other USB sticks and the external USB hdd is working when connected to a Windows machine.

What can I do to fix this?

---

### Post by TheFu on 2022-03-08
There might not be anything you can do, as support is completely dependent on the USB controller of the storage device.

Start by using **lsusb** to get the USB identifier and look up whether that is supported or not.  If it uses a proprietary driver that isn't available for Linux, return it to the place of purchase and get a more generic storage device.  This used to happen all the time about 10 yrs ago, when larger HDDs were just coming out.

With some hardware, there might need to be specific USB connection settings invoked.  Those are usually noted in the 'supported usb hardware' list and the option might force using a slower connection than your hardware claims.

In short, you'll need to become familiar with the specific chips used by both sides of the connection to see if there are any known compatibility issues.  For example, I had to apply a firmware update to a 7-port USB3 hub for it to work at USB3 speeds. The vendor was great and even offered to replace my new device for a used one, with the needed firmware, since I didn't/don't have Windows with a USB3 controller, necessary to apply the firmware.

After you get the USB identifier, you'll know if this is a minor issue, easily corrected, or something never gonna work because the vendor doesn't support Linux.

BTW, I hope you've already tried using a different USB cable and a different USB port into the computer. Try the simple things first.

---

### Post by ubfan1 on 2022-03-08
Is the USB HDD powered with a separate power supply?  Maybe not enough power to the device.  USB Y splitters were available to allow a device to be powered from two USB ports, but not sure how good that would be, depends upon the internal USB wiring if that actually supplies more power.

---

### Post by MAFoElffen on 2022-03-08
> **ubfan1 said:**
> Is the USB HDD powered with a separate power supply?  Maybe not enough power to the device.  USB Y splitters were available to allow a device to be powered from two USB ports, but not sure how good that would be, depends upon the internal USB wiring if that actually supplies more power.
Agreed.

I see this a lot. Especially if someone is trying to use a non-external powered USB hub... And overloading the power supplied by the USB port.

TheFu is also right, in that just because a USB device works with Windows and/or Mac, does not mean it has internal drivers for Linux. On USB devices, if it support MAC, then more likely to support Linux, but not a guaranty. I still find that even with some Laptop and Notepad internal devices (like fingerprint readers, and SmartCard Readers), that are on the USB bus, but do not have drivers that support Linux. 

What brand and model is the storage device?

---

### Post by TheFu on 2022-03-08
Good catch on the low-power issue. I've seen that, long ago.  I stopped buying USB-only powered HDD storage. I always get it with external power AND plug in that power.  Portable spinning disks tend to be really slow.  Flash and SSD storage is relatively cheap for a few hundred Gigs these days. Those can handle the low power AND speed we all want.  As soon as there are moving parts, the amps required drastically increase to just above the USB specs ability to provide power.

BTW, if using 2 USB adapters to feed power, be certain to have the 2nd plug on a different bus. Often the power limitation is per-bus, not just per-port.

---

### Post by mIk3_08 on 2022-03-09
> **ubfan1 said:**
> Is the USB HDD powered with a separate power supply?  Maybe not enough power to the device.  USB Y splitters were available to allow a device to be powered from two USB ports, but not sure how good that would be, depends upon the internal USB wiring if that actually supplies more power.

> **MAFoElffen said:**
> Agreed.
I see this a lot. Especially if someone is trying to use a non-external  powered USB hub... And overloading the power supplied by the USB port.
TheFu is also right, in that just because a USB device works with  Windows and/or Mac, does not mean it has internal drivers for Linux. On  USB devices, if it support MAC, then more likely to support Linux, but  not a guaranty. I still find that even with some Laptop and Notepad  internal devices (like fingerprint readers, and SmartCard Readers), that  are on the USB bus, but do not have drivers that support Linux. 
What brand and model is the storage device?

> **TheFu said:**
> Good catch on the low-power issue. I've seen that,  long ago.  I stopped buying USB-only powered HDD storage. I always get  it with external power AND plug in that power.  Portable spinning disks  tend to be really slow.  Flash and SSD storage is relatively cheap for a  few hundred Gigs these days. Those can handle the low power AND speed  we all want.  As soon as there are moving parts, the amps required  drastically increase to just above the USB specs ability to provide  power.
BTW, if using 2 USB adapters to feed power, be certain to have the 2nd  plug on a different bus. Often the power limitation is per-bus, not just  per-port.

I totally agree with you guys. I also experience this kind of issue but I resolve this issue then. My external SSD installed to a USB external enclosure works smoothly now without any errors and failures. regards.

---

