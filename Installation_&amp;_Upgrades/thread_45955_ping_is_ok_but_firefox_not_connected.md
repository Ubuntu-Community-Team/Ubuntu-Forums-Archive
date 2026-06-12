---
title: "ping is ok but firefox not connected"
date: 2005-07-02
forum: Installation &amp; Upgrades
---

### Post by m1nx on 2005-07-02
Hello,

Just install Ubuntu,
I use single ethernet port ADSL modem at WinXP as a Internet sharing
the other hand I have another computer installed ubuntu connected to
Internet through that XP

I use two network card at my XP, first eth0 connected to ADSL modem
have Dynamic IP (given by modem), and the other eth1 have fix IP
(given by Internet Sharing App.) and connected to my Ubuntu 5.04
(my ubuntu have dynamic IP from modem ... i think ??? )

why ?
I can PING to [www.yahoo.com](www.yahoo.com) and my ISP, etc. etc., smoothly, 
but firefox browse nowhere
...connecting to www. yahoo.com.... (always.....!!).

what must todo? cause usually I use slax-live 4.2 and that work well without setting anything

thanks
-mx-

---

### Post by crashtest on 2005-07-02
[QUOTE=m1nx]Hello,

Just install Ubuntu,
I use single ethernet port ADSL modem at WinXP as a Internet sharing
the other hand I have another computer installed ubuntu connected to
Internet through that XP

I use two network card at my XP, first eth0 connected to ADSL modem
have Dynamic IP (given by modem), and the other eth1 have fix IP
(given by Internet Sharing App.) and connected to my Ubuntu 5.04
(my ubuntu have dynamic IP from modem ... i think ??? )

why ?
I can PING to [www.yahoo.com](www.yahoo.com) and my ISP, etc. etc., smoothly, 
but firefox browse nowhere
...connecting to www. yahoo.com.... (always.....!!).

what must todo? cause usually I use slax-live 4.2 and that work well without setting anything

thanks
-mx-[/QUOTE]

I wonder if you're having DNS problems?  Try putting [http://64.21.33.9/](http://64.21.33.9/) into firefox, and see if you get anything.  (Should take you to ubuntuforums.org)

---

### Post by m1nx on 2005-07-03
yes....
it's work..!!
then what must todo ??
 :roll: 

-mx-

---

### Post by mingus on 2005-07-03
[QUOTE=m1nx]yes....
it's work..!!
then what must todo ??
 :roll: 

-mx-[/QUOTE]

Sytem/Preferences/Networking - DNS tab

Try 2 things, first, use the IP of your ICS machine; it may pass thru the DNS (like a router)

Or enter your ISP's DNS addresses.  You can see this in XP networking.

---

### Post by m1nx on 2005-07-05
I try to fill with ICS IP 192.168.0.1 but still same...

how to get ISP DNS, there is a tool ??

thx
-mx- :-k

---

### Post by mingus on 2005-07-05
[QUOTE=m1nx]I try to fill with ICS IP 192.168.0.1 but still same...

how to get ISP DNS, there is a tool ??

thx
-mx- :-k[/QUOTE]

Did your ADSL modem come with a software utility to set it up?  Or more likely the modem has a web browser interface, so you can access it with Firefox or IE?  This should tell you the modem's gateway IP and the DNS servers.

Also try in XP, right-click on the network adapter, go to properties, click on the TCP/IP selection, then click properties, and the Advanced tab.  You might see the DNS there.

---

### Post by mingus on 2005-07-06
I came across the following . . . also suggest you search the Forums for "Internet Connection Sharing" and "ICS" . . .

[https://wiki.ubuntu.com/forum/hardware/InternetConectionSharing](https://wiki.ubuntu.com/forum/hardware/InternetConectionSharing)

---

### Post by wylfing on 2005-07-06
This almost surely has nothing to do with your ISP. It has to do with the fact that many "cheap" modems choke on IPv6 requests. Unfortunately, the Ubuntu build of Firefox likes to try IPv6 by default. The solution is to tell Firefox to stop it.

1. In Firefox, type about:config in the address bar and click Go.
2. Type ipv6 in the Filter box. This should limit the list of configuration options to just one called "network.dns.disableIPv6".
3. Double-click network.dns.disableIPv6 to change it from false to true.

Now Firefox will stop confusing your modem. Happy browsing!

---

### Post by m1nx on 2005-07-11
\\:D/  YESSS.....

You did it .... you did it .... horray .....

thanks every body, wylfing your suggest right on the target !!

-mx-

---

### Post by bakert on 2006-02-16
wylfing, you saved my life.  Thanks so much!

---

