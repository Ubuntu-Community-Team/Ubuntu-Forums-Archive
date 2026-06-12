---
title: "Driver Issues Belkin D7050e v5000uk"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by azexian on 2008-01-12
I was resonantly forced to change my old D7050 v4000 belkin card, for the above card, as it died, and the only thing the store had was the newer model, hoping it would be just as easy to use as the old one, I changed the old one, and took this one home, unfortunately there doesn't seem to be a driver for this listed anywhere on the web :(

```

$ lsusb -v | less

Bus 005 Device 008: ID 050d:705e Belkin Components 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components


```

I've tried the madwifi driver, the rt73 driver, ndiswrapper (which detected the device, but failed to connect to any networks) and the relink driver, I may be going wrong with one of these, so if anyone has had any success with any of these driver that would be good to know, I just can't find anyone with this device on the web, and I'm beginning to fear that it is unsupported.

---

### Post by macstyle@freeshells.ch on 2008-02-10
Hi,

I make it work with wpa and ndiswrapper driver from the cd, but  I got this error but I'm sure that i've got all better:

[  407.591761] wlan0: duplicate address detected!

If you want try with my cd driver let me know

ndiswrapper
utils version: 1.9
driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586 

lsusb
Bus 005 Device 002: ID 050d:705e Belkin Components

/etc/network/interface

auto wlan0
iface wlan0 inet static
address 192.168.178.7
netmask 255.255.255.0
gateway 192.168.178.1
wpa-psk your key
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid your ssid

---

### Post by steveth45 on 2008-03-02
The actual chipset for this version of the adapter (050d:705e) is Realtek's RTL8187B. I have the same adapter, and I took an existing driver (Johnny Cuervo's modified version of Realtek's modifications of an open source driver)  and added the proper USB id to make it work. Get it at my webpage: [http://steveth45.net/blog/?p=67]("http://steveth45.net/blog/?p=67"). I'm using it right now, so I can tell you that it works.

-steveth45

---

