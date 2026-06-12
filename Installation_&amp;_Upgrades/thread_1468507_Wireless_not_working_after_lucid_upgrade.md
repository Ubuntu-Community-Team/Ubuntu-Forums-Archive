---
title: "Wireless not working after lucid upgrade"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by eshandy on 2010-05-01
Hi there.

I need help. After upgrading from Karmic to Lucid, no wireless networks are found on my computer—an acer travelmate 5510.

On Karmic, wifi worked flawlessly "out of the box"—no windows drivers or anything needed. I have checked under Administration/hardware drivers; it tells me "no proprietary drivers are in use on this system." Cabled internet access through my wifi router works fine.

I would really appreciate anyone who can help me get wifi up and running under Lucid. Despite having used Karmic for a while, I am relatively new to the inner workings of Ubuntu / linux systems, and really don't know where to go from here.

Thanks
—eshandy

sudo lshw -C net readout:

[FONT=Courier New]  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:c0200000-c020ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:21:01:6c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.11.3 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:21 ioport:a000(size=256) memory:c0300000-c03000ff
[/FONT]

iwconfig readout:
[FONT=Courier New]lo        no wireless extensions.

eth0      no wireless extensions.[/FONT]

---

### Post by Robertjm on 2010-05-01
I had a similar problem with my HP laptop when I first installed LL (alpha2).

For whatever reason it had turned my wifi completely off. To resolve my problems I clicked on the wifi logo on the top panel and selected "Create New Wireless Network." It then saw the local wifi networks from my neighborhood. I clicked on mine and it connected. 

Also, do you have a open LAN port on your router and a spare RJ45 cable? If so, connect by way of the hardwire and make sure there are no updates for your system.

Good luck!!

Robert

---

### Post by eshandy on 2010-05-01
> **Robertjm said:**
> I had a similar problem with my HP laptop when I first installed LL (alpha2).

For whatever reason it had turned my wifi completely off. To resolve my problems I clicked on the wifi logo on the top panel and selected "Create New Wireless Network." It then saw the local wifi networks from my neighborhood. I clicked on mine and it connected. 

Also, do you have a open LAN port on your router and a spare RJ45 cable? If so, connect by way of the hardwire and make sure there are no updates for your system.

Good luck!!

Robert
Hi Robert.

Thank you for your reply. Unfortunately, that doesn't cut it in my case. I think Lucid is completely unable to recognize my wireless card, or something. I am not sure.

On the one hand, the lshc -c readout shows that I have an Atheros AR5001 wireless adapter (which is true)

But on the other hand, I have a feeling that a wireless connection should then show up when running iwconfig?!?

I am stumped. At any rate, the network manager applet in the top right shows no options for wireless connections.

I just booted from a Karmic live-CD to check my wifi card. No problems whatsoever. It was instantly recognized, and I was online with no delay. I may just have to revert to Karmic.

At any rate&#8212;thank you for taking the time to reply

&#8212;eshandy

---

### Post by Robertjm on 2010-05-01
Just did a quick Google for wifi not working in Lucid and there was a post from March where someone discovered the wifi was turned off in their BIOS after the upgrade. Don't ask me how that happened.

Anyways, it was an Atheros, though a different one. You might want to check that.

[SOLVED: Atheros AR9285 Wireless Card not working]("http://ubuntuforums.org/showthread.php?t=1442374")

---

### Post by eshandy on 2010-05-01
Hi Robert.

Thanks for the reply. I don't see an option in my bios to enable / disable my wireless card.

Iif the wireless card was disabled in the bios, shouldn't it also be disabled when booting from a karmic live-cd? This, however, works like a charm. Also, the lamp for my wireless card can be switched on and off with the wireless network switch, which seems to indicate that there's some sort of connection to the card, even if Lucid refuses to recognize it.

Anyway, thanks again taking the time to respond.

---

### Post by garvinrick4 on 2010-05-01
Did you right click on wireless icon and make sure you are enabled?

---

### Post by eshandy on 2010-05-02
> **garvinrick4 said:**
> Did you right click on wireless icon and make sure you are enabled?
 
Hey, Gavin.

Thanks for the reply. Yeah, I tried that. Problem is, no wireless connection options show up when I click the wireless icon. All I have is a cabled ethernet connection, and even that is somewhat sketchy.

My feeling is that Lucid fails to recognize my wireless card (Atheros AR 5001). I tried Ndiswrapper, but to no avail.

I guess I'll have to revert to Karmic, where everything works flawlessly.

Again, thanks for the reply.

---

### Post by eshandy on 2010-05-02
I have now reverted to Karmic. It seemed to be the only way to get my wireless running. Shame. I really liked the looks of the lynx, not to mention the faster boot time.

