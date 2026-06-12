---
title: "hp dv9008nr install problem"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by challman on 2007-03-15
I've got a HP dv9008nr laptop. When I boot the 6.10 liveCD, it get a blank or blurry screen with nothing on it. I have to reset power and retry. I then booted the liveCD but changed the display options to VGA 1024x768. This time I got a screen. It booted and I clicked the install icon. I got the OS to install, but when I boot it off the HD, I get the same screen. I'm not sure if it's video drivers or what. After trying numerous resolution changes, I found a thread about acpi. I booted it and set acpi=off. It booted up and I logged on. Here is my hardware:

1.6 GHz AMD Turion™ 64 X2 Dual-Core Mobile Technology TL-50 2 X 256KB L2 Cache
1024MB DDR2 System Memory (2 Dimm)
NVIDIA GeForce Go 6150 (UMA) up to 128MB (shared)
100GB 5400RPM (SATA)
LightScribe SuperMulti 8X DVD±RW with Double Layer Support
17.0” WXGA+ High-Definition BrightView Widescreen Display (1440 x 900)
High speed 56k modem
Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)
802.11b/g WLAN

I still have the following problems:

1. ACPI. I'd like to get this working. The laptop won't power off when I shutdown.
2. Sound appears to be inoperative.
3. My wireless network adapter is greyed out.

---

### Post by teaker1s on 2007-03-15
your series of laptop not one I've played with, but I believe you share the same issues and some of the hardware that dv6000 series laptops have, I've started a wiki page about it and I believe it will assist you
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")

---

### Post by challman on 2007-03-21
Here's the latest. Sometimes when it boots, I get the signon screen. Sometimes I get some strange picture of fuzzy clouds with horizontal lines. If I boot with "acpi=off" I get the signon screen every time. Here is what is still wrong with my install:

1. Not using nvidia driver therefore can't use the resolutions the hardware is capable of.
2. Wireless not working.
3. No power management (due to acpi=off).

I've tried following some of the instructions I've found online. I started with installing ndiswrapper and the latest driver for the BroadCom wireless. I didn't have much luck, so I figured I'd get the screen working. Seems simple enough, right? Wrong! I've searched and tried almost everything I can find online but I STILL can't get the driver working properly. I downloaded the x86 version of the nvidia driver, NVIDIA-Linux-x86-1.0-9755-pkg1.run and followed their instructions. When I did startx, I got an API problem. It said something about 9755 and 7184. So I downloaded and installed NVIDIA-Linux-x86-1.0-7184-pkg1.run.. The API error is now gone. However, I still can't get X started. It's telling me "screen(s) found, but none have a usable configuration". I've tried changing refresh rates, modeline and resolutions, but I can't get it working. Any ideas?

I've attached my xorg.conf and Xorg.0.log files.

---

### Post by challman on 2007-03-21
Ok, here are the files:

---

### Post by teaker1s on 2007-03-21
> **challman said:**
> Here's the latest. Sometimes when it boots, I get the signon screen. Sometimes I get some strange picture of fuzzy clouds with horizontal lines. If I boot with "acpi=off" I get the signon screen every time. Here is what is still wrong with my install:

1. Not using nvidia driver therefore can't use the resolutions the hardware is capable of.
2. Wireless not working.
3. No power management (due to acpi=off).

I've attached my xorg.conf and Xorg.0.log files.

nvidia driver should have offered to configure for you ,if you use 
```
sudo dpkg-reconfigure xserver-xorg
``` to configure xserver, if it won't work on nvidia then use " vesa" as driver. 
I would prefer to assist with wireless, as my experience with ubuntu and the nvidia beta driver was less than successful and I prefer not to make the situation worse.

Wireless if we check in terminal
```
lspci
```
```
lsusb
```
If you see broadcom bcm4311 then the link in my signature is good if you have bcm 4306 or another make then post output.
we can also see if wireless is on and unconfigured or off and needs driver by
```
iwconfig
```
post output

---

### Post by challman on 2007-03-23
I was able to get my graphics working somewhat. I changed the driver from nvidia to nv and set a boot parameter of vga=792.

I followed your instructions on the link about ndiswrapper. I had v1.18 installed. I removed it and installed v1.38:

chris@dv9008nr:~$ ndiswrapper -v
utils version: 1.9
driver version:        1.38
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1

chris@dv9008nr:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311:103C:1363) present (alternate driver: bcm43xx)
        device (14E4:4311) present (alternate driver: bcm43xx)

