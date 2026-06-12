---
title: "eth1 but no ip?"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by susan on 2006-09-26
Hi folks,
I'm trying to introduce my sister to linux. I'm in Ga she's in NC so I can't jump on her box but I'm in need of some help.
Ok, she's using netgear 511, which uses Rtl 8169 chipset, I have 2 and I know they work.

I cannot for the life of me get her connected. She has cable broadband so this should be easy! I've run gentoo, arch, dsl, elive, debian several BSD's all with this nic.....I am doing something stupid - please point it out.
we've done ifup eth1 (the rtl nic is on eth1),dhclient eth1, and we've gone through the gui network setting config app. 

What am i forgetting folks? I want my sister to come on over to the darkside and I picked ubuntu so she would not get scared off.....and here I am not able to do the basics for her LOL.

Specifically, she is using kubuntu Dapper but I'm sure you folks can help me](*,) 

Thanks in advance,

McRae

---

### Post by susan on 2006-09-27
bump

the card is detected......

---

### Post by wieman01 on 2006-09-27
Ok, tell me quickly... Is this a wired or wireless network? Then I'll start right away.

---

### Post by wieman01 on 2006-09-27
I assume it wireless... Please do the following to help us help you. :-)

Post the contents of:
> ifconfig
> iwconfig
> iwlist eth1 scan
> route
> gedit /etc/network/interfaces
> gedit /etc/resolv.conf
> sudo /etc/init.d/networking restart
Run the commands from a terminal & post the contents. It's important to understand what's going on. 

Also are you using any kind of encryption/authentication? WEP, WPA, WPA2? Does the router have DHCP enabled? MAC filtering enabled?

---

### Post by susan on 2006-09-27
Wow, look at all the help:) 

It's wired ethernet. I'm not at the computer but ifconfig shows eth1 with no inet address.

etc/network/interfaces we configured with auto eth1

nothing in etc/resolv.conf - I would think dhcp would supply this - no?

That's all I can give from memory. When I get home I'll get her on the phone and show her how to log onto the account i've set up for her here. I told her ya'll would be gentle;) 

I'll follow along with her on phone. Thanks for the support. Looks like your forum actually lives up to it's friendly reputation.

---

### Post by wieman01 on 2006-09-27
WAH... Guys, a gal! HELP! ;-)

Please make sure that you show us "/etc/network/interfaces" and tell us a bit more about your hardware. The reason why I mention hardware is that the problem could lie there.

In particular if you connect to a modem that serves as we DHCP router. Very often the cables that are shipped along with the modems are so-called "cross-over" ethernet cables meant for PC-to-PC usage. Fell into the same trap once.

"/etc/network/interfaces" is most important as well as the output of "sudo /etc/init.d/networking restart". We'll figure out the rest.

---

### Post by susan on 2006-09-27
Hi, 
OK, I've got my sister susan on the phone (she's not online - yet) and I'm going to have her run this and give me the out put. Here is what we have:
The computer is an IBM a21p using a netgear 511 ethernet nic, which uses a common realtek chipset(wired). 

lspci shows - shows the realtek being detected.

/etc/network/interfaces shows

auto lo 
iface lo inet loopback

auto eth0 
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto atho 
iface atho inet dhcp

auto wlan0
iface wlan0 inet dhcp 

Wieman01 asked about the cord - the cable cord between her box and modem is cat 5 patch cord. 

Thanks again for helping. If we can get her connected you'll get a pretty new forum member!
Let me know your next thoughts..

McRae

---

### Post by NetworkGuy on 2006-09-27
Stupid question?  Is there a Internet router involved?   

If not, have you tried rebooting the cablem modem with the computer turned on and working?

---

### Post by susan on 2006-09-27
network guy, no router involved she told me she plugs straight into the modem.....rebooting the modem > if that is it ..... i'm going to be very embarrassed - but happy;) Let me call her and do it. I'll report back in a minute.

McRae

---

