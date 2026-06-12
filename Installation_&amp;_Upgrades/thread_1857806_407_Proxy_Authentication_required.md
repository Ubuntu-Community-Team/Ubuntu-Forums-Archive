---
title: "407: Proxy Authentication required"
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by ajaykanth on 2011-10-11
Hi,

I have installled Natty (Ubuntu 11.04) recently.
while trying to do "sudo apt-get update", I am getting the below error:-

Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) natty/main Sources                                               
  407  Proxy Authentication Required
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) natty/restricted Sources
  407  Proxy Authentication Required
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) natty/multiverse Sources
  407  Proxy Authentication Required.
.
.
.
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/natty/partner/source/Sources)  407  Proxy Authentication Required
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/natty/partner/binary-i386/Packages)  407  Proxy Authentication Required
W: Failed to fetch [http://packages.ros.org/ros/ubuntu/dists/natty/main/binary-i386/Packages](http://packages.ros.org/ros/ubuntu/dists/natty/main/binary-i386/Packages)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty/main/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/natty/main/source/Sources)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty/restricted/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/natty/restricted/source/Sources)  407  Proxy Authentication Required
.
.
.

NOTE:
Please note the following settings and observations before giving response. Thanks again.

# my PC is behind a firewall and I have manually configured the proxy and able to access internet now.
# The Proxy has been successfully set at the following locations:-
   1. /etc/apt/apt.conf  
   2. Have set the proxy in "Synaptic Package Manager" correctly.
   3. Have set Proxy (manual) in Firefox > Edit > Preferences > Advanced > Network > settings > "Manual Proxy configuration" >> then...gave the proxy and port details.
   4. By default, if I echo $http_proxy, the following info is being shown:-
       http_proxy = http://<proxyhost>:port

       But, with reference to some forum, I have set a new values as :-
       gksudo gedit /etc/bash.bashrc
       //and I have set the below values
       export http_proxy = [http://username:password@proxyhost:port1](http://username:password@proxyhost:port1)

Kindly go through the available configurations (as done above) and suggest if I am missing some thing ...

---

### Post by ajaykanth on 2011-10-12
Just to update:-
I even tried updating Proxy settings system wide as:-
1. Network Proxy >> Apply System Wide >> Give Authentication Details.

Still, apt-get update is not working completely. 

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty/multiverse/binary-i386/Packages](http://ftp.iitm.ac.in/ubuntu/dists/natty/multiverse/binary-i386/Packages)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty-updates/restricted/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/natty-updates/restricted/source/Sources)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty-updates/main/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/natty-updates/main/source/Sources)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty-updates/multiverse/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/natty-updates/multiverse/source/Sources)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty-updates/universe/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/natty-updates/universe/source/Sources)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty-updates/main/binary-i386/Packages](http://ftp.iitm.ac.in/ubuntu/dists/natty-updates/main/binary-i386/Packages)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty-updates/restricted/binary-i386/Packages](http://ftp.iitm.ac.in/ubuntu/dists/natty-updates/restricted/binary-i386/Packages)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty-updates/universe/binary-i386/Packages](http://ftp.iitm.ac.in/ubuntu/dists/natty-updates/universe/binary-i386/Packages)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages](http://ftp.iitm.ac.in/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty-security/restricted/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/natty-security/restricted/source/Sources)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty-security/main/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/natty-security/main/source/Sources)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty-security/multiverse/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/natty-security/multiverse/source/Sources)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty-security/universe/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/natty-security/universe/source/Sources)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty-security/main/binary-i386/Packages](http://ftp.iitm.ac.in/ubuntu/dists/natty-security/main/binary-i386/Packages)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty-security/restricted/binary-i386/Packages](http://ftp.iitm.ac.in/ubuntu/dists/natty-security/restricted/binary-i386/Packages)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty-security/universe/binary-i386/Packages](http://ftp.iitm.ac.in/ubuntu/dists/natty-security/universe/binary-i386/Packages)  407  Proxy Authentication Required
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/natty-security/multiverse/binary-i386/Packages](http://ftp.iitm.ac.in/ubuntu/dists/natty-security/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

---

