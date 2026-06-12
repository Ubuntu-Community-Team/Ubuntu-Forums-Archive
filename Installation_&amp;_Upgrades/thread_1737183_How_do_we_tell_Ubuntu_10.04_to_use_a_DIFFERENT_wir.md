---
title: "How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by rocksockdoc on 2011-04-23
How do I tell Ubuntu to use a DIFFERENT wireless radio than the card that is inside the laptop?

I plugged into my Ubuntu 10.04 laptop an "Amped UA600 500mW 5dBi Wireless Router" with two USB cords.
When I click on the wireless networking applet, it connects using the internal laptop radio card (wlan0).

Doing an "ifconfig", I see the following:
```

eth0 Link encap:Ethernet  HWaddr 00:a0:c3:3a:93:38
lo Link encap:Local Loopback
wlan0 Link encap:Ethernet  HWaddr 00:0a:8d:37:b3:ba

```

I called up the company tech support 1-888-742-8830) who called me a day later and said they "know of people" who use this portable router & antenna combination on Linux but that they aren't allowed to support it so he couldn't tell me what to do to get it working.

I 'think' all I need to do is (somehow) tell Ubuntu to use 'it' instead of the existing internal wireless card.

How is that done?

---

### Post by coffeecat on 2011-04-23
Your output from ifconfig shows only one wireless device, wlan0. When you plug this Amped device in, does Ubuntu detect it? If it does and if it has the driver to support it, you can tell the system to use it in preference to the internal card by means of the network manager applet. You need the MAC code (=HWAddr in ifconfig) for this. See my posts in this thread for how to do it:

