---
title: "Slow d/l speeds on Kernel 6.2.0-26"
date: 2023-08-04
forum: Installation &amp; Upgrades
---

### Post by handrew on 2023-08-04
Updated to kernel 6.2.0-26 and did a speedtest. 16mbits/sec
While kernel 5.19.0-50 is fine.                           540mbits/sec
While kernel 5.15.0-78 is fine.                           538mbits/sec
Uploads were unaffected.

As 5.19 is coming to end of suport life I installed and made active 5.15.0-78-generic #85-Ubuntu SMP and it works fine and supported to 2027.

So anyone have any suggestions? 

System report as follows pertaining to NETWORK.

Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: Dell driver: r8169
    v: kernel pcie: speed: 2.5 GT/s lanes: 1 port: 3000 bus-ID: 01:00.0 chip-ID: 10ec:8168
  IF: enp1s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
  IF-ID-1: lxcbr0 state: down mac: <filter>

---

### Post by MAFoElffen on 2023-08-06
Are you sure you don't have something else going on?

I mean, I believe you, though this is just a quick check from my workstation, to my server, then to speedtest.net. This is also how I check & benchmark my SR-IOV VFS ports:
```

mafoelffen@msi-ubuntu:~$ iperf -c 10.0.0.3 -f m -P 2
------------------------------------------------------------
Client connecting to 10.0.0.3, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  1] local 10.0.0.11 port 59314 connected with 10.0.0.3 port 5001
[  2] local 10.0.0.11 port 59300 connected with 10.0.0.3 port 5001
[ ID] Interval       Transfer     Bandwidth
[  1] 0.0000-10.1292 sec  56.6 MBytes  46.9 Mbits/sec
[  2] 0.0000-10.1439 sec  55.5 MBytes  45.9 Mbits/sec
[SUM] 0.0000-10.0390 sec   112 MBytes  93.7 Mbits/sec
[ CT] final connect times (min/avg/max/stdev) = 11.880/11.884/11.887/0.005 ms (tot/err) = 2/0

mafoelffen@msi-ubuntu:~$ speedtest-cli
Retrieving speedtest.net configuration...
Testing from Comcast Cable (71.197.252.194)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Comcast (Portland, OR) [176.58 km]: 25.202 ms
Testing download speed................................................................................
Download: 323.82 Mbit/s
Testing upload speed......................................................................................................
Upload: 6.09 Mbit/s

mafoelffen@msi-ubuntu:~$ uname -r
6.2.0-26-generic

```
Tomorrow, when I'm through with what I'm doing tonight, I'll compare that with older kernels.

---

### Post by somebodeez on 2023-08-11
I got a big update to my Ubuntu yesterday, afterwards I rebooted my laptop Acer Aspire A515-55 and everything seemed alright until about 15/20 minutes later and my ethernet gradually broke, rebooted  but got the same again, WiFi is fine though, I've not had anything like it before, but after many hours I discovered I must have got a Kernel 6.2.0-26 update, there doesn't seemed to be much help on the internet for this, but I found a helpful post somewhere and installed Grub Customizer which had to be done via the ppa and reverted back to the previous Kernel 5.19.0-50 and everything is once again working.

I've got the Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet and there's clearly some major fault/issue/bug with this new Kernel 6.2.0-26.

I've attempted multiple times to to switch to the new Kernel and reboot, but everytime I get the same result and broken ethernet/internet. I thought I'd add to the thread so that it was clear this is not an isolated issue that the original poster is having.

---

### Post by MAFoElffen on 2023-08-12
Please file a bug report at Launchpad, then post the URL of theBug report back here in a post. Somehow, there may be a firmware bug with your combination of hardware, with that Kernel. Doing so not only helps "you"... But also helps other users with similar hardware.

Not doing so, leaves this unfixed for both you and others.

Please help with this process. This is how Linux gets "better" and things get resolved. It takes a community.

---

### Post by somebodeez on 2023-08-13
@MaFoElffen, having looked at the ReportingBugs page (link below) it's clear that someone with a much greater understanding of Ubuntu's inner workings and bug reporting skills needs to be making a bug report on this major problem, I've been using Ubuntu for quite a few years as my main OS so I'm well aware to a degree of how the Linux community works, and recognize that this will only be fixed if a detail report is made, but that is way beyond my pay grade.

