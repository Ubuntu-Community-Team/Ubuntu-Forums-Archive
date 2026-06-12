---
title: "install linksys WUSB100v2 in ubuntu 10.04"
date: 2012-03-20
forum: Installation &amp; Upgrades
---

### Post by Ericyue on 2012-03-20
hi to all , 

i am currently install wireless usb stick for my machine. i have follow these link 


[http://ubuntuforums.org/showthread.php?t=1685150&page=4](http://ubuntuforums.org/showthread.php?t=1685150&page=4)
[http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)
[http://forums.fedoraforum.org/showthread.php?p=1353558](http://forums.fedoraforum.org/showthread.php?p=1353558)

but still cannot work .. although i can see the ra0 in the ifconfig and iwconfig but it still cannot detect the wireless network.

ifconfig -->
eth0      Link encap:Ethernet  HWaddr 70:71:bc:ac:b8:14  
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7271:bcff:feac:b814/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4756 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5740227 (5.7 MB)  TX bytes:712044 (712.0 KB)
          Interrupt:28 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19896 (19.8 KB)  TX bytes:19896 (19.8 KB)

ra0       Link encap:Ethernet  HWaddr 98:fc:11:c5:ca:50  
          inet6 addr: fe80::9afc:11ff:fec5:ca50/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1068 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:84600 (84.6 KB)

iwconfig -->
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



please help me .. thanks ..

---

### Post by Ericyue on 2012-03-20
hey guys , i have succesfully install and it can detect the wireless but now comes another problem also .. it keep fail to connecting and keep ask for the password. the password is 100% correct but it keep fail to connect. 

Do anyone know why it keep fail ?

---

### Post by Bucky Ball on 2012-03-20
A wild guess but have you tried switching off the N capability?

---

### Post by Ericyue on 2012-03-21
Dear Bucky Ball

i  don't think it is related to the wireless since i have 3 more machine and they use usb stick without any connection problem .  i online search and they say most probably is about the newer version cannot use . but when i install the older version , it give me -->

make: ***[Linux] Error 2


any idea about that ??? thanks in advance

---

### Post by Bucky Ball on 2012-03-21
Have you plugged in an ethernet cable, plugged in the USB dongle and updated, then checked 'Additional Drivers'? Installing manually may now conflict with whatever driver Ubuntu offers, if it does offer you one. 

Are the other machines Linux? If not, irrelevant. ;)

Also, have you manually input the access point's (router's) details in Network Manager (right click and 'Edit Connections')?

---

### Post by Ericyue on 2012-03-21
thanks for your reply.

I have plug in the ethernet cable and also the usb stick..

the previous machine are all ubuntu 10.04 LTS but the different is i have two different model of linksys usb stick (AE1000 and WUSB100v2)

i have done install 2 AE1000 and now installing the WUSB100v2 .. the method i use in AE1000 is not working with WUSB100v2 ..

and now i dunno how to solve that .. 

hope who knows about this question can give a reply to me . thanks in advance.

---

### Post by Bucky Ball on 2012-03-21
If you are installing with 10.04 LTS on this machine, have you checked that the network setup details are identical to the (functioning) others?

---

### Post by Mark Phelps on 2012-03-21
I know this is unlikely, but since each Wireless USB stick has its own unique MAC address, if your wireless router is set to screen Mac addresses (as part of the security feature), you would need to do the following:
1) Access the wireless router (through a wired connection) on another PC
2) Access the Wireless Security tab (presuming their is one)
3) If Mac Address filterin is enabled, disable it
4) See if you can connect now using the WUSB100 with the other PC
5) If you can, look at the Client List table in your Wireless router for the other PC. Write down the MAC address of the WUSB100
6) After you re-enable Mac Address Filtering (something you should always have ON at home, unless you live MILES away from anyone else), go into the security tab and manually add the entry for the Mac address you wrote down.

Just had another thought -- the AE1000 is N-class, right? If the WUSB100 is "G" (guessing this because the "100" in the name could refer to the "100" in the network speed handled), ensure that your wireless router is set to allow mixed mode (N and G).

---

### Post by Ericyue on 2012-03-23
Thanks all for your reply

i have found a link that it teach me and it works ..

[http://www.linuxforums.org/forum/wireless-internet/159738-ubuntu-9-10-wusb100v2-solved.html](http://www.linuxforums.org/forum/wireless-internet/159738-ubuntu-9-10-wusb100v2-solved.html)

go to the second page and download the attached file from comment number 12 (#12)

follow the link till "make" and "sudo make install " 

then go to terminal and type --> mv /etc/Wireless/RT3070STA /etc/Wireless/RT2870STA

then reboot and finally go to terminal again and type

modprobe RT3070STA and reboot

hope to help who meet this installation problem also :p

---

### Post by Bucky Ball on 2012-03-23
Nice work and hopefully your excellent explanation of a fix will help others. ;)

---

### Post by Xekeno on 2012-04-23
Hello

I am trying to get the WUSB100v2 to work on Ubuntu 10.04

I did some tinkering around and I got it to see the wireless router.

Ok basically I can see the router and it can see that there is a internet connection to connect too. However when I try to connect it just keeps trying to connect and never connects.

It asks me for a password which I gave and I know it's the right pw to access the router however like I said above it just keeps trying to connect and then asks me for the password again.

Any idea what I can do to remedy the wusb100v2 to actually connect?

Thank you
Best Regards,
xekeno

---

### Post by Xekeno on 2012-04-23
Ok I am just wondering does anyone know how I change the

Ra0 setup?

Currently it's Ra0 RTxx70 nickname rt3070

What I want it to be is Ra0 RT2870

Anyone know how to change it?

Thanks in Advance

---

### Post by Bucky Ball on 2012-04-23
> **Xekeno said:**
> Ok I am just wondering does anyone know how I change the

Ra0 setup?

Currently it's Ra0 RTxx70 nickname rt3070

What I want it to be is Ra0 RT2870

Anyone know how to change it?

Thanks in Advance

I suggest you post a new thread with a descriptive title regarding your issue rather than jumping on this month old one (buried 12 posts in). You will get more and more specific help. ;)

---

