---
title: "Daily freezes on Thinkpad T40p after Dapper upgrade"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by shooz on 2006-06-14
Hey folks --

I have a Thinkpad T40p (1.5GB ram, ATI Radeon R250 Lf [FireGL 9000] video, Atheros AR5211 wifi) and everything was working great with Breezy, but now with Dapper I'm experiencing complete freeze ups once or twice a day.

The freezes are total lock ups -- I can't ping the machine after it happens.  First I thought it had to do with the xorg ATI driver, so I've switched to the vesa driver, but it is still happening.  The system has frozen both when using the wired and wireless network.  I am using the madwifi driver from the restricted kernel modules package.

What can I try to start to diagnose the problem?  The lock ups don't leave any messages behind in the various log files so I am at a loss on how to fix this.

Here is an lspci:
```

0000:00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)
0000:02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5211 802.11ab NIC (rev 01)

```

thanks for any help!
shooz

---

### Post by eylisian on 2006-06-15
No help here (yet? =). I am though having the same issues on a Thinkpad T30.
No logging of what went down prior to the crash (that I am aware of at this point) here either. The machine was solid as a rock under Breezy as well.

Epiphany sure is holding up though! It restores the crashed session like a charm.

If i find something out I will let you know, if you find something out please post it! This is driving me crazy.

---

### Post by Verteiron on 2006-06-19
I had this exact problem on an IBM Thinkpad T30. I fixed it by adding the following to my /etc/rc.local file.

echo "15" > /proc/acpi/thermal_zone/THM0/polling_frequency

Make sure you put this -before- the "exit 0" line. The problem with my laptop seemed to be heat-related. The fans were not coming on in time to keep the system cool. This tells the system to check the temp every 15 seconds, which in theory should be enough time to change the fan speed as needed.

Or perhaps it's just a coincidence, but I haven't had it freeze once since I added this line, and it was freezing 2-3 times a day before that.

---

### Post by shooz on 2006-06-21
The temperature thing is interesting, I just installed emifreq-applet and added a bunch of temp monitors to my toolbar.  Currently:

CPU 49C
MiniPCI 44C
HDD 31C
GPU 50C
Fan 3725 RPM

It also seems that the WiFi indicator LED is always stuck on when my laptop freezes -- could that point to the WiFi driver as a problem?

-shooz-

---

### Post by shooz on 2006-06-21
Experimenting with the temperature theory, I just ran cpuburn (burnP6) long enough to get my CPU temperature up to 80C and the fan speed never increased past the 3.6k RPM speed.  It is not clear how this is controlled on my particular Thinkpad model (t40p) or even if 80C is sufficient to raise the fan speed.  Goosing the polling_frequency, as a previous poster suggested, does not change anything.

I am, however, able to manually raise the fan speed using the commands outlined at [http://www.thinkwiki.org/wiki/How_to_control_fan_speed:](http://www.thinkwiki.org/wiki/How_to_control_fan_speed:)
```

echo 0x2F 0x07 > /proc/acpi/ibm/ecdump

```

Which brings the fan to the max speed as decribed on the thinkpad wiki (4k RPM).

-shooz-

---

### Post by caspar_wrede on 2006-06-22
My thinkpad x31 is freezing with Dapper too. I'm using kubuntu and had no such problems with breezy. Do I need to mention that this is totally unacceptable? The last total freezes I experienced were with Win95 ;) 

Any body have any ideas?

---

### Post by shooz on 2006-06-23
Just had another freeze.  Crashed while I was just typing in a text editor while listening to an audio stream on a wired network. CPU temperature was at 52C, so I guess that rules out a temperature problem.

Going to try running for a while without the wireless driver (ath_pci) loaded.

shooz

---

### Post by guine on 2006-06-23
I think getting dapper working properly is a pretty iffy proposition.  My dapper install wont boot anymore for some reason.  I had a friend who also had this problem on multiple dapper installs and he just went back to breezy which is working fine for him.  If I dont get any ideas soon Im probably just going to be joining him back on breezy.  Maybe theyll put out a new version of dapper soon which is more stable.

---

### Post by hagar on 2006-07-03
Same problem here with my Thinkpad X31. I think I can rule out the temperature theory, I have 1-2 complete freezes a day in an air-conditionend room while working mostly with a CPU frequency of 600 MHz. With Breezy my CPU fan was almost never on and I experienced not a single crash.

Anyone solved this?

thx,
a.

---

### Post by ellion on 2006-07-06
yeah,

Same problem here (T30). I'm quite sure that it is a cooling problem. I have that applett mentioned above running for a few days now. Though tempartures vary when it freezes it's mostly around 65-70° afte a reboot. Mostly it freezes after some action pushing the CPU loading, like opening firefox, switching workspace in eclipse etc.

I'll try that ACPI directive above, hoping that it'll change something :)

---