Canonical have unleashed a new Kernel which is/was clearly utterly unfit for release, I personally haven't just got a laptop which I just use for simple Internet use, but it's the main hub of my home network, it runs as a media server for all my household devices (Samba) with a centralized MySQL database for my media, as well as an almost 24/7 Bittorrent server/clent, and numerous other things like video encoding and web browsing, and this bug/problem didn't just break my internet, it broke my whole network, it wasn't just a case of connecting to WiFi and changing the Static IP of my laptop in my router and everything was hunky dory, it wasn't, I was minding my own business and out of the blue through no fault of my own everything was suddenly broken, and it took me a whole day to fix my network re-scrape my media library and repopulate the MySQL database, to get everything working again, and that was after I'd spent a couple of hours trying to figure out what had gone wrong in the first place.

Looking at this Launchpad thing it looks like I'd be lucky to make a bug report if I spent the whole weekend working on it, with no guarantee of 'Ubuntu' being fixed at the end of it, I hope you would therefore understand that in my case at least, realistically I need to be looking to find a new unbroken OS (Fedora maybe) to use instead.

BUG REPORTING LINK:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by MAFoElffen on 2023-08-13
I've been supporting Linux for over a decade. I understand. Before that I supported UNIX. I have supported Windows OS since version 1.0 in 1988.

What I also understand is that Linux Distributions are pieced together from a lot of things that are controlled by a lot of upstream projects. The desktop environments, desktop managers, kernel, networking, application packages, volume managers, fonts, icons, etc. Ubuntu, as a project, tries to support what they choose to be included into their distribution.

The problem with that Kernel is from releases, code and regressions from kernel.org. It would be triaged by Launchpad, then reported upstream. Whether Canonical came up with a patch, or someone upstream came up with that patch, or someone from SUSE or RedHat, or from someone's couch or Den, no matters.

Supporting IT professionally for over 34 years now... I don't blame Ubuntu, Debian, any other distribution project... Problems happen. Problems get resolved. We used to say that a release was a point in time, with bugs included at no extra cost. We were kidding. We always hoped there were none. But things do happen. Fedora has their share of bugs.RedHat, SUSE. Whatever you use, remeber that it is Linux. No one is immune. I support Linux as a whole. But lean towards Ubuntu as what I use and prefer.

What I like about the Ubuntu Community... There is not enough room on the page to describe that here. There is a good group of people here who sincerely want to help each other. I have made some very good friends here. I believe in this project, and want to make it work for people.

---

### Post by somebodeez on 2023-08-13
As it turns out the documentation is significantly more complex and time consuming than making the actual bug report, I started reading and quite quickly just entered 'ubuntu-bug' in a Terminal and made a report, whether I've made a report of the correct standard or not I'm not sure, but I have made it and described the problem I'm experiencing and that it is entirely repeatable.

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/2031240](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/2031240)

---

### Post by MAFoElffen on 2023-08-13
Let them decide where it goes, what package it goes to and how to handle it. You have done your part by reporting it. Thank you. I added a comment and am following it.

---

### Post by somebodeez on 2023-08-14
@MAFoElffen, Commenting on the bug report I think you got as confused about that incomplete thing as I did, that was me, after I nearly finished I noticed it said 'Incomplete' in the title/status bar, so I clicked on it expecting to get a to-do list of things to complete, but I didn't and it just changed to new and added that bit at the bottom of the bug report which didn't seem to have a delete option, so I left it at is was in case I screwed it up, and my bad for choosing 'upgrade' it seemed the correct option since I'd just received an update, but I guess it's in the correct section now.

For the time being Ubuntu is working as before on the old Kernel so I'll keep it as it is for now and if they want me to perform any tasks like crashing the network on the new Kernel and provide the necessary logs I'm quite happy to do that for them, it's not intermittent or anything, it is 100% repeatable so that won't be a problem, all they need to do is let me know what to do and I'll happily do it for them.

