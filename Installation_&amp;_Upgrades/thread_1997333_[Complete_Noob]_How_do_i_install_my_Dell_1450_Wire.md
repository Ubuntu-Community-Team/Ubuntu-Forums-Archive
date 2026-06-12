---
title: "[Complete Noob] How do i install my Dell 1450 Wireless Adapter?"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by Xtract01 on 2012-06-05
Hello everyone :)!

I recently moved from windows vista -.- to the almighty Ubuntu! I love the theme, I'm falling in love with everything.

However, I have a dell 1450 wireless adapter that won't work on here as i have no clue on how to install the drivers off the CD i have. I've looked at other threads in this forum and still i can't find my answer. It works on windows vista, i just need guidance on how to install drivers off a CD .
Any help is really appreciated.
Thanks everyone :)!

P.S: I'm using a hideous long grey wire that runs through my house to my modem.:(

---

### Post by carl4926 on 2012-06-05
We need to be sure what device you have.
Open a terminal and post the result of

```
lspci -nnk | grep -iA2 net
```

---

### Post by Xtract01 on 2012-06-05
> **carl4926 said:**
> We need to be sure what device you have.
Open a terminal and post the result of

```
lspci -nnk | grep -iA2 net
```

Hey, :) Here are the results:

04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5786 Gigabit Ethernet PCI Express [14e4:169a] (rev 02)
    Subsystem: Lenovo Device [17aa:1015]
    Kernel driver in use: tg3

---

### Post by carl4926 on 2012-06-05
Is that all the info you got? 

1. Because it's only the Wired connection info
2. It's a Lenovo product ref and you quoted a Dell machine?

---

### Post by efflandt on 2012-06-05
What does **lspci** in a terminal show for your wireless device?  Dell laptops I have seen in the past typically used Broadcom wireless.

With that long cable connected, see if Additional Drivers shows one or more drivers for it.  If it is a Broadcom one or the other should work (you cannot activate both at the same time).  When you activate one it will load from the internet.  Not sure if you might need to reboot.

Then with the wired internet unplugged, see if you get sort of a radiating wireless icon where the double arrows were for ethernet.  If that driver does not work, Deactivate that one and Activate the other one.  If you do get one of them showing the wireless icon, you should be able to right click that icon and select your wireless router, and then enter its wireless security settings.

---

### Post by Xtract01 on 2012-06-05
> **carl4926 said:**
> Is that all the info you got? 

1. Because it's only the Wired connection info
2. It's a Lenovo product ref and you quoted a Dell machine?

Yes, that was everything that popped up. I'm using a lenovo pc.


I'm having trouble with the installing drivers for the Dell 1450 wireless adapter (Image below)
[http://i.ebayimg.com/00/s/NDg1WDQ5Ng==/$%28KGrHqVHJE4E88eUSnL7BPW2GVzqmQ~~60_35.JPG]("http://i.ebayimg.com/00/s/NDg1WDQ5Ng==/$%28KGrHqVHJE4E88eUSnL7BPW2GVzqmQ%7E%7E60_35.JPG")

---

### Post by Xtract01 on 2012-06-05
> **efflandt said:**
> What does **lspci** in a terminal show for your wireless device?  Dell laptops I have seen in the past typically used Broadcom wireless.

Hello :). I typed** lspci** into the terminal.
Here are the results : 

00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82946GZ/PL/GL PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5786 Gigabit Ethernet PCI Express (rev 02)

---

### Post by carl4926 on 2012-06-05
Is that connected via USB?

---

### Post by carl4926 on 2012-06-05
what do you get from

```
lsusb
```

---

### Post by Xtract01 on 2012-06-05
> **carl4926 said:**
> what do you get from

```
lsusb
```

I typed lsusb into the terminal :).
Here are the results : 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 413c:8104 Dell Computer Corp. Wireless 1450 Dual-band (802.11a/b/g) Adapter [Intersil ISL3887]
Bus 001 Device 005: ID 054c:01bd Sony Corp. MRW62E Multi-Card Reader/Writer
Bus 002 Device 002: ID 04b3:310c IBM Corp. Wheel Mouse
Bus 002 Device 003: ID 04b3:301a IBM Corp. 
Bus 002 Device 004: ID 04b3:301b IBM Corp. SK-8815 Keyboard

---

### Post by carl4926 on 2012-06-05
Doesn't the Additional Drivers offer to install anything?

---

### Post by Xtract01 on 2012-06-05
> **carl4926 said:**
> Doesn't the Additional Drivers offer to install anything?

No it doesn't :confused:.

---

### Post by carl4926 on 2012-06-05
Might be time to invest in a USB device that works out of the box
I can point you to one, less than $10 or £10 depending where you are?

---

### Post by Xtract01 on 2012-06-05
> **carl4926 said:**
> Might be time to invest in a USB device that works out of the box
I can point you to one, less than $10 or £10 depending where you are?

I have a cd containing the drivers for the adapter. Would this help you, help me??

Here's a screenshot i took of the driver i can't install myself : 
[http://tinypic.com/r/qsl4w0/6](http://tinypic.com/r/qsl4w0/6)

---

### Post by sanderj on 2012-06-05
Google " ID 413c:8104 Dell Computer Corp. Wireless 1450 Dual-band " ... which will give hints, among which [http://ubuntuforums.org/archive/index.php/t-1818988.html](http://ubuntuforums.org/archive/index.php/t-1818988.html) saying 

> Hi, connect to your wired internet connection then try this please.
sudo apt-get install linux-firmware-nonfree
 

HTH

---

### Post by carl4926 on 2012-06-05
that's an .rpm
you need .deb

---

### Post by Xtract01 on 2012-06-05
> **carl4926 said:**
> that's an .rpm
you need .deb

Oh, ok. :\ Darn.

---

### Post by Xtract01 on 2012-06-05
> **sanderj said:**
> Google " ID 413c:8104 Dell Computer Corp. Wireless 1450 Dual-band " ... which will give hints, among which [http://ubuntuforums.org/archive/index.php/t-1818988.html](http://ubuntuforums.org/archive/index.php/t-1818988.html) saying 

 

HTH

I already tried that with no success. :\

---

### Post by carl4926 on 2012-06-05
> **Xtract01 said:**
> I already tried that with no success. :\

Are you sure?

Anyway, this device will work
[http://www.ebuyer.com/149672-tenda-wireless-n150-usb-adapter-w311u](http://www.ebuyer.com/149672-tenda-wireless-n150-usb-adapter-w311u)

Look around wherever you live in the world. ebay is everywhere.

---

### Post by Xtract01 on 2012-06-05
> **carl4926 said:**
> Are you sure?


That are you sure? Made me think.

Restarted my PC...

MAGIC! :guitar: It's working now.. Thank you all!!!

---

