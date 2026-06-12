---
title: "Cannot connect to detected WiFi"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sephoroth on 2009-10-03
Hey everyone,

For some reason my Ubuntu installation (Karmic Koala) has suddenly lost the ability to connect to the internet via WiFi (though it can detect many connections).  I am not so sure this is a Karmic Koala issue as I've seen similar issues from others occurring before and it potentially happened to me once on Jaunty Jackelope.  I am unsure if this has something to do with recent installation of kubuntu-desktop and network manager conflictions.  Since its installation, I have removed Kubuntu altogether along with NetworkManager which has been replaced with Wicd (which hasn't solved any issues).

My Broadcom BCM4322 isn't able to connect to secure or insecure connections despite having no problems with WiFi in Windows or ethernet in Ubuntu.

[quote=ifconfig]
eth2      Link encap:Ethernet  HWaddr 00:24:2c:20:c1:ef  
          inet6 addr: fe80::224:2cff:fe20:c1ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:7625
          TX packets:4 errors:262 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:452 (452.0 B)  TX bytes:572 (572.0 B)
          Interrupt:21 

eth2:avahi Link encap:Ethernet  HWaddr 00:24:2c:20:c1:ef  
          inet addr:169.254.9.140  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:65 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5771 (5.7 KB)  TX bytes:5771 (5.7 KB)
[/quote]

[quote=lshw]  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:22:19:e7:e7:0c
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.102 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:19 memory:f0888000-f0888fff ioport:30d0(size=8) memory:f0889c00-f0889cff memory:f0889800-f088980f
  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth2
       version: 01
       serial: 00:24:2c:20:c1:ef
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:21 memory:f0400000-f0403fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
[/quote]

[quote=iwconfig]lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:232  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.
[/quote]
Any help would be appreciated.  Thanks.


Edit - I also thought I'd add I am running the restricted "Broadcom STA Wireless driver" (wl) and am on an x64 release (though probably irrelevant).

---

### Post by Sephoroth on 2009-10-03
I also thought I'd add I am running the restricted "Broadcom STA Wireless driver" (wl) and am on an x64 release (though probably irrelevant).

---

### Post by Niels den Otter on 2009-10-05
There appear to be a lot of threads talking about broken wireless (&& NetworkManager?).

I have the same Broadcom hardware you have (using Macbook 5,1) and I use the STA drivers. Connecting to wireless was sometimes problematic, but appears to broke completely a couple of days ago. This morning I tried booting previous kernel (2.6.31-10-generic) and this appears to make big difference. I am now able to connect again.

Could you try if this works for you?


-- Niels

---

### Post by Nazty on 2009-10-06
I am not really sure if this info is really relevant in your cases guys but I had similar problems after upgrading to v.9.10... I decided to uninstall the Network Manager's packages and get the latest ones in attempt to fix this issue and it worked for me with my Intel 4965 AGN Wi-Fi adapter. Follow the steps below if you would like to try this as well. 


> # First uninstall Network Manager and its related packages

sudo apt-get remove network-manager-gnome network-manager network-config network-manager-openconnect network-manager-vpnc


> 
# Next add this to your apt sources.list:

