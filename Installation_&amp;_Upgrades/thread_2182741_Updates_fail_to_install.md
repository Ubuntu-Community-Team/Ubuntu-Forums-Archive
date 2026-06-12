---
title: "Updates fail to install"
date: 2013-10-22
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2013-10-22
Using the Update Manager I get an error message 'Failed to download package files' 'check your internet connection' after it runs for about a minute with message 'applying changes'. I am using a Dell mini 10 netbook. The internet connection is by direct Erthernet cable to a router and there are no problems as my desktop computer is working fine. 

Using Ubantu 12.04 LTS
[FONT=arial]
Error message 'Details' :
Failed to fetch [/FONT][http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.2.8-11ubuntu6.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.2.8-11ubuntu6.1_i386.deb)[FONT=arial] 404 Not Found [IP: [/FONT][194.169.254.10]("tel:194.169.254.10")[FONT=arial] 80][/FONT]
[FONT=arial]Failed to fetch [/FONT][http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_3.4.2-0ubuntu0.6.3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_3.4.2-0ubuntu0.6.3_i386.deb)[FONT=arial] 404 Not Found [IP:[/FONT][194.169.254.10]("tel:194.169.254.10")[FONT=arial] 80][/FONT]

---

### Post by bapoumba on 2013-10-22
> **angel mike said:**
> Using the Update Manager I get an error message 'Failed to download package files' 'check your internet connection' after it runs for about a minute with message 'applying changes'. I am using a Dell mini 10 netbook. The internet connection is by direct Erthernet cable to a router and there are no problems as my desktop computer is working fine. 

Using Ubantu 12.04 LTS
[FONT=arial]
Error message 'Details' :
Failed to fetch [/FONT][http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.2.8-11ubuntu6.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.2.8-11ubuntu6.1_i386.deb)[FONT=arial] 404 Not Found [IP: [/FONT][194.169.254.10]("tel:194.169.254.10")[FONT=arial] 80][/FONT]
[FONT=arial]Failed to fetch [/FONT][http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_3.4.2-0ubuntu0.6.3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_3.4.2-0ubuntu0.6.3_i386.deb)[FONT=arial] 404 Not Found [IP:[/FONT][194.169.254.10]("tel:194.169.254.10")[FONT=arial] 80][/FONT]

I also get a 404 on these links. Could you please post your sources.list (cat /etc/apt/sources.list) or there is an issue with the repos (then temporarily try with the main servers).

---

### Post by ibjsb4 on 2013-10-22
3.2.8-11ubuntu6.1_i386.deb
Could it of been dropped?

I see these
3.2.8-11ubuntu6.2_i386.deb
3.2.8-11ubuntu6_i386.deb

[http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procps/](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procps/)

---

