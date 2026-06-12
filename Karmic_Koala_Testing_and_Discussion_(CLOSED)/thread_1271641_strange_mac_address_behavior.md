---
title: "strange mac address behavior"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xlnt01 on 2009-09-21
I'm experiencing something very strange here.
I'm getting a different mac address almost every time I reboot my computer. 
When I run:
ip a
It shows me different mac addresses and also my DHCP reservations does not work since they are bound to mac addresses...

I only have one nic on my motherboard and I have never seen this kind of behavior earlier.
This is the output of dmesg |grep eth0
atl1 0000:02:00.0: eth0 link is up 1000 Mbps full duplex

Has anyone else experienced this and where does ubuntu get the strange mac addresses from?

---

### Post by xlnt01 on 2009-09-21
I'm I really the only one having this problem?

---

### Post by xlnt01 on 2009-09-28
Still no one else having this issue?

---

### Post by VMC on 2009-09-28
> **xlnt01 said:**
> I'm experiencing something very strange here.
I'm getting a different mac address almost every time I reboot my computer. 
When I run:
ip a
It shows me different mac addresses and also my DHCP reservations does not work since they are bound to mac addresses...

I only have one nic on my motherboard and I have never seen this kind of behavior earlier.
This is the output of dmesg |grep eth0
atl1 0000:02:00.0: eth0 link is up 1000 Mbps full duplex

Has anyone else experienced this and where does ubuntu get the strange mac addresses from?

I've never bothered with or even thought of using ip a comand. No reason to since my connections just work. You are having problems with DHCP reservations. I'll check now and see if mine change as well. Here's my dmesg output:

```
dmesg |grep eth0
[    3.650699] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   15.154512] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.156393] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   15.156801] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   25.840018] eth0: no IPv6 routers present

```

---

### Post by wizard10000 on 2009-09-28
> **xlnt01 said:**
> I'm experiencing something very strange here.
I'm getting a different mac address almost every time I reboot my computer. 
When I run:
ip a
It shows me different mac addresses and also my DHCP reservations does not work since they are bound to mac addresses...

I only have one nic on my motherboard and I have never seen this kind of behavior earlier.
This is the output of dmesg |grep eth0
atl1 0000:02:00.0: eth0 link is up 1000 Mbps full duplex

Has anyone else experienced this and where does ubuntu get the strange mac addresses from?

That's not a MAC address.

---

### Post by doas777 on 2009-09-28
nope. I believe the "0000:02:00.0" is the time offset from boot. dmesg is usually layed out that way.

run ifconfig to find your mac

make sure that the package macchanger is not installed.

---

### Post by xlnt01 on 2009-09-28
Thanks for the tip but macchanger is not installed. Still I get a new mac address on my eth0 on every boot.

This is so weird...

And I have also tried replace network-manager with wicd but I still get a new mac address upon reboot so I guess that takes network-manager out of the equation.

---

### Post by xlnt01 on 2009-09-28
Even with a fixed IP set I get a new mac address. This is really annoying...

---

### Post by jocko on 2009-09-28
> **xlnt01 said:**
> Even with a fixed IP set I get a new mac address. This is really annoying...
Are you sure it's the mac address that's changing? Isn't that hardcoded in the actual nic?
Check for "HWaddr" in the output of:
```
ifconfig
```

---

### Post by miegiel on 2009-09-28
> **jocko said:**
> Are you sure it's the mac address that's changing? Isn't that hardcoded in the actual nic?
Check for "HWaddr" in the output of:
```
ifconfig
```

It's not hardwired, it's in a flashable part of the network chip. For all normal purposes it's fixed but you (and software) can change it.

*ip a* and *ifconfig eth0* both will spew out the mac/hardware address.

```
user@machine:~$ ip a
...
(other NICs)
...
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether **[COLOR="Red"]00:a0:d1:af:79:1b[/COLOR]** brd ff:ff:ff:ff:ff:ff
    inet 10.1.1.12/8 brd 10.255.255.255 scope global eth0
    inet6 fe80::2a0:d1ff:feaf:791b/64 scope link 
       valid_lft forever preferred_lft forever
...
(other NICs)
...
user@machine:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr **[COLOR="Red"]00:a0:d1:af:79:1b[/COLOR]**  
          inet addr:10.1.1.12  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::2a0:d1ff:feaf:791b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1268190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:959304 errors:0 dropped:0 overruns:0 carrier:19
          collisions:0 txqueuelen:1000 
          RX bytes:1405419010 (1.4 GB)  TX bytes:544808106 (544.8 MB)
          Interrupt:28
```
Back in a few min, rebooting to see if anything changes. Not that I really expect it  will change :twisted:

