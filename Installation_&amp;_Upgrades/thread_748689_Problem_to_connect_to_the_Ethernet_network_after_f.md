---
title: "Problem to connect to the Ethernet network after fresh installation"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by vazir on 2008-04-07
:confused: 

Hi Folks,

I am new to Linux. I bought a new HP PC (a6400f E2200) and installed Ubuntu 7.10 Desktop version on the machine. Installation went pretty smooth. After login, the Ethernet network is not coming up. There is no wireless card for this computer. I have tried System/Administration/Network menu to configure DHCP, it did not work. I tried Static IP, still it is not able to talk to the network. 

The /etc/networks/interfaces file is as follows:
/***************************
auto lo
iface lo inet loopback

iface eth0 inet dhcp
address 192.168.1.65
netmask 255.255.0.0
gateway 192.168.1 254


auto eth0

/***************************
 
I would appreciate if you can provide some help to get the linux platform on the network.

Thanks,
  Vazir

---

### Post by Pumalite on 2008-04-07
Double check your Gateway.

---

### Post by vazir on 2008-04-07
I have other PCs running on the network, I don't see any problem. Also when I log into the router, I don't even see the DHCP request receiving nor when I set the IP to static IP, ping does not get any response.

Thanks,
  Vazir

---

### Post by Pumalite on 2008-04-07
I noticed a 'period' is missing in your Gateway. It might be a typo.

---

### Post by vazir on 2008-04-07
It was typo while typing the message. Since I can get the file from the network, I typed it myself. Actual entry is fine.

---

### Post by Pumalite on 2008-04-07
Best thing would be a router providing you with dynamic ip and DHCP at boot.

---

### Post by vazir on 2008-04-08
I tried sudo ifdown followed by sudo ifup, still no success. I tried rebooting connecting to 2 different routers, same problem. DHCP is not able to get IP address nor able to get static ip working. I don't know what to do?

---

### Post by stefe on 2008-04-10
same problem here using eeepc and heron

---

### Post by u_i_we_all_buntu on 2008-05-16
Seems that a lot of ppl are having the same problem as you (and I).  We all bought the a6400f 2.2ghz dual core 3Gb RAM + 500Mb disk. 
... but can't run Linux on it.  Problem seen in other Linuxen.

Found one guy's solution after googling around (summary: installed
a compatible network card).

 see:   [http://www.nabble.com/rtl811-8168-td16829263.html](http://www.nabble.com/rtl811-8168-td16829263.html)

---

### Post by alguin2 on 2008-05-22
FOUND THE SOLUTION!

Please read the thread by AgDon92 "[8.04. Problem with Realtek Ethernet card r8168.]("http://ubuntuforums.org/showthread.php?t=799662&highlight=a6400f")" .

This got the **_Realtek RTL8168C/RTL8111C NIC_** that came on-board the HP a6400f working. 

BTW, the **_a6400f NOW ROCKS_** as a Ubuntu Linux box!!!

---

