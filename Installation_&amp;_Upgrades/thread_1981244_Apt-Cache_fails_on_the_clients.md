---
title: "Apt-Cache fails on the clients"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by lisanels47 on 2012-05-16
Server:  Ubuntu 12.04 running apt-cache as shown in this doc:
[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

Client: Ubuntu 12.04 (And hopefully 11.10 clients) With 01proxy method to use apt-cache.

Appears to be a issue with apache since I get a 403 error, and also can't verify the apt-cache with server:3142


Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed/universe Translation-en
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/oneiric/partner/source/Sources)  403  Access to cache prohibited

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  403  Access to cache prohibited

---

### Post by kylewhittington on 2012-05-17
I'm having the same issue. The server running apt-cacher was recently upgraded from 11.10 to 12.04 after which I started getting this error. Clients are still running 11.10... I was hoping to be able to upgrade the clients using the cached packages from the server, but I'm getting this same error.

---

### Post by lisanels47 on 2012-05-17
Ok, still no solution, so I installed the apt-cacher on a 11.10 client system.  Setup DNS to point apt.mydomain.com to that system... 

Once I get this fixed on the 12.04 server, I'll just change the DNS entry for apt.

---

### Post by kylewhittington on 2012-05-31
Ok - seems like I've sorted it. In my /etc/apt-cacher/apt-cacher.conf, I commented out the 'group' and 'user' settings which by default use www-data. Once I commented them out and restarted apt-cacher service, the client was no longer having the access prohibited error.

Hope that helps anyone else having the same issue.

---

### Post by Agone on 2012-06-15
I have the same problem, 
your solution don't solve my problem,
i solve it with 
uncomment "allowed_hosts = *" in apt-cacher.conf
thanks

---

### Post by bmarsh on 2012-07-30
Tried both of the apt-cacher.conf fixes above (group, allowed hosts) and neither one solves my problem.

---

### Post by lisanels47 on 2012-07-30
Mine is now working.  In /etc/apt-cacher

apache.conf:Alias /apt-cacher /usr/share/apt-cacher/apt-cacher-cgi.pl
apache.conf:
apache.conf:<DirectoryMatch /usr/share/apt-cacher/>
apache.conf:    Options ExecCGI
apache.conf:    AddHandler cgi-script .pl
apache.conf:    AllowOverride None
apache.conf:    order allow,deny
apache.conf:    allow from all
apache.conf:</DirectoryMatch>

apt-cacher.conf:allowed_hosts = *

---

### Post by Ool on 2012-10-27
Hi,
Don't forget to check your allowed_hosts configuration in /etc/apt-cacher/apt-cacher.conf file.
cf: [http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher](http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher)
Perhaps default settings change with an upgrade. 
regards

---

### Post by laughmo on 2012-11-01
Thank Agone!

i solve it with 
uncomment "allowed_hosts = *" in apt-cacher.conf
thanks

---

