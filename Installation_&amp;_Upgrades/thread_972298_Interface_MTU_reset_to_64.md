---
title: "Interface MTU reset to 64"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by krugger on 2008-11-05
Hi,

I have upgraded on my laptop to the new 8.10 release, and on reboot the network stopped working. Apparently the DHCP failed with an error message saying request too long. After debuging for a bit I found that on upgrade the interface mtu had been reset to 64 instead of the usual 1500.

So,

sudo ifconfig eth0 mtu 1500 

fixed the problem. Kind of weird, hope it isn't a generalized problem, will be upgrading more computers over the next weeks.

Krugger

---

### Post by pdaoust on 2009-03-24
I was struggling with this same problem, and I couldn't figure out how the heck to make the new MTU to stick -- I'd go
```
sudo ifconfig eth0 mtu 1500
```
then
```
sudo dhclient eth0
```
and I'd get a connection, and it would work fine -- until reboot. It turned out that NetworkManager was causing the troubles -- our 'auto eth0' entry in NM was getting an erroneous automatic MTU of 64 from somewhere (perhaps our crappy router?) and it wouldn't allow me to change it. So what I did was delete 'auto eth0' and create my own entry with an explicit MTU.

(NB: trying to set an explicit MTU in an 'auto' connection through NetworkManager doesn't work. I've tried.)

Hope this helps someone in the future!
Paul

---

### Post by The Conductor on 2009-04-30
Still there in 8.10.  It does appear to be DHCP-server or router related.  My machine does it at the Holiday Inn in Boxboro, MA but nowhere else.  I found the same fix independently; this response from dhclient

send_packet: Message too long

tipped me off to run

ifconfig -s
[FONT=Fixedsys]Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0     64     0             0              0               0           0                      2              0                0               0      BMRU
[/FONT]
64-byte MTU, what gives?  So I set the MTU to the usual 1500 and connected and now I am posting this on the forum.  It looks like you have to run the fix over and over, but not every single time you boot.  The laptop is a Dell D600.

---

### Post by The Conductor on 2009-05-11
It appears this is a fairly well-understood interoperability problem.  The bug is in the router and there is no obvious way (without making unsafe assumptions about the network environment) to program a client to do The Correct Thing when the router gives a spurious MTU value.  

[https://lists.ubuntu.com/archives/ubuntu-devel/2007-December/024845.html](https://lists.ubuntu.com/archives/ubuntu-devel/2007-December/024845.html)

Sadly, this may be one of those cases where you have to emulate MS Windows behavior, bug-for-bug, not because MS does it well, but because equipment vendors do lazy testing and if it works with Windows machines, they think they have a marketable product.  Which is to say, make the same unsafe assumptions MS does.

---

