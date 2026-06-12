---
title: "New update kernel problems - network not working samsung nc10"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by Stankoman on 2010-03-09
Hi all

I updated ubuntu today... and got the grub message which i fixed. 

Now ubuntu is running fine, yet the WIRED internet connection does not work. It just pops up Disconnected.

Im using the sky2 driver on my samsung nc10, and it seems to be working properly except it does not connect...

So I completely reinstalled the whole system, yet the problem re-appears. 

Im guessing the latest kernel update messed up my network connection.

Any ideas ?

---

### Post by Stankoman on 2010-03-09
bump for justice...

help anyone ?

---

### Post by Stankoman on 2010-03-10
So new updates on the issue

I can set up my IP static... and ping my other computers. 

DHCPrequest is not getting any replies from the router... And i have no idea why. Changed the mac address also, no difference ...

---

### Post by Stankoman on 2010-12-24
As I remember. I had to adjust the dhcp setting. 

After the update, my settings got overridden and the network would not send its MAC address to the router. 
Router would therefor not give me any IP's. So I got discoennected.

Anyway. This was the fix:

go to:  /etc/dhcp3/dhclient.conf 

And add (or uncomment) inside the file: 
send dhcp-client-identifier 1:MAC_ADDRESS_FROM_NETWORK_CARD

You have to manually type the MAC_ADDRESS_FROM_NETWORK_CARD

If you want to get the address:
ifconfig | grep HW

That was it. 
Hope that helps

---

