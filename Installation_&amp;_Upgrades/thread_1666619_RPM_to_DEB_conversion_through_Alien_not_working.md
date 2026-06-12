---
title: "RPM to DEB conversion through Alien not working"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by espressobeanie on 2011-01-13
I'm not sure why this is happening, but if anyone knows about Alien and converting .rpm to .deb packages, it would be much obliged:

aurora@Aurora-Systems:~/Downloads$ chmod 755 range-2.2.10-1.i586.rpm
aurora@Aurora-Systems:~/Downloads$ sudo alien -i range-2.2.10-1.i586.rpm
[sudo] password for aurora: 
    dpkg --no-force-overwrite -i range_2.2.11-2_i386.deb
dpkg: error processing range_2.2.11-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 range_2.2.11-2_i386.deb
Unable to install at /usr/share/perl5/Alien/Package/Deb.pm line 92, <GETPERMS> line 426.
    find range-2.2.11 -type d -exec chmod 755 {} ;
    rm -rf range-2.2.11

---

