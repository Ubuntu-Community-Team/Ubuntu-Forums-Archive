---
title: "HOw to update my system"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by Rakesh055 on 2011-03-01
I Have Installed Ubuntu 10.04 according to the steps mentioned in the following pdf 

[http://cssoss.files.wordpress.com/2010/12/eucabookv2-0.pdf](http://cssoss.files.wordpress.com/2010/12/eucabookv2-0.pdf)

the problem is after installation i am unable to connect to internet. i have connected internet on LAN but cannot detect it on console. unless i update the system i cannot get GUI.

Please help me with this problem?

---

### Post by matt_symes on 2011-03-01
Hi

You have installed the server edition if you have followed those instructions.

Although you can install a GUI in the server edition it is optomised for server loads.

Is it possible for you to download the desktop version from here and install that ?  (say downloaded from work or a library)

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

That should have more luck connecting to your network.

Kind regards

---

### Post by Rakesh055 on 2011-03-01
Hey thanks for that reply, but how can i install the desktop edition from the console of a server.

---

### Post by matt_symes on 2011-03-01
Hi

Is your internet connection wired or wireless ?

From the terminal post the output of

```
sudo lshw -C network
```

Also post the output of

```
cat /etc/network/interfaces
cat /etc/resolv.conf
cat /etc/nsswitch.conf 
```

What is the output of

```
sudo service networking status
```

What is the IP address of your router ?

Kind regards

---

### Post by Rakesh055 on 2011-03-01
my internet connection is wireless but wifi drivers in this are disabled which i cannot enable from console. i tried with LAN connection of Airtel but i could not connect directly.

the output of sudo lshw -c network

i have one wireless interface which is disabled
Ethernet interface which is gigabit ethernet

as it is on other system i cannot type all totally

the output of /etc/network/interfaces.

eth0 with all the address which i have given while installation according to the document provide3d above and added eth1 as given in the same

the output of /etc/resolv.conf

search example.com
nameserver 192.168.10.2

the output of /etc/nsswitch.conf

the passwd, group and shadow is compat

hosts : files mdns4_minimal [NOTFOUND=return] dns mdsn4
networks: files

protocols, services, ethers and rpc: set to db files.

i dont know exactly all these but i have given the output.

---

### Post by matt_symes on 2011-03-01
Hi

We really need the full output of

```
sudo lshw -C network
```

and also

```
cat /etc/network/interfaces
```

What is the IP address of your router ?

As you have both wired and wireless connection i think your best bet is to try to connect to the router using you wired connection, so go and find a network cable and post back the full results of the 2 commands above.

In the meantime i will have a look at the guide you followed.

Kind regards

---

### Post by Rakesh055 on 2011-03-01
ya fine, thanks... i will give you the output by today evening because i need to go to my room to get you the output by connecting to the LAN.

the exact output also i will give you reply by evening.

Later you can suggest me the better way to connect to the net.

---

### Post by matt_symes on 2011-03-02
Hi

No problem, i will wait for the output.

Here's what i suggest we try to do.

I am assuming you have a router connected to a modem. If this setup is incorrect then you must tell me.

Plug an Ethernet cable from your PC into your router. Plug the uplink from your router into the modem and ensure the modem is connected.

If your router is configured for dhcp then it should give you an IP address. We can check this with ifconfig. If not we can configure the router using a browser. We can then check connectivity to the net.

We will need to make sure your configuration files are correct for dhcp and networking service is up and running. We will need to check the card is working. Then we can take it from there.

Are you behind a proxy server at all ?
Is my assumption about your setup correct ?

Kind regards

---

### Post by Rakesh055 on 2011-03-03
Ya the setup you said was right... but the DNS should be given by us only.

So i tried for the DNS used by provider in the internet. i got it and changed in the /etc/resolv.conf........ 

still it is not pinging to any website.

---

### Post by matt_symes on 2011-03-03
Hi

It's very hard to help you without knowing what you have set up and without seeing you configuration files. Still ....

I assume you are connected to your router. I assume your router is connected to your modem and that is connected.

I assume your /etc/network/interfaces file will look something like this

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

assuming the logical name of your connection is eth0 and you want DHCP from your router or

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1
```

if you want a static ip adress (example) 192.168.1.99 and your routers address is 192.168.1.1 (change as appropriate)

I assume net working is started

```
sudo /etc/init.d/networking restart
```

I assume for the process of testing the are no blocking firewall rules on your server.

```
sudo iptables -F
```

I assume you have an IP address. 

```
ifconfig
```

and that it is on the same subnet as you router (example say your routers ip address is 192.168.1.1 and your ip address is 192.168.1.100).

I assume you can ping your router (using the exammple ip addreses above

```
ping 192.168.1.1 -c 3
```

```
matthew@matthew-laptop:/home$ ping 192.168.1.1 -c 3
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=4.25 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=4.51 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=2.85 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 2.850/3.871/4.510/0.733 ms
matthew@matthew-laptop:/home$
``` 

I assume from your pc you can open a browser and access the routers configuration page by typing the IP address into the browser. I assume you have configured it correctly.

I assume you can ping an external ip address like googles dns server at 8.8.8.8 and you get a response.

```
matthew@matthew-laptop:/home$ ping -c 3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=50 time=30.8 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=51 time=29.0 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=50 time=27.1 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 27.110/28.984/30.844/1.537 ms
matthew@matthew-laptop:/home$ 
```

I assume you have a valid dns server in your resolv.conf file (the dns server offered by your router or an external one such as openDNS)

[http://theos.in/windows-xp/free-fast-public-dns-server-list/](http://theos.in/windows-xp/free-fast-public-dns-server-list/)

```
matthew@matthew-laptop:/home$ cat /etc/resolv.conf
nameserver 192.168.1.1
nameserver 8.8.8.8
```

I assume you can use nslookup to get the ip address from a known name

```
matthew@matthew-laptop:/home$ nslookup www.google.com
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
www.google.com  canonical name = www.l.google.com.
Name:   www.l.google.com
Address: 74.125.230.148
Name:   www.l.google.com
Address: 74.125.230.147
Name:   www.l.google.com
Address: 74.125.230.144
Name:   www.l.google.com
Address: 74.125.230.145
Name:   www.l.google.com
Address: 74.125.230.146

matthew@matthew-laptop:/home$ 

```

Between each of these steps are substeps you can check if failure such as checking the hardware is recgonised, the correct drivers are loaded, kernel routing table is valid etc...
 
I have no idea where you are at the moment so i really don't know how to help you.

Kind regards

---

### Post by Rakesh055 on 2011-03-07
the output for $sudo lshw -c network is

[
 *-network
         description: Ethernet interface
         product:
         vendor:
         physical id: 0
         bus info: pci@0000:04:00.0
         logical name: eth0
         version : 02
         serial: 00247e25d95e
          capacity 1gb/s
        width 64bit
        clock 33mhz


and output for cat /etc/network/interfaces

auto eth0
iface eth0 inet static
      address 192.168.10.121
      netmask 255.255.255.0
      network 192.168.10.0
      broadcast 192.168.10.255
      dns-nameservers 192.168.10.2
      dns-search example.com
]

these were the outputs you asked.... these were done according to the documntations... i was trying in many ways but these were the  outputs which i got after connecting to LAN

---

### Post by Rakesh055 on 2011-03-09
Can i download packages of Ubuntu Gnome and install on server through command prompt?

---

### Post by matt_symes on 2011-03-09
Hi
 
I am actually going to have a good read of the document you have been following to try to work out where you are with this and what you are trying to achieve.

> Can i download packages of Ubuntu Gnome and install on server through command prompt?

It's certainly possible to install, via the command line, the packages required for gnome. 

But to answer your question: Possibly. I will have a better understanding when i have read the document. It might take a day or two.

Personally i would try to fix the issues with the current install.

Kind regards

---