I'm always getting popups telling me there's updates available though, and given what's just happened and the catastrophic effect it had, I am extremely dubious about actually going a head and allowing any updates again for now, until this is fixed I'm definitely going to refrain from hitting the 'Install' button again, and if it isn't fixed then I don't believe it's an option to carry on with an operating system that can't be kept up to date, so obviously I would have to change, but for now it is working as it should on Kernel 5.19.0-50-generic so I'll leave it as it is.

Anyway what happened to the first guy, he's done what I was gonna do hasn't he, sod that, that's to much like hard work and he's off rocking Manjaro by now(probably).

---

### Post by MAFoElffen on 2023-08-14
LOL. Yup. Oh well. 

Yes. Kernel 6.2.0-26 has some "challenges". Some with the current linux-firmware package.

I'm finding issues with some i915 and amdgpu firmware... where things are there, loading, and should be working, but just don't. For me with 13thGen i9, (truly) missing firmware files...

---

### Post by osos1 on 2023-08-21
This might be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2028999](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2028999)

Please confirm your experience on that bug as well to ensure some attention

---

### Post by MAFoElffen on 2023-08-22
I made a link between, and with the info on that original bug report, may have traced the error to a kernel commit that changed on of the default settings. Just a suspicion. I quote the Kernel Change log on what is was about...

Please do 
```

sudo lshw -C Network | grep -e 'product:' -e 'driver='

```
to see if yours is using the same network module as a driver.

---

### Post by vtripolitakis on 2023-08-22
Hello all,

I had the very same issues which are apparent for about 2-3 weeks. I suspect they coincide with the 6.2 kernel rollout.
I upgraded my kernel to 6.2.16 and I can confirm that download speeds are back to normal (~1Gbps).
As a note, I had evidenced during my investigation that the number of dropped packets on the receiving (RX) side was high, contrary to the transmitting (TX) side which was zero.
Further, I had noticed that this didn't happen with all connections. Some connections were stable around 1Gbps and other (having a lot of dropped packets) were around 40-50Mbps. I suspect this is attributed to the TCP slow-start behaviour.

Regards,
Vangelis

---

### Post by MAFoElffen on 2023-08-22
@vtripolitakis -- Thank you for finding and testing that fix.

