---
title: "Persistent apt-get error"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by atatistcheff on 2007-11-19
I'm experiencing an error whenever I update my system with apt-get.  The error is happening on two Ubuntu systems.  On both of these I've installed the amap tool from THC.  The problem is that upon finishing the amap installation (an apt-get package itself), it went out to find the latest application definitions file.  However, that file had moved to a new location so the automatic update failed.  

The problem is that now every time I install or update anything with apt-get, it still tries to find the amap application definitions update at the end of the installation.  Everything installs fine but the amap error is kind of a pain.  I guess what I need to do is find out where apt-get is getting the idea that it has to keep checking for this update.  I'm assuming since it failed that last step when installing amap it is going to keep trying until it succeeds.  How can I get apt-get to stop looking in the wrong place (or looking at all for that matter)?  

Here's the output at the end of my latest apt-get session, note that amap was installed weeks ago and not during this apt-get session.

Setting up amap (4.8-1.1) ...
Upgrading trigger, response and rpc files ...
Running Online Update for fingerprints, connecting to [www.thc.org/thc-amap](www.thc.org/thc-amap)
Error: file could not be found by web server: HTTP/1.1 302 Found
Date: Mon, 19 Nov 2007 15:03:36 GMT
Server: Apache
Location: [http://freeworld.thc.org/appdefs.resp](http://freeworld.thc.org/appdefs.resp)
Content-Length: 282
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>302 Found</title>
</head><body>
<h1>Found</h1>
<p>The document has moved <a href="http://freeworld.thc.org/appdefs.resp">here</a>.</p>
<hr>
<address>Apache Server at [www.thc.org](www.thc.org) Port 80</address>
</body></html>

dpkg: error processing amap (--configure):
 subprocess post-installation script returned error exit status 255
Setting up apt-utils (0.6.43.3ubuntu3) ...
Errors were encountered while processing:
 amap
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Pumalite on 2007-11-19
Run:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

P.S. Make sure you have build-essential[sudo apt-get install build-essential]

Report back with error messages if you keep having trouble.

---

### Post by atatistcheff on 2007-11-19
Thanks for the quick reply.  I executed the commands you suggested and still get the error.  Here's the output.  I know the correct URL for the amap fingerprints, just don't know where apt-get is getting the incorrect URL from (i.e. what file).


alext@sysa:/var/lib/apt/lists$ sudo dpkg --configure -a
Setting up amap (4.8-1.1) ...
Upgrading trigger, response and rpc files ...
Running Online Update for fingerprints, connecting to [www.thc.org/thc-amap](www.thc.org/thc-amap)
Error: file could not be found by web server: HTTP/1.1 302 Found
Date: Mon, 19 Nov 2007 15:31:55 GMT
Server: Apache
Location: [http://freeworld.thc.org/appdefs.resp](http://freeworld.thc.org/appdefs.resp)
Content-Length: 282
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>302 Found</title>
</head><body>
<h1>Found</h1>
<p>The document has moved <a href="http://freeworld.thc.org/appdefs.resp">here</a>.</p>
<hr>
<address>Apache Server at [www.thc.org](www.thc.org) Port 80</address>
</body></html>

dpkg: error processing amap (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 amap
alext@sysa:/var/lib/apt/lists$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 4B in 3s (1B/s)
Reading package lists... Done
alext@sysa:/var/lib/apt/lists$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  gnome-cups-manager python-netcdf
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?
Setting up amap (4.8-1.1) ...
Upgrading trigger, response and rpc files ...
Running Online Update for fingerprints, connecting to [www.thc.org/thc-amap](www.thc.org/thc-amap)
Error: file could not be found by web server: HTTP/1.1 302 Found
Date: Mon, 19 Nov 2007 15:32:27 GMT
Server: Apache
Location: [http://freeworld.thc.org/appdefs.resp](http://freeworld.thc.org/appdefs.resp)
Content-Length: 282
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>302 Found</title>
</head><body>
<h1>Found</h1>
<p>The document has moved <a href="http://freeworld.thc.org/appdefs.resp">here</a>.</p>
<hr>
<address>Apache Server at [www.thc.org](www.thc.org) Port 80</address>
</body></html>

dpkg: error processing amap (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 amap
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Pumalite on 2007-11-19
Remove amap
sudo dpkg --remove --force-remove-reinstreq <packagename>
sudo apt-get update
sudo apt-get upgrade
Reinstall if need be.

---

### Post by atatistcheff on 2007-11-19
Yes, removing amap would most likely remove the error too.  However the package works fine, it just contains the wrong URL to update it's fingerprint file.  The best solution would be to fix the amap package with the correct URL.  I'm willing to live with this error as it doesn't affect anything and is just an annoyance, however, do  you know who I can contact to get the URL updated in the installation package?  Or how to find that out?

Thanks

---

### Post by Pumalite on 2007-11-19
You are welcome. Sorry, I don't know how to get the right URL.

---

