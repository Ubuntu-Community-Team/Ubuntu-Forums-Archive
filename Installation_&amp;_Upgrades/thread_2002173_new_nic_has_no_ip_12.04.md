---
title: "new nic has no ip 12.04"
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by hawaiiman on 2012-06-12
Hello, Noob took on building a new server. Started with 11.10 server and upgraded to 12.04. I need a second ethx (server...) . All I could get here in N.E. Thailand is a TP-Link tg-3468 which uses the Realtek 8111c chipset. My onboard device uses the Realtek 8111b chipset. Got the autorun.sh to run, so the original r8169 driver is out and both are running the r8168. The onboard works fine. For some reason it's shown as eth1 and the nic as eth0. The link shows up for the eth0 in ifconfig, and plugged in to my laptop, they exchange a few packets. Laptop sees "unknown network no network access" . Eth0 is not getting an IP# . Pretty sure I need to edit some files around, like adding eth0 to /etc/network  interfaces, but don't know what they all might be, or what to enter.
The cd that came with the card has information for doing all that, but Debian commands aren't listed.> 
<Set the network related information>
    1. Set manually
        a. Set the IP address of your machine.

            # ifconfig ethX "the IP address of your machine" 

        b. Set the IP address of DNS.

           Insert the following configuration in /etc/resolv.conf.
        
            nameserver "the IP address of DNS"

        c. Set the IP address of gateway.

            # route add default gw "the IP address of gateway"

    2. Set by doing configurations in /etc/sysconfig/network-scripts
       /ifcfg-ethX for Redhat and Fedora, or /etc/sysconfig/network
       /ifcfg-ethX for SuSE. There are two examples to set network 
       configurations.

        a. Fixed IP address:
            DEVICE=eth0
            BOOTPROTO=static
            ONBOOT=yes
            TYPE=ethernet
            NETMASK=255.255.255.0
            IPADDR=192.168.1.1
            GATEWAY=192.168.1.254
            BROADCAST=192.168.1.255

        b. DHCP:
            DEVICE=eth0
            BOOTPROTO=dhcp
            ONBOOT=yes    

<Modify the MAC address>
    There are two ways to modify the MAC address of the NIC.
    1. Use ifconfig:

        # ifconfig ethX hw ether YY:YY:YY:YY:YY:YY

       ,where X is the device number assigned by Linux kernel, and
          YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

    2. Use ip:

        # ip link set ethX address YY:YY:YY:YY:YY:YY

       ,where X is the device number assigned by Linux kernel, and
          YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

<Force Link Status>

    1. Force the link status when insert the driver.

       If the user is in the path ~/r8168, the link status can be forced 
       to one of the 5 modes as following command.

        # insmod ./src/r8168.ko speed=SPEED_MODE duplex=DUPLEX_MODE autoneg=NWAY_OPTION

        ,where
            SPEED_MODE    = 1000    for 1000Mbps
                    = 100    for 100Mbps
                    = 10    for 10Mbps
            DUPLEX_MODE    = 0    for half-duplex
                    = 1    for full-duplex
            NWAY_OPTION    = 0    for auto-negotiation off (true force)
                    = 1    for auto-negotiation on (nway force)
        For example:

            # insmod ./src/r8168.ko speed=100 duplex=0 autoneg=1

        will force PHY to operate in 100Mpbs Half-duplex(nway force).

    2. Force the link status by using ethtool.
        a. Insert the driver first.
        b. Make sure that ethtool exists in /sbin.
        c. Force the link status as the following command.

            # ethtool -s ethX speed SPEED_MODE duplex DUPLEX_MODE autoneg NWAY_OPTION

            ,where
                SPEED_MODE    = 1000    for 1000Mbps
                        = 100    for 100Mbps
                        = 10    for 10Mbps
                DUPLEX_MODE    = half    for half-duplex
                        = full    for full-duplex
                NWAY_OPTION    = off    for auto-negotiation off (true force)
                        = on    for auto-negotiation on (nway force)

        For example:
        
            # ethtool -s eth0 speed 100 duplex full autoneg on

        will force PHY to operate in 100Mpbs Full-duplex(nway force).