[http://ubuntuforums.org/showthread.php?t=1682546](http://ubuntuforums.org/showthread.php?t=1682546)

I'm a bit unclear as to what this Amped device is. I presume it's more than just a wireless network card. What is it?

---

### Post by rocksockdoc on 2011-04-23
> **coffeecat said:**
> What is it?

It is a higher power 802.11 wireless WiFi device than what is inside the laptop:
- Laptop = 1dBi antenna + 50mW WiFi radio
- UA600 = 5dBi antenna + 600mW WiFi radio

>    [B]High Power Wireless-300N 600mW USB Adapter 
**[UA600]("http://www.ampedwireless.com/products/ua600.html")**[/B]** ... Extend the Range of your Wi-Fi Network**[Here is the technical support web page]("http://www.ampedwireless.com/support/model/ua600.html") (see pic and quote below) describing it:
- [Setup Guide]("http://www.ampedwireless.com/datasheets/support/UA600_SetupGuide_LR.pdf") (windows only information!)
- [User's Guide]("http://www.ampedwireless.com/datasheets/support/UA600_UsersGuide.pdf") (windows only information!)
- [Datasheet]("http://www.ampedwireless.com/datasheets/Amped_UA600_Datasheet_LR.pdf") (see screenshot included below)

> **coffeecat said:**
> Your output from ifconfig shows only one wireless device, wlan0

I don't disagree. 

What I need is for ifconfig to show the Amped wireless USB router/antenna device. I'm not sure what that entails, since I've never "added" a wireless device before.

> **coffeecat said:**
> When you plug this Amped device in, does Ubuntu detect it?

I'm not sure how to tell. The little blue light that lights up when I plug it into Windows does 'not' light up on Ubuntu 10.04.

> **coffeecat said:**
>  if it has the driver to support it

Unfortunately, the Amped support technician said only that 'some people got it to work on Linux" but that he didn't know anything about Linux himself so he couldn't even advise me as to the next step.

Here is a description of the UA600 WiFi device:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189813&stc=1&d=1303591188[/IMG]

See also: [**Wireless USB Adaptor Issue**]("http://ubuntuforums.org/showthread.php?t=1723077")

---

### Post by coffeecat on 2011-04-23
If Ubuntu has the driver for your device, it should detect it and load the driver into memory. The fact that ifconfig doesn't show it may not be good. Plug the device in and post the output of:

```
lsusb
```There should be a line corresponding to the device. At the very least it will show an ID number in the form xxxx:yyyy which can be googled to see what chipset it has.

---

### Post by rocksockdoc on 2011-04-24
> **coffeecat said:**
> Plug the device in and post the output of: lsusb

Thanks for the list-short USB tip (lsusb). 

Googling, I find interesting uses of lsusb for reference:

[LIST]
[*][lsusb manpages]("http://manpages.ubuntu.com/manpages/hardy/man8/lsusb.8.html")
[*][Wireless USB Adaptor Issue]("http://ubuntuforums.org/showthread.php?t=1723077")
[*] [ 	[ubuntu] [SOLVED] Webcam not detected, yet seen in lsusb]("http://ubuntuforums.org/showthread.php?t=824408")
[*][Steps to manually mount a USB flash drive in GNU/Linux]("http://linuxhelp.blogspot.com/2007/03/steps-to-manually-mount-usb-flash-drive.html")
[*]etc.
[/LIST]
Unfortunately, when I plug in the UA600 wifi range extender, nothing makes that dinging sound nor does any application show up ... but ... in lsusb ... I 'do' see an extra line added:

> 
$ lsusb
... stuff ... 
Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. 
... stuff ... 


I'm not sure 'what' that all means ... but I'll dig a bit further at what this tells me and what I should then do in order to get the wifi range extender to work on Linux. 

Either that, or I should find a known-good wifi extender that is known to work on Linux.

---

### Post by coffeecat on 2011-04-24
The "0bda:8172" is the important bit. Also the fact that it is a Realtek chipset. Googling 0bda:8172 threw up this forum thread which might be useful for you.

[http://ubuntuforums.org/showthread.php?t=1466185](http://ubuntuforums.org/showthread.php?t=1466185)

Although that thread  appears to refer to a different device it has the same ID Obda:8172 and therefore works with the same driver. It seems that the kernel that comes with Lucid/10.04 doesn't come with the driver but there are a couple of fixes mentioned in that thread.

---

### Post by rocksockdoc on 2011-04-24
> **coffeecat said:**
> The "0bda:8172" is the important bit. Also the fact that it is a Realtek chipset. Googling 0bda:8172 threw up this forum thread which might be useful for you

Ah. Interesting. Thanks. I am relatively new to Linux and had never heard of the ls-usb command.

That thread you referenced seems to be for a USB wifi device (so it's similar to mine in that respect):
- [**Mvix Solido driver (rtl8712/8172) on 10.04**]("http://ubuntuforums.org/showthread.php?t=1466185")

Their device (see screenshot below) is very similar in form factor (USB WiFi extender) as mine!

But, more importantly, I finally have some search terms which are more productive than the "UA600 doesn't work in Ubuntu" (or similar) which got me nowhere prior in my searches about this problem. :)

**HERE IS THE DEVICE OF THAT THREAD (which apparently uses the same Realtek chip set as my device):**
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189944&stc=1&d=1303692546[/IMG]

Following suggestions in the thread, I installed the Ubuntu Software Center "ndiswrapper driver  installation tool" (I'm not sure why, but it is apparently used to  'wrap' Windows wireless drivers - so it seemed like a no brainer to at  least see if that helps. 

**HERE IS WHAT I INSTALLED (I'm not sure if this ever mattered though):**
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189945&stc=1&d=1303693215[/IMG]

Doing a search with my new-found keywords, I find in [post #6 of this thread]("http://ubuntuforums.org/showpost.php?p=10124181&postcount=6"), the following information (assuming it's correct):
- [**Wireless driver stopped working (8712u,rtl8192s_usb)**]("http://ubuntuforums.org/showthread.php?p=10716355#post10716355")

> According to Realtek the hardware ID 0bda:8172 is Realtek RTL8191S**[COLOR=DarkRed]U[/COLOR]** chip  set. The driver is "RTL8191S**[COLOR=DarkRed]U[/COLOR]** Linux Version 0006.20100625".There are some debugging hints in that thread, which I followed to see the same reputed bug.

**NOTE: That "[COLOR=DarkRed]U[/COLOR]" in the chip-set name seems to make a huge difference (since Ubuntu10.04  only has the "E" & not the "U").**

Reading on, I then checked my kernel, which is apparently version 2.6.32-31-generic (I'm relatively new to Linux so this is a basic starting point for me):
```

$uname -a
...
Linux library 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:24:35 UTC 2011 i686 GNU/Linux
```When I plug in and then unplug the USB cord of the Amped UA600 WiFi range extender, I see the following in my /var/log/messages file (rather than doing a "dmesg | tail"):

```

...
usb 2-1: new high speed USB device using ehci_hcd and address 2
usb 2-1: configuration #1 chosen from 1 choice 
r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned. [B][COLOR=DarkRed]<=== huh?[/COLOR]
[/B] ...
Linux kernel driver for RTL8192 based WLAN cards
Copyright (c) 2007-2008, Realsil Wlan
...
rtl8192_proc_init_one+0x25/0x460 [r8192s_usb]
rtl8192_usb_probe+0x148/0x191 [**[COLOR=DarkRed]r8192s_usb[/COLOR]**]       <==== **[COLOR=DarkRed]NOTE: This will be useful for the modinfo command syntax![/COLOR]**
...
usbcore: registered new interface driver rtl819x**[COLOR=DarkRed]U[/COLOR]**   <=== **[COLOR=DarkRed]NOTICE that "U" (Ubuntu has only the "E")[/COLOR]**
usb 2-1: firmware: requesting RTL8192S**[COLOR=DarkRed]U[/COLOR]**/rtl8192sfw.bin
...
usb 2-1: USB disconnect, address 3
...

```Looking at the bug reports, it seems that Ubuntu doesn't have the desired file, which is apparently the following:
```

/lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/rtl8192sfw_bin

```What my Ubuntu 10.04 has, instead, are the following files:
```

ls -l /lib/firmware/RTL*

/lib/firmware/RTL8192E:
total 52
-rw-r--r-- 1 root root   344 2010-12-14 08:25 boot.img
-rw-r--r-- 1 root root   848 2010-12-14 08:25 data.img
-rw-r--r-- 1 root root 42944 2010-12-14 08:25 main.img

/lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**:
total 244
-rw-r--r-- 1 root root 75984 2010-12-14 08:26 rtl8192sfw492.bin
-rw-r--r-- 1 root root 89616 2010-12-14 08:26 rtl8192sfw74.bin
-rw-r--r-- 1 root root 80976 2010-12-14 08:26 [COLOR=DarkRed]rtl8192sfw.bin[/COLOR]

```The solution may be as simple as a "ln -s" of what Ubuntu has with what Ubuntu is looking for when I plug in the USB WiFi adapter ... but I need to read further to be sure about that (as I may end up downloading the driver that Ubuntu is apparently looking for instead).

NOTE: I did 'not' run this command; but this may end up being the solution:
```

$ sudo ln -s /lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**/rtl8192sfw.bin /lib/firmware/RTL819[COLOR=Black]2[/COLOR][COLOR=DarkRed][COLOR=Black]S[/COLOR]**U**[/COLOR]/rtl8192sfw_bin

```A quick look in the /lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless directory shows an "rtl818x" directory with the following contents:
```

$ ls -alsF /lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rtl818x/*
...
44 -rw-r--r--  1 root root 43176 2011-04-08 16:36 rtl8180.ko
72 -rw-r--r--  1 root root 73640 2011-04-08 16:36 rtl8187.ko

```Actually, I was expecting to see a file called "r81[COLOR=DarkRed]92_usb[/COLOR].ko" ... so ... maybe I need to install it?

Before I actually install anything, I need to read more about this since there is apparently a downloadable driver from [post #6]("http://ubuntuforums.org/showpost.php?p=10124181&postcount=6") of that thread:
> - Driver downloaded from Realtek as recommended 
--->Please download RTL8191SU Linux driver source from below URL.
[http://www.realtek.com.tw/downloads/...true#RTL8191SU]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SU")

- Driver installation according to the directions given [HERE.]("http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html") 

**Unfortunately, for me, I can't 'find' the drivers at that web site. **They 'imply' they're there, but I haven't found them (yet). [IMG]http://ubuntuforums.org/attachment.php?attachmentid=189950&stc=1&d=1303708150[/IMG]

Unfortunately, I can't get the syntax for "modinfo" to work; so I can't provide any information from that suggested command.

* EDIT: I belatedly realized the modinfo syntax can be gleaned from the dmesg output, namely:*
```

$ modinfo r8192s_usb

```

---

### Post by rocksockdoc on 2011-04-24
This is (very slowly) starting to make (some) sense ... but I don't have a background on how device drivers work on Ubuntu. 

I've never dealt with a reputed Ubuntu bug before; but it's beginning to dawn on me that my problem is a known bug in Ubuntu 10.04 ... 

[Post #35]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/35") and [post #36]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/36") of [this thread]("http://ubuntuforums.org/showpost.php?p=10125636&postcount=17") may be relevant to the problem that I'm seeing (could it be the same bug?):
-[ [STAGING] realtek rtl8192su chipset based USB wireless devices fail to work    ]("http://ubuntuforums.org/showpost.php?p=10125636&postcount=17")

** Here is post #35 (excerpted):**
```

[logari81]("https://launchpad.net/%7Elogari81") wrote on 2010-11-15:  [ #35]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/35") 
...
 [COLOR=DarkRed]**We have just confirmed this bug using the LiveCD of Ubuntu 10.10**[/COLOR] with the the following device:
 Bus 001 Device 006: ID 0b05:1786 ASUSTek Computer, Inc.
**[COLOR=DarkRed]  After connecting the wifi stick, the driver r8192s_usb cannot find the firmware:[/COLOR]**
...
 looking at:[ http://lxr.linux.no/#linux+v2.6.36/drivers/staging/rtl8192su/r8192S_firmware.c]("http://lxr.linux.no/#linux+v2.6.36/drivers/staging/rtl8192su/r8192S_firmware.c")
it seems that the driver r8192s_usb looks for a firmware file /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/rtl8192sfw.bin 
but the directory RTL8192S**[COLOR=DarkRed]U[/COLOR]** doesn't exist in Maverick. 
...
We first tried copying the firmware file from RTL8192S[COLOR=DarkRed]**E**[/COLOR]:
 sudo cp /lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**/rtl8192sfw.bin /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/
 after this the wifi stick could detect wireless networks but couldn't connect (the filesize of this firmware is 80976 bytes).
...
Then we tried a different version of the firmware:
 wget [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)
  gunzip rtl8192sfw.bin.gz
  sudo mv rtl8192sfw.bin /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/
...
With this one the wifi stick could both detect wireless networks and connect to them (the filesize of the used firmware is 68368 bytes).
...

```**And here is post #36:**
```

[Laurynas Butkus]("https://launchpad.net/%7Elaurynas-butkus") wrote on 2010-11-16: [ #36]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/36")   
 Copied firmware folder from CD to /lib/firmware/(kernel version/.
 Default Ubuntu driver r8192s_usb works perfectly!
 We're on Ubuntu Maverick 64bit.
 Ubuntu currently wouldn&#8217;t load kernel driver automatically, so we added to /etc/modules:
r8192s_usb
 To load manually by hand:
sudo modprobe r8192s_usb
 Works on Ubuntu Maverick 64bit with following cards:
Canyon wireless LAN USB adapter 150N CNP-WF518N2 (rtl8188su)
Delock USB 2.0 wlan_n Stick 300 Mbps (rtl8191s)

```So, here is what I just did:
```

    http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
    $ gunzip rtl8192sfw.bin.gz
    $ sudo mkdir /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**
    $ sudo mv rtl8192sfw.bin /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/.

```Taking a look at file permissions, I see the following:
```

$ ls -alsF /lib/firmware/RTL*

/lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**:
total 264
 4 drwxr-xr-x  2 root root  4096 2011-04-23 03:54 ./
16 drwxr-xr-x 50 root root 16384 2011-04-24 22:55 ../
76 -rw-r--r--  1 root root 75984 2010-12-14 08:26 rtl8192sfw492.bin
88 -rw-r--r--  1 root root 89616 2010-12-14 08:26 rtl8192sfw74.bin
80 **[COLOR=DarkRed]-rw-r--r--[/COLOR]**  1 root root 80976 2010-12-14 08:26 **[COLOR=DarkRed]rtl8192sfw.bin[/COLOR]**

/lib/firmware/RTL8192S[COLOR=DarkRed]**U**[/COLOR]:
total 88
 4 drwxr-xr-x  2 root root  4096 2011-04-24 22:56 ./
16 drwxr-xr-x 50 root root 16384 2011-04-24 22:55 ../
68 **[COLOR=DarkRed]-rw-r--r--[/COLOR]**  1 foo  foo  68368 2011-04-24 22:54 **[COLOR=DarkRed]rtl8192sfw.bin[/COLOR]**

```

---

### Post by rocksockdoc on 2011-04-24
I belatedly realized the "modinfo" syntax could be gleaned from the output of the dmesg command, namely:

```

$ dmesg | tail 
...
rtl8192_proc_init_one+0x25/0x460 [r8192s_usb]
rtl8192_usb_probe+0x148/0x191 [**[COLOR=DarkRed]r8192s_usb[/COLOR]**] <== **[COLOR=DarkRed]NOTE: Useful for the modinfo command syntax![/COLOR]**
...

``````

$ modinfo r8192s_usb
...
filename:       /lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
...

```

---

### Post by rocksockdoc on 2011-04-24
OK. I didn't even reboot after installing the 'correct' drivers into the correct location.

[LIST]
[*] In summary, (apparently) the Realtek (0bda:8172) hardware was 'looking' for this driver:
[LIST]
[*]/lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/rtl8192sfw_bin
[/LIST]
 
[*]Ubuntu 10.04 only had this driver:
[LIST]
[*]/lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**/rtl8192sfw_bin
[/LIST]
 
[/LIST]
   After installing the (hopefully correct) driver, I just plugged in the two USB connectors of the Amped UA600 WiFi extender into my laptop USB ports #2 and #3 and for the first time, the little blue LED on the WiFi extender began to blink. (It 'looks' like it connects - but I don't get any connectivity though.)

Looking at dmesg ouput, I can see that it's (sort of) working ... only ... now, ironically, I'm back to the original question. Which, I guess, is a good thing!  :)

Here's my original question:

[LIST]
[*]I (now) have two active wireless cards (i.e., I have two WiFi radios)
[*]My wireless ISP provider (WISP) uses MAC address filtering
[*]So, I need to change the MAC address of the desired WiFi radio
[*]And, then, I need to somehow disable the internal WiFi radio in favor of the USB WiFi radio
[/LIST]
The question is how to favor the (new) external USB WiFi device and deprecate the (old) internal WiFi radio?

A new ifconfig command reveals the presence of both "wlan0" and now, "wlan1":
```

$ ifconfig | grep wlan
...
wlan0     Link encap:Ethernet  HWaddr 00:0a:8d:37:b3:ba
wlan1     Link encap:Ethernet  HWaddr f8:78:8c:a1:45:f4
...

```Let's say the WISP MAC filtering is expecting "DE:AD:BE:EF:CA:FE".

I can manually change the MAC address of the wlan1 card using ifconfig:
```

[COLOR=DarkRed]**MANUALLY**[/COLOR] right click on the Ubuntu networking icon & deselect "Enable Networking" <=== this is a critical step!
$ sudo ifconfig wlan1 down hw either de:ad:be:ef:ca:fe
$ sudo ifconfig wlan1 up
[COLOR=DarkRed]**MANUALLY**[/COLOR] reselect "Enable Networking" <=== this is a critical step!

```NOTE: I need a way to "automate" this MAC-changing process!

Now, I'm back to the original question. 
[COLOR=DarkRed]**Q: How do I set up the Ubuntu 10.04 laptop so that the connection to the WISP is via wlan1 and not wlan0?**[/COLOR]

I tried creating a specific connection - but (so far) that just makes the connection icon spin and "look" like it connects (with four bars no less); but there is no 'real' connection established. This 'was' mentioned in the bug report. 

So, somehow, maybe, I got the wrong driver (I need to doublecheck as this makes no sense to have a good connection showing four bars yet no Internet connectivity - as if an authentication step was missing - somehow).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189954&stc=1&d=1303716676[/IMG]

I did figure out one way (albeit ugly) to deprecate the internal wlan0 WiFi radio in favor of the external WiFi radio wlan1 though:
```

MANUALLY right click on the wireless network connection & uncheck "Enable Networking"
$ sudo ifconfig wlan0 down
MANUALLY re-check "Enable Networking"

```Using that method, only wlan1 shows up in a subsequent ifconfig.

Looking at the /var/log/* files, these seem to be involved:
```

/var/log/kern.log
...
=================>ieee80211_authentication_req():auth->algorithm is 0
Linking with wisp_wifi,channel:1, qos:1, myHT:0, networkHT:0, mode:6
Linking with wisp_wifi,channel:1, qos:1, myHT:0, networkHT:0, mode:6
=====>rtl8192SU_link_change 1
<=====rtl8192SU_link_change 2
===>ieee80211_associate_procedure_wq(), chan:1
rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
=================>ieee80211_authentication_req():auth->algorithm is 0
rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
rtl819xU:qos active process with associate response received
Associated successfully
Using G rates:108
Successfully associated, ht not enabled(0, 0)
=====>rtl8192SU_link_change 1
=============>ARFR0+rate_index*4:0xfff
<=====rtl8192SU_link_change 2
============>normal associate

``````

/var/log/debug
...
rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
rtl819xU:rtl8192_qos_association_resp: network->flags = 10,1
rtl819xU:qos active process with associate response received
periodic_update(): Roamed from BSSID 00:14:F2:A0:B0:C0 (wisp_wifi) to 00:0F:8F:A1:B1:C1 (wisp_wifi)

``````

/var/log/syslog
...
library NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> associated
library NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> completed
library kernel: <=====rtl8192SU_link_change 2
library kernel: ============>normal associate
periodic_update(): Roamed from BSSID 00:14:F2:A0:B0:C0 (wisp_wifi) to 00:0F:8F:A1:B1:C1 (wisp_wifi)

``````

/var/log/daemon.log
...
library NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> associated
library NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> completed
periodic_update(): Roamed from BSSID 00:14:F2:A0:B0:C0 (wisp_wifi) to 00:0F:8F:A1:B1:C1 (wisp_wifi)

``````

/var/log/messages
...
Associated successfully 
Using G rates:108
Successfully associated, ht not enabled(0, 0)
=====>rtl8192SU_link_change 1
=============>ARFR0+rate_index*4:0xfff
<=====rtl8192SU_link_change 2
============>normal associate


```The output from the following commands may provide some debugging data:
```

$ lsmod
...
Module                  Size  Used by
r8192s_usb            346039  0
...

``````

$ lspci
...
nothing specific to the wlan that I could find

``````

$ lsusb
...
Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. 

``````

$ modinfo r8192s_usb
...
filename:       /lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
...

```

---

### Post by coffeecat on 2011-04-25
Do **not** change the MAC address of either of the devices. Look at the thread I link to - specifically post #2 in that thread - in post #2 of this thread. It is very easy to achieve what you want by means of network manager. I described the process in 2-3 sentences. If you find yourself using ifconfig or finding it difficult, you are complicating things.

---

### Post by rocksockdoc on 2011-04-25
I'm a bit confused because I went to a wireless hotspot and it 'still' looked connected to the wisp!

So, the 'driver' or something isn't working exactly right (normally it won't 'show' as connected with 5 bars unless it's actually connected); so something is slightly amiss. 

BTW, at a hotspot, which doesn't use MAC address filtering, BOTH the internal wifi card and the external USB wifi card seem to connect.

**How can I tell WHICH connection is what I'm actually using?**

Googling, some suggest I use the "route" command (but I'm not sure what it's actually telling me yet):
```

$ route
...
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.120.110.128  *               255.255.255.128 U     2      0        0 wlan1
default         10.120.110.129  0.0.0.0         UG    0      0        0 wlan1

```Others say to use the 'arp' command (again, I'm not sure what it's telling me):
```

$ arp
...
Address HWtype HWaddress Flags Mask Iface
10.120.110.129 ether 00:90:fb:45:82:aa  C  wlan1

```Since I manually pressed the "disconnect" button for the internal card (wlan0) on the wireless connection pulldown, I 'think' those commands are telling me that I'm only using the external (wlan1) USB wifi extender. 

Right?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189999&stc=1&d=1303756077[/IMG]

---

### Post by rocksockdoc on 2011-04-25
> **coffeecat said:**
> Do **not** change the MAC address of either of the devices. Look at the thread I linked to - specifically post #2 in that thread

I'm going to summarize (what I can figure out) about the referenced thread:
- [**My experience with disabling one of two wireless adapters in Ubuntu**]("http://ubuntuforums.org/showthread.php?t=1682546")

**Options listed in that thread (some good, most bad):**

[LIST=1]
[*]Locate the on-board  wireless adapter and remove it (i.e., this is a bad idea)
[*] Blacklist the appropriate modules in  /etc/modprobe.d/
[*] Create a script that would autorun and evoke the "iwdown" command in some way
[*]Create a startup script that turns off the adapter using the "iwconfig" command
[*]Manually disconnect the internal wlan0 in the "Network Manager" each time you connect to WiFi
[*]Edit Connections in the Network manager to only use a single adapter with a specific MAC address
[/LIST]
Looking at that suggested last (i.e., hopefully best) option above:

[LIST=1]
[*]Right click on the Network Manager icon in the main Ubuntu 10.04 top menu bar
[*]Left click on Edit Connections -> Wireless tab
[*]Left click to highlight your desired connection & press the "Edit" button
[*]Left click on the "Wireless" tab & enter the desired MAC into the "MAC address" field
[LIST]
[*]This option locks this connection to the network device specified by the MAC address entered here. Example: 00:11:22:33:44:55
[/LIST]
 
[*]Left click the "Apply" button
[*]Then, when you start up, the Network Manager should only use the wireless device with that MAC address.
[/LIST]
A bit of confusion arises because I am not sure whether to put in the "real" MAC address of the external USB WiFi radio or to enter the purposefully set MAC address (e.g., DEADBEEFCAFE) because my WISP provider uses MAC filtering for authentication.

I can set the MAC address of the external USB WiFi radio to DEADBEEFCAFE using this procedure:
```

$ sudo ifconfig wlan0 down hw ether DE:AD:BE:EF:CA:FE
$ sudo ifconfig wlan0 up

```QUESTION1:
 Which MAC address do I put in the "Network Manager" "Wireless" tab "MAC Address" field?

QUESTION 2: 
And, ideally, how do I get that manual MAC-address setting to be automatic upon reboot?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190003&stc=1&d=1303756770[/IMG]

---

### Post by rocksockdoc on 2011-04-25
It looks like a LOT of people have been similarly burned by this Ubuntu bug:
- [Ubuntu Karmic 32bit Realtek 8192SU driver]("http://ubuntuforums.org/showthread.php?p=10719084#post10719084")
- [Realtek RTL8192SU driver compiling issues]("http://ubuntuforums.org/showthread.php?t=1425697")
-[ [STAGING] realtek rtl8192su chipset based USB wireless devices fail to work    ]("http://ubuntuforums.org/showpost.php?p=10125636&postcount=17")
**- **[Mvix Solido driver (rtl8712/8172) on 10.04]("http://ubuntuforums.org/showthread.php?t=1466185")
- [Firmware for Realtek 8192  ]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/firmware-for-realtek-8192-a-761714/page2.html")
etc.
[B] 
Here's my summary for that thread of the workaround to this Ubuntu bug.

[/B]> **rocksockdoc said:**
> Yesterday, I tried to get an external WiFi  radio to work in my Ubuntu 10.04 laptop (effort detailed here):
- [**How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?**]("http://ubuntuforums.org/showthread.php?p=10718746#post10718746")

On my version of a ( 2.6.32-31-generic) pristine Ubuntu 10.04 laptop installation:
```
$uname -a
...
Linux library 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:24:35 UTC 2011 i686 GNU/Linux

```At first, Ubuntu would not recognize the [Amped UA600 USB WiFi radio adapter ]("http://www.ampedwireless.com/support/model/ua600.html")when it was plugged into the laptop USB port.

```

$ ifconfig | grep wlan   
...
eth0 Link encap:Ethernet  HWaddr 00:a0:c3:3a:93:38
wlan0 Link encap:Ethernet  HWaddr 00:0a:8d:37:b3:ba

```First, I determined the device identifier using 'list short USB":
```

$ lsusb
...
Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. 

```Then, in the /var/log/messages (dmesg | tail), I determined what driver Ubuntu was (mistakenly) looking for:
```

usb 2-1: new high speed USB device using ehci_hcd and address 2
usb 2-1: configuration #1 chosen from 1 choice
r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned. <=== huh?
 ...
Linux kernel driver for RTL8192 based WLAN cards
Copyright (c) 2007-2008, Realsil Wlan
...
rtl8192_proc_init_one+0x25/0x460 [r8192s_usb]
rtl8192_usb_probe+0x148/0x191 [r8192s_usb]       **[COLOR=DarkRed]<==== NOTE: This will be useful for the modinfo [/COLOR]**command syntax!
...
usbcore: registered new interface driver rtl819xU [COLOR=DarkRed]**  <=== NOTICE the "U" (Ubuntu has only the "E")**[/COLOR]
usb 2-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
...
usb 2-1: USB disconnect, address 3
...

```Placing that keyword into "module information", I could see the desired driver:
```

$ modinfo r8192s_usb
...
filename:       /lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
...

```A quick look in the   /lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless directory   shows an "rtl818x" directory with the following contents:

```

$ ls -alsF /lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rtl818x/*
...
44 -rw-r--r--  1 root root 43176 2011-04-08 16:36 rtl8180.ko
72 -rw-r--r--  1 root root 73640 2011-04-08 16:36 rtl8187.ko

```The problem appears to be that Ubuntu is looking for the following location  (which doesn't exist):
```

$ ls /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/rtl8192sfw_bin
...
ls: cannot access /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/rtl8192sfw_bin: No such file or directory

```The file exists (rtl8192sfw_bin); it's just in a different location on Ubuntu:
```

$ ls -alsF /lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**
...
/lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**:
total 244
-rw-r--r-- 1 root root 75984 2010-12-14 08:26 rtl8192sfw492.bin
-rw-r--r-- 1 root root 89616 2010-12-14 08:26 rtl8192sfw74.bin
-rw-r--r-- 1 root root 80976 2010-12-14 08:26 rtl8192sfw.bin

```[Post #35]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/35") and [post #36]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/36") of [this thread]("http://ubuntuforums.org/showpost.php?p=10125636&postcount=17") provided a (different sized, same-named file):
-[ [STAGING] realtek rtl8192su chipset based USB wireless devices fail to work    ]("http://ubuntuforums.org/showpost.php?p=10125636&postcount=17")



Here's what I did to obtain that differently-sized file (I guess I should call it a "driver"):
```

http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
    $ gunzip rtl8192sfw.bin.gz
    $ sudo mkdir /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**
    $ sudo mv rtl8192sfw.bin /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/.

```Finally, I was able to get Ubuntu to recognize the external WiFi radio when plugged in:
```

$ ifconfig | grep wlan
...
wlan0     Link encap:Ethernet  HWaddr 00:0a:8d:37:b3:ba
wlan1     Link encap:Ethernet  HWaddr f8:78:8c:a1:45:f4

```Now that the driver is finally working, I can get back to the original question asked in that thread:
- [**How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?**]("http://ubuntuforums.org/showthread.php?p=10718746#post10718746")

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189999&stc=1&d=1303756077[/IMG]

---

### Post by rocksockdoc on 2011-04-26
I tested the setup today from a local hotspot.

I was easily able to tell Ubuntu to use the external USB wifi extender (wlan1) and it worked just fine even when I changed the MAC address of the USB wifi extender.

However, back at home, with my WISP using MAC address filtering, for some strange and incomprehensible reason, I can 'only' be on the Internet with the internal wifi card (with its MAC address changed).

For some strange incomprehensible reason, the driver that I installed to work around the Ubuntu 10.04 bug does NOT allow a connection to the WISP! 

I do remember this being mentioned in the bug report but I thought I followed all instructions appropriately and used the suggested Realtek driver in that bug report. Sigh.

So, I 'still' can't connect, at home anyway, to my WISP with the WiFi extender even though I 'can' switch from the internal wifi card (wlan0) to the external USB WiFi extender (wlan1). 

Luckily I can (still) connect to the WISP (after changing the MAC of the internal card) with the internal wifi card (wlan0); but the whole point of this thread was to be able to use the more powerful USB wifi extender to connect to the WISP! :(

I wonder if that makes this problem "SOLVED" or not?

---

### Post by rocksockdoc on 2011-04-27
It appears I'm sailing in uncharted seas ... 

Since I couldn't connect with the Amped UA600, I bought a 'similar' looking "ID 1740:9603 Senao":
- Enenius EUB9603 Wireless 11b/g/n Hight Power USB Adapter (2,000 mW, & a 5 dBi detachable antenna)

[LIST=1]
[*]Plugging it into two available USB slots, nothing happens (as before with the Realtek chips)
[*]"lsusb" reveals it's uses the "1740:9603 Senao" chipset
[LIST]
[*]Bus 001 Device 006: ID 1740:9603 Senao
[/LIST]
 
[*]"ifconfig | grep wlan" reveals there is no wlan1 external adapter (just the wlan0 internal radio card):
[LIST]
[*]wlan0 Link encap:Ethernet  HWaddr 00:a3:f8:2e:e7:df
[/LIST]
 
[*]"iwconfig | grep wlan" also reveals only the internal card connection point:
[LIST]
[*]wlan0 IEEE 802.11abgn  ESSID:"linksys"
[/LIST]
 
[*]"lsmod | grep rt2" didn't reveal any entries
[*]A search for "1740:9603 Senao" in these Ubuntuforums reveals only a single thread:
[LIST]
[*] [SOLVED] [Engenius eub9703 usb]("http://ubuntuforums.org/showthread.php?t=1623442&highlight=1740%3A9603+Senao") by phoenixpb, November 17th, 2010
[/LIST]
 
[*]I've tried all that was listed in that thread ... but it's not the same situation as that OP was emulating with Wine so he apparently had the necessary drivers (the unit doesn't come with Linux drivers).
[*]So I sent a message to Senao technical support (fae@senaousa.com) from this web page
[LIST]
[*][http://www.senaousa.com/support.html](http://www.senaousa.com/support.html)
[/LIST]
[/LIST]
It seems that Linux drivers are still in the dark age when it comes to supporting common devices. :(

Any idea how to get Linux to recognize this external USB device?

---

### Post by rocksockdoc on 2012-03-27
> **rocksockdoc said:**
> **How can I tell WHICH connection is what I'm actually using?**

For the record, I ran into this problem again with both eth0 and wlan0 connected; so I opened up a separate thread to get at the bottom of how to tell which NIC is the one that's currently being used by Ubuntu!

[LIST]
[*] [How can I tell WHICH connection Ubuntu is actually using? (wlan0, wlan1, eth0, etc.)]("http://ubuntuforums.org/showthread.php?t=1947931")
[/LIST]

---

### Post by bogan on 2012-03-28
Hi!,** Rocksockdoc**,

I am fascinated by your voyage of nondiscovery.

I had similar problems but cured them with the r8172_usb driver downloaded from the Realtek Site shown in your Thumbnail. It works with both the installed Realtek RTL8191SU card and the USB Dongle RTL8188SU.

They work together and both show in the Network Manager Connections drop down and connect much more reliably than with the r8192_usb driver. So I do not care which is doing the work.

FYI The reason I have both is that sometimes the RTL8191 does not reconnect after Suspend or Hibernate, and plugging in the RTL8188 Dongle prompts the NM to reactivate scanning and connects both { usually! } so I do not have to Reboot.

Chao!, **bogan**

---

