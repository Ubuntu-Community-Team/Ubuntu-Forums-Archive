---
title: "New ubuntu installation: Software center &amp; gufw installation problem"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by harish.lanjewar on 2011-03-19
1) I'hv just installed Ubuntu 10.10 from ubuntu site. While updating through update manager or while getting any software installed by software center i get following message. 

"Failed to download repository information

Check your Internet connection."

i think it is not able get through proxy identification, though i'hv entered my proxy username & password and done all the proxy server settings.

2) I'm also not able to install gufw firewall. After using following command 
"sudo apt-get install gufw"

i get following response.

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gufw"

I'hv Community maintained open-source software (universe) repository checked in my software sources.

while doing it through software center again gives me the message as:

"Failed to download repository information

Check your Internet connection."

[IMG]file:///tmp/moz-screenshot.png[/IMG]while installing it from gufw community site, the software center terms the gufw installation file as "dependency is not satisfiable" and does not offer any installation option.

3) While reloading or updating any packages i get following message:

"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

---

### Post by harish.lanjewar on 2011-03-20
During installation of softwares from Software centre i'm getting following messages in Details box:

"  W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  Error reading from server - read (104: Connection reset by peer)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  Error reading from server - read (104: Connection reset by peer)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required
, E:Some index files failed to download, they have been ignored, or old ones used instead.  "


Though i'hv entered proxy settings applied it system-wide...How to go about it?

---

### Post by harish.lanjewar on 2011-03-21
I'hv found solution for my Synaptic Package Manager (SPM)  by doing proxy settings in SPM, i'hv gufw installed and everything. Only thing is my other applications like Update Manager and Software Center doesnt accept proxy settings. I hv edited my  /etc/bash.bashrc to add following lines: 

export  http_proxy=http://username:password@proxyserver.com:3095/
export  ftp_proxy=http://username:password@proxyserver.com:3095/

or else did this too:

Acquire::http::proxy "http://[user]:[password]@[proxy](:[port])/"

but to no avail...

Please help me with this...

Also how to enable nvidia driver...I'hv it installed still system is not able to enable it....

What are the ports you need to manage for safeguarding firewall through gufw and what are other rules to improve unwanted attacks???

---

