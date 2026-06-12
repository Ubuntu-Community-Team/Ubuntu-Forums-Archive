---
title: "Ad-hoc network, NM --&gt; Oops"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gunksta on 2010-03-18
I'm using Kubuntu, but I suspect that I will need to play with the command line to fix this -- which is fine -- I used the CLI to break it all in the first place. I'm using an updated version of Lucid. AFAIK, it was not an upgrade that broke the system -- I think it was my playing around.

When I'm on the road I often use my Blackberry to get me an Internet connection, in places where wireless is a non-starter. This week, I wanted to share my connection with a co-worker. I attempted to set up an ad-hoc network and somewhere in the process, I managed to break network manager. Not I can't use my wireless at all, although the light is on and I know the STA module is loaded.

The wireless card is a broadcom 4312, that was working 100% fine. I know I installed (and then removed) dnsmasq and played with some things I found on the Internet. I thought NM would take over again on a restart -- which it did the first few times. Not sure what I changed, but NM is now disabled and I can't seem to get my network cards (other than the external crack-berry) to work at all.

Here is lshw output:

andy@Yates:~$ sudo lshw -c network                                                                                                                               
[sudo] password for andy:                                                                                                                                        
  *-network DISABLED                                                                                                                                             
       description: Ethernet interface                                                                                                                           
       product: 82567LM Gigabit Network Connection                                                                                                               
       vendor: Intel Corporation                                                                                                                                 
       physical id: 19                                                                                                                                           
       bus info: pci@0000:00:19.0                                                                                                                                
       logical name: eth0
       version: 03
       serial: 00:26:b9:a7:50:b7
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.7-7 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f6ae0000-f6afffff memory:f6adb000-f6adbfff ioport:efe0(size=32)
  *-network DISABLED
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: c4:17:fe:64:25:4c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


The last "card" is not a problem -- it's virtual.

Here is what I have in /etc/NetworkManager/nm-system-settings.conf

# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


I did try to change this to true, but that resulted in NM continuing to be disabled and the light on my wireless card no longer responded to my use of the external on-off switch for the wireless card.

When I run ifconfig, the only network connections I see are loopback and my ppp connection via the blackberry.

Thoughts?

---

### Post by go2dell on 2010-03-18
Could your problem be related to [Bug #526272]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/526272")?

---

### Post by gunksta on 2010-03-18
I suppose it is possible, but I think it is a separate issue. For example, my applet tells me that NetworkManager has been disabled. See this - 

andy@Yates:~$ nm-tool

NetworkManager Tool

State: asleep

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unmanaged
  Default:           no
  HW Address:        00:26:B9:A7:50:B7

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unmanaged
  Default:           no
  HW Address:        C4:17:FE:64:25:4C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 




For some reason NetworkManager is refusing to take control of my network devices. Not sure why. And, I'm not sure if I am experiencing a bug or if I've managed to tweak a setting somewhere, that's the frustrating part. It could be something stupid that I've done.

---

### Post by gunksta on 2010-03-18
I do love Kubuntu - but I was able to fix this EASILY by installing nm-applet. Somehow I had managed to get NetworkManager to NOT manage my network connections. The KDE applet does not include a way to re-engage NetworkManager. The default nm-applet makes this real easy. Now I can see and use my networks again.

---