### Post by NetworkGuy on 2006-09-27
Make sure you run sudo dhclient eth1 after the modem has rebooted.

---

### Post by susan on 2006-09-27
NetWork Guy - Well I'm happy, but feeling stupid. That was it!
I'm so glad that I could tell my sister had nothing to do with Linux!! Hopefully we've made a convert of her.

Wieman01 & Networkguy - We thank you!! I'm sure Susan will be logging in later now that she has entered the linux world.


Yahoooooo

Thanks Again,
McRae (Susan's Brother)

---

### Post by NetworkGuy on 2006-09-27
No problem.

And welcome to the community.

---

### Post by wieman01 on 2006-09-28
Yeah, welcome, mate. You'll enjoy this forum. Wired ethernet is a piece of cake. :-) Try wireless!

---

### Post by Psquared on 2006-10-24
> **wieman01 said:**
> Yeah, welcome, mate. You'll enjoy this forum. Wired ethernet is a piece of cake. :-) Try wireless!

OK, here we go ....

ifconfig:

> 

eth0      Link encap:Ethernet  HWaddr 00:0F:B0:56:E7:75  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe56:e775/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2709 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2876 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2160855 (2.0 MiB)  TX bytes:413110 (403.4 KiB)
          Interrupt:185 Base address:0x3000 

eth1      Link encap:UNSPEC  HWaddr 00-02-3F-51-65-40-A0-DD-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:32 dropped:32 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5104 (4.9 KiB)  TX bytes:5104 (4.9 KiB)


iwconfig


> 
root@Laptop[/home/Peyre]# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.


iwlist eth1 scan

> 
root@Laptop[/home/Peyre]# iwlist eth1 scan
eth1      Interface doesn't support scanning.



route

> 
root@Laptop[/home/Peyre]# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
root@Laptop[/home/Peyre]# 




gedit /etc/network/interfaces

> 
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

iface eth1 inet dhcp




gedit /etc/resolv.conf 

> 
search midsouth.rr.com
nameserver 65.24.7.3



sudo /etc/init.d/networking restart

> 
root@Laptop[/home/Peyre]# /etc/init.d/networking restart
Reconfiguring network interfaces...ifup: interface lo already configured
Internet Software Consortium DHCP Client 2.0pl5
Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
All rights reserved.

Please contribute if you find this software useful.
For info, please visit [http://www.isc.org/dhcp-contrib.html](http://www.isc.org/dhcp-contrib.html)

sit0: unknown hardware address type 776
eth1: unknown hardware address type 24
sit0: unknown hardware address type 776
eth1: unknown hardware address type 24
Listening on LPF/eth0/00:0f:b0:56:e7:75
Sending on   LPF/eth0/00:0f:b0:56:e7:75
Sending on   Socket/fallback/fallback-net
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.102 -- renewal in 43200 seconds.
done.
root@Laptop[/home/Peyre]# 


How come I have no wireless? This is a Toshiba Laptop with Intel Proset IPW2200BG builtin NIC. Works fine with Windows. Network-Manager shows 2 ethernet cards - no wireless.

Thanks in advance.

---

### Post by wieman01 on 2006-10-24
A IPW2200? That should work out of the box. Got one myself. Have you installed "gnome-network-manager" by chance? Or perhaps Wifi-Radar?

---

### Post by Psquared on 2006-10-25
> **wieman01 said:**
> A IPW2200? That should work out of the box. Got one myself. Have you installed "gnome-network-manager" by chance? Or perhaps Wifi-Radar?

I have both installed. Maybe I should mention I am using Elive??? However, it shouldn't make any difference because it uses the same interfaces, commands, etc.

Wifi-Radar scans but says there are no wireless extensions present. It also says that eth1 does not support scanning. It is treating eth0 and eth1 as wired ethernet. Wifi-radar does give me the option to setup a wifi, but i have to manually enter the SSID. It does not detect the broadcast SSID. Should I set it up manually?

When I first installed Elive Network-Manager showed a wireless card, but after some upgrades, which I was compelled to do, the wireless card went away.

What to do? Will Wifi-radar setup wifi when the system does not detect the presence of the ipw2200?

---

### Post by wieman01 on 2006-10-25
> **Psquared said:**
> What to do? Will Wifi-radar setup wifi when the system does not detect the presence of the ipw2200?
First of all I am afraid that tools such as Wifi-Radar or NetworkManager won't be of much help. You need to set up the driver manually. The bad news is that your system has not been recognized out of the box. The good news is there is a fairly reliable howto that I have successfully used as well to update my driver & wireless framework:

[http://www.ubuntuforums.org/showthread.php?t=26623&highlight=howto+ipw2200]("http://www.ubuntuforums.org/showthread.php?t=26623&highlight=howto+ipw2200")

I would try it first before we go ahead.

---

### Post by Psquared on 2006-10-25
Thanks ... I've tried that already and it was a no go. Luca's "how to" won't work on Elive because the Makefile looks for the kernel headers where Ubuntu installs them, and Elive installs them someplace else.

I was thinking I could modify the "Makefile" but I'm not an advanced enough user to do that. I did go into Synaptic this morning and found IPW2200 vers. 1.0.3 and installed it. I have not had a chance to check, but lets assume that ipw2200 is now installed and compiled with ieee80211. Where do we go from there?

---

### Post by wieman01 on 2006-10-25
I don't know much about Elive to be honest.

Assuming that the driver has been installed & is working, a scan should detect your network:
> iwlist scan
Before you scan please update your "interfaces" configuration file:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp
Please the results.

---

### Post by Psquared on 2006-10-26
> **wieman01 said:**
> I don't know much about Elive to be honest.

Assuming that the driver has been installed & is working, a scan should detect your network:

Before you scan please update your "interfaces" configuration file:

Please the results.

No luck. I get the message saying it can't scan.

The hardware is not being detected because its not setup properly. Back to the drawing board.

I found a website that describes a method where I can point the "make" to the correct directory. I tried to do that, but the versions of ieee80211 and ipw2200 must be incompatible. I need to uninstall/delete all the files and start from scratch.

---

### Post by wieman01 on 2006-10-26
One stumbling-block usually is the wireles hardware switch. Sometime the wireless network is simply turned off, and you will have to turn it on by "switching" it on (FN + Fx). Just a thought... perhaps the problem is just as simple (have seen it before).

---

### Post by Psquared on 2006-10-26
> **wieman01 said:**
> One stumbling-block usually is the wireles hardware switch. Sometime the wireless network is simply turned off, and you will have to turn it on by "switching" it on (FN + Fx). Just a thought... perhaps the problem is just as simple (have seen it before).

No, its on. The switch is on the side. A light comes on when it is switched on. Besides, it works in Windows.

I've downloaded the files

firmware
ieee80211
ipw2200

Luca's guide doesn't work. The make fails citing a "rules" error. <sigh> unless you know of something else I guess I'll delete all references to the existing ipw2200 and ieee80211 and start from scratch.

---

### Post by wieman01 on 2006-10-26
Honestly I won't be able to help you much if you're not using 100% pure Ubuntu if you know what I mean. Sitting in front of your computer would somehow change things, but remotely I am afraid I won't be much of help...

---

### Post by Psquared on 2006-10-27
> **wieman01 said:**
> Honestly I won't be able to help you much if you're not using 100% pure Ubuntu if you know what I mean. Sitting in front of your computer would somehow change things, but remotely I am afraid I won't be much of help...

I understand. I am going to make it a work in progress. I think if I follow the instructions for installing the firmware and compiling ieee80211 and ipw2200 in the right folder it might get done. I'm surprised no one on the Elive forum has not posted a How To, but I guess its so new.

It is very cool anyway. First time I've used Enlightenment where everything "almost" worked. I was having trouble with sound, but I got that working so I can beat this problem.

Might pop in from time-to-time and ask a specific "make" or "build" question.

Thanks for your efforts.

---

### Post by xiownthisplacex on 2006-11-10
Hi everyone.. I have a problem with the wireless also.. At school(in windows) we need to download a file called SecureW2 in order to access the essid=e-U
Now, ive just installed Ubuntu 6.1 and i needed to do this [http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102) in order to get my wireless working in ubuntu..
But i could only get the guest-e-U(thats for us to connect in order to download the SecureW2) and i cant even see the e-U on network-manager.
when i do wut wieman01 asked to do i get this:
ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:C0:A8:A9:FD:16  
          inet6 addr: fe80::2c0:a8ff:fea9:fd16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:229755 (224.3 KiB)  TX bytes:3777 (3.6 KiB)
          Interrupt:177 Memory:c0200000-c0202000 

eth1      Link encap:Ethernet  HWaddr 00:03:25:33:00:E3  
          inet addr:10.10.1.19  Bcast:10.10.255.255  Mask:255.255.0.0
          inet6 addr: fe80::203:25ff:fe33:e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:907 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:769222 (751.1 KiB)  TX bytes:263100 (256.9 KiB)
          Interrupt:50 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6560 (6.4 KiB)  TX bytes:6560 (6.4 KiB)

iwconfig:
lo        no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

eth0      IEEE 802.11b  ESSID:"guest-e-U"  Nickname:"e-U"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:14:F2:8F:3B:70   
          Bit Rate=11 Mb/s   Tx-Power:25 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-57 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist eth1 scan:

eth1      Interface doesn't support scanning.

iwlist eth0 scan:

eth0      Scan completed :
          Cell 01 - Address: 00:40:05:31:FE:8C
                    ESSID:"openDeec"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-81 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:14:F2:7E:3F:E0
                    ESSID:"guest-e-U"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-81 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:14:F2:8F:3B:70
                    ESSID:"guest-e-U"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:0/100  Signal level:-54 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

route:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.0.0       *               255.255.0.0     U     0      0        0 eth1
default         10.10.254.254   0.0.0.0         UG    0      0        0 eth1

gedit /etc/network/interfaces:

auto lo
iface lo inet loopback

iface eth1 inet dhcp



auto eth1

gedit /etc/resolv.conf:

search deec.uc.pt
nameserver 10.10.0.1


sudo /etc/init.d/networking restart:

* Reconfiguring network interfaces...                                                                                                                       There is already a pid file /var/run/dhclient.eth1.pid with pid 7955
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:03:25:33:00:e3
Sending on   LPF/eth1/00:03:25:33:00:e3
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 10.10.0.1
bound to 10.10.1.19 -- renewal in 3385 seconds.


A little help connecting to e-U please? Thanx.

---

### Post by wieman01 on 2006-11-10
You need to download a file & store it on your PC? Man, this sounds a bit like EAP... Tough encryption standard, but not sure if that's really the case.

Can you get more details from you network administrator? I cannot help you if you don't provide more information concerning the network environment, authentication & encryption methods they are using.

---

### Post by xiownthisplacex on 2006-11-10
I was told to go here
[http://student.dei.uc.pt/~jemart/802.1x.html](http://student.dei.uc.pt/~jemart/802.1x.html)
but when i do the very first line i get this:

alex@kalex:~$ iwconfig eth0 essid "e-U" enc open
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth0 ; Operation not permitted.

Any suggestions?

---

### Post by wieman01 on 2006-11-10
> **xiownthisplacex said:**
> I was told to go here
[http://student.dei.uc.pt/~jemart/802.1x.html](http://student.dei.uc.pt/~jemart/802.1x.html)
but when i do the very first line i get this:

alex@kalex:~$ iwconfig eth0 essid "e-U" enc open
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth0 ; Operation not permitted.

Any suggestions?
This is TTLS... Ok, first time I do that. Please open this file:
> sudo gedit /etc/network/interfaces
Now paste this content (make a safety copy of the content before you go ahead):
> auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
[COLOR="Blue"]wpa-driver wext[/COLOR]
wpa-conf managed
wpa-ssid [COLOR="Red"]e-U[/COLOR]
wpa-ap-scan 1
wpa-eap TTLS
wpa-key-mgmt IEEE8021X
wpa-anonymous-identity [COLOR="Red"]anonymous@dei.uc.pt[/COLOR]
wpa-identity [COLOR="Red"]username@student.dei.uc.pt[/COLOR]
wpa-password [COLOR="Red"]password[/COLOR]
wpa-phase2 auth=PAP
Of course you need to have the right credentials for **wpa-anonymous-identity**, **wpa-identity**, and **wpa-password**. But I reckon you know them already.

Now restart the network:
> sudo /etc/init.d/networking restart
What's the output?

What wireless adapter are you using (e.g. IPW2200)? This plays a role for **"wpa-driver wext"**. Please let me know how you go. I am curious if this works because I will update my own Howto with it.

_**EDIT 1:**_
Please post the contents of "/etc/network/interfaces" once you have updated it.

_**EDIT 1:**_
When asked for a password, enter your user password (sudo)...

---

### Post by xiownthisplacex on 2006-11-10
My wireless adapter is 03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

/etc/network/interfaces

 auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid e-U
wpa-ap-scan 1
wpa-eap TTLS
wpa-key-mgmt IEEE8021X
wpa-anonymous-identity [email]anonymous@alunos.deec.uc.pt[/email]
wpa-identity [email]my_user@alunos.deec.uc.pt[/email]
wpa-password my_password
wpa-phase2 auth=PAP

when i do a sudo /etc/init.d/networking restart i get this

 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth1=eth1.
There is already a pid file /var/run/dhclient.eth0.pid with pid 5457
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:c0:a8:a9:fd:16
Sending on   LPF/eth0/00:c0:a8:a9:fd:16
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
Trying recorded lease 192.168.2.2
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
                                                                         [ ok ]


i dont not know if this worked or not, because i am now home for the weekend :) but on monday the first thing im gonna do is check if this worked or not and get back to you.. Thanx for the help and i hope this works, lol.

---

### Post by wieman01 on 2006-11-10
> wpa-anonymous-identity [COLOR="Red"]anonymous@alunos.deec.uc.pt[/COLOR]
wpa-identity [COLOR="Red"]my_user@alunos.deec.uc.pt[/COLOR]
wpa-password [COLOR="Red"]my_password[/COLOR]
Alright. My pleasure. :-)

Just make sure you replace the read bits with your credentials... Otherwise you won't be able to authenticate.

_**EDIT:**_
"wext" should be the right "wpa-driver".

---

### Post by xiownthisplacex on 2006-11-11
The wpa driver? I downloaded this file wpa_supplicant-0.4.9.tar.gz from here [http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/) so, what should go in the wext? Sorry if i dont understand any of this, i am only using linux since wednesday..

---

### Post by wieman01 on 2006-11-11
Oh, I see... Sorry then. Open a terminal & type in this command:
> sudo apt-get install wpasupplicant
Then press enter & key your user password when prompted. This installs wpa-supplicant. Got that? 

We continue from there.

---

### Post by xiownthisplacex on 2006-11-11
I already have that installed and here sudo gedit /etc/wpa_supplicant.conf i already put this info there:

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1

# se a placa nao suporta scanning, usar ap_scan=0
ap_scan=1

network={
  ssid="e-U"
  key_mgmt=IEEE8021X
  eap=TTLS
  anonymous_identity="anonymous@alunos.deec.uc.pt"
  identity="my_user@alunos.deec.uc.pt"
  password="my_password"
  phase2="auth=PAP"
}

what i was asking is what is my right wpa-dricer? because you told me this:
 EDIT:"wext" should be the right "wpa-driver".

---

### Post by wieman01 on 2006-11-11
You have got a Broadcom chip. I think "wext" will be the right driver, but I am not sure if the Linux driver for Broadcom chipsets supports TTLS. You must try though.

There are 2 way to configure your network:
1. /etc/wpa_supplicant.conf
2. /etc/network/interfaces

This is my preferred way is "/etc/network/interfaces". To configure it, please do this from command line:
> sudo gedit /etc/network/interfaces
Then paste this & save:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
[COLOR="Blue"]wpa-driver wext[/COLOR]
wpa-conf managed
wpa-ssid [COLOR="Red"]e-U[/COLOR]
wpa-ap-scan 1
wpa-eap TTLS
wpa-key-mgmt IEEE8021X
wpa-anonymous-identity [COLOR="Red"]anonymous@dei.uc.pt[/COLOR]
wpa-identity [COLOR="Red"]**username**@student.dei.uc.pt[/COLOR]
wpa-password [COLOR="Red"]**password**[/COLOR]
wpa-phase2 auth=PAP
Is **[COLOR="Blue"]"eth0"[/COLOR]** the right interface for your wireless adapter? 

Replace the read sections with your credentials (given to you by your network administrator):
> wpa-anonymous-identity [COLOR="Red"]anonymous@dei.uc.pt[/COLOR]
wpa-identity [COLOR="Red"]**username**@student.dei.uc.pt[/COLOR]
wpa-password [COLOR="Red"]**password**[/COLOR]
Then restart the network:
> sudo /etc/init.d/networking restart

---

### Post by xiownthisplacex on 2006-11-13
Ok. i altered /etc/network/interfaces and when i do a sudo /etc/init.d/networking restart i get this:

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:c0:a8:a9:fd:16
Sending on   LPF/eth0/00:c0:a8:a9:fd:16
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]

and then nothing happens, so i restart the computer and when i starts up again i cant connect to any wireless router, not even at home, through network manager or wifi radar... i dont think that this worked because i cant connect to anything except wired networks..

---

### Post by wieman01 on 2006-11-13
Yes, this only works if your school network is within reach. If you start up your network back home, you will get an error message. You have to change it back to the original settings.

Have you tried this configuration at school with your own credentials (e.g. username, password, etc.)?

---

### Post by xiownthisplacex on 2006-11-13
Yes and it doesnt work ](*,)  i dont find the e-U nor the guest-e-U

---

### Post by wieman01 on 2006-11-13
Have you got Wifi-Radar or Gnome-Network-Manager installed? No surprise then, you cannot configure "/etc/network/interfaces" in the way we did & run one of these tools at the same time...

Also, when trying to connect through wireless, the Ethernet cable must be unplugged.

One more question: What do you mean "cannot fine e-U or the guest-e-U"? Do you scan for it this way (command line)?
> iwlist scan

---

### Post by xiownthisplacex on 2006-11-13
Ok, when i do iwlist scan i get: 
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:14:F2:8F:3B:70
                    ESSID:"guest-e-U"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:0/100  Signal level:-57 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:40:05:31:FE:8C
                    ESSID:"openDeec"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-74 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:14:F2:8F:17:90
                    ESSID:"guest-e-U"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:0/100  Signal level:-90 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:14:F2:7E:3F:E0
                    ESSID:"guest-e-U"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-85 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

sit0      Interface doesn't support scanning.

i didnt do it like that, i meant in the network manager :) i didnt know about this command.. ok, im gonna have class now and when i get out im gonna try it with both wifi radar and network manager off.. thanx..

