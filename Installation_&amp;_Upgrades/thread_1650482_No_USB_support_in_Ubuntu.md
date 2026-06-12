---
title: "No USB support in Ubuntu"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by o2mcgovem on 2010-12-21
Hi, I've got an old laptop kicking around and my Gran has decided she wants it. It's a [Medion MIM2080]("http://www.techradar.com/reviews/pc-mac/laptops-portable-pcs/laptops-and-netbooks/medion-mim-2080-27036/specification"), the most horrific piece of tech I've ever encountered. My parents bought it me about eight years ago from Woolworths for cheap and I had to visibly hide my disappointment. I saved and upgraded to a Dell a year later.

Anyway, my Gran is probably perfect for Ubuntu. I wubi'd 10.10 and everything works (even suspend and wireless) except the USB ports. If I plug in a memory stick, camera or external CD-ROM drive, Ubuntu does nothing (though the peripheral may whirr). They work in Windows.

When I boot into Ubuntu, sometimes I catch a glimpse of some text mentioning USB after the boot screen has disappeared. My friend says this is relevant and might help people help me out.

Does anyone have any ideas? I don't really know where to begin with this one. I would post a log but I don't really know where to find one for this kinda thing. Any help would be much appreciated.

Thanks,
Michael.

P.S. Ubuntu works well with 3G "dongles", right? I'm assuming she'll buy a PAYG one to connect to the internet because she'll not use it too frequently.

---

### Post by davidmohammed on 2010-12-21
the spec in the link said 256GB - that's too small for 10.10 - you need a min of 1GB.  That may be a factor

in a terminal session can you reply with 

dmesg | grep usb

also

lspci

and

lsusb

n.b. the first reports how the kernel recognises your USB devices.

lspci reports what physical devices are connected
lsusb reports what usb devices are connected

use code tags in your reply for each copy and paste of the output.

---

### Post by o2mcgovem on 2010-12-21
Thanks for the speedy reply. It has 1GB of memory now, I upgraded it. 

Here's the stuff you asked for...

```

family@ubuntu:~$ dmesg | grep usb
[    0.163260] usbcore: registered new interface driver usbfs
[    0.163291] usbcore: registered new interface driver hub
[    0.163347] usbcore: registered new device driver usb
[    0.768177] usb 1-4: new high speed USB device using ehci_hcd and address 2
[   16.324073] usb 1-4: device not accepting address 2, error -110
[   16.436514] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   31.992072] usb 1-4: device not accepting address 3, error -110
[   32.104052] usb 1-4: new high speed USB device using ehci_hcd and address 4
[   42.536040] usb 1-4: device not accepting address 4, error -110
[   42.648045] usb 1-4: new high speed USB device using ehci_hcd and address 5
[   53.080094] usb 1-4: device not accepting address 5, error -110

```

```

family@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 CPU Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:06.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)

```

```

family@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Hope this is alright, Michael.

---

### Post by davidmohammed on 2010-12-21
scratching my head - lsusb is reporting no usb devices connected.  but the dmesg is reporting various usb errors...

have you any usb devices actually connected?

if so, please plug each one in turn - rerun the dmesg trace command.  Does the output change in any way or do you still see those errors?

Also, when plugging in each device, does lsusb change its output?

I have read that 10.10 has particular issues like yours with old slow speed usb devices connected in combination with standard "high" speed usb 2.0 devices.

---

### Post by o2mcgovem on 2010-12-21
Yeah I had my memory stick plugged in and it didn't seem to notice.

10.04 also had this problem, but I believe that 9.10 didn't. I have a Karmic CD somewhere that I could use to see if this is the case, if it'd help.

I plugged it into a different USB port and it's all the same. I then plugged in the external CD drive that came with the laptop (it has two USB leads, presumably because it needs more juice). When I did that, it changed and the memory stick now shows up in computer. Then the a message came up saying "Unable to mount Ubuntu 10.10 i386" already mounted or busy. I checked computer again, and the CD was there.

New code. 

```

