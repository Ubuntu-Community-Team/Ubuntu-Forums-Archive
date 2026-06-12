---
title: "[SOLVED] 8.10 upgrade - loss of Wireless USB in 2.6.27-7-generic"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Insane_Homer on 2008-10-13
hi there,

Not sure if this is a know bug.

I took the plunge and updated my 8.04 installation to 8.10 beta yesterday. All went pretty smoothly however I lost my USB wireless device when using the 2.6.27-7-generic.

I saw a USB initialization error during the 1st 2 boot sessions, but only got the Ubuntu logo since then so not sure exactly what it was. If someone could point me to the relevant log file locations I'd be happy to dig them out.

All other USB devices appeared to be working fine (mouse, keyboard, printer and external HDD). I swapped the wireless card from the external USB card to the on board mobo without success.

I was able to boot into the 2.6.24-19-generic kernel and compile the driver for the wireless driver just fine (serialmonkey rt73) driver and initialize it just fine with the RutiLT(.18) application. I'm making this post right now via that connection and getting a strong 54MB connection.

The Mobo is **Asus M2A-VM HDMI, AMD 690G+SB600, HDMI, Socket-AM2,m-ATX,DDR2,Firewire,PCI-Ex16**

Wireless Card is **Linksys(Cisco) Compact Wireless G-USB Adapter - Model WUSB54GC**

---

### Post by Rocket2DMn on 2008-10-13
Moved to Intrepid Ibex Testing and Discussion.

---

### Post by paxmark1 on 2008-10-13
I dont know exactly what I did that got my Hawking WUSB54GC to work.  It stopped when I put the 8.10 beta on.  RTutilit would not work for me (I am in kubuntu, but it worked for me with 7.10 I know)  The serial monkey drivers (RT73) would not compile for me, they have in the past.  I loaded in some headers some way. I did not modify any black lists as I had in the past as told by serial monkey.  

But a few upgrades, and a reboot, and there it was up and finding neighbours (encrypted) wireless networks.  I unplugged it, as I am not using wireless presently.  So I can't tell you if WPA etc. works or not. Wish you luck.   

peace, mark

---

### Post by lonniehenry on 2008-10-13
Insane_Homer 
I am using the 2.6.27-7-generic kernel 64 bit with the linksys wusb54gc and it is just works.  It uses the rt73usb driver that is enabled in the kernel. Did you try blacklisting the wireless device that you had on the motherboard as it may still be trying to use it?

---

### Post by Insane_Homer on 2008-10-14
Hi, I got this one solved.

As said above (thanks) it appears the rt73usb driver is now properly supported in the new kernel.

to get it to work i had to open...

```
gksu gedit /etc/modprobe.d/blacklist

```

for the serialmonkey drivers to work I had.. (as per the serialmonkey installation instructions.)

```
blacklist rt73usb
```

All I did was change that to 

```
blacklist rt73
```

thus disabling the rt73 ? (not sure if this is the case or even necessary)
and re-enabling the rt73usb

network manager applet had to be re-enabled (RuTilT did not behave very nicely - it saw the network(s) but I was unable to enter the network key)

I entered the key ok and was online in no time!

Most notably connecting at 54Mb/s thus negating the need to serial monkey drivers!

YAY!

:popcorn:

---