<Jumbo Frame>
    Transmitting Jumbo Frames, whose packet size is bigger than 1500 bytes, please change mtu by the following command.

    # ifconfig ethX mtu MTU

    , where X=0,1,2,..., and MTU is configured by user.

    RTL8168B/8111B supports Jumbo Frame size up to 4 kBytes.
    RTL8168C/8111C and RTL8168CP/8111CP support Jumbo Frame size up to 6 kBytes.
    RTL8168D/8111D supports Jumbo Frame size up to 9 kBytes.

Any help appreciated, and my students will be grateful too!

---

### Post by hawaiiman on 2012-06-12
BTW to clarify: WAN is running fine with internet access obtained from a LAN port of an ADSL connected wifi router. Just setting it up at home and will put it on the fiber modem with static IP later when working. Not sure if having eth0 the LAN and eth1 the WAN is a problem.

---

### Post by darkod on 2012-06-12
And what are you trying to set, static IP I guess?

Edit /etc/network/interfaces (with sudo permissions because it's a system file), and the entry for the new eth0 should be like:

auto eth0
iface eth0 inet static
   address x.x.x.x
   netmask x.x.x.x
   gateway x.x.x.x (if using one)
   dns-nameservers x.x.x.x y.y.y.y (if using one)

If the server is accessing the internet through eth1, then on eth0 you would need only address and netmask, that's enough to work in a private LAN.

---

### Post by hawaiiman on 2012-06-12
I just put the machine together and installed 11.10 server, then upgraded to 12.04 with unity.
I have it at home now running behind a wifi router which deals dhcp. The connection is adsl. ight now, I'd be very happy to see eth0 get an IP from dhcp.I have the cable plugged in to my laptop as an example LAN. 
The server will be installed at my high school. We have many clients running wxp, a website, email serve. The school has fiber and a static IP#. I'll to to add your settings to /interfaces. What other places do I need to have settings?

---

### Post by darkod on 2012-06-12
If it's the server OS, nowhere. Is it server with GUI installed, or desktop OS with added server roles?

For dhcp it's even easier. It should be:
```
auto eth0
iface eth0 inet dhcp
```

But in order to receive dhcp IP from your home router, you have to connect it to the correct eth0 interface, right?

---

### Post by hawaiiman on 2012-06-12
since it was server 11.10 with gui added, then upgraded to12.04, I believe it has theupgraded server packages. I am working from terminal out of the gui.
have root now. 
i saved the dhcp linesyou just sent but no ip and laptop won't connect

---

### Post by hawaiiman on 2012-06-12
For some eason the eth1 is the WAN getting internet and dhcp from the router. This is an onboard with realtek 8111b chipset.I have removed the r8169 driver, and installed the r8168, it's working fine. The eth0 is intended as the LAN. It's a tp-link with the realtek 8111c chipset, and the r8168 drive is the recommended driver for it.
Its after midnight here in Thailand. I'll check for your post in the morning. Thank you very much.

---

### Post by darkod on 2012-06-12
I don't understand completely your setup.
The eth1 is the WAN connected to the router and receiving dhcp address correctly.

How do you plan to use eth0? Is it supposed to be a gateway for the rest of the private LAN? So that the internet for the computers on the LAN passes through this server?

The cable you connect to eth0, is it in a network with dhcp server? Otherwise, where would eth0 get a dhcp address from?

---

### Post by hawaiiman on 2012-06-12
Right now the server is at my home, but when running, I will take it to the school where I teach. 
1-yes
2yes it will be the dhcp server for an LAN with 30+ clients which run wxp. So, although right now its getting dhcp from the WAN, it'spurpose is to be the dhcp server and have a static ip and access the internet through fiber modem.
It will also be email host, host our website,and serve database.
3 the cat5 connected between eth0 and my laptop is to use the laptop as an example of LAN, as a test bed.

---

### Post by hawaiiman on 2012-06-12
correction to 2 above. It is supposed to be getting dhcp from 192.168.1.3 (the server) but as yet is not

---

### Post by darkod on 2012-06-13
> **hawaiiman said:**
> Right now the server is at my home, but when running, I will take it to the school where I teach. 
1-yes
2yes it will be the dhcp server for an LAN with 30+ clients which run wxp. So, although right now its getting dhcp from the WAN, it'spurpose is to be the dhcp server and have a static ip and access the internet through fiber modem.
It will also be email host, host our website,and serve database.
3 the cat5 connected between eth0 and my laptop is to use the laptop as an example of LAN, as a test bed.

You can't use the laptop as an example of a LAN unless a dhcp server is running on it. Is it?

When you simply connect the test server to the laptop, nothing will happen. Especially if you connect them directly with a cable, not using a hub or switch. For direct cable connection you would need cross-over cable, and most network cables are not. Teh yare standard straight-through cables and need to be used with a switch/hub.

But in any case, your test can't work without dhcp server running on the laptop.

So, at the end, will this server be a dhcp server for the LAN or that will be the 192.168.1.3 server? Because if this server is not supposed to be dhcp for the LAN, you don't actually need two interfaces. In that case the server will be just like any computer on the LAN, it can have its static IP, but will be receiving internet from the same router like all the other computers. That means only one interface is needed.

---

### Post by hawaiiman on 2012-06-13
yes, I see your point, but you seem to have my plan turned around 180. The dhcp in this case comes from the WAN side, from an internet connected router (via adsl). The laptop connected to eth0 will in this case become a client of the server and obtain nat from it.Of course in this case it would be double nat, but at this point that's not a problem (?). the server has this 198... ip because it is a client of the router. I can't disable nat on the router, as it's firmware is locked out of most settings by the isp. I can't do much else as the phone line from adsl has the small plug and my spare router has an rj45. I took the server to school today and connected it to the LAN there. It was connected to a switch (level 2) and the hp-ml-350 server (level 3) to WAN (fiber). The situation with eth 0 stayed exactly the same. The problem , here is that I don't know all the places to enter information, and what to enter, like in /etc/network/interfaces. I know ther are libs and at least a conf or two to be dealt with here. I just don't know what to do.

---

### Post by darkod on 2012-06-13
The settings are only in /etc/network/interfaces.

So, you have eth0 configured for dhcp and it didn't receive an IP from the LAN at work? I assume there is a dhcp server running on the LAN at work.

I don't understand 100% what do you want to test. On this server, if eth1 connects to the WAN and the eth0 to the LAN to act as server for the computers on the LAN, then eth0 should have private static IP in a range that you decide. The IP depends only on your choice what range you want to use in your LAN.

For example, like 10.10.0.1. Then it should have dhcp server running on this server if the computers on the LAN expect to be issued addresses by this server.

If you can do some sort of diagram what do you want to achieve, it might help.

---

### Post by hawaiiman on 2012-06-13
All I am trying to do is have a test bed for this new server. I realize that in it'sfinalfom, it will have a stqtic IP. Perhaps I'm wrong, but I don't believe if I give it it's static IP now, underneath a dhcp router and connected to a different isp that it will be able to see the internet. 
I'm trying to get this machine set up so it has it's most basic functions at home, thentake it to school, unhook the other server, give it it's static ip, configure it with subnet, etc. and be done with it. It would be quite inconvenient for the clients at school to have the system offline while i play around with it. Diagram is not needed . At home: ADSL->router/switch->server->client. Then ..At school: Fiber->fiber to ethernet converter->server->switch->client.
As I said earlier, the same result when connected through the school system replacing client position. Internet access ok, no link on eth0.

---

### Post by darkod on 2012-06-13
1. Make sure you have the
auto eth0
in /etc/network/interfaces. That tells the OS to activate the interface at boot. Without it it won't activate regardless of other settings.

2. To double check if eth0 is working fine, configure it with dhcp (same like eth1 temporarily) and connect it to your router at home. Can it receive an IP?

3. If that works fine, configure eth0 with private static IP that you plan to use in the LAN at school (but not in the same range as your home router range), for example 10.10.0.1, mask 255.255.255.0. Configure your laptop with static IP 10.10.0.100, mask 255.255.255.0, gateway 10.10.0.1.

Then try a ping to 10.10.0.1 from your laptop. It should work. Note that internet might not work until you enable ipv4 forward in /etc/sysctl.conf because only then the server will start forwarding packets between eth1 and eth0. You will also need few settings in iptables if you want the server to act as router, but all that can be done later after the networking works as you expect it, with successful ping, etc.

---

### Post by hawaiiman on 2012-06-13
1. I worried that having eth1 be wan and eth0 be lan so I changed the content in .../interfaces to read as follows:

# The primary internet interface
auto eth0 iface eth0 inet dhcp


# The primary network interface
auto eth1
iface eth1 inet dhcp

2.yes and it also sees the default "it works" at the 198.162.1.3 where the website will be.
192.168.1.3     255.255.255.0

3. since i've screwed this up before, please walk me though this step by step. --thanks

---

### Post by darkod on 2012-06-13
There is nothing to screw up. If you changed your mind and you want eth1 to be your LAN internal interface, configure it with something like:
```
# Internal LAN interface
auto eth1
iface eth1 inet static
   address 10.10.0.1
   netmask 255.255.255.0
```

Then on the laptop go into Network and in the properties of your wired connection set:
IP 10.10.0.100
Subnet 255.255.255.0
Gateway 10.10.0.1
DNS 8.8.8.8 (Google DNS for example)

Then open command prompt on the laptop and try:
ping 10.10.0.1

That should return the ping from your server. If all of that works out, you're good to go.

At that moment the laptop will still not have full internet access.

On the server open /etc/sysctl.conf to edit with:
sudo nano /etc/sysctl.conf

Uncomment (remove the # from the start of) the line saying net.ipv4.ip_forward=1

Save the changes with Ctrl + O and exit nano with Ctrl + X.

Then on the server do:
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

Now test if your laptop has internet access through the server. It should.

If that works, the only thing left is to make the iptables command permanent because executing it like that in command line will only set it up temporary. After a reboot it won't work.
But first do this test and making it permanent is easy.

---

### Post by hawaiiman on 2012-06-13
sorry about the delay.I hope I haven't inconvenienced you. got very uncomfortable,soI'm going to shut down and move everything soI can sit on the sofa.Thanks again. I'llsend an update

---

### Post by hawaiiman on 2012-06-13
I wasn't sure if the static ip etc. you recommended here s/b for lan or wan side. i set for wan side of server and left lan side at auto and dhcp.when i pinged 10.10.0.100 i get error /bin/ping ping -b -c 5 -n 10.10.0.100

---

### Post by darkod on 2012-06-13
> **hawaiiman said:**
> I wasn't sure if the static ip etc. you recommended here s/b for lan or wan side. i set for wan side of server and left lan side at auto and dhcp.when i pinged 10.10.0.100 i get error /bin/ping ping -b -c 5 -n 10.10.0.100

That was for LAN side. That's why I left the comment # Internal LAN interface.

For the WAN side you will either use dhcp or static IP depending on your provider router/connection.

Also I said to set the 10.10.0.100 on your laptop and try to ping your server at 10.10.0.1.

---

### Post by hawaiiman on 2012-06-13
Sorry, brain strain. I can't find a way toping with w7-64u...searched the net, it saus you can't.Looking at the lights on the card for the lan, the server is green and the client is red. I presume that means packets are going but not returning

---

### Post by hawaiiman on 2012-06-13
btw the name of the server shows ip of 192.168.122.1, apparently from the router

---

### Post by darkod on 2012-06-13
Don't worry about the IP on the interface towards the router. We are talking about the LAN test now, the internal interface.

Sure you can ping with win7, just open command prompt.

Hold the windows logo button and R, type 'cmd' in the small window that opens, hit Enter.

Now you have the command prompt open, just execute:
ping 10.10.0.1 (if you used my example address for the server interface)

Note that before that you need to configure the win7 computer with static IP on the same range, as I already said.

---

### Post by hawaiiman on 2012-06-13
request timed out

---

### Post by darkod on 2012-06-13
> **hawaiiman said:**
> request timed out

You have the laptop connected to the internal interface of the server and configured with static IP in the same range? If you open the command prompt again on the laptop and try:
ipconfig

what IP does it give you?

---

### Post by hawaiiman on 2012-06-14
Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\Jack  - Petchanan>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Wireless LAN adapter Wireless Network Connection 3:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Wireless LAN adapter Wireless Network Connection 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::55c2:827f:ae4b:e149%11
   IPv4 Address. . . . . . . . . . . : 192.168.1.2
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::41e1:a900:bd66:7385%10
   IPv4 Address. . . . . . . . . . . : 10.10.0.100
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 10.10.0.1

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e76:24bc:b5e1:fefe:3266
   Link-local IPv6 Address . . . . . : fe80::24bc:b5e1:fefe:3266%15
   Default Gateway . . . . . . . . . : ::

Tunnel adapter isatap.{B5F98C05-4D84-4CB1-BCBB-CB3948C98165}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{224021FF-BF58-4A97-99FD-1E501F263856}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter 6TO4 Adapter:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

C:\Users\Jack  - Petchanan>

---

### Post by hawaiiman on 2012-06-14
When I had the new server at school as I described befoe, I disconnected the cable from the LAN to one of the active clients and ran a temporary cable to the output port of the server. Same result as with laptop, no link.

---

### Post by darkod on 2012-06-14
> **hawaiiman said:**
> When I had the new server at school as I described befoe, I disconnected the cable from the LAN to one of the active clients and ran a temporary cable to the output port of the server. Same result as with laptop, no link.

You mean you connected the laptop and the test server directly with cable, network port to network port?

Did you notice in one of my posts earlier that this can work ONLY if you are using a so called cross-over cable? With most network cables, you can't connect machines directly. You need to have a switch/hub for example, and connect the laptop to the switch with one cable, and the server to the switch with another cable. Then you can test the ping.

If you have them connected directly, with a straight cable (not cross-over cable) it can't work.

If your router at home has wired ports that would mean it has switch integrated. Connect your laptop network port to one of the ports of the router, and also connect the network port of the server (the correct interface) to the router. Then test the ping.

It doesn't matter if your laptop is connected to your wi-fi network at the same time, it won't interfere with the test. Just make sure you have them connected through a switch because directly with a cable won't work unless it's cross-over cable.

---

### Post by hawaiiman on 2012-06-14
ok, That got rid of the ed light on the card on server, but ping timed out, same as before. BTW tried it with both ports on the server...same.

---

### Post by darkod on 2012-06-14
OK, step by step we are getting closer.

The ipconfig you posted is from your win7 laptop right? It looks configured good with the 10.10.0.100 address.

Double check that the server is also configured good with 10.10.0.1. If you can, post the result of:
ifconfig

on the server. Or just look at it, if you can't post it. It should say that the address is 10.10.0.1.

---

### Post by hawaiiman on 2012-06-14
Yes, I think will get done eventually.
 Everyone at school (teachers in my office) was very impressed with Ubuntu and I dual booted one machine today to give them to use and get used to. It would make all of our jobs so much easier if all the classroom and office machines were Ubuntu and just the 6 student machines in the library winxp. Our standing server is going fast. I hope I get the new drives for it soon.
ok: 
lo      Link encap:Local Loopback
        inet addr:127.0.0.1Mask:255.0.0.0
        inet6 addr: ::1/1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:950 error:0 dropped:0 overruns:0 frame:0
       TX packets:950 error:0 dropped:0 overruns:0 carrier:0
       collisions:0 txquelen:0
       RX bytes:148807 (0148.8 KB) TX bytes:148807 (148.8 KB)
typed...whew
there is also a device called virbr0 I believe this is a modem card that was in the machine briefly, but was removed. it shows 0 activity and an ipof 192.168.122.255 mask 255.255.255.0 

As nothing else is shown, I gues that's due to the staic ip being out of range of the ip's dealt by my router (192.168.........)

---

### Post by darkod on 2012-06-14
That should show both your wired interfaces, eth0 and eth1 too, but it doesn't show any of them. Even without ip assigned they should show.

Double check /etc/network/interfaces. Do you have the auto ethX lines? Without it the interface doesn't activate.

It might be a driver issue, or similar, but it seems your network interfaces are not activated. Right now it's normal that the ping returns no reply.

---

### Post by hawaiiman on 2012-06-16
I took a few days away from it, got some rest. I decided to do a fresh install with 12.04 server, I added desktop, and everything went fine. I received a later driver version from TP-Link and the aurun.sh installed it perfectly. eth0 is on the internet. 
I am wondering whether the attempt to do a test bench at home is a valid idea. I do prefer to work at home, but trying to set up with both nic using dhcp seems potentially troublesome. I do have the key and permission to use the server room at school. During any time. I could take the server there and try to set it up using the actual fiber connection and use the actual static ip, etc, as well as connecting to the actual LAN.
According to the readme file for the nic, I should add commands to the /etc/network/interfaces file similar to:
"a. eth0"
            DEVICE=eth0
            BOOTPROTO=static
            ONBOOT=yes
            TYPE=ethernet
            NETMASK=255.255.255.0 (atual is 255.255.255.248 =2[not sure why the =2])
            IPADDR=192.168.1.1(will use actual)
            GATEWAY=192.168.1.254(will use actual for all)
            BROADCAST=192.168.1.255

        "b. eth1"
            DEVICE=eth1
            BOOTPROTO=dhcp
            ONBOOT=yes   


Not sure if this is correct or sufficient.

---

### Post by darkod on 2012-06-16
I am not familiar with that kind of setting up the interfaces, so I can't say anything for or against it.
In the /etc/network/interfaces I use:
```
auto ethX
iface ethX inet static
   address x.x.x.x
   netmask x.x.x.x
   gateway x.x.x.x
   dns-nameservers x.x.x.x y.y.y.y
```

That would be all. But there will be small differences for eth0 and eth1. Lets assume this:
eth0 is WAN (fibre connection)
eth1 is LAN

On both interfaces you would use static IP because a server wouldn't have dhcp even on the LAN, you can't afford your server changing the IP sometimes automatically. So, on eth0 you would have public static IP depending on the fibre connection settings, and on eth1 you would have private static IP depending on the range your LAN is running.

The gateway and dns-nameservers are set up only on eth0 since that will be the connection towards the WAN (internet).
On eth1 you set up only address and netmask so that it belongs to the LAN range.

That should be sufficient to get it running.

If this server needs to be a router for the rest of the computers on the LAN, firewall for them, etc, you set it up later one step at a time.
The first main step is to make it work with the eth0 and eth1 settings, to confirm the server has internet connection through the fibre, and that the computers on the LAN can ping the server private IP.

After that you can deal with the roles you want to assign to your server one by one.

---

### Post by hawaiiman on 2012-06-16
excellant!!  Yes the sever will be a router, a firewall, a webhost, a database, and possible dns server. As you said, one step at a time.

This o/s seems to have a self checking feature, when I started # gedit /interfaces in /etc/network    I received error warning in the terminal:
(gedit:2919): Glib-GIO-WARNING **: Missing callback called fullpath = /root/.local/share/recently-used.xbel

should this go in interfaces? Should "xbel" have a value for "x" ?

I plan on using Firestarter, the gui based firewall. If so should I disable apparmor first?

---

### Post by darkod on 2012-06-16
You need to edit interfaces with sudo, if using gedit better with gksu (the version for GUI programs). I usually use nano and don't have gedit installed on a server, but you can use it if it's easier for you.

I think those errors about gedit are not important, I have seen similar ones and still editing the file works. But open it for editing with:
```
gksu gedit /etc/network/interfaces
```

After you make the changes and save and close the file, you will need to either restart the server or the network with:
```
sudo /etc/init.d/networking restart
```

After that the interfaces should work with the new configuration.

---

### Post by hawaiiman on 2012-06-16
Re: PM. This old server runs freebsd, so I assume this accounts for some differences.
I am confused that the LAN addresses seem to be public, but not sure.  also not sure how much of this needs to be in /interfaces of the new  server, and if it is in a usable form.
If the current setup is less than Ideal, I will have to learn more  before I change it. Right now, I want a server I can just swap in to  replace our old one. The old one may go back in, and for some reason,  the net-admin is desiring to put a switch at the fiber interface and try  to run both servers and (I assume) split the network. I wish my Thai was better, sowe could discuss it.

---

### Post by darkod on 2012-06-16
For the interface towards the WAN, consult your admin too. The info can help you determine the correct settings.

In reality it's very simple.
The address will be assigned by your admin.
The netmask is 255.255.255.248 according to your PM.
The gateway will also be advised by your admin.
The dns-nameservers also.

That is all you need for the WAN and after you have those settings entered, the server should have internet access if connected correctly.

On the LAN side, the address and netmask will depend on the range running on your LAN. It should match the current setup and I can't see why there would be public IPs on the LAN. Make sure when talking about LAN, we are not simply talking about the network port and the cables, we are actually talking about the network port that will be connected to your internal network. From that point of view, it shouldn't have a public IP, only a private one.
If you are still confused what IP to use, again the admin can clear this up for you, he can advise you what to use for your network.

---

### Post by hawaiiman on 2012-09-29
The school changed the isp several times and the Ubuntu machine was parked. Recently they've gone to a fast ADSL line with a PPPoe router/modem. The current thinking is to get an enterprise firewall/router to handle the security and put the Ubuntu server in as a DNS cache, and other duties. I've got the same ISP at home as the school does now, so I brought it home and formatted it, put a fresh copy of 12.04 server (32bit) and am trying to set that up. I'm trying modem/router-server-switch-laptop first. I've got the two machines to ping each other. eth0 is dhcp and gets on internet fine, other nic ended up as eth2. It's set as 10.10.0.1 on 255.255.255.0 and the DNS 192.168.1.1. The laptop is on 10.10.0.100, as you suggested previously, with 255.255.255.0 and DNS 192.168.1.1 .
They ping each other ok, but even though I tried the next suggestion about portforwarding eth2 which was in the same posting, there is no pass through to the internet for the laptop.
I've heard that we could change topology to router/modem-switch-server and switch-LAN perhaps directing the client windows machines to 127.0.0.1 and use just the one NIC (eth0). The Thai teacher I work with who is in charge of the nework (not a qualified admin, however). doesn't get that, and I haven't done that before.
The router we want to get provides for assigning static ip's on the LAN.

---

### Post by hawaiiman on 2012-09-29
Darko, hope you are still around. After many hours I got the nic card drivers properly in, and used your suggestions about a static 10.10.0.1 etc. and when I used the ...POSTROUTING...command it worked and laptop got on the internet! So what needs to be done to make the ip tables changes permanent??

---

### Post by rytec on 2012-10-09
Hello,

I'm struggling with kind of same issue here.
I have Ubuntu server 10.04 2 network cards in it.
eth0 is LAN side and has fixed ip, eth1 will be having a dynamic ip from the isp provider when they come next week.
Now i was already testing the eth1 card to put it also in the same LAN side to obtain an IP from the dhcp server running on the server, can this work for only testing?
Because when i restart the interfaces eth1 does not get an IP
And I'm worried and thinking that this NIC isn't working properly but the output with ifconfig -a gives me all kind of information about eth1 
I also have ipv4forward enabled and later on when the actual isp line is there i will also activate the NAT in iptables.
But first I'd like to know if I can test eth1 to get an ip from the dhcp server on eth0 ?
If I give eth1 a static IP in the range of the LAN I can ping to it. but why does it not get a dhcp IP ?
I also have tried a new NIC but it gives me the same result

Even after connecting a router to this nic and did a restart it gave me this same result :
/etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth2.pid with pid 7936
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth2/00:0e:2e:37:20:83
Sending on   LPF/eth2/00:0e:2e:37:20:83
Sending on   Socket/fallback
ssh stop/waiting
ssh start/running, process 10443
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth2/00:0e:2e:37:20:83
Sending on   LPF/eth2/00:0e:2e:37:20:83
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14

---

### Post by hawaiiman on 2012-10-09
> **darkod said:**
> There is nothing to screw up. If you changed your mind and you want eth1 to be your LAN internal interface, configure it with something like:
```
# Internal LAN interface
auto eth1
iface eth1 inet static
   address 10.10.0.1
   netmask 255.255.255.0
```
 
Then on the laptop go into Network and in the properties of your wired connection set:
IP 10.10.0.100
Subnet 255.255.255.0
Gateway 10.10.0.1
DNS 8.8.8.8 (Google DNS for example)
 
Then open command prompt on the laptop and try:
ping 10.10.0.1
 
That should return the ping from your server. If all of that works out, you're good to go.
 
At that moment the laptop will still not have full internet access.
 
On the server open /etc/sysctl.conf to edit with:
sudo nano /etc/sysctl.conf
 
Uncomment (remove the # from the start of) the line saying net.ipv4.ip_forward=1
 
Save the changes with Ctrl + O and exit nano with Ctrl + X.
 
Then on the server do:
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
 
Now test if your laptop has internet access through the server. It should.
 
If that works, the only thing left is to make the iptables command permanent because executing it like that in command line will only set it up temporary. After a reboot it won't work.
But first do this test and making it permanent is easy.
 
This worked for me when I did EXACTLY as advised. Of course noting that your nics have different numbers. Server is in place and functioning. :-)

---

### Post by hawaiiman on 2012-10-09
Just to review: I am running 12.04 server with GUI. WAN is to ADSL modem/router and eth0 (WAN) is set for DHCP. Gateway is 192.168.1.1. ETH1 (LAN) is 10.10.0.1 and LAN range is 10.10.0.10;10.10.0.150 mask 255.255.255.0. ETH1 is static and dealing DHCP to clients. I tried using 192.168.1.whatever on the LAN side and this just doesn't work.
One issue was the onboard ehternet was running realtec r8169 for driver which is in the kernel, but the added nic (ETH1) is not a 10/100 card. All the 10/100/1000 cards which use realtec drivers require r8168. R8168 will also run the 10/100 devices. I downloaded current r8168, removed r8169, and installed r8168. :-)

---

### Post by hawaiiman on 2012-10-20
One thing after another, update. Darkod, thanks for the patient help. I since changed to 10.04 which I kept pretty lean . It's so much easier to fix things when things are more available to change. UFW..out, dhcp3..out, bind9..out, dnsmasq..in. Firewall supplied by enterprise router with QOS. Considering posting a "simple router behind adsl" thread..Marking this solved.

---

