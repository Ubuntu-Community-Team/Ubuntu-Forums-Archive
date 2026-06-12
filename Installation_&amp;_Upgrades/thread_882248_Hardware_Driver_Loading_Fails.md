---
title: "Hardware Driver Loading Fails?"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by MatthijsL on 2008-08-06
Installed Ubuntu today (as a dualboot system next to window XPhome) and well all seemed well until I pushed the time to restart after installation (i'm a real linux n00b) so at first my monitor says "mode not supported" after some friends help with tweaking grub (adding vga=791 in a commandline) it starts REALLY SLOW (takes about 6 min to start up) and i saw some errors flashing by.. so my friend advised me to make a post here and put this here aswell

[http://pastebin.ubuntu.com/34922/plain/](http://pastebin.ubuntu.com/34922/plain/)

it seems to be my emmn "Dmesg"

and this

[http://pastebin.ubuntu.com/34925/plain/](http://pastebin.ubuntu.com/34925/plain/) 
"lshw" ?

I hope anyone can help me with this, and tell what the problem actually is and what I can do to fix it. 

Thanks in Advance

---

### Post by spiderbatdad on 2008-08-06
can't tell for sure but it looks like it hangs trying to configure the wireless networking.

In the same way you edited /boot/grub/menu.lst to add vga=791, I suggest you delete quiet splash, so that you can see where it hangs during the boot process. It also looks like you might benefit from pci=routeirq...so the end of you kernel line would look like: ro pci=routeirq vga=791

There are some other messages I haven't seen before, but maybe the above will get your system booting more normally.

---

### Post by MatthijsL on 2008-08-07
I'm going to try that now then, I've also seen a message in the loading part (even with quiet splash in the kernel line) where it shows

[xx.xx.xx.xx] Loading Hardware Drivers [fail]

and a little bit further down the list (i've put 'x' on the place where numbers are don't remember what they were)

[xx.xx.xx.xx] Loading Bluetooth

The last one takes very very long and then it decides it has to show me a line with error in it and then continue. Thing is my pc doesn't even have bluetooth.:confused:

---

### Post by spiderbatdad on 2008-08-07
> **MatthijsL said:**
> I'm going to try that now then, I've also seen a message in the loading part (even with quiet splash in the kernel line) where it shows

[xx.xx.xx.xx] Loading Hardware Drivers [fail]

and a little bit further down the list (i've put 'x' on the place where numbers are don't remember what they were)

[xx.xx.xx.xx] Loading Bluetooth

The last one takes very very long and then it decides it has to show me a line with error in it and then continue. Thing is my pc doesn't even have bluetooth.:confused:

That definitely sounds like some boot options are required. Not sure which though. Commonly used are noapic, or noapic nolapic, your dmesg shows currently using local apic, I don't know if disabling it will help. 
In my dmesg, I get "apic disabled by bios try using lapic." so I use lapic as a boot option. You might have to play around with a few options to find what works best. maybe start with "ro noapic nolapic vga=791"

Hope you get it fixed. Mine looks like this "ro lapic pci=routeirq"

---

### Post by MatthijsL on 2008-08-07
[  179.029946] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x09 failed for offset 0x0000 with error -110.
[  181.537582] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0400 with error -110.
[  181.551345] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[  181.564957] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.

These are some of the lines that cause a hell of a lot of trouble aswell, I already got help from a friend with removing bluetooth and my dmesg looks like this now:

[http://pastebin.ubuntu.com/35058/plain/](http://pastebin.ubuntu.com/35058/plain/)

I'll try to experiment with your advice aswell, also as a reply on one of your previous posts. you mentioned it hangs trying to configure wireless networking. This might have something to do with having 2 wireless adapters in my pc one adapter in a pci slot and 1 usb adapter.

---

### Post by ThaRabbit on 2008-08-07
so 2 WiFi devices, and I understand you're using the USB one (broadcom chip).

From what I know, rt2x00 modules are buggy at best, if you're not using it you may try to blacklist the modules for this PCI wirless card you're not using:

```
sudo gedit /etc/modprobe.d/blacklist
```

At the bottom of this file, add these lines:
rt2x00usb
rt2x00lib
rt2x00pci

save and reboot

Let us know :)

If this does not resolve the issue, I would recommend trying the updated rt2x00 drivers as described here:
[http://ubuntuforums.org/showthread.php?p=5535920](http://ubuntuforums.org/showthread.php?p=5535920)

Or simply removing the PCI Wireless card, as it seems to be causing a lot of trouble when you're not using it ;)

---

### Post by MatthijsL on 2008-08-07
that didn't work... removing the pci card i thought was causing it resulted in not having internet so.. i pulled out the wireless usb adapter and bingo... i got rid of those 4 error lines. so i think any other problems i still have might be off-topic soo Thanks everybody :D

---