family@ubuntu:~$ dmesg | grep usb
[    0.159250] usbcore: registered new interface driver usbfs
[    0.159281] usbcore: registered new interface driver hub
[    0.159339] usbcore: registered new device driver usb
[    0.763825] usb 1-4: new high speed USB device using ehci_hcd and address 2
[   16.316059] usb 1-4: device not accepting address 2, error -110
[   16.428140] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   32.004094] usb 1-4: device not accepting address 3, error -110
[   32.116125] usb 1-4: new high speed USB device using ehci_hcd and address 4
[   42.548099] usb 1-4: device not accepting address 4, error -110
[   42.660534] usb 1-4: new high speed USB device using ehci_hcd and address 5
[   53.092069] usb 1-4: device not accepting address 5, error -110
[  276.860203] usb 1-3: new high speed USB device using ehci_hcd and address 6
[  292.416149] usb 1-3: device not accepting address 6, error -110
[  292.528127] usb 1-3: new high speed USB device using ehci_hcd and address 7
[  308.084135] usb 1-3: device not accepting address 7, error -110
[  308.196125] usb 1-3: new high speed USB device using ehci_hcd and address 8
[  318.628163] usb 1-3: device not accepting address 8, error -110
[  318.740195] usb 1-3: new high speed USB device using ehci_hcd and address 9
[  329.172174] usb 1-3: device not accepting address 9, error -110
[  405.312110] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  406.392271] usb 3-1: not running at top speed; connect to a high speed hub
[  409.232162] usb 1-2: new high speed USB device using ehci_hcd and address 10
[  409.280243] scsi2 : usb-storage 3-1:1.0
[  409.284560] usbcore: registered new interface driver usb-storage
[  424.788123] usb 1-2: device not accepting address 10, error -110
[  424.900112] usb 1-2: new high speed USB device using ehci_hcd and address 11
[  440.456268] usb 1-2: device not accepting address 11, error -110
[  440.568157] usb 1-2: new high speed USB device using ehci_hcd and address 12
[  451.000197] usb 1-2: device not accepting address 12, error -110
[  451.112148] usb 1-2: new high speed USB device using ehci_hcd and address 13
[  461.544123] usb 1-2: device not accepting address 13, error -110
[  495.376122] usb 2-2: new full speed USB device using uhci_hcd and address 2
[  496.416180] usb 2-2: not running at top speed; connect to a high speed hub
[  499.227383] scsi3 : usb-storage 2-2:1.0
[  499.227885] usbcore: registered new interface driver ums-cypress
family@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 CPU Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:06.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)
family@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0951:1624 Kingston Technology 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

It takes a while, but I can open both. What's going on? :s :p

---

### Post by o2mcgovem on 2010-12-21
I unplugged the memory stick, ran lsusb to make sure it didn't still think it was plugged in, and then reinserted it. It doesn't show up in lsusb or computer.

---

### Post by davidmohammed on 2010-12-22
ok - with both no memory stick and no usb-cdrom connected (that is no usb devices connected) do you still get those dmesg error messages? - if you do, something else in the laptop is being recognised as a low speed usb device.  onboard webcam?

Can you disable any usb-devices through the bios?

---

### Post by o2mcgovem on 2010-12-22
Nope, no error message until I plug something in.

There's nothing in the BIOS either, it's really very basic.

Cheers for the help so far by the way :)

---

### Post by davidmohammed on 2010-12-22
... also just plugging in the CDROM you get the dmesg errors?

If you dont get the error message then maybe maverick is struggling with your memory stick.  

Do you have another USB device that you can plug-in? (preferably something quite recent that is USB 2.0 compatible)

---

### Post by davidmohammed on 2010-12-22
ok - think I found the bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/54273").  Reading through this, there are various suggestions you can try - hopefully one will work for you.

---

### Post by o2mcgovem on 2010-12-22
> **davidmohammed said:**
> ok - think I found the bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/54273").  Reading through this, there are various suggestions you can try - hopefully one will work for you.

Wow thanks :D. I've tried a couple and no luck so far. [Increasing the timeout]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/54273/comments/35") doesn't work, and the one line that fixes everything doesn't either: 

```

family@ubuntu:~$ sudo modprobe -r ehci_hcd
FATAL: Module ehci_hcd is builtin

```

There is no updated BIOS, the manufacturer doesn't seem to have a support page for this machine. 

I googled it to see what else I could find, but none of the solutions applied or helped. It seems that removing ehci_hcd removes USB 2.0 support, which I guess just means slower transfers. I don't really care about this, my Gran's gonna be using it and she's not going to be doing anything in a hurry I don't think. Is there another command to unload this module?

As an aside, do you think this problem will be present in other linux distributions? I've never tried another one but something like linux mint looks just as simple as Ubuntu.

---

### Post by davidmohammed on 2010-12-23
all ubuntu derived distros as far as I can see use the same/similar stock ubuntu kernel - so yes you'll most likely have the same issue.

Dont know about the fatal error message and how to remove.

I'm very surprised your bios doesnt have a "disable/enable legacy USB Support" option or similarly named.  Its a very very common bios option.

---

### Post by o2mcgovem on 2010-12-23
Aw man, gutted.

I know, the BIOS is really simple. Options are date/time, admin passowrd, POST beep, shared memory, wireless LAN and boot order.

Thanks for trying anyway, if I ever fix it I'll post back. Have a good Christmas (if you celebrate) :)

---