---

### Post by wieman01 on 2006-11-13
Yeah... uninstall both tools... they will interfere. And also unplug the Ethernet cable. Let me know how it goes. We can talk later. ;-)

---

### Post by wieman01 on 2006-11-13
By the way... Perhaps it is advisable to continue using Ethernet at school. Without NetworkManager or Wifi-Radar wireless networking will become less convenient, believe me. That is because you will have to live without them if you continue to use this configuration. Just a thought.

---

### Post by xiownthisplacex on 2006-11-13
I deleted wifi-radar and network manager, but now i cant connect via ethernet either, do i have to use network manager in order to connect via ethernet? i tried wireless also, but it didnt work by not finding e-U..

---

### Post by xiownthisplacex on 2006-11-13
add me on msn [email]xiownthisplacex@hotmail.com[/email] or aim xiownthisplacex, maybe its better to talk there and then post wutever outcome here :)

---

### Post by wieman01 on 2006-11-13
Oh no... Ok, please post this file:
> sudo gedit /etc/network/interfaces
Actually, no. You don't need NetworkManager or Wifi-Radar for Ethernet at all. This is odd. Post the contents of that file and we'll see. Added you to my contact list (MSN).

---

### Post by xiownthisplacex on 2006-11-13
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid e-U
wpa-ap-scan 1
wpa-eap TTLS
wpa-key-mgmt IEEE8021X
wpa-anonymous-identity [email]anonymous@alunos.deec.uc.pt[/email]
wpa-identity my [email]user@alunos.deec.uc.pt[/email]
wpa-password my pass
wpa-phase2 auth=PAP

