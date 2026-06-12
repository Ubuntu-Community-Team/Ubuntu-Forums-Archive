---
title: "Error installing amavisd-new  error=Starting amavisd: hostname: Unknown host"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by lemit on 2007-09-25
apt-get install amavisd-new

LÃ¤ser paketlistor... FÃ¤rdig
Bygger beroendetrÃ¤d         
Reading state information... FÃ¤rdig
amavisd-new Ã¤r redan den senaste versionen.
0 uppgraderade, 0 nyinstallerade, 0 att ta bort och 0 ej uppgraderade.
1 ej helt installerade eller borttagna.
BehÃ¶ver hÃ¤mta 0B arkiv.
Efter uppackning kommer 0B ytterligare diskutrymme anvÃ¤ndas.
StÃ¤ller in amavisd-new (2.4.2-6) ...
Creating/updating amavis user account...
Starting amavisd: hostname: Unknown host
 The value of variable $myhostname is "", but should have been
 a fully qualified domain name; perhaps uname(3) did not provide such.
 You must explicitly assign a FQDN of this host to variable $myhostname
 in amavisd.conf, or fix what uname(3) provides as a host's network name (failed).
invoke-rc.d: initscript amavis, action "start" failed.
dpkg: fel vid hantering av amavisd-new (--configure):
 underprocess post-installation script gav felkod 1
Fel uppstod vid hantering:
amavisd-new
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@mail01:~#

ERROR
The value of variable $myhostname is "", but should have been
 a fully qualified domain name; perhaps uname(3) did not provide such.
 You must explicitly assign a FQDN of this host to variable $myhostname

then hostname of the machine is mail01.jms.se
root@mail01:~# 
root@mail01:~# hostname
mail01.jms.se
root@mail01:~# 

what is the problem, why can´t i install this app

---

