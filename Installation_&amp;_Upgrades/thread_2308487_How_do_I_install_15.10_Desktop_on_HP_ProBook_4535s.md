---
title: "How do I install 15.10 Desktop on HP ProBook 4535s"
date: 2016-01-03
forum: Installation &amp; Upgrades
---

### Post by robert48 on 2016-01-03
Hello

I've downloaded, burnt and checked the latest 15.10 Desktop 64bit CD iso.

I put it in a 3.5 year old HP Probook 4535s notebook and it starts to install ok. It gets to 'Installing the 'grub2' package...' part, about 2/3rds into the install, and then just hangs. I left it overnight to see if that would help and it didn't help. The notebook has been running Ubuntu 12.04 to 14.04 for its life. The latest attempt to upgrade by fresh install is my current goal.  

The drive I am trying to install to is a sata 500GB HDD. The bios settings are for sata AHCI and the UEFI is the default boot method.

I've tried with a usb startup but that just returned "boot error"

I'm at a loss at what to try next. Any ideas?

Bob

---

### Post by coldraven on 2016-01-04
Firstly are you sure it hangs or is it just the screen going to sleep? I don't know why install discs have the screen saver enabled, it always freaks me out when it appears to have crashed.
Secondly, I had problems using 15.10 on this 5 y.o. HP 6715b laptop when a kernel upgrade was installed recently. I had to roll back to a previous kernel, see my post here:
[http://ubuntuforums.org/showthread.php?t=2300290&p=13399995#post13399995](http://ubuntuforums.org/showthread.php?t=2300290&p=13399995#post13399995)

I know this does not solve your problem but at least you will be aware of it.
Oops! I meant that I fixed it by following the advice in that post (the first link)

---

### Post by oldfred on 2016-01-04
Just to see all the details:

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by robert48 on 2016-01-07
Hi guys, thanks for all your comments.

I fiddled around with the BIOS (I have the latest apparently dated 2012) and disabled UEFI. The notes in the BIOS said it was BETA software and cautioned about using it. After a number of attempts, using a live CD with a live usb I managed to get a desktop. However the boot was very slow and the Network Interface Controller did not work (RJ45 port). I am thinking that the NIC may be related to boot problems.

I ran ```
sudo lshw -c network
``` and got:-

*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 06
       serial: 10:1f:74:f3:72:4b
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:30 ioport:5000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlo1
       version: 01
       serial: 74:de:2b:81:de:c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.2.0-23-generic firmware=N/A ip=192.168.1.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:d5000000-d500ffff

The wireless interface wlo1 works ok, the wired interface enp2s0 does not. I was expecting to see eth0 for the Ethernet interface.

```
sudo ifconfig
``` returns:-

enp2s0    Link encap:Ethernet  HWaddr 10:1f:74:f3:72:4b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24134 (24.1 KB)  TX bytes:24134 (24.1 KB)

wlo1      Link encap:Ethernet  HWaddr 74:de:2b:81:de:c8  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76de:2bff:fe81:dec8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67011 (67.0 KB)  TX bytes:19057 (19.0 KB)

I tried the off and on staple fix with ```
sudo ifconfig enp2s0 down && sudo ifconfig enp2s0 up
``` but I still could not use the port. My ethernet cable works fine on another machine.

Any ideas as to what I am missing here?

---

### Post by oldfred on 2016-01-07
Do not know specifics on wireless drivers, many threads though on those issues.
Can you use a wired Ethernet connect for Install? That usually works and is much faster.

Have you updated UEFI/BIOS from HP to newest version for your system? That often fixes many issues particularly if stated as new/experimental.

Some other HP, may be similar as UEFI is often the same even for different models by brand.
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
      
 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try different USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by robert48 on 2016-01-07
Progress...bit by bit (almost literally!)

The slow boot and black screen, (boot about 5 minutes or so, black screen hides Desktop, fn_f1 puts machine to sleep, press of power button brings up Desktop) is over.

The fix was discovered when playing with grub and a warning was shown when doing update-grub which said 'Warning, GRUB_HIDDEN_TIMEOUT=0 when GRUB_TIMEOUT is set is no longer supported.'

So I went to ```
sudo gedit /etc/default/grub

``` and put a # to comment out GRUB_HIDDEN_TIMEOUT=0 as below:-

...
GRUB_DEFAULT=0
# GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
...
All is now well with an acceptable normal boot period and a visible Desktop at end of boot. Note that this was the first change I have made to this file. It seems to ship with the 'warning' configuration as default! It should be looked at in my opinion.

The only remaining issue for me is to get the NIC working. Any specific ideas on that?

Thanks again for the hand holding, I really do appreciate it.

EDIT

Found it! Upon close inspection of the RJ45 port using a x25 eye glass I discovered (clip to the bottom) pins 1 and 2 from the left, buckled and a bit wobbly. Someone has been rather reckless in pushing an object into the port. I have straightened out the pins as best I can to stop any short across them but the port is lost I think. Soldering on a new port is a tad too risky given that wireless works ok. The wobbly pins could well have been the cause of the malaise although I did get a clean boot (repeatable) when I made the amendment to the grub file above. Anyway, pleased I got there in the end, Many thanks to all for the generous assistance, I learned a lot!

Best Regards
Bob

---

### Post by oldfred on 2016-01-07
Best to start a separate thread on wireless issue with that in title.

I think this is what they want & there is a wireless or Ethernet script available. Look at sticky threads.
lspci > ~/abs-network.txt
lsusb >> ~/abs-network.txt
ifconfig >> ~/abs-network.txt
iwconfig >> ~/abs-network.txt
Attach (via the paperclip in advanced edit menu) the abs-network.txt file which will be in your home folder.

---

