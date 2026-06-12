---
title: "My Kubuntu cant surf the internet"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by oedha on 2007-08-20
Hi all....
so far i used edubuntu 7.04 ( i used it since version 5 ) and have no 
problems.
But now...when i tried to test Kubuntu 7.04. i got problem which it can't 
connect to the internet
What's wrong...!! ( it also happen with Skole.....both of them used 
KDE. )

What i did......
1. manual ip setting ( 192.168.111.122, sub 255.255.255.0, gate 192.168.111.1)
2. Ipsetting from ifconfig ( ifconfig eth0 192.168.111.122 )
3. edit the /etc/resolv.conf with nameserver ipdns1 up to ipdns3
4. Set the konqueror to direct connection to the internet
 
Status :
I can ping to all lokal network but....i cant ping to my ipdns...of course i 
cant surf the internet( local fine even more than just ping )

Question :
1. What should i do next ? ( this case also happen when i tried Skole )
2. When i reboot....why the system became so slow ??
3. Why the default ip ( 69.something ) still appear when i tried to ping my 
ipdns? ? i have changed the ip before
4. Where can i insert the gateway address manually ?
 
Thank you,

Harun - Lampung - Indonesia

---

### Post by HW_Hack on 2007-08-22
I had a similiar problem when I was messing with using a fixed IP versus a fully DHCP setup. Here in the US I've got a Comcast cable modem attached a standard broadband router. It seems I had to enter the IP address of Comcasts look-up (IP address lookup) router before I could surf or ping comercial sites. The entry was made into the primary DNS setting 

I used a PC at work to google Comcasts name servers IP address  .....

Is there a reason your going manual vs DHCP ? 

- Good luck

---

