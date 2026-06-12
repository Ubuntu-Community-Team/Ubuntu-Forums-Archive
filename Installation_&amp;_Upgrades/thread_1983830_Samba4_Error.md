---
title: "Samba4 Error"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by Glitchified on 2012-05-20
Hi, I was wondering if there was a solution to this error?

Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"

This happens every time I try to download Samba4, and therefore every other app I try to install.  Does anyone have any idea how to fix this?

---

### Post by BenginM on 2012-05-21
I believe you want to install samba not samba4 ..

[http://wiki.samba.org/index.php/Samba4](http://wiki.samba.org/index.php/Samba4)

read the description of samba4 in a terminal execute ..

apt-cache show samba4

so , you need to purge samba4 

sudo apt-get purge samba4

---

### Post by Glitchified on 2012-05-21
Thanks alot, this really helped me.

---

### Post by Dondo70 on 2012-06-08
Hi every one.
My problem is this:[B]
Installing package(s) with command apt-get -y  install sudo ..[/B] 

.................................
14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl:[COLOR=Red]** Permission denied dpkg: error processing samba4 (--configure):**[/COLOR]:confused: 
subprocess installed post-installation script returned error exit status 126 Setting up sudo (1.8.3p1-1ubuntu3.3) ... 
Installing new version of config file /etc/pam.d/sudo ... 
Errors were encountered while processing:  samba4 E: Sub-process /usr/bin/dpkg returned an error code (1) [B].. 

install failed![/B]

someone has an idea how to fix it?
Thanks

---

### Post by sunta on 2012-07-05
> **Dondo70 said:**
> Hi every one.
My problem is this:[B]
Installing package(s) with command apt-get -y  install sudo ..[/B] 

.................................
14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl:[COLOR=Red]** Permission denied dpkg: error processing samba4 (--configure):**[/COLOR]:confused: 
subprocess installed post-installation script returned error exit status 126 Setting up sudo (1.8.3p1-1ubuntu3.3) ... 
Installing new version of config file /etc/pam.d/sudo ... 
Errors were encountered while processing:  samba4 E: Sub-process /usr/bin/dpkg returned an error code (1) [B].. 

install failed![/B]

someone has an idea how to fix it?
Thanks

sudo chmod +x /usr/share/samba/setoption.pl
sudo apt-get -f install


that will get you past the error you describe. but you will loop in the errors that follow.
sadly dont bother with samba4

---

