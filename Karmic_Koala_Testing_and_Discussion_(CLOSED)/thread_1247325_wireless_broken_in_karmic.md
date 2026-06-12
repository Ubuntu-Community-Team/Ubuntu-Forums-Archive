---
title: "wireless broken in karmic"
date: 2009-08-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by schmolch on 2009-08-22
I use karmic on 2 all-intel thinkpads and since 2 days the wireless is dead.
Sometimes it sees my router and sometimes it doesn't but it never succeeds in establishing a connection.

---

### Post by superhick on 2009-08-22
Hi, I also had issues with wireless (thinkpad w500) and all problems were caused by apparmor :(
try stopping it and see if it works:

sudo /etc/init.d/apparmor stop

---

### Post by linux6994 on 2009-08-23
I have a T40 and dropped back to Jaunty. I hope this work around works. If it works I will go backup to Karmic.

---

### Post by peterson_espacoporto on 2009-08-23
I have an Acer Aspire 3620 and have the same problem using ath5k.. I've created a bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/395657](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/395657)

I tried uninstalling apparmor but it still didn't work =/

---

### Post by MacUntu on 2009-08-23
IWL3945: WPA2 connections time out all the time but I'm not sure yet this is an Ubuntu/OS problem (recently upgraded router firmware).

---

### Post by Dominator86 on 2009-08-24
My Wifi stick is based on the rt2870 chip and worked out of the box in Jaunty and doesn't work at all in Karmic.

Here is the dmesg output from plugging it in:

Jaunty:
```
[  119.780038] usb 1-3: new high speed USB device using ehci_hcd and address 3
[  119.958523] usb 1-3: configuration #1 chosen from 1 choice
[  120.106548] rtusb init --->
[  120.107318] 
[  120.107320] 
[  120.107321] === pAd = e1299000, size = 566744 ===
[  120.107322] 
[  120.107326] <-- RTMPAllocAdapterBlock, Status=0
[  120.109692] usbcore: registered new interface driver rt2870
[  124.479115] <-- RTMPAllocTxRxRingMemory, Status=0
[  124.481343] -->RTUSBVenderReset
[  124.481455] <--RTUSBVenderReset
[  124.838162] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  124.838206] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  124.838248] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  124.838292] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  124.839428] 1. Phy Mode = 9
[  124.839430] 2. Phy Mode = 9
[  124.869232] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  124.882353] 3. Phy Mode = 9
[  124.889854] MCS Set = ff ff 00 00 01
[  124.899859] <==== RTMPInitialize, Status=0
[  124.901476] 0x1300 = 00064300
[  129.958521] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 142
```

Karmic:
```
[   84.236040] usb 1-3: new high speed USB device using ehci_hcd and address 3
[   84.385607] usb 1-3: configuration #1 chosen from 1 choice
[   84.472553] cfg80211: Calling CRDA to update world regulatory domain
[   84.498620] cfg80211: World regulatory domain updated:
[   84.498627] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   84.498632] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   84.498636] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   84.498640] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   84.498644] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   84.498647] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   84.689038] phy0: Selected rate control algorithm 'minstrel'
[   84.690684] Registered led device: rt2800usb-phy0::radio
[   84.690748] Registered led device: rt2800usb-phy0::assoc
[   84.690810] Registered led device: rt2800usb-phy0::quality
[   84.691142] usbcore: registered new interface driver rt2800usb
[   84.742921] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   84.751197] rtusb init --->
[   84.751263] usbcore: registered new interface driver rt2870
[   84.781300] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.
[   84.789766] rtusb init --->
[   84.789779] Error: Driver 'rt2870' is already registered, aborting...
[   84.789786] usbcore: error -17 registering interface 	driver rt2870
[   84.900796] rt2800usb 1-3:1.0: firmware: requesting rt2870.bin
[   85.150645] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Any ideas?

---

### Post by Matt Behrens on 2009-08-24
Well, you're not alone.  Been having trouble with ath9k too (and I'm not alone in that very specific problem...)  I can usually connect and sometimes even work well, but then it'll go south on me.

---

### Post by scaine on 2009-08-24
> **peterson_espacoporto said:**
> I have an Acer Aspire 3620 and have the same problem using ath5k.. I've created a bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/395657](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/395657)

I tried uninstalling apparmor but it still didn't work =/

It would be useful if more people could pop onto the bug report and hit the "affects me too" button.  I'm getting the same issue with a old Intel Mac Mini, using Ath5K driver.

---

### Post by derrick81787 on 2009-08-25
I had this issue with my Dell mini 9, but it was fixed by just opening the "Hardware Drivers" program and installing the correct driver.  There were two drivers available, but I don't remember which one I used, and I'm not at my computer at the moment.

After doing this, I remembered having this drivers installed on previous versions of Ubuntu.  I don't know if it was because of Karmic or if it was because I was using UNR, but this time the driver manager didn't pop up automatically, but had to be started manually.

---

### Post by peterson_espacoporto on 2009-08-25
derrick81787, was it something like madwifi? If that's the case, I thought we weren't supposed to use this anymore since ath5k replaced it... :confused:

---

### Post by scaine on 2009-08-27
I believe that the Ath5K driver now replaces madwifi, since madwifi depends on HAL, which is deprecated in Karmic.  For this reason, there is no backport modules package available in Karmic, which would have given you the ath_pci option on Jockey, if it existed.

From : [http://madwifi-project.org/](http://madwifi-project.org/)
[> ]("http://madwifi-project.org/wiki/About/ath5k")**[ath5k]("http://madwifi-project.org/wiki/About/ath5k")** is a relatively new and emerging driver and does not depend on the HAL. It is intended to replace [MadWifi]("http://madwifi-project.org/wiki/MadWifi") in the long run and exceed it feature-wise. [ath5k]("http://madwifi-project.org/wiki/About/ath5k") is where most of our development resources are spent on now.So, Ath5K is the only usable driver, but I can't make this work - at all - in Karmic.  It has a 30% signal if I'm lucky (should be nearer 80%) and although it "sees" my SSID, it won't connect.

I'll try downgrading my SSID to WEP (it's currently WPA2) and see if that makes any difference.

---

### Post by Lucretius on 2009-08-27
same problem using an aspire one...

I upgraded to an intel wireless card, however as of yesterday it;s taking an age to connect to my router.

once connection is established, it takes a while for firefox to connect to web pages... afterwards it seems okay.

This is the same on both wireless and wired though.

---

### Post by NCLI on 2009-08-27
> **scaine said:**
> I believe that the Ath5K driver now replaces madwifi, since madwifi depends on HAL, which is deprecated in Karmic.  For this reason, there is no backport modules package available in Karmic, which would have given you the ath_pci option on Jockey, if it existed.

From : [http://madwifi-project.org/](http://madwifi-project.org/)
[url="http://madwifi-project.org/wiki/About/ath5k"]So, Ath5K is the only usable driver, but I can't make this work - at all - in Karmic.  It has a 30% signal if I'm lucky (should be nearer 80%) and although it "sees" my SSID, it won't connect.

I'll try downgrading my SSID to WEP (it's currently WPA2) and see if that makes any difference.
Might as well disable it then >.>

---

### Post by peterson_espacoporto on 2009-08-27
scaine, mine is WEP and it won't connect =/

---

### Post by nickmcg on 2009-08-29
Dominator86

I have the same problem - it seems to be that karmic is using the rt2800usb/rt2x00usb/rt2x00lib drivers instead of the rt2870sta driver which was in jaunty

Nick

---

### Post by biasquez on 2009-08-29
wifi detected but it doesn't work on Ubuntu karmic

[ 13.756879] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[ 13.756881] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 13.756930] iwlagn 0000:07:00.0: enabling device (0000 -> 0002)
[ 13.756938] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 13.756949] iwlagn 0000:07:00.0: setting latency timer to 64
[ 13.756964] iwlagn 0000:07:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x565CBE3F
[ 13.909555] iwlagn 0000:07:00.0: Failed, HW not ready
[ 13.909569] iwlagn 0000:07:00.0: PCI INT A disabled

---

### Post by peterson_espacoporto on 2009-08-30
there's an update to wireless-tools. Didn't upgrade cause I'd have to download millions of other packages.

I'm gonna try tomorrow and check if the problem's solved...

---

### Post by nickmcg on 2009-08-30
I'm fully up to date, but the problem's still there

---

### Post by caryb on 2009-08-30
I'm sorry but I can't relate! as you can see by my signature I have a T61. I connect to WEP at home & WAP at work with no problems.


Cary

---

### Post by biasquez on 2009-08-30
> **caryb said:**
> I'm sorry but I can't relate! as you can see by my signature I have a T61. I connect to WEP at home & WAP at work with no problems.


Cary


you have this card Wireless Intel 3945ABG, 
do you use iwlagn module?

---

### Post by caryb on 2009-08-30
> **biasquez said:**
> you have this card Wireless Intel 3945ABG, 
do you use iwlagn module?

I did a lsmod but no that module does not seem to be loaded. Is this a Gnome thing/problem :confused:


Cary

---

### Post by peterson_espacoporto on 2009-08-30
> Is this a Gnome thing/problem 


Nope, my Kubuntu is affected as well =/

---

### Post by homeless4ever on 2009-09-04
> **Dominator86 said:**
> My Wifi stick is based on the rt2870 chip and worked out of the box in Jaunty and doesn't work at all in Karmic.

Here is the dmesg output from plugging it in:

Jaunty:
```
[  119.780038] usb 1-3: new high speed USB device using ehci_hcd and address 3
[  119.958523] usb 1-3: configuration #1 chosen from 1 choice
[  120.106548] rtusb init --->
[  120.107318] 
[  120.107320] 
[  120.107321] === pAd = e1299000, size = 566744 ===
[  120.107322] 
[  120.107326] <-- RTMPAllocAdapterBlock, Status=0
[  120.109692] usbcore: registered new interface driver rt2870
[  124.479115] <-- RTMPAllocTxRxRingMemory, Status=0
[  124.481343] -->RTUSBVenderReset
[  124.481455] <--RTUSBVenderReset
[  124.838162] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  124.838206] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  124.838248] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  124.838292] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  124.839428] 1. Phy Mode = 9
[  124.839430] 2. Phy Mode = 9
[  124.869232] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  124.882353] 3. Phy Mode = 9
[  124.889854] MCS Set = ff ff 00 00 01
[  124.899859] <==== RTMPInitialize, Status=0
[  124.901476] 0x1300 = 00064300
[  129.958521] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 142
```

Karmic:
```
[   84.236040] usb 1-3: new high speed USB device using ehci_hcd and address 3
[   84.385607] usb 1-3: configuration #1 chosen from 1 choice
[   84.472553] cfg80211: Calling CRDA to update world regulatory domain
[   84.498620] cfg80211: World regulatory domain updated:
[   84.498627] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   84.498632] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   84.498636] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   84.498640] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   84.498644] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   84.498647] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   84.689038] phy0: Selected rate control algorithm 'minstrel'
[   84.690684] Registered led device: rt2800usb-phy0::radio
[   84.690748] Registered led device: rt2800usb-phy0::assoc
[   84.690810] Registered led device: rt2800usb-phy0::quality
[   84.691142] usbcore: registered new interface driver rt2800usb
[   84.742921] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   84.751197] rtusb init --->
[   84.751263] usbcore: registered new interface driver rt2870
[   84.781300] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.
[   84.789766] rtusb init --->
[   84.789779] Error: Driver 'rt2870' is already registered, aborting...
[   84.789786] usbcore: error -17 registering interface 	driver rt2870
[   84.900796] rt2800usb 1-3:1.0: firmware: requesting rt2870.bin
[   85.150645] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Any ideas?

