---
title: "Problems to install MYSQL - dependency problems prevent configuration of mysql-server"
date: 2014-07-21
forum: Installation &amp; Upgrades
---

### Post by deme2 on 2014-07-21
I tried install MySql by sudo apt-get install mysql-server but I got stuck because I couldn't start or I didn't know how to. Anyway, I removed by  sudo aptitude purge mysql-server and try to install by sudo apt-get install -f mysql-server. Now I am getting the error below. But why do I get such error if I remove the previous installation?

Setting up mysql-community-server (5.6.19-1ubuntu14.04) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing package mysql-community-server (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up mysql-community-client (5.6.19-1ubuntu14.04) ...
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-community-server (= 5.6.19-1ubuntu14.04); however:
  Package mysql-community-server is not configured yet.


dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                    Processing triggers for libc-bin (2.19-0ubuntu6) ...
Errors were encountered while processing:
 mysql-community-server
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried sudo apt-get dist-upgrade and the result is

Setting up linux-generic (3.13.0.32.38) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Errors were encountered while processing:
 mysql-community-server
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

