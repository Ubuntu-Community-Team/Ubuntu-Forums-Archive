---
title: "Why does installing os need internet connection? how to avoid?"
date: 2015-07-05
forum: Installation &amp; Upgrades
---

### Post by Higgins909 on 2015-07-05
When I installed 14.04 lts on my server, it was like 4gb iso or something but it was basically used as a boot drive and downloaded everything off the internet... 
that made me very angry lol but even more when I had to do it a second time...

I downloaded the 15.04 and found out its only 616mb.
how do I avoid downloading from the internet again? not only is a waste of bandwidth for me, but it takes longer too.

I think I'm going to have to reinstall as samba is very messed up and I need that.

---

### Post by TheFu on 2015-07-06
No need to reinstall just to fix samba.  You can **purge** the samba install and re-install it which will start over from scratch - just for samba.

if you don't want to download stuff from the internet during the installation, don't connect the network and/or don't check the "get updates during install" checkbox.  I find it easier to just pull the cable.  Of course, immediately after the install is completed and rebooted, it would be smart to patch the system.  The distribution ISOs are usually a month old, so getting the latest security patches really is important if the system is on any network.

---

### Post by kerry_s on 2015-07-06
you don't need internet for install. it will install without internet.

---

### Post by Bucky Ball on 2015-07-06
I think you'll find that the server install is the same as the minimal install. You do need internet to install. Regular desktop install conventions do not apply. :)

As far as I know, the server is the minimal.iso with server apps and related bits added. They are summoned down the line. They are not included with the base Ubuntu kernel in the .iso.

---

### Post by grahammechanical on 2015-07-06
The 14.04 (trusty) server ISO images are only 575 MB in size. So, I do not know what ISO you downloaded at 4 GB in size. Even a full Ubuntu desktop ISO image (1.1 GB) is not that big.

If we want to reduce the amount of updates needed after installation then we can install a daily built ISO image. They contain all the updates made to 14.04.2 since it was released. They are still being built for 14.04 (trusty) as work is moving on to release 14.04.3 at the end of August.