chris@dv9008nr:~$ lspci | grep Bro
03:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

chris@dv9008nr:~$ lspci -n | grep 03
00:03.0 0604: 10de:02fd (rev a1)
00:05.0 0300: 10de:0244 (rev a2)
00:0b.0 0c03: 10de:026d (rev a3)
00:0b.1 0c03: 10de:026e (rev a3)
00:10.1 0403: 10de:026c (rev a2)
00:18.3 0600: 1022:1103
03:00.0 0280: 14e4:4311 (rev 01)

chris@dv9008nr:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

chris@dv9008nr:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



I don't know why Access Point above shows Invalid, but I'm unable to enable my wireless adapter. My wireless setup utilizes WPA-PSK, but just to get this working I changed it to WEP 64bit ASCII. Let me know what to try next.

And THANKS!!!

---

### Post by challman on 2007-03-24
Ok, I got the wireless working, somewhat. I realized I made a mistake one day during frustrations. I changed the eth1 entry in /etc/iftab to wlan0. While reviewing your procedures, I reviewed that file and saw my edit. I commented it out & rebooted. Now the light is lit blue, so the adapter is working finally, however, iwconfig shows the Access Point: Not-Associated. I've verified the WEP key and ESSID. I've also changed Afturburner to 0 in .conf.. I've got a D-Link 624:

Super G Mode: Disabled
Extended Range Mode : Disabled
WMM Function (Wireless Qos): Disabled
802.11g Only Mode : Enabled
SSID Broadcast : Enabled
WEP
Authentication Open System
WEP 64bit ASCII

What do I need to do now?

---

### Post by challman on 2007-03-24
chris@dv9008nr:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID: off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management: off
          Link Quality: 0  Signal level: 0  Noise level: 0
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

sit0      no wireless extensions.

---

### Post by challman on 2007-03-24
Progress!!

I found some other posts that showed iwconfig commands. Appearantly, my ESSID isn't set properly, so I did:

iwconfig wlan0 essid "######"

Now the ESSID shows properly and it's is Associated to my AP. I am not getting a DHCP address yet......  :|

---

### Post by teaker1s on 2007-03-24
maybe a look at this link will help
[http://www.ubuntuforums.org/showthread.php?t=341357]("http://www.ubuntuforums.org/showthread.php?t=341357")

---

### Post by challman on 2007-03-29
I am submitting this reply on my laptop with Ubuntu and using my wireless network. WOOHOO!!

Thanks for all the help.

I had to make some changes to /etc/network/interfaces :

auto wlan0
iface wlan0 inet dhcp
wireless-channel 11
wireless-mode managed
wireless-essid Private_Network
wireless-keymode open
wireless-key s:<insertKey>


Now on to WPA. I've got knetworkmanager installed, but it doesn't list any wireless networks or adapters. When I connect a network cable, it sees and configures it. I've got WPAsupplicant installed and I created /etc/default/wpasupplicant but I don't know where to go next. I've Googled for some good instructions, but nothing I've found has worked.

---

### Post by teaker1s on 2007-03-29
I'm affraid that I've not really played with kde, I can tell you that linux wireless is a lucky dip, some hardware works with some wireless management programs and bombs with others, I'd advise trying another manager program as well

---

### Post by challman on 2007-06-04
Well, I've figured out what the problem was.

Originally, when I started with Kubuntu, I was running 6.10 x86. I had forgotten that my laptop was an AMD64. I was able to get the wireless working with the 32bit Windows drivers (bcmwl5.inf/sys). Soon after, I wanted to use the 64bit version of Kubuntu, so I decided to download 7.10 AMD64. I forgot one important rule: Don't use new software on new hardware. I had more software issues (long story) so I went back to 6.10 AMD64 this time. The entire time, I had been booting the kernel with "acpi=off irqpoll=on". No matter what I tried, I could NOT get ndiswrapper to work. I had tried 7.04 AMD64, 6.06.1 AMD64 and 6.10 AMD64. While on 6.10 AMD64 I started searching for other hits on HP laptops. I found a post stating APIC problems. I then started booting trying different parameters until this: "noapic". Now my wireless lights up blue and it connects!!!!

I'm hoping that over time, the APIC problems get resolved either in the kernel or by HP (haha).

I have my Nvidia 6150 9755 drivers loaded and running. I just have to figure out how to get the resolution to run at 1440x900.

One day when I'm really bored, I think I'll try the upgrade to 7.04 AMD64...



Thanks to everyone for your help!!

---

