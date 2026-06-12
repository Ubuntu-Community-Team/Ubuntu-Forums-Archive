---
title: "Fix for FTP failures when using some (cheaper) DSL routers"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by Wielenga on 2007-04-10
After many failed attempts to use and install  Ubuntu with my router, FTP sessions did not work. Neither did web browsing. I discovered that this is due to some issues on some DSL routers. (something to do with IP V6). Most companies provide patches but not mine :( 
 

This is how I fixed it.

During install. (with the text based installer)

first create a fixed IP address or Reserve an IP address in your router. See your router documentation.

Get the DNS server IP address(es) from your ISP.  If it is not published, do an IPCONFIG /all on a windows machine that works and is connected to your router. This will tell you the DNS servers :-) (the address should not start with a 192)

plug your network card in BUT NOT THE CABLE (mine is a laptop) and let the DHCP configuration fail.

Goto manually configuring the network connection:
using your reserved IP address (in my case 192.168.0.25)
subnet mask 255.255.255.0 (in most cases)
Gateway address (usually ending on a 1 ie 192.168.0.1)
in the name servers box enter DNS ip address 1 DNS, ip address 2 (just in case the first one fails) and if you plan to use samba etc. at some point, add your router's DNS ip
in my case: (note the spaces)

xxx.xxx.xxx.44 xxx.xxx.xxx.45 192.168.0.1

Plug in your cable!!!! and continue the install.

Post install, you can achieve the same in the network manager where the DNSs are under a seperate Tab. Note that you have to use a fixed Ip address and not DHCP as the DHCP will most likely override you manual entry. If you have done the process above during install you usually don't have to do it again after installation.

Works like a treat and helped some of my friends with the same issues.

---