Looking into what they were discussing behind the scenes of that commit. I came up with these three queries to check on that on my server. If you both could run them on your machines, this may uncover what those might be:
```

mafoelffen@msi-ubuntu:~$ [COLOR=#ff0000]sudo lspci | grep 'Ethernet'[/COLOR]
06:00.0 Ethernet controller: Intel Corporation Device 125c (rev 04)
09:00.0 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)
09:00.1 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)
09:10.0 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
09:10.1 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
09:10.2 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
09:10.3 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
09:10.4 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
09:10.5 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
09:10.6 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
09:10.7 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
09:11.0 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
09:11.1 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
09:11.2 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
09:11.3 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
09:11.4 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
09:11.5 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)

# Based on the bus addresses of the NIC's, I came up with the RegEdit match to include those in this query:
mafoelffen@msi-ubuntu:~$ [COLOR=#ff0000]grep . /sys/bus/pci/devices/0000:0[6,9]:[0,1][0,1].[0-7]/*link* 2>/dev/null | grep -iv 'unknown'[/COLOR]
/sys/bus/pci/devices/0000:06:00.0/current_link_speed:5.0 GT/s PCIe
/sys/bus/pci/devices/0000:06:00.0/current_link_width:1
/sys/bus/pci/devices/0000:06:00.0/max_link_speed:5.0 GT/s PCIe
/sys/bus/pci/devices/0000:06:00.0/max_link_width:1
/sys/bus/pci/devices/0000:09:00.0/current_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:00.0/current_link_width:4
/sys/bus/pci/devices/0000:09:00.0/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:00.0/max_link_width:4
/sys/bus/pci/devices/0000:09:00.1/current_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:00.1/current_link_width:4
/sys/bus/pci/devices/0000:09:00.1/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:00.1/max_link_width:4
/sys/bus/pci/devices/0000:09:10.0/current_link_width:0
/sys/bus/pci/devices/0000:09:10.0/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:10.0/max_link_width:4
/sys/bus/pci/devices/0000:09:10.1/current_link_width:0
/sys/bus/pci/devices/0000:09:10.1/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:10.1/max_link_width:4
/sys/bus/pci/devices/0000:09:10.2/current_link_width:0
/sys/bus/pci/devices/0000:09:10.2/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:10.2/max_link_width:4
/sys/bus/pci/devices/0000:09:10.3/current_link_width:0
/sys/bus/pci/devices/0000:09:10.3/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:10.3/max_link_width:4
/sys/bus/pci/devices/0000:09:10.4/current_link_width:0
/sys/bus/pci/devices/0000:09:10.4/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:10.4/max_link_width:4
/sys/bus/pci/devices/0000:09:10.5/current_link_width:0
/sys/bus/pci/devices/0000:09:10.5/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:10.5/max_link_width:4
/sys/bus/pci/devices/0000:09:10.6/current_link_width:0
/sys/bus/pci/devices/0000:09:10.6/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:10.6/max_link_width:4
/sys/bus/pci/devices/0000:09:10.7/current_link_width:0
/sys/bus/pci/devices/0000:09:10.7/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:10.7/max_link_width:4
/sys/bus/pci/devices/0000:09:11.0/current_link_width:0
/sys/bus/pci/devices/0000:09:11.0/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:11.0/max_link_width:4
/sys/bus/pci/devices/0000:09:11.1/current_link_width:0
/sys/bus/pci/devices/0000:09:11.1/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:11.1/max_link_width:4
/sys/bus/pci/devices/0000:09:11.2/current_link_width:0
/sys/bus/pci/devices/0000:09:11.2/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:11.2/max_link_width:4
/sys/bus/pci/devices/0000:09:11.3/current_link_width:0
/sys/bus/pci/devices/0000:09:11.3/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:11.3/max_link_width:4
/sys/bus/pci/devices/0000:09:11.4/current_link_width:0
/sys/bus/pci/devices/0000:09:11.4/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:11.4/max_link_width:4
/sys/bus/pci/devices/0000:09:11.5/current_link_width:0
/sys/bus/pci/devices/0000:09:11.5/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:09:11.5/max_link_width:4

# And to see the driver used for each:
mafoelffen@msi-ubuntu:~$ [COLOR=#ff0000]sudo lshw -C Network | grep -e 'product:\|driver='[/COLOR]
       product: Intel Corporation
       configuration: broadcast=yes driver=iwlwifi driverversion=6.2.0-26-generic firmware=72.a764baac.0 so-a0-gf-a0-72.uc ip=10.0.0.11 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       product: Intel Corporation
       configuration: autonegotiation=on broadcast=yes driver=igc driverversion=6.2.0-26-generic duplex=full firmware=2017:888d ip=10.0.0.5 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       product: 82576 Gigabit Network Connection
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=6.2.0-26-generic duplex=full firmware=1.2.1 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       product: 82576 Gigabit Network Connection
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=6.2.0-26-generic firmware=1.2.1 latency=0 link=no multicast=yes port=twisted pair
       product: 82576 Virtual Function
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic duplex=full ip=10.0.0.10 latency=0 link=yes multicast=yes speed=1Gbit/s
       product: 82576 Virtual Function
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic latency=0 link=no multicast=yes
       product: 82576 Virtual Function
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic duplex=full ip=10.0.0.11 latency=0 link=yes multicast=yes speed=1Gbit/s
       product: 82576 Virtual Function
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic latency=0 link=no multicast=yes
       product: 82576 Virtual Function
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic duplex=full ip=10.0.0.12 latency=0 link=yes multicast=yes speed=1Gbit/s
       product: 82576 Virtual Function
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic latency=0 link=no multicast=yes
       product: 82576 Virtual Function
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic duplex=full ip=10.0.0.13 latency=0 link=yes multicast=yes speed=1Gbit/s
       product: 82576 Virtual Function
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic latency=0 link=no multicast=yes
       product: 82576 Virtual Function
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic duplex=full ip=10.0.0.14 latency=0 link=yes multicast=yes speed=1Gbit/s
       product: 82576 Virtual Function
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic latency=0 link=no multicast=yes
       product: 82576 Virtual Function
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic duplex=full ip=10.0.0.15 latency=0 link=yes multicast=yes speed=1Gbit/s
       product: 82576 Virtual Function
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic latency=0 link=no multicast=yes
       product: 82576 Virtual Function
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic duplex=full ip=10.0.0.16 latency=0 link=yes multicast=yes speed=1Gbit/s
       product: 82576 Virtual Function
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic latency=0 link=no multicast=yes

```