[http://cdimage.ubuntu.com/ubuntu-server/trusty/daily/](http://cdimage.ubuntu.com/ubuntu-server/trusty/daily/)

As part of the install process of the server edition we are ask to select which Package Tasks we want installed. These packages are said to be installed from the CD but I guess they will need updating at some point.

[https://help.ubuntu.com/lts/serverguide/installing-from-cd.html#install-tasks](https://help.ubuntu.com/lts/serverguide/installing-from-cd.html#install-tasks)

> During the Server Edition installation you have the  option of installing additional packages from the CD. The packages are  grouped by the type of service they provide.

 
[LIST]
[*] 	        DNS server: Selects the BIND DNS server and its documentation.


[*] 	        LAMP server: Selects a ready-made Linux/Apache/MySQL/PHP server.


[*] 	         		Mail server: This task selects a variety of packages useful for a general purpose mail  server system. 	        


[*] 	        OpenSSH server: Selects packages needed for an OpenSSH server.


[*] 	        PostgreSQL database: This task selects client and server packages for the PostgreSQL database.


[*] 	        Print server: This task sets up your system to be a print server.


[*] 	        Samba File server: This task sets up your  system to be a Samba file server, which is especially suitable in  networks with both Windows and Linux systems.


[*] 	         		Tomcat Java server: Installs Apache Tomcat and needed dependencies. 	        


[*] 	         		Virtual Machine host: Includes packages needed to run KVM virtual machines. 	        


[*] 	                 Manually select packages: Executes aptitude allowing you to individually select packages. 	        

[/LIST]



Regards.

---

### Post by Bucky Ball on 2015-07-06
> **grahammechanical said:**
> The 14.04 (trusty) server ISO images are only 575 MB in size. So, I do not know what ISO you downloaded at 4 GB in size. Even a full Ubuntu desktop ISO image (1.1 GB) is not that big.

If we want to reduce the amount of updates needed after installation then we can install a daily built ISO image. They contain all the updates made to 14.04.2 since it was released. They are still being built for 14.04 (trusty) as work is moving on to release 14.04.3 at the end of August.

[http://cdimage.ubuntu.com/ubuntu-server/trusty/daily/](http://cdimage.ubuntu.com/ubuntu-server/trusty/daily/)

As part of the install process of the server edition we are ask to select which Package Tasks we want installed. These packages are said to be installed from the CD but I guess they will need updating at some point.

[https://help.ubuntu.com/lts/serverguide/installing-from-cd.html#install-tasks](https://help.ubuntu.com/lts/serverguide/installing-from-cd.html#install-tasks)

Regards.


And that explains that. All the server bits are on the CD. Doesn't explain why when I tried to install the server edition two months ago it stalled at exactly the same place as the mini.iso: can't find internet connection. The machine I was installing on has no ethernet port, only wireless, and that couldn't be set up. So I went for a vanilla xubuntu and killed what I didn't want. Not ideal, but ok. :-k

Out of curiousity, do you get to the details you provide above, grahammechanical, when you boot the server install media with an ethernet cable in?

---

### Post by TheFu on 2015-07-06
I had the same issue with the mini.iso - no network, not install.  No question that it didn't work. Plus the installation program recognized my wifi, but not the USB GigE network adapter ... The mini.iso has a few kernel options - the "install drivers for my system" didn't. After the install, no networking devices were available.
I expected the mini.iso to require an internet connection.

A default ubuntu server with just ssh installed is fairly bloated, but it will install without an internet connection, but if there is any network connection (like on a lab LAN), the install will get stuck.

I don't run non-LTS releases, so if these things have been fixed since 14.04, I dunno.

---

### Post by Higgins909 on 2015-07-06
> **TheFu said:**
> No need to reinstall just to fix samba.  You can **purge** the samba install and re-install it which will start over from scratch - just for samba.

if you don't want to download stuff from the internet during the installation, don't connect the network and/or don't check the "get updates during install" checkbox.  I find it easier to just pull the cable.  Of course, immediately after the install is completed and rebooted, it would be smart to patch the system.  The distribution ISOs are usually a month old, so getting the latest security patches really is important if the system is on any network.
I tried to purge it a few times now its pretty messed up even more now lol, wont start at all.
Errors popup when I try to check service of programs.
I have a thread for this and its looking grim.

I think what your talking about may only be for the desktop version tho.
I remember back around 12.04 server edition, that there wasn't any of this install by net like it is now.
I'm thinking about doing this in a week after building my new gaming computer, as I can use the proxy server. So I don't mess up my squid caches.
Because I set it up to cache some of the files that my games have and some are big games. I've seen 9.2MByte though steam... 
So awesome. my real internet is 3MB my cache drive is slow...

---

### Post by TheFu on 2015-07-06
Definitely NOT desktop installs here.

I stopped doing those after Unity became the default. Switched to 'server' and add a WM on a few "desktops" - this solves the pulse audio, network-manager, unity-lense tracking and general bloat issues with the desktop releases.  I mostly run servers, so NOT having a GUI/menu isn't an issue.

---

### Post by bab1 on 2015-07-07
> **grahammechanical said:**
> The 14.04 (trusty) server ISO images are only 575 MB in size. So, I do not know what ISO you downloaded at 4 GB in size. Even a full Ubuntu desktop ISO image (1.1 GB) is not that big.

If we want to reduce the amount of updates needed after installation then we can install a daily built ISO image. They contain all the updates made to 14.04.2 since it was released. They are still being built for 14.04 (trusty) as work is moving on to release 14.04.3 at the end of August.

[http://cdimage.ubuntu.com/ubuntu-server/trusty/daily/](http://cdimage.ubuntu.com/ubuntu-server/trusty/daily/)

As part of the install process of the server edition we are ask to select which Package Tasks we want installed. These packages are said to be installed from the CD but I guess they will need updating at some point.

[https://help.ubuntu.com/lts/serverguide/installing-from-cd.html#install-tasks](https://help.ubuntu.com/lts/serverguide/installing-from-cd.html#install-tasks)



Regards.
Unfortunately the Samba install via tasksel is flawed.  It is NOT for a file server at all.  The tasksel default assumes a Samba v4 AD-DC (not a file server at all) is being configured.  This will create errors if all you want is a Samba file server.  The OP is trying to install Samba v4 as a file server (standalone).  For that type of install what is more proper is to install via apt-get using ```
sudo apt-get install samba
```...the user will of course need internet access for the install.

---