I have the exact problem on my wireless dongle also. I've tried Alpha 5 and it didn't seem to fix it.

---

### Post by nickmcg on 2009-09-06
I've the same problem, the only way round that I've found is to backlist rt2800usb -  add the line 'blacklist rt2800usb' in /etc/modprobe.d/blacklist.conf

That will let you use rt2870sta.

I can't get the newer rt2800usb to work at all (see [http://ubuntuforums.org/showthread.php?t=1256810](http://ubuntuforums.org/showthread.php?t=1256810) )

Cheers

Nick

---

### Post by homeless4ever on 2009-09-07
> **nickmcg said:**
> I've the same problem, the only way round that I've found is to backlist rt2800usb -  add the line 'blacklist rt2800usb' in /etc/modprobe.d/blacklist.conf

That will let you use rt2870sta.

I can't get the newer rt2800usb to work at all (see [http://ubuntuforums.org/showthread.php?t=1256810](http://ubuntuforums.org/showthread.php?t=1256810) )

Cheers

Nick

I've tried this and it works! Thanks nickmcg.

---

### Post by qhaz on 2009-09-07
I have had some success with this setup.
Karmic testing
2.6.31-7-generic
Belkin N1 USB Wifi adapter - model F5D8051
driver rt2870

I have put rt2800usb in the /etc/modprobe.d/blacklist.conf
I installed "wicd" network manager
I installed "rutilt" wlan manager