---

### Post by wieman01 on 2006-11-13
Ok, to reenable Ethernet just copy this ("sudo gedit /etc/network/interfaces"):
> auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
"eth1" seems to be your Ethernet connection. This configuration has worked before (see post #25) and should you get hooked up to the wired network.

Restart the computer & it should be up & running. 

As for the wireless connection using TTLS (sript) have you talked to you network administrator? Are you using this username: "user@alunos.deec.uc.pt"? This is a generic user, so I am not sure if this is correct. Can you ask the administrator to give you a hand?

To get NetworkManager working again, just reinstall it. We will start all over again. :-)

---

### Post by xiownthisplacex on 2006-11-14
Ok, im gonna try that now..I have asked him, but he seems to know less than me! lol! he doesnt know either, he said hes very busy and cant lose time with that..But today im gonna ask another person, hopefully he'll know what to do.. Well, i dont have [email]user@alunos.deec.uc.pt[/email], i have my user name in "user".. In a little while i will get back to you.. Thanx

---

### Post by xiownthisplacex on 2006-11-14
Ok. I have tried to contact every administration possible that could help me..and no one knows! lol, what a bunch of losers! But i did get a response from the school's administration saying for me to go to my department's administration because they have contacted them to help me tomorrow..So hopefully, and i truly hope that they will resolve my problem, and if they do i will post it here for you to make your howto, ok?

