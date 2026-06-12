---
title: "Frostwire working for dapper  and edgy"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by Franscisco on 2007-04-14
If you have dapper 6.06 or edgy 6.10 in your box, you can make Frostwire work following these steps.

To know what version you have paste what is inside the parenthesis (lsb_release -cd)

download java from APPLICATIONS, ADD AND REMOVE PROGRAMS. Search for java. make sure the SHOW box has ALL AVAILABLE APPLICATIONS. in ALL, you will find java 5.0 plugins, and java 5.0 runtime. 

or
using automatix, install java 5.0
download automatix from [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation) 

so, after downloading java from either add and remove or automatix,
 open the TERMINAL and paste what is inside the parenthesis (sudo update-alternatives --config java) from here, you choose  the option you see here /usr/lib/jvm/java-1.5.0-sun/jre/bin/java 

To make sure in the TERMINAL paste what is in the parenthesis (sudo apt-get remove frostwire) this will make sure there is no Frostwire versions.

 after that, in the TERMINAL, paste what is inside the parenthesis  (wget -c [http://www.users.on.net/~stubby/FrostWire-4.10.9-2.i586.deb](http://www.users.on.net/~stubby/FrostWire-4.10.9-2.i586.deb)
sudo dpkg -i FrostWire-4.10.9-2.i586.deb)
 
This should work!

---