I can bring up ra0 with rutilt
I configured WPA 1/2 passphrase under properties in wicd
bingo . . . connection with my homepc AP
Now I must check to see if I can use 'monitor' mode (unable to do this with the ndiswrapper option)
;-)

---

### Post by megamania on 2009-09-09
I have a
Network controller: Intel Corporation Wireless WiFi Link 5100

I could connect wirelessly, but had no internet.

In my case, installing **wicd** from synaptic immediately solved the problem.

See here:
[https://answers.launchpad.net/ubuntu/+question/79379](https://answers.launchpad.net/ubuntu/+question/79379)

As I said, I didn't follow all the steps in the thread, but just installed wicd, which removed Network Manager.

Hope that helps someone. I was nearly going back to 9.04...

---

### Post by peterson_espacoporto on 2009-09-29
I've got news:

Wireless works great on Ubuntu Alpha 6. Didn't need to install wicd and I believe it should work fine on any *buntu...

---

### Post by linux6994 on 2009-09-30
Alpha 6 did the trick for me with the b43-fwcutter with a bcm43XX.

---

### Post by bluenova on 2009-09-30
> **peterson_espacoporto said:**
> I've got news:

Wireless works great on Ubuntu Alpha 6. Didn't need to install wicd and I believe it should work fine on any *buntu...

With which driver? *usb or *sta?

---

### Post by nickmcg on 2009-10-01
> **bluenova said:**
> With which driver? *usb or *sta?

I still have to blacklist *usb :(

---

### Post by tommcd on 2009-10-03
I am using a wireless card with the rt61 driver. It worked fine in Jaunty. In Karmic network manager shows no wireless connections.
lsmod shows the rt61pci driver is loaded.
I can bring up wlan0 with ifconfig.
Using "iwlist wlan0 scanning" it finds my wireless access point.
I can manually add my WEP key and essid with iwconfig.
But when I try to get an IP address with "sudo dhclient wlan0" it connects sometimes, but mostly not.
I tried disabling apparmor, and I tried that rutilt with no success yet. I'll try wicd and see if that helps.

Anybody using the rt61 wireless card in Karmic? Are you having better luck than me?

---

### Post by tommcd on 2009-10-03
Well, I have success with wicd!!! Wicd easily enabled my wireless card and got me online. It persists after a reboot.
My conclusion is that network manager in Karmic beta is borked. For anyone having wireless problems in Karmic, first make sure the proper drivers are being loaded with lsmod. Then get online with a wired connection if you can and install wicd. Note that this will remove network-manager and network-manager-gnome.
I'm still puzzled why I was having such trouble getting online with ifconfig and iwconfig at the terminal. Perhaps network-manager was interfering with it somehow.
EDIT: It seems that wicd has enabled my integrated atheros wireless on my laptop instead of my rt61 pcmcia card. This is the first time that the integrated wireless has worked on my laptop. This is a pleasant surprise indeed.

---

### Post by peterson_espacoporto on 2009-10-03
Ok, weird news: Ubuntu beta works, Kubuntu beta doesn't (!)

---

### Post by jward3010 on 2009-10-03
My Intel PRO/Wireless 5300 AGN doesn't work.

It's detected:
```
**john@vostro:~# sudo lshw -C network**
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:6a:56:2d:9c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:f6000000-f6001fff
```

But you'll notice DISABLED up top, this is my problem. Network manager's drop menu says same thing - "Wireless is disabled" - ALL SWITCHES ARE ENABLED and it's working perfect in Vista and Jaunty. Anything I can do?

---

### Post by jward3010 on 2009-10-03
Ok, a little more now.

I tried running iwconfig to connect myself to the AP but it's horribly complicated at the mo so I gave up.

WICD has saved the day, I installed and everything is detected correctly.

---

### Post by wilee-nilee on 2009-10-03
I ran into this same problem with a upgrade. So I happened to have a month old daily Karmic live Cd that has a working Network manager, I did a fresh install with that and before updating I switched to WICD then did the update and, wireless is working. Kind of a unusual way of fixing this bug but it seemed like the only choice for me.

---

### Post by jward3010 on 2009-10-03
I might just do that, I'm still in experimental phase and don't mind a few reinstalls. Regardless, I've filed a bug because I'm not seeing a solution anywhere thats simple. Hence no good for ordinary users and needs to be fixed for official release date.

Here's the link in case you people want to add to it:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/441768](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/441768)

---

### Post by wilee-nilee on 2009-10-04
I always store my irreplaceable stuff on a external HD, the laptop I used this method on is a tester anyway. If anybody wants a copy of the ISO I have that is a month old they will have to instruct me on how to make it available, I don't have a clue in this area; among others. I suspect though that there are archives that can be accessed.

---

### Post by jward3010 on 2009-10-04
One thing I've yet to do is try Karmic Beta on another laptop other than mine. My sister has a Vaio with very popular wireless stuff in it (some Intel 3945 stuff) so I'd say everything would work there. Regardless I'd like to find someone else with a **Vostro 1520** and see how they're getting on. The 5300 seems to work in Karmic, just not on my laptop, could be something specific about my hardware combination.

---

### Post by tommcd on 2009-10-05
Well, the posts from Jward3010 and WilleeNillee seems to confirm my suspicion that network manager is borked at this point in Karmic. I don't see any other way to explain how network manager would not enable wireless cards, yet wicd can do it with no problem.
Hopefully this will be fixed before Karmic goes to the final release.

---

### Post by jward3010 on 2009-10-05
Somewhat "borked" at least (I like that word, borked).

About to do a Karmic reinstall soon and I'll report back if something else happens.

---

### Post by fdoving on 2009-10-05
I have the same problem with intel 3945ABG on a Dell Latitude D620.

---

### Post by buzzmandt on 2009-10-05
> **peterson_espacoporto said:**
> Ok, weird news: Ubuntu beta works, Kubuntu beta doesn't (!)

the knetwork plasma manager has been borked (i like that word too) for quite sometime now.  I've been using kubuntu but with nm-applet instead and have completely removed the plasma manager.  I keep a fresh copy of wicd ready for install by doing
```
sudo apt-get update
sudo apt-get install -d wicd
sudo apt-get dist-upgrade
```

the -d option is for it to download only, it will tell you that gnome manager and networkmanager will be removed but it won't because it's not installing it.

then if the networkmanager borks you can do sudo apt-get install wicd even without an internet connection and it will install it from the downloaded package.

---

### Post by jward3010 on 2009-10-05
Thats what I do with wicd, just download. Never tried an offline install though.

---

### Post by arrrghhh on 2009-10-12
i'm trying to use the RT2870 driver as well, and wicd isn't fixing it either... when i blacklist the rt2800 driver, i at least get some networks shown as available, but i cannot connect to any of them, whether they're secured or not.  some of the time my network doesn't even show up, and there's several that have never shown up with this card, but my 2200bg on my laptop works fine.

so is there some way to patch the new kernel to work with this driver?  nothing i've tried thus far has worked - i've never been able to connect to a network with this new card.  any help would be greatly appreciated!

---