---

### Post by vtripolitakis on 2023-08-22
@MAFoElffen

there you are:
```
vulcan# lspci |grep 'Ethernet'
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
```

```
root@vulcan:/home/vaggelis# grep . /sys/bus/pci/devices/0000:0[3,9]:[0,1][0,1].[0-7]/*link* 2>/dev/null | grep -iv 'unknown'
/sys/bus/pci/devices/0000:03:00.0/current_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:03:00.0/current_link_width:1
/sys/bus/pci/devices/0000:03:00.0/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:03:00.0/max_link_width:1
```

**Note: now I'm running** ```
6.2.16-060216-generic
```

---

### Post by somebodeez on 2023-08-22
[FONT=Ubuntubeta][COLOR=#000000]@MAFoElffen[/COLOR][/FONT]

[FONT=Ubuntubeta][COLOR=#000000]I've seen this bug report has had some activity today, so just incase it's helpful in anyway, I've executed those as well for you.


[/COLOR][/FONT]```
sudo lspci | grep 'Ethernet'
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)




```

```
sudo lshw -C Network | grep -e 'product:\|driver='
       product: Ice Lake-LP PCH CNVi WiFi
       configuration: broadcast=yes driver=iwlwifi driverversion=6.2.0-26-generic firmware=72.daa05125.0 Qu-c0-hr-b0-72.uc ip=192.168.1.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=6.2.0-26-generic duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.1.10 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s

