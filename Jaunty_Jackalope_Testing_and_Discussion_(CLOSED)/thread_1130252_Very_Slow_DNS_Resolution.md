---
title: "Very Slow DNS Resolution"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by marcuskuhn on 2009-04-19
Hi,

first, as this is my first post, I want to say how much I appreciate the help offered in these forums. I have used the Information very often so far but never had to register to ask a questions because all the answers were already here :-)

But now I have a problem which I couldn't resolve with the information I found so far:

My DNS resolution is very slow. Even though Pings are as fast (or only marginally slower) as usual and I can use the full speed  of my connection (DSL in Switzerland). I have changed the DNS Settings (to the OpenDNS Servers) in the NetworkManager and afterwards on the Router, it didn't help. I also used a different browser (than Firefox) and deactivated IPv6 to be on the safe side but the resolving of Domain Names still takes around 2-4s or even longer.

I have this issue since Saturday but can't really say if it is in connection with an Update.

Many thanks in advance, best,

Marcus

---

### Post by psyke83 on 2009-04-19
I've noticed a strange behaviour when using NetworkManager via a DHCP connection (wired or wireless).

NetworkManager assigns two DNS addresses - the first being 192.168.0.1 (my wireless router), and the second being the first actual DNS address as configured within my router.

Try editing your connection in NetworkManager, and change from DHCP to (I think) "DHCP addresses only", and manually enter your DNS address to either a) only your router's address, or b) only your ISP's/openDNS addresses.

---

### Post by Asraniel on 2009-04-19
this might the be the ipv6 dns bug that some routers have, try to disable ipv6

---

### Post by marcuskuhn on 2009-04-19
Thanky for the fast answers!

I tried this by setting it manually to the adress of my router (before I had already entered the OpenDNS adresses this way) and it didn't help.

I already deactivated IPv6 according to this short tutorial: [http://ubuntuforums.org/showpost.php?p=7087946&postcount=42](http://ubuntuforums.org/showpost.php?p=7087946&postcount=42)

Best,

Marcus

---

### Post by marcuskuhn on 2009-04-20
Anybody have another idea?

---

### Post by philinux on 2009-04-20
How does one time the dns resolution?

---

### Post by marcuskuhn on 2009-04-20
Maybe its naive from my side, but when I try to ping it takes a while until it shows the IP (unusualy long) something or load a Website it shows "Looking up x" very long which leads me to conclude that the computer has a problem in resolving the Domain into an IP address.

Best,

Marcus

---

### Post by psyke83 on 2009-04-20
> **marcuskuhn said:**
> Maybe its naive from my side, but when I try to ping it takes a while until it shows the IP (unusualy long) something or load a Website it shows "Looking up x" very long which leads me to conclude that the computer has a problem in resolving the Domain into an IP address.

Best,

Marcus

I happens to me as well. I suspected that perhaps the MTU may impact lookup times, but lowering the MTU value didn't help for me (perhaps the MTU doesn't impact DNS resolution anyway).

What router model/firmware do you use? It may be a factor. I'm using a D-Link DI-524, B4 revision with firmware 2.07. I don't see this slow resolution in Windows XP, Vista or Windows 7.

---

### Post by marcuskuhn on 2009-04-20
I don't have another OS installed, but my Netbook which is running the Jaunty NBR and which I didn't update in the last week doesn't have the problem. Neither on WLAN nor on cable. My Router is the one provided by my ISP, a netopia 3397GP ADSL2 Router.

To further confirm the problem is related to DNS, when I enter an IP-Adress directly, browsing is as fast as usual.

---

### Post by t.alex on 2009-04-20
take a look at /etc/resolv.conf and play with the servers and see if it makes a difference

---

### Post by marcuskuhn on 2009-04-20
> **t.alex said:**
> take a look at /etc/resolv.conf and play with the servers and see if it makes a difference
thx, this helped. I had three entries in the list, two of those:
> nameserver 138.188.101.186
nameserver 138.188.101.189
removing those fixes the problem, but in the file it says it will overwrite itself, so how can I make this fix permanent?

