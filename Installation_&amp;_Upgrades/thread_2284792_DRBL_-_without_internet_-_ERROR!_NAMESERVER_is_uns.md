---
title: "DRBL - without internet - ERROR! NAMESERVER is unset!"
date: 2015-07-01
forum: Installation &amp; Upgrades
---

### Post by lgbainbridge on 2015-07-01
I am running ubuntu 14.04 LTS in a VMWare environment (only 1 NIC).  I also installed Clonezilla/DRBL.  I have gotten everything working ONLY when I have an internet connection.  When I remove the internet connection the "sudo drblpush -i" command cannot finish building.  I get an error an error just as it tries to build:
"ERROR! NAMESERVER is unset!"
"Please set it in config file "drblpush.conf" or /etc/resolv.conf

I went into /etc/resolv.conf and it stated not to manually change as it would be overwritten.

Can anyone help me get the "sudo drblpush -i" working without an internet connection?  I am sure it is obvious but I do not have much experience with Ubuntu outside of building this Clonezilla Server.

thanks in advance.

---

### Post by dino99 on 2015-07-02
hopes it will help you  [http://www.geekyprojects.com/cloning/setup-a-clonezilla-server-on-ubuntu/](http://www.geekyprojects.com/cloning/setup-a-clonezilla-server-on-ubuntu/)

---

