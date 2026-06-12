---
title: "Encryption does not work."
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by wisedesi on 2005-11-15
Hi All,

I have tried searching forums and found some help but did not work for me. 
I just installted UBUNTU and installtion went fine. It also recognized my wireless pcmcia card without any problem (which was my biggest worry).
Now I have issues configuring the WEP.

All I am doing is going in the network setting and setting up properties for ESSID, Key Type and WEP key. It just does not work. It is not able to get any IP address, I have looked my router log and it does tries to getsomething. First I was using string, I chaned my setting to hex only also without luck.

When I removed WEP all worked fine. Also looked at /etc/network/interface and tried to modify the setting over there with no luck. One interesting thing was I have my routher set on channel 9 and when I performed scanning with iwlist it shows as channel 3 , after hardcoing in /etc/network/interface all looks fine.

FYI. Any help will be appriciated. It is ATT plugNshare card.

---

### Post by daller on 2005-12-01
[QUOTE=wisedesi]Hi All,

I have tried searching forums and found some help but did not work for me. 
I just installted UBUNTU and installtion went fine. It also recognized my wireless pcmcia card without any problem (which was my biggest worry).
Now I have issues configuring the WEP.

All I am doing is going in the network setting and setting up properties for ESSID, Key Type and WEP key. It just does not work. It is not able to get any IP address, I have looked my router log and it does tries to getsomething. First I was using string, I chaned my setting to hex only also without luck.

When I removed WEP all worked fine. Also looked at /etc/network/interface and tried to modify the setting over there with no luck. One interesting thing was I have my routher set on channel 9 and when I performed scanning with iwlist it shows as channel 3 , after hardcoing in /etc/network/interface all looks fine.

FYI. Any help will be appriciated. It is ATT plugNshare card.[/QUOTE]

"ATT plugNshare"-sounds pretty "No-name" to me...

It is a known bug that many NIC's does not support WEP on Linux...

Have you tried ndiswrapper (using windows drivers) to get it to work???

I assume that your pc uses the intel i368 architecture! (ndiswrapper has a hard time running on AMD64)

See this howto:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

---