thx again!

---

### Post by psyke83 on 2009-04-20
> **marcuskuhn said:**
> thx, this helped. I had three entries in the list, two of those:

removing those fixes the problem, but in the file it says it will overwrite itself, so how can I make this fix permanent?

thx again!

NetworkManager writes these entries. Edit your connection profile, IPv4 tab. Change from "Automatic (DHCP)" to "Automatic (DHCP) addresses only", and enter your DNS information manually. The /etc/resolv.conf should then mirror this setting.

---

### Post by marcuskuhn on 2009-04-20
I allready did that, before my second post I think. It now works and I will report back if it changed back. Otherwise I would be interested where those two DNS-Server IPs came from...

Best

---

### Post by marcuskuhn on 2009-04-21
I now switched to a new network, the one at my University, and the problem is back, attached my resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 138.188.101.186
nameserver 138.188.101.189
nameserver 130.82.128.1
search unisg.ch.
```

Any idea where those two DNS-entries are coming from?

---

### Post by carlgm on 2009-04-21
Try using: [http://www.opendns.com/](http://www.opendns.com/)

---

### Post by lithorus on 2009-04-21
> **marcuskuhn said:**
> I now switched to a new network, the one at my University, and the problem is back, attached my resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 138.188.101.186
nameserver 138.188.101.189
nameserver 130.82.128.1
search unisg.ch.
```Any idea where those two DNS-entries are coming from?
After you switched to the university connection, did you edit the profile for that connection also?

---

### Post by marcuskuhn on 2009-04-21
> **lithorus said:**
> After you switched to the university connection, did you edit the profile for that connection also? Yes I did but still had to edit the file manually. And about the OpenDNS suggestion. I already did that before my first post.

Thx,

Marcus

---

### Post by marcuskuhn on 2009-04-21
So, just arrived back home, even with the edited Config the two DNS-Server mentioned above reappear in my list and I have to edit them out manually.

Any suggestions?

Thx

---

### Post by jon_herr on 2009-04-22
I'm having the same problem...

It started after my first vpnc connection to my work was established - once I connected it correctly added in the dns servers and search domain for my work environment.

But...
Now it continues to use these settings, overwriting the file, every time I start up.

There must be something broken with vpnc, or how network manager gets it's information for generating the 'resolv.conf' file everytime networking is started.

Help!

:confused:

*UPDATE* Ok, this problem has been around since 2006 - and there is much confusion about the correct expectations are for the conditions that cause "resolvconf" to update /etc/resolv.conf

What _should_ happen - at every startup or when networking is started / stopped on a dhcp'd network computer - the /etc/resolv.conf file should be updated with the information provided by the dhcp server.  Period.
What _DOES_ happen - at least for me - is the information is updated from my dhcp server (correctly) but then it proceeds to add in the information from my last vpnc session (not right) so my dns searches all have to wait for my non-existent work dns servers to time out before checking with my local dns server (router).  

The dns entries for the vpnc connection should only exist when a vpnc connection is active, it should NOT exist when disconnected from the vpnc tunnel.

One so called "solution" that some have found is to remove the "resolveconf" package...  which will stop this updating behavior.

command line:
sudo apt-get remove resolvconf

Note that the above 'fix' actually breaks some functionality, but network-manager can still update resolv.conf file correctly.

---

### Post by jon_herr on 2009-04-22
For clarity...

One so called "solution" that some have found is to remove the "resolveconf" package... which will stop this updating behavior.

command line:
sudo apt-get remove resolvconf

Note that the above 'fix' actually breaks some functionality, but network-manager can still update resolv.conf file correctly.

---

### Post by marcuskuhn on 2009-04-23
Thanky for the Info jon_herr, I will try it, thx!

---

