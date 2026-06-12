---
title: "Feisty doesn't see Wireless Card that worked on Edgy"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by Ortnet on 2007-05-20
I've been combing the forums, but I can't seem to find resolution to my current issue.

I had been running Edgy for over 6 months, when I decided to take the plunge and upgrade to Feisty. The upgrade hosed the entire computer, so I did a fresh install. Since it didn't import any old settings, I am starting from scratch, but with exactly the same hardware that I had for Edgy.

The wireless card I have is not detected, even though the driver is installed.
[B]
1. Installed wireless driver using ndiswrapper[/B] following the instructions [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless")
	rhianna@rhianna-desktop:~/Desktop/Rhianna$ [COLOR="Blue"]sudo ndiswrapper -i Mrv8000c.INF[/COLOR]
	Installing mrv8000

**2. Confirmed installed drivers**
	rhianna@rhianna-desktop:~/Desktop/Rhianna$ sudo ndiswrapper -l
	Installed ndis drivers:	
	[COLOR="Blue"]mrv8000c        driver present, hardware present [/COLOR]

**3. Per instructions, made drivers install automatically**
	rhianna@rhianna-desktop:~/Desktop/Rhianna$ sudo depmod -a
	rhianna@rhianna-desktop:~/Desktop/Rhianna$ sudo modprobe ndiswrapper
	rhianna@rhianna-desktop:~/Desktop/Rhianna$ sudo ndiswrapper -m
	Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper

**4. Went to System | Administration | Network, but no wireless card appeared**

**5. Output of lspci**
	rhianna@rhianna-desktop:~/Desktop/Rhianna$ lspci
	00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
	00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
	00:08.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
	00:0a.0 Ethernet controller: [COLOR="Blue"]Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)[/COLOR]
	00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
	00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
	00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
	00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
	00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
	01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

**6. Output of ifconfig	**
	rhianna@rhianna-desktop:~/Desktop/Rhianna$ ifconfig
	eth0      Link encap:Ethernet  HWaddr 00:07:95:EF:B5:72  
	          UP BROADCAST MULTICAST  MTU:1500  Metric:1
	          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	          collisions:0 txqueuelen:1000 
	          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
	          Interrupt:16 Base address:0x6000 
	eth0:avah Link encap:Ethernet  HWaddr 00:07:95:EF:B5:72  
	          inet addr:169.254.9.13  Bcast:169.254.255.255  Mask:255.255.0.0
	          UP BROADCAST MULTICAST  MTU:1500  Metric:1
	          Interrupt:16 Base address:0x6000 
	lo        Link encap:Local Loopback  
	          inet addr:127.0.0.1  Mask:255.0.0.0
	          inet6 addr: ::1/128 Scope:Host
	          UP LOOPBACK RUNNING  MTU:16436  Metric:1
	          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
	          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
	          collisions:0 txqueuelen:0 
	          RX bytes:3416 (3.3 KiB)  TX bytes:3416 (3.3 KiB)

**7. Output of iwconfig**
	rhianna@rhianna-desktop:~/Desktop/Rhianna$ iwconfig
	lo        no wireless extensions.
	eth0      no wireless extensions.

Any ideas? Does anyone know how I can get the card listed? If this is documented elsewhere, I would very much appreciate a link. I may not be using the right search keywords.

Thanks!

---

### Post by solomarv on 2007-05-20
What does "ifconfig -a" show? If it shows your wireless there, then you need to enable it. For example, if it shows "wlan0" there, you need to run "ifconfig wlan0 up".

---

### Post by Ortnet on 2007-05-20
I think that's where I'm having an issue. I don't have a wlan0 setting showing up. All I get is a couple of eth0 (eth0 and eth0:avah) and a lo.

How do I add the wlan0??

The thing I find puzzling is that sudo ndiswrapper -l gives me
	Installed ndis drivers:	
	mrv8000c        driver present, hardware present 

So, it sees both the hardware and the driver...

---

### Post by solomarv on 2007-05-20
Check out [https://answers.launchpad.net/ubuntu/+question/6138](https://answers.launchpad.net/ubuntu/+question/6138). It talks about getting your type of card working in Ubuntu.

---

### Post by Ortnet on 2007-05-20
I followed the thread using the mrv8335x.inf driver, but I get exactly the same result.

The ndiswrapper -i command appears to work, as the output shows driver present, hardware present. I follow the other instructions as well (sudo depmod -a; sudo modprobe ndiswrapper; sudo ndiswrapper -m

However, when I run iwconfig, I still get:
	rhianna@rhianna-desktop:~/Desktop/Rhianna$ iwconfig
	lo        no wireless extensions.
	eth0      no wireless extensions.

And when I run ifconfig, I still get:
	rhianna@rhianna-desktop:~/Desktop/Rhianna$ ifconfig
	eth0      Link encap:Ethernet  HWaddr 00:07:95:EF:B5:72  
	          UP BROADCAST MULTICAST  MTU:1500  Metric:1
	          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	          collisions:0 txqueuelen:1000 
	          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
	          Interrupt:16 Base address:0x6000 
	eth0:avah Link encap:Ethernet  HWaddr 00:07:95:EF:B5:72  
	          inet addr:169.254.9.13  Bcast:169.254.255.255  Mask:255.255.0.0
	          UP BROADCAST MULTICAST  MTU:1500  Metric:1
	          Interrupt:16 Base address:0x6000 
	lo        Link encap:Local Loopback  
	          inet addr:127.0.0.1  Mask:255.0.0.0
	          inet6 addr: ::1/128 Scope:Host
	          UP LOOPBACK RUNNING  MTU:16436  Metric:1
	          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
	          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
	          collisions:0 txqueuelen:0 

No wlan0 is showing up, and the System | Administation | Networking only gives me the eth0 option.

Any other thoughts?

---

### Post by Ortnet on 2007-05-21
I just used [this link]("https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29") which outlined steps to uninstall ndiswrapper, download the latest version (1.44), download the latest driver. 

I followed every step as written. However, when I get to Step 6 - Install the device and configure the network settings, what I see on the screen is different from what is being illustrated. My output of iwconfig yields only lo and eth0 - there is no wlan0 output.

Every other step showed success, including that the driver is loaded and the hardware is present. I know it's functioning, because before I switched to Feisty, it was running fine in Edgy.

Any other suggestions??

---

### Post by neopia9 on 2007-08-17
I'm having the same problem here, except I'm using Xubuntu 7.04. I follow the steps, but the system still doesn't seem to acknowledge that the wireless card exists. Any ideas?

---

### Post by walkerk on 2007-08-17
what does your /etc/network/interfaces look like?
```
gedit /etc/network/interfaces
```

---

