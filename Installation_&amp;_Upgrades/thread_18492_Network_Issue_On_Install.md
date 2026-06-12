---
title: "Network Issue On Install"
date: 2005-03-07
forum: Installation &amp; Upgrades
---

### Post by rshd301 on 2005-03-07
I have tried on a few occasions to install Ubuntu but seem to be hitting the same problem over and over again. During installation, both my mobo ethernet and my PCI ethernet are recognised but DHCP fails on each.

I know that there is no issue with the connections as I have other OS's using them without any problem.

I have used Ubuntu on another PC before and would dearly love to get this matter resolved and be up and running with it again.

Can I resolve the problem after installation in any way or is there a cheat during the installation.

Look forward to your assistance.

---

### Post by tkiesel on 2005-03-07
[QUOTE=rshd301]I have tried on a few occasions to install Ubuntu but seem to be hitting the same problem over and over again. During installation, both my mobo ethernet and my PCI ethernet are recognised but DHCP fails on each.

I know that there is no issue with the connections as I have other OS's using them without any problem.
[/QUOTE]


Hi rshd301,

I had the exact [same behavior](http://www.ubuntuforums.org/showpost.php?p=67140&postcount=9)  on my machine too. I could see that the ethernet card was recognized as 'eth0' in Ubuntu's Device Manager. [Computer -> System Configuration -> Device Manager] Under the advanced tab, I saw "net.interface    string   eth0"

All I had to do was configure eth0 in the interfaces file. 

my /etc/network/interfaces
```
# Used by ifup(8 ) and ifdown(8 ). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
#end
```
This tells Ubuntu to use eth0 and to configure using DHCP. You'll probably be able to copy that verbatim and have at least one of your ethernet connections working. (whichever one was assigned the name 'eth0'.) If Ubuntu named your second ethernet adapter 'eth1' (a good chance of that, I think) you'd go ahead and add 
```
auto eth1
iface eth1 inet dhcp
```
before the #end of /etc/network/interfaces and have both of them rocking with DHCP.

That's how it worked for me. :) Good luck!!

---

