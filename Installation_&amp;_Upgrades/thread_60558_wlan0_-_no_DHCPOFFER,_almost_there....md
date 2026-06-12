---
title: "wlan0 - no DHCPOFFER, almost there..."
date: 2005-08-28
forum: Installation &amp; Upgrades
---

### Post by KurtB on 2005-08-28
Hi,

I believe I'm just one step away getting my wifi configured fot ubuntu, but I just don't get any IP...

WIFINIC: Belkin54G PCMCIA - "bcmwl5a"-case
AP: Belkin 125mbps router, configured as AP

I followed the howto's I found on this forum concerning ndiswrapper & bcmwl5 and got this far:

- Power LED=ON on PC card, LINK=BLINKS
- System -> admin -> network: wlan0 = active
- iwlist wlan0 scan -> OK, sees my SSID & I get link quality, freq info etc,...

```

sudo dhclient wlan0 

```

returns:
DHCPDISCOVER wlan0 to 255.255.255.255 port 67
...
NO DHCP OFFER received
no working leases in persistent database - sleeping

and I also noticed in the bcmwl5a folder from /etc/ndiswrapper that in the *.conf file no parameters are set for SSID| & WEP|

Is this correct?
I did
sudo iwconfig wlan0 essid <mywifi>
sudo iwconfig wlan0 enc <mykey>
though

What is going wrong in my final step to get my wireless connection up and running?

---

### Post by Toddy on 2005-08-28
I was getting the same type of results until I switched my routers authentication from "shared" to "open".  Then I was good...

---

### Post by KurtB on 2005-08-28
thx for the reply,

but I think it is already "open" (that's what it says when I boot under Win XP)

Or do you mean the configuration of the WNIC just before setting essid & enc?

---

### Post by votum on 2005-08-29
hi,
> Is this correct?
I did
sudo iwconfig wlan0 essid <mywifi>
sudo iwconfig wlan0 enc <mykey>

I think this code could be better

```
sudo iwconfig wlan0 key restricted <mykey>
```

---

### Post by KurtB on 2005-08-31
Hi,

thx for the reply.

I just tried:
```
sudo iwconfig wlan0 key restricted <mykey>
``` 

But it keeps saying that there is'nt a DHCP OFFER received

and I did to restart my cablemodem.

On top of that my ISP-subscrition includes 2 IP's. And my router is set as AP -not as a router- so it should get an OFFER from my ISP's DHCP server (or am I wrong?)

---

### Post by hamil on 2005-09-01
[QUOTE=KurtB]Hi,

thx for the reply.

I just tried:
```
sudo iwconfig wlan0 key restricted <mykey>
``` 

But it keeps saying that there is'nt a DHCP OFFER received

and I did to restart my cablemodem.

On top of that my ISP-subscrition includes 2 IP's. And my router is set as AP -not as a router- so it should get an OFFER from my ISP's DHCP server (or am I wrong?)[/QUOTE]
 Hello!
I have the same problems and same symbols, but maybe this is some issue with the network provider???

Anyone have any ideas??? 
I have tried the wifiradar to connect, and it communicates with my network provider, but it is not able to get an ip...

HELP! :)

---

### Post by pwabrahams on 2008-02-18
I have the same problem -- no DCHP offer received -- but some more information about it:

1. I can get a connection under Windows, so it must be possible to get a connection under Linux if Linux asks nicely for one.  But what "nicely" means, I know not.

2. Resetting the router -- at least in some circumstances -- enables the router to issue the necessary DHCP offer to Linux.  Unfortunately that works only when you have physical access to the router, and at the moment I don't.

Maybe this extra information will help someone find a solution to the problem.

---

