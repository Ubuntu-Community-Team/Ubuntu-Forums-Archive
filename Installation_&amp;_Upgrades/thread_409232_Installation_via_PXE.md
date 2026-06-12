---
title: "Installation via PXE"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by Doodles2000 on 2007-04-14
Hi All,
   First question post for me here in the land of ubuntu (please be gentle).

The Story goes something like:

Running Ubuntu Feisty on my PC.  The wifes PC running on Edgy.  I have setup a local ubuntu (dapper server) box to act as an internal web server(apache), file server, DHCP server and local ubuntu repository mirror.
I am trying to get the dapper server box to also act as a PXE install box.

Currently using apt-mirror to mirror the main restricted multiverse and universe stores for dapper,edgy and feisty.  This is quite happily working and supplying LAN speed updates to the local PC's (wooo hooo!) via apache.  

Sym links have been made:

/var/www/archive.ubuntu.com -> /var/spool/apt-mirror/mirror/archive.ubuntu.com and /var/www/ubuntu -> /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu

I have also followed tutorials in here to setup a PXE boot server.  This works fine, clients happily boot and load the appropriate installer via PXE.

Go through the installer - answer the country, keyboard questions and enter in the IP address of the local mirror server into the install screens.

after a breif pause it comes back with cannot download a file.  Can some one assist in pinpointing where the problem may lay?

below is a snippett of the syslog file from the client on a failure

Apr 15 00:20:14 choose-mirror[5672]: DEBUG: command: wget -q [http://archive.ubuntu.com/ubuntu/dists/edgy/Release](http://archive.ubuntu.com/ubuntu/dists/edgy/Release) -O - | grep ^Suite: | cut -d' ' -f 2 
Apr 15 00:20:17 choose-mirror[5672]: DEBUG: command: echo 5  > /proc/sys/net/ipv4/tcp_syn_retries 
Apr 15 00:20:17 choose-mirror[5672]: DEBUG: command: wget -q [http://192.168.0.252/ubuntu//dists/edgy/Release](http://192.168.0.252/ubuntu//dists/edgy/Release) -O - | grep ^Suite: | cut -d' ' -f 2 
Apr 15 00:20:17 choose-mirror[5672]: DEBUG: command: wget -q [http://192.168.0.252/ubuntu//dists/edgy/Release](http://192.168.0.252/ubuntu//dists/edgy/Release) -O - | grep ^Codename: | cut -d' ' -f 2 
Apr 15 00:20:17 choose-mirror[5672]: INFO: codename set to: edgy 
Apr 15 00:20:17 choose-mirror[5672]: DEBUG: command: wget -q [http://192.168.0.252/ubuntu//dists/edgy/main/binary-i386/Release](http://192.168.0.252/ubuntu//dists/edgy/main/binary-i386/Release) -O - | grep Architecture 
Apr 15 00:20:17 anna-install: Queueing udeb edgy-support for later installation
Apr 15 00:20:17 main-menu[2756]: DEBUG: resolver (libc6): package doesn't exist (ignored) 
Apr 15 00:20:17 main-menu[2756]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Apr 15 00:20:17 main-menu[2756]: INFO: Falling back to the package description for console-setup-udeb 
Apr 15 00:20:17 main-menu[2756]: INFO: Falling back to the package description for console-setup-udeb 
Apr 15 00:20:17 main-menu[2756]: INFO: Menu item 'download-installer' selected 
Apr 15 00:20:17 net-retriever: gpgv: Signature made Wed Oct 25 17:13:17 2006 UTC using DSA key ID 437D05B5
Apr 15 00:20:17 net-retriever: gpgv: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
Apr 15 00:20:17 anna[5721]: wget: server returned error 404: HTTP/1.1 404 Not Found^M 
Apr 15 00:20:17 anna[5721]: wget: server returned error 404: HTTP/1.1 404 Not Found^M 
Apr 15 00:20:17 anna[5721]: wget:  
Apr 15 00:20:17 anna[5721]: server returned error 404: HTTP/1.1 404 Not Found^M 
Apr 15 00:20:17 anna[5721]:  
Apr 15 00:20:17 anna[5721]: wget:  
Apr 15 00:20:17 anna[5721]: server returned error 404: HTTP/1.1 404 Not Found^M 
Apr 15 00:20:17 anna[5721]:  
Apr 15 00:20:20 anna[5721]: WARNING **: bad d-i Packages file 

I am guessing the problem is with the server returning 404 errors.  I do not know which files it cannot find.

Am happy to post up more config files if required.

Any help would be appreciated

Mark

---

