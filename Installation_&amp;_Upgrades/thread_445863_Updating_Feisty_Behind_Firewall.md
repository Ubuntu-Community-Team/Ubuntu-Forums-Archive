---
title: "Updating Feisty Behind Firewall"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by aleksf on 2007-05-16
I' relatively new to Ubuntu and I like it, however I have this problem that's been driving me nuts for days now. 

I am behind the firewall at work that requires authentication and can not get to update my machine. I have tried all the recipes (Synaptic network settings with proxy IP address, port, username and passwrod, /etc/apt/apt.conf with same, command line 'export http_proxy ...' and then 'apt-get update') but nothing seems to work.

My browser works fine on Ubuntu after I authenticate myself and remeber the username/password. 
For updates on a Gentoo box, I specify http-user and http-passwd in /etc/make.conf and /usr/sbin/emerge-webrsync for wget and all goes through fine. However, on Ubuntu I can not go through the firewall.

It would be nice if someone would put out an official How-To on this issue.

Other than this problem, I'm really happy with Ubuntu (it's the first Linux distro my wife does not complain about using, which is really a good sign ;-)

Thanks,

Alex

---

### Post by beatbros on 2007-05-25
Hi,
you should edit the wget configuration file:

gksudo gedit /etc/wgetrc

find the relevant settings:

http proxy &
ftp proxy &
use proxy


here is a sample with authentication 

# You can set the default proxies for Wget to use for http and ftp.
# They will override the value in the environment.
http_proxy = [http://USER:PASSWORD@PROXYIP_or_DNS_name:PROXYPORT/](http://USER:PASSWORD@PROXYIP_or_DNS_name:PROXYPORT/)
ftp_proxy = [http://USER:PASSWORD@PROXYIP_or_DNS_name:PROXYPORT/](http://USER:PASSWORD@PROXYIP_or_DNS_name:PROXYPORT/)

# If you do not want to use proxy at all, set this to off.
use_proxy = on


without authentication

# You can set the default proxies for Wget to use for http and ftp.
# They will override the value in the environment.
http_proxy = [http://PROXYIP_or_DNS_name:PROXYPORT/](http://PROXYIP_or_DNS_name:PROXYPORT/)
ftp_proxy = [http://PROXYIP_or_DNS_name:PROXYPORT/](http://PROXYIP_or_DNS_name:PROXYPORT/)

# If you do not want to use proxy at all, set this to off.
use_proxy = on

Please note that if you have  a ftp proxy you should change my snippet sample accordingly to your configuration.

bye

---

### Post by Offoffoff on 2007-06-04
How to use proxy settings in comandline? It would be better if user can't see that password....

---

### Post by eentonig on 2007-06-04
You could make that file unreadable for regular users.

---