```

```
grep . /sys/bus/pci/devices/0000:0[6,9]:[0,1][0,1].[0-7]/*link* 2>/dev/null | grep -iv 'unknown'
Nothing, No output.


```

---

### Post by MAFoElffen on 2023-08-22
> **somebodeez said:**
> [FONT=Ubuntubeta][COLOR=#000000]@MAFoElffen[/COLOR][/FONT]

[FONT=Ubuntubeta][COLOR=#000000]I've seen this bug report has had some activity today, so just incase it's helpful in anyway, I've executed those as well for you.


[/COLOR][/FONT]```
sudo lspci | grep 'Ethernet'
[COLOR=#ff0000]01:00.0[/COLOR] Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)




```

```
sudo lshw -C Network | grep -e 'product:\|driver='
       product: Ice Lake-LP PCH CNVi WiFi
       configuration: broadcast=yes driver=iwlwifi driverversion=6.2.0-26-generic firmware=72.daa05125.0 Qu-c0-hr-b0-72.uc ip=192.168.1.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       configuration: autonegotiation=on broadcast=yes driver=[COLOR=#ff0000]r8169[/COLOR] driverversion=[COLOR=#ff0000]6.2.0-26-generic[/COLOR] duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.1.10 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s

```

```
[COLOR=#ff0000]grep . /sys/bus/pci/devices/0000:0[6,9]:[0,1][0,1].[0-7]/*link* 2>/dev/null | grep -iv 'unknown'[/COLOR]

```
Nothing, No output.

With your output, your amended RegEdit for that command should be
```

grep . /sys/bus/pci/devices/0000:0[1]:[0][0].[0]/*link* 2>/dev/null | grep -iv 'unknown'

```
Try that...

---

### Post by somebodeez on 2023-08-22
[COLOR=#000000][FONT=Ubuntubeta][I]@MAFoElffen

[/I][/FONT][/COLOR]Here you go, it seems I've got the same output as **vtripolitakis** [COLOR=#000000]apart from [/COLOR]01:00.0 instead of 03:00.0

```

grep . /sys/bus/pci/devices/0000:0[1]:[0][0].[0]/*link* 2>/dev/null | grep -iv 'unknown'
/sys/bus/pci/devices/0000:01:00.0/current_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:01:00.0/current_link_width:1
/sys/bus/pci/devices/0000:01:00.0/max_link_speed:2.5 GT/s PCIe
/sys/bus/pci/devices/0000:01:00.0/max_link_width:1

```

---

### Post by MAFoElffen on 2023-08-22
I think I need to modify the query.

Here is what was discussed (snippet):
```

diff --git a/Documentation/ABI/testing/sysfs-bus-pci b/Documentation/ABI/testing/sysfs-bus-pci
index 8bfee557e..c86c8ab00 100644
--- a/Documentation/ABI/testing/sysfs-bus-pci
+++ b/Documentation/ABI/testing/sysfs-bus-pci
@@ -347,3 +347,17 @@ Description:
         If the device has any Peer-to-Peer memory registered, this
             file contains a '1' if the memory has been published for
         use outside the driver that owns the device.
+
+What:        /sys/bus/pci/devices/.../link_pm/clkpm
+        /sys/bus/pci/devices/.../link_pm/l0s_aspm
+        /sys/bus/pci/devices/.../link_pm/l1_aspm
+        /sys/bus/pci/devices/.../link_pm/l1_1_aspm
+        /sys/bus/pci/devices/.../link_pm/l1_2_aspm
+        /sys/bus/pci/devices/.../link_pm/l1_1_pcipm
+        /sys/bus/pci/devices/.../link_pm/l1_2_pcipm
+Date:        October 2019
+Contact:    Heiner Kallweit <hkallweit1@gmail.com>
+Description:    If ASPM is supported for an endpoint, then these files
+        can be used to disable or enable the individual
+        power management states. Write y/1/on to enable,
+        n/0/off to disable.

```
Where they added link_pm into the sysfss to change that, so the path comes out as....
```

/sys/bus/pci/<device_name>/link_pm/*

```
So the query should probably rather be this to see if the patch is applied
```

grep . /sys/bus/pci/0000:[0,1][0-9]:[0,1][0,1].[0-7]/link_pm/* | grep -iv 'unknown'

```
If the output says "No such file or directory", then the patch is not applied.

---

### Post by MAFoElffen on 2023-08-22
Typo in last post and won't let me edit it. Should be

Path:
```

/sys/bus/pci/devices/<device_name>/link_pm/*

```
Query:
```

grep . /sys/bus/pci/devices/0000:[0,1][0-9]:[0,1][0,1].[0-7]/link_pm/* | grep -iv 'unknown'

```

---

### Post by somebodeez on 2023-08-22
With that new query the output is No such file or directory.

```

grep . /sys/bus/pci/devices/0000:[0,1][0-9]:[0,1][0,1].[0-7]/link_pm/* | grep -iv 'unknown'
grep: /sys/bus/pci/devices/0000:[0,1][0-9]:[0,1][0,1].[0-7]/link_pm/*: No such file or directory

```

---

### Post by bast1aan on 2023-08-29
When moving to the 6.2 kernel I immediatly got problems with my display and USB dock. Before I was running the 6.1 mainline kernel and everything worked OK.
I don't quite understand why Ubuntu is using the 6.2 kernel. It is already unmaintained according to kernel.org, so that means they have to backport all kind of patches to maintain it..

---

### Post by ubfan1 on 2023-08-29
Maybe for the scheduled release (Apr.) of 23.04, the 6.2 kernel was the lastest tested choice, and that eventually works its way back to the hwe packages for the LTS releases.  Anyway, they'll only maintain it 9 months before the next release supercedes it.

---

### Post by Jingo on 2023-11-09
Installing r8168-dkms seems to solve or at least increase the speed.

> apt install r8168-dkms

suggested here: [https://askubuntu.com/q/1488178](https://askubuntu.com/q/1488178)

---

### Post by MAFoElffen on 2023-11-09
Can you go out to that bug report and say that please?

---