deb [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main


> # and import the PPA key:

    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BC8EBFE8 


> # Next run the following

    sudo apt-get update; sudo sudo apt-get install network-manager-gnome network-manager network-config network-manager-openconnect network-manager-vpnc

# Which should bring you the latest NM trunk dailies; reboot after this 


*  You can find the links to the NM's PPA repository on this website - [http://www.asoftsite.org/s9y/archives/164-ubuntu-network-manager-team-offers-daily-builds-for-trunk-aka-0.8-now.html]("http://www.asoftsite.org/s9y/archives/164-ubuntu-network-manager-team-offers-daily-builds-for-trunk-aka-0.8-now.html")


I hope this helps!

---

### Post by Grimhound on 2009-10-06
> **Nazty said:**
> I had this problem as well after upgrading to v.9.10... I decided to re-install the Network Manager packages in attempt to fix the issue and it worked for me with my Intel 4965 AGN Wi-Fi adapter. Follow the steps below if you would also like to try this. 


# First uninstall network manager and its related packages

sudo apt-get remove network-manager-gnome network-manager network-config network-manager-openconnect network-manager-vpnc


# Next add this to your apt sources.list:

deb [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main


# and import the PPA key:

    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BC8EBFE8 


# Next run

    sudo apt-get update; sudo sudo apt-get install network-manager-gnome network-manager network-config network-manager-openconnect network-manager-vpnc


# Which should bring you the latest NM trunk dailies; reboot after this 


*  You can find the links to the NM's PPA repository on this website - [http://www.asoftsite.org/s9y/archives/164-ubuntu-network-manager-team-offers-daily-builds-for-trunk-aka-0.8-now.html]("http://www.asoftsite.org/s9y/archives/164-ubuntu-network-manager-team-offers-daily-builds-for-trunk-aka-0.8-now.html")


I hope this helps!

Thank you so much!
[IMG]http://imgur.com/P1Jfv.jpg[/IMG]

---

### Post by Niels den Otter on 2009-10-06
Thanks for your suggestion. I added the NetworkManager PPA to my sources.list, but this didn't make a difference for me. Today a new kernel package arrived (2.6.31-12-generic) and my problem is now solved (this message is the proof ;-)).

May be some drivers build incorrectly or ....? Could have been anything. 

Anyway thanks again. I use the latest kernel && wireless again.


-- Niels

---

### Post by 16sinker on 2009-10-06
> **Niels den Otter said:**
> Thanks for your suggestion. I added the NetworkManager PPA to my sources.list, but this didn't make a difference for me. Today a new kernel package arrived (2.6.31-12-generic) and my problem is now solved (this message is the proof ;-)).

May be some drivers build incorrectly or ....? Could have been anything. 

Anyway thanks again. I use the latest kernel && wireless again.


-- Niels

So Niels, if you couldn't "connect to detected Wifi", how did you get the update to 2.6.31-12? Just curious, as I would also like to get that update, but I can't connect to the internet on my Ubuntu machine. Any help would br appreciated.

---

### Post by mudi on 2009-10-06
Every time I've had trouble connecting to a network via Network Manager, I open up a terminal and

>sudo stop network-manager
>sudo start network-manager

And everything works smoothly after that.  Just a thought...

(for some reason 'restart' doesn't work the same way, even though in theory it should be exactly the same.  weird)

---

### Post by 16sinker on 2009-10-06
Thanks, but stopping and starting network-manager as you suggested, didn't do a thing for me. When I started network-manager the terminal output was "running process 1598." Any idea what that means? I still am not connected, even with my normal network shown as available.

---

### Post by kindofabuzz on 2009-10-06
I had the same thing happen on a fresh install of 9.10. Hooked up an ethernet cable and did updates. there was an update to NM. Worked fine after that.

---

### Post by Sephoroth on 2009-10-07
> **Niels den Otter said:**
> There appear to be a lot of threads talking about broken wireless (&& NetworkManager?).

I have the same Broadcom hardware you have (using Macbook 5,1) and I use the STA drivers. Connecting to wireless was sometimes problematic, but appears to broke completely a couple of days ago. This morning I tried booting previous kernel (2.6.31-10-generic) and this appears to make big difference. I am now able to connect again.

Could you try if this works for you?


-- Niels

Thanks for the advice.  I hadn't realized I had done a kernel update before my last restart XD.  WiFi is back in order (and am typing from it now).

> **Niels den Otter said:**
> Thanks for your suggestion. I added the NetworkManager PPA to my sources.list, but this didn't make a difference for me. Today a new kernel package arrived (2.6.31-12-generic) and my problem is now solved (this message is the proof ;-)).

May be some drivers build incorrectly or ....? Could have been anything. 

Anyway thanks again. I use the latest kernel && wireless again.


-- Niels


For some reason, the 2.6.31-12-generic isn't showing up under GRUB (or Startup Manager) even though it should have been installed on a very recent Partial Upgrade which included a regeneration of GRUB's config files....

> **16sinker said:**
> So Niels, if you couldn't "connect to detected Wifi", how did you get the update to 2.6.31-12? Just curious, as I would also like to get that update, but I can't connect to the internet on my Ubuntu machine. Any help would br appreciated.

Read what I quoted XD.

---

### Post by 16sinker on 2009-10-07
OK, problem solved by disconnecting router and connecting ethernet wire to my Ubuntu machine. I had 82 updates awaiting me, including network manager update. I don't have time to take the updates now , but I feel sure this will solve my wifi connection problem this afternoon when I do take them. Thanks for the simple solution.

---

