---
title: "vpnc error &quot;No route to host&quot;"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by dwesner on 2009-11-25
I've just installed vpnc on Ubuntu 9.04 and when attempting to do a vpnc-connect, I can't get past the "No route to host" step.  I have thus far gone through the following steps to get to where I am now.  

Through Snyaptic Package Manager, installed   **[FONT=&quot]network-manager-vpnc [/FONT]**[FONT=&quot]package.[/FONT]

[FONT=&quot]Made vpnc SSL capable by performing the following steps manually:[/FONT]
[LIST]
[*]    [FONT=&quot]Built the deb Packages:[/FONT] apt-get install fakeroot debhelper dpatch
[*]    [FONT=&quot]Compiled vpnc with SSL Support:  [/FONT][FONT=&quot]apt-get install libgcrypt11-dev openssl libssl-dev[/FONT]
[*][FONT=&quot]Downloaded vpnc source:  [/FONT]  [FONT=&quot]apt-get source vpnc[/FONT]
[*][FONT=&quot]Uncommented the following two lines in the [/FONT]  [FONT=&quot]vpnc-0.5.3/Makefile:[/FONT]
[/LIST]
[INDENT]# OPENSSL_GPL_VIOLATION = -DOPENSSL_GPL_VIOLATION
# OPENSSLLIBS = -lcrypto[/INDENT]
[LIST]
[*]  [FONT=&quot]Built the Package: [/FONT]  [FONT=&quot]dpkg-buildpackage –rfakeroot[/FONT]
[*]  [FONT=&quot]Installed the Package:   [/FONT]  [FONT=&quot]dpkg –i vpnc_0.5.3-1_i386.deb[/FONT]
[/LIST]
        [FONT=&quot]Downloaded the **pcf2vpnc** perl script[/FONT]:    
[INDENT]wget [http://svn.unix-ag.uni-kl.de/vpnc/trunk/pcf2vpnc](http://svn.unix-ag.uni-kl.de/vpnc/trunk/pcf2vpnc)
 chmod +x pcf2vpnc
[/INDENT]  [FONT=&quot]Downloaded and Installed the **cicsco-decrypt.c** program, which is required by **pcf2vpnc**[/FONT]:
[INDENT][FONT=&quot]http://www.unix-ag.uni-kl.de/~massar/soft/cisco-decrypt.c[/FONT]
 [FONT=&quot]gcc -Wall -o cisco-decrypt cisco-decrypt.c $(libgcrypt-config --libs --cflags)
cp cisco-decrypt /usr/sbin/[/FONT]
[/INDENT]    [FONT=&quot]Converted my working Cisco .pcf files (from my Windows client) to a .conf file to work with vpnc, and make the default vpnc connection:[/FONT]
[INDENT]./pcf2vpnc dataswitch.pcf > myvpnnetwork.conf
cp myvpnnetwork.conf /etc/vpnc.conf
[/INDENT]  [FONT=&quot]I've also attempted to add various route and nameserver commands to my /etc/resolv.conf file, to no avail:
[/FONT]    [INDENT]    [LEFT][LEFT]route add -host 216.163.46.76 gw 192.168.0.1[/LEFT][/LEFT]
  [FONT=&quot]route add -host 216.163.46.76 -ifp tun0 216.163.46.76[/FONT][/INDENT]  [FONT=&quot]As root, whenever typing vpnc or vpnc-connect, after entering my password, I get the following error:
[/FONT][INDENT][FONT=&quot]vpnc: receiving packet: No route to host[/FONT]
[FONT=&quot][/FONT][/INDENT]It is also obvious by issuing commands such as "ifconf -a" and "netstat -r" that I do not have a VPN tunnel established.  

Does anyone have any ideas on how to debug?  I've been googling for hours and cannot find any reference to this particular problem. 

Thanks,
David

---

