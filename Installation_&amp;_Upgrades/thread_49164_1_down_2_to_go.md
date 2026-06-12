---
title: "1 down 2 to go"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by charlieuk on 2005-07-15
the machine I have installed ubunto on has successfully detected the LAN and can see all the machines thereon, how ever whenever i attemt to go online I get the error message 'connection refused when trying to contact *whoever*


Also, If I attempt to enable windows networking so I can add the machine to the work group I get the message ;smb support is not running, You don't have smb installed, please install smb support to enable file sharing in windows networks'

Does this have anything to do with the problem above ???

---

### Post by az on 2005-07-15
[QUOTE=charlieuk]the machine I have installed ubunto on has successfully detected the LAN and can see all the machines thereon, how ever whenever i attemt to go online I get the error message 'connection refused when trying to contact *whoever*


Also, If I attempt to enable windows networking so I can add the machine to the work group I get the message ;smb support is not running, You don't have smb installed, please install smb support to enable file sharing in windows networks'

Does this have anything to do with the problem above ???[/QUOTE]


By default, the box will try to make a dhcp connection.  DO you have a dhcp server on your network?


"Please install smb" means go into synaptic and install samba.  By default, an ubuntu box can listen but cannot talk to the network.

---

### Post by charlieuk on 2005-07-15
TY Azz M8

the router I am using for the workgroup is DHCP compatible althought all the other machines have been manually configured

my other problem is that although I did 1 semester in unix scripting about 8yrs ago, I haven't used it since, and I have yet to get to find out where to start scripting in this enviroment, I was hoping there were GUI solutions to this ...never mind :)

---

### Post by charlieuk on 2005-07-15
OK I've installed smb taken ethernet card off DHCP and configured it manually, still getting same error when trying to connect to net, does the LAN card need to be installed using its cd ???

---

