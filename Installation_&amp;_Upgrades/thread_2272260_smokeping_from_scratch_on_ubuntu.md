---
title: "smokeping from scratch on ubuntu"
date: 2015-04-05
forum: Installation &amp; Upgrades
---

### Post by brendon5 on 2015-04-05
Hello everyone. I'm fairly new to ubuntu and I have tried following several guides exactly and none of them provide all of the instructions necessary to get smokeping working. I have written these instructions after following several guides. I'm trying to browse to my local ip [http://192.x.x.x/cgi-bin/smokeping.cgi](http://192.x.x.x/cgi-bin/smokeping.cgi) which I have configured in general and I just get that the page can't be displayed. I've restarted all the services several times and I get no errors. If there's a step by step guide that actually includes all the steps necessary, I'd appreciate that, but so far they just assume you know half the stuff already. Also I tried chmod 755 to allow write access to files and it didn't work, so I had to do 777 which I'm told is not the best, but it seems to work ok for now. I really don't know much about ubuntu or apache or smokeping, but I'd really like to get smokeping going rather than spending $200 on pingplotter (pingplotter.com)

I have Ubuntu 14.04lts
Instructions I followed are below:

sudo apt-get install aptitude
aptitude install smokeping curl libauthen-radius-perl libnet-ldap-perl libnet-dns-perl libio-socket-ssl-perl libnet-telnet-perl libsocket6-perl libio-socket-inet6-perl apache2 sendmail
let it run
sudo apt-get install vim
sudo chmod 777 /etc/smokeping/config.d/General
vim /etc/smokeping/config.d/General
(Make sure that mailhost contains the primary MX for your email domain)
=== General ===
owner    = some guy
contact  = [email]someguy@gmail.com[/email]
mailhost = ASPMX.L.GOOGLE.COM
# NOTE: do not put the Image Cache below cgi-bin
# since all files under cgi-bin will be executed ... this is not
# good for images.
cgiurl   = http://<youriphere>/cgi-bin/smokeping.cgi
# specify this to get syslog logging
syslogfacility = local0
# each probe is now run in its own process
# disable this to revert to the old behaviour
# concurrentprobes = no
@include /etc/smokeping/config.d/pathnames
=== End General ===
sudo chmod 777 /etc/smokeping/config.d/Alerts
vim /etc/smokeping/config.d/Alerts
=== Alerts ===
to = [email]me@email.com[/email]
from = [email]smokeping@email.com[/email]
“nano /etc/smokeping/config.d/Targets”
remark = Welcome to the SmokePing website of ‘Example Company’
<output omitted>
+ Local
menu = Local
title = Local Network
++ LocalMachine
menu = Local Machine
title = This host
host = localhost
=== End Alerts ===
sudo chmod 777 /etc/smokeping/config.d/Targets
vim /etc/smokeping/config.d/Targets (change as you see fit)
sudo /etc/init.d/smokeping restart
browse to http://<youriphere>/cgi-bin/smokeping.cgi

---

### Post by brendon5 on 2015-04-05
Actually it does work, I just was browsing to the wrong ip. It's supposed to be the ip address of the computer/server that it's on. You can find this by running 'ifconfig'. Well, if anyone wants to use this as a guide, it does work. However, I think leaving the folders on permission 777 isn't good for security reasons. They could be changed back to 755. After making changes to General, Alerts, or Targets, you need to run sudo /etc/init.d/smokeping restart

---