---

### Post by pwabrahams on 2010-05-03
I too am in wireless-less hell.  I'm using **wicd** for my wireless connections.  After every previous upgrade I had to recompile it using the instructions provided by Dr. Kurian (I think) in the kubuntu forum, and then it worked.  This time that wasn't sufficient.  It appears that **wicd** detects the wireless network but isn't sending the correct password.  That might not be so bad except that it never offers me an opportunity to specify the password.

---

### Post by tango32601 on 2010-05-04
Similar problem upgrading to 2.6.32-21 (UBUNTU 10.04) from 2.6.31-20.

Reading some Debian information I see that the propitiatory drivers were REMOVED
in the upgrade. You can fix it by 

     apt-get install firmware-linux-free firmware-linux-nonfree

But I have not tried this myself because now I can't get to the net. I will have to 
use another machine or use an ethernet cable.

---

### Post by AmonAlden on 2010-05-04
I just installed Lucid on a Presario V2000.  I checked my settings in preboot and my wireless is enabled there.  Whenever I configure my network it just says "you are now disonnected".  However when I sudo lshw it shows me the following:

*-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:64:20:83
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

How can I change this to ENABLED?

---

### Post by MarcusMarcus on 2010-05-06
I'm having similar issue. I am using a Samsung NP-N310 netbook. Wireless worked just great with Ubuntu 9.10 (though I had to use ndiswrapper to get it to work). When I upgraded to Ubuntu 10.04 the wireless would stop detecting wireless networks most of the time. The wireless is enabled in Ubuntu and in the BIOS. I have the computer set to dual boot to windows 7 starter and the wireless works fine in windows. I put ubuntu 9.10 back on and get wireless fine again. I do a clean install (Not an upgrade) to 10.04 and wireless again stops working. This is not consistent though. Some times the wireless works flawlessly in 10.04 on the netbook. I'll boot it, it works, I reboot, it stops working. Or it wont work and I'll reboot and it will work again. Some times it takes 1 reboot, sometimes 30+ before the wireless will work again. Other days I can reboot it numerous times without any problem. Seems very flacky and it is only doing this in Ubuntu 10.04.

I did the "sudo lshw" as well and got the following results:
*-network DISABLED
description: Wireless interface
Product: Realtek Semiconductor Co.,Lrd.
vendor: Realtek Semiconductor Co.,Lrd.
physical id:0
bus info: pci0000:02:00.0
logical name: wlan0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_masster cap_list ethernet physical wireless
configuration: broadcast=yes driver=rtl819xE latency=0 multicast=yes wireless=802.11bgn
resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff

Someone please help, I don't want to go back to 9.10

---

### Post by eltonw on 2010-05-06
How I installed Lucid Lynx (10.4) UNE:

[http://ubuntuforums.org/showthread.php?p=9203922#post9203922]("http://ubuntuforums.org/showthread.php?p=9203922#post9203922") [#136]

[COLOR="DarkRed"]**Network connections are working.**[/COLOR]

HTH...):P

---

### Post by MarcusMarcus on 2010-05-10
I followed the steps you did. Unfortunately it did not resolve the issue I am having on my Samsung netbook. Thanks though!

Any other suggestions out there?

---

### Post by Skilly on 2010-12-01
What the HELL is the problem with Ubuntu wireless!!!!???? How in GOD'S name can it really be possible that we are STILL battling with this so far down the line!!!??? After struggling on and off with dodgy wireless since Intrepid I FINALLY got to a stage where it's working and low and behold the last update to 2.6.32-26-generic has again gone and stuffed everything up!!!!! This is seriously undermining the usefulness of Ubuntu. This issue is way past it's sell-by date. IT'S TIME TO SORT OUT WHATEVER DODGY BUILD PROCESS IS IN PLACE THAT STOPS UBUNTU WIRELESS FOR CERTAIN CARDS\ROUTERS FROM WORKING WHEN NEW KERNELS ARE RELEASED!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by plexos on 2012-09-10
> **Robertjm said:**
> Just did a quick Google for wifi not working in Lucid and there was a post from March where someone discovered the wifi was turned off in their BIOS after the upgrade. Don't ask me how that happened.

Anyways, it was an Atheros, though a different one. You might want to check that.

[SOLVED: Atheros AR9285 Wireless Card not working]("http://ubuntuforums.org/showthread.php?t=1442374")

EUREKA! That was it. I spent a day going round and round with other things wasting my time. Now I remember I upgraded the BIOS but didn't imagine it would turn off the wireless. Thanks [Robertjm]("http://ubuntuforums.org/member.php?u=135474"),

---