---

### Post by wieman01 on 2006-11-14
Thanks a lot, man. Your comments will be appreciated. It'd be cool to know if this works. But yes, tell them that you need the username & password, otherwise you are just wasting your time. :-)

By the way: Does Ethernet work now?

_**EDIT:**_
Remember when you try my script: You need to disable/uninstall NetworkManager & Wifi-Radar before you try it.

---

### Post by xiownthisplacex on 2006-11-15
Ok, ive been given a script(its supposed to work) and i get this(i changed eth1 that the script had to eth0):
$ sudo e-U
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
NetworkManager: no process killed
ERROR: Module ipw2200 does not exist in /proc/modules
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth0 ; Invalid argument.


can u please go on msn, maybe you could solve the problem and i could show u the script..

---

### Post by xiownthisplacex on 2006-11-15
I found one problem, i changed the ipw220 to my broadcom driver, but i still get this:

libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
NetworkManager: no process killed
ERROR: Module bcm43xx does not exist in /proc/modules
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth0 ; Invalid argument.

---

### Post by wieman01 on 2006-11-15
Ahem, where does this error mesasge come from? I cannot see you on line right now so I guess we have to wait.

Does NetworkManager give you this error message?

---

### Post by xiownthisplacex on 2006-11-16
No, i get this message from the terminal after i installed a script i was given, when i do sudo e-U(this is to connect to e-U) and i get that message..

---

