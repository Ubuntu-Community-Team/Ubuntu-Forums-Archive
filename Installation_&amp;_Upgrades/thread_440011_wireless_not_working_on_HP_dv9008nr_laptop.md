---
title: "wireless not working on HP dv9008nr laptop"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by challman on 2007-05-11
I've installed 7.04 on a desktop (x86) and a laptop (amd64). The desktop wireless is working after configuring /etc/network/interfaces (it's using a Trendnet PCI card). My HP laptop has been driving me nuts. I can't get it to work. Here's my hardware specs:

1.6 GHz AMD Turion™ 64 X2 Dual-Core Mobile Technology TL-50 2 X 256KB L2 Cache
1024MB DDR2 System Memory (2 Dimm)
NVIDIA GeForce Go 6150 (UMA) up to 128MB (shared)
100GB 5400RPM (SATA)
LightScribe SuperMulti 8X DVD±RW with Double Layer Support
17.0” WXGA+ High-Definition BrightView Widescreen Display (1440 x 900)
High speed 56k modem
Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)
802.11b/g WLAN

Here's some info I think you'll need to help me:

chris@dv9008nr:~$ lspci | grep Bro
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
chris@dv9008nr:~$ lsusb
Bus 002 Device 002: ID 046d:c518 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
chris@dv9008nr:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

chris@dv9008nr:~$ modprobe -l | grep ndis
/lib/modules/2.6.20-15-generic/kernel/drivers/usb/net/rndis_host.ko
/lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
chris@dv9008nr:~$ ndiswrapper -l
bcmwl6 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)
chris@dv9008nr:~$ ndiswrapper -v
utils version: 1.9
driver version:        1.42
vermagic:       2.6.20-15-generic SMP mod_unload
chris@dv9008nr:~$ more /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:36:8b:87:31 arp 1
#eth1 mac 00:14:a5:ea:50:7f arp 1
wlan0 mac 00:14:a5:ea:50:7f arp 1
chris@dv9008nr:~$ more /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-keymode open
wireless-channel 11
wireless-key s:1qaz2wsx3edc4
wireless-essid PrivateNetwork
wireless-mode managed
chris@dv9008nr:~$ more /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
blacklist bcm43xx

# drivers wireless ACX
#blacklist acx
blacklist ndiswrapper
chris@dv9008nr:~$


Any assistance would be helpful and greatly appreciated!!!

---

### Post by challman on 2007-05-17
"Help me! Help me, Spock!"

---

### Post by IgnorantGuru on 2007-05-17
Have you done a search on howto's for Broadcomm?  On my HP laptop, I didn't have any luck with the stock driver.  Here's what worked for me... my notes on how I finally did it (blindfolded and drunk)...

```

Method using ndiswrapper				[SUCCESS]
	http://www.ubuntuforums.org/showthread.php?t=285809

	#Disable kernel driver
	pico /etc/modprobe.d/blacklist
		Add line:  blacklist bcm43xx

	install ndiswrapper-utils

	#Obtain original bcmwl5.sys and .inf driver from Windows folder or HP CD or elsewhere
	ndiswrapper -i bcmwl5.inf
	ndiswrapper -l
		Should return driver and hardware present
	pico /etc/modules
		Add line:  ndiswrapper
		#This causes kernel to load ndiswrapper automatically, otherwise use modprobe ndiswrapper

	#Reboot - eth1 should now be present and working

```

Also note that if you're using x64 Ubuntu, I don't know if HP has 64 bit drivers.  That prevented me from using the 64 bit version of SUSE with this wireless card, but that was many months ago.  I haven't looked recently.

---

### Post by IgnorantGuru on 2007-05-17
Also, perhaps painfully obvious, but on my NX6125 there is a button to activate wireless (lan and bluetooth combined).  If the blue light isn't on, the wireless card won't work.  I assume you know this if your model has it, but just in case.  You said "any help".  :)  Forgetting the blue light has had me pulling my hair more than once.

---

### Post by challman on 2007-05-18
Thanks. The slide switch for wireless is definitely on, however the light is amber. Therefore, I assume the driver isn't loading properly? I does go blue while the OS is loading but then goes back to amber. I'm going to try what you suggested. I also downloaded the latest XP-32 and Vista-64 wireless drivers from HP. I'll let you know what happens.

---

### Post by IgnorantGuru on 2007-05-18
On the NX6125 there is no amber that I'm aware of, just blue or off, but that may be a difference with the model.  If possible I would suggest booting into Windows to see if the wireless is working there as a control.

I tried the stock driver that comes with Ubuntu (but requires the firmware to be added), as well as a driver on the net.  The only one that worked was the one that came with the machine which I plucked from the Windows folder.  And like I said if you're using the 64 bit version of Ubuntu you'll need a 64 bit driver (which may or may not be available).

I would also suggest trying to find out what Broadcomm model it is (the Dell model number didn't prove useful), and see if you can find any scuttle-butt on it.

I'm interested to hear your progress.  Also don't hesitate to email HP.  I sent them a query just to drum up some linux feedback and was surprised to actually receive a reply from a manager in their linux division.  Turns out he was running linux on the same laptop I had and he had some helpful suggestions (re the video, IIRC).

---

### Post by challman on 2007-06-04
Well, I've figured out what the problem was.

Originally, when I started with Kubuntu, I was running 6.10 x86. I had forgotten that my laptop was an AMD64. I was able to get the wireless working with the 32bit Windows drivers (bcmwl5.inf/sys). Soon after, I wanted to use the 64bit version of Kubuntu, so I decided to download 7.10 AMD64. I forgot one important rule: Don't use new software on new hardware. I had more software issues (long story) so I went back to 6.10 AMD64 this time. The entire time, I had been booting the kernel with "acpi=off irqpoll=on". No matter what I tried, I could NOT get ndiswrapper to work. I had tried 7.04 AMD64, 6.06.1 AMD64 and 6.10 AMD64. While on 6.10 AMD64 I started searching for other hits on HP laptops. I also started to review the log files. I found in /var/log/dmesg where ndiswrapper was loading the driver but couldn't use IRQ 0 (I've read that this isn't a valid IRQ). Then I found a post stating APIC problems and IRQ problems were related. I then started booting trying different parameters until this: "noapic". Now my wireless lights up blue and it connects!!!!

I'm hoping that over time, the APIC problems get resolved either in the kernel or by HP (haha).

I have my Nvidia 6150 9755 drivers loaded and running. I just have to figure out how to get the resolution to run at 1440x900.

One day when I'm really bored, I think I'll try the upgrade to 7.04 AMD64...



Thanks to everyone for your help!!

---

### Post by IgnorantGuru on 2007-06-06
Thanks for the update - and nice job chasing the problem down.  Also make sure your fans are running in battery mode with noapic.  I had problems with an earlier version of Ubuntu not turning the fans on.

---