Nope, no change here, still *00:a0:d1:af:79:1b*

---

### Post by doas777 on 2009-09-28
if it really is changing, then I guess you could install macchanger, and use it to set your mac at login, to a specific addr.

---

### Post by NullHead on 2009-09-28
Why not just set a static IP and hwaddress in /etc/network/interfaces? 

Here's an example: 
```
auto eth0
iface eth0 inet static
    address 192.168.x.x
    gateway 192.168.x.x
    netmask 255.255.255.0
    hwaddress xx:xx:xx:xx:xx:xx
```

Where address is your IP address, hwaddress is your MAC address, gateway is usually your router's IP address (probably 192.168.1.1).

---

### Post by xlnt01 on 2009-09-29
If I edit the /etc/network/interfaces and add:
iface eth0 inet static
address	192.168.10.11
netmask	255.255.255.0
gateway	192.168.10.254
Then eth0 will not come online upon reboot. Seems like there's work going on in dev that are changing the way the network works.
I can manually bring it up after reboot by using ifup eth0 but running /etc/init.d/networking start/stop does not seem to work anymore in karmic.

And maybe I could set the mac address in /etc/network/interfaces as well but that still does not solve the actual issue which is that I would like to use DHCP and reserve my ip in the dhcp server to my actual mac address and still the question, what is it that make it change mac address on every boot? That's the question.

---

### Post by doas777 on 2009-09-29
> **xlnt01 said:**
> If I edit the /etc/network/interfaces and add:
iface eth0 inet static
address    192.168.10.11
netmask    255.255.255.0
gateway    192.168.10.254
Then eth0 will not come online upon reboot. Seems like there's work going on in dev that are changing the way the network works.
I can manually bring it up after reboot by using ifup eth0 but running /etc/init.d/networking start/stop does not seem to work anymore in karmic.

And maybe I could set the mac address in /etc/network/interfaces as well but that still does not solve the actual issue which is that I would like to use DHCP and reserve my ip in the dhcp server to my actual mac address and still the question, what is it that make it change mac address on every boot? That's the question.


do you hav4e
```
auto eth0
``` above your snippet of code?

---

### Post by xlnt01 on 2009-09-30
> **doas777 said:**
> do you hav4e
```
auto eth0
``` above your snippet of code?

I missed that, thanks for pointing it out. Now It brings up eth0 upon boot with my static ip on eth0 but I still get random mac addresses!?!?
Going to do a complete reinstall of my computer once the beta is out and hopefully this strange mac address behavior will be history then.
But still I would really like to know what it is that changes it...

---

### Post by doas777 on 2009-09-30
> **xlnt01 said:**
> I missed that, thanks for pointing it out. Now It brings up eth0 upon boot with my static ip on eth0 but I still get random mac addresses!?!?
Going to do a complete reinstall of my computer once the beta is out and hopefully this strange mac address behavior will be history then.
But still I would really like to know what it is that changes it...

before nuking, look at this:
[http://www.alobbs.com/macchanger](http://www.alobbs.com/macchanger)

you can use macchanger to set your mac to any arbitrary value, so i would just change it to the one that your router expects.

---

### Post by NullHead on 2009-09-30
You can also specify your mac address in /etc/network/interfaces. That's what the line "hwaddress xx:xx:xx:xx:xx:xx" is for. Simply find out what you'd like your mac address to be, and specify it in /etc/network/interfaces

---

### Post by xlnt01 on 2009-09-30
Thanks for the suggestions they sure solve the dhcp problems but still, what the heck is it that keep changing the mac address? Never experienced this with any other linux dist/ubuntu version/windows on this computer before so there's got to be something within karmic that makes it change the mac address every time I reboot the computer. So now I want to find out why it does. Can't sleep well at night until then :lolflag:

---

