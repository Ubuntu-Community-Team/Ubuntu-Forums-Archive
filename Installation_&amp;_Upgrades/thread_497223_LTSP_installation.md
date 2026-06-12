---
title: "LTSP installation"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by c2y on 2007-07-10
I try to install LTSP and I follow these instructions from  [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

    This page aims to describe the quickest way to get a ltsp server running on an existing ubuntu or kubuntu (xubuntu comes with a ltsp option in the installer, edubuntu even sets up ltsp in its default install) desktop system.

You need to set up one static interface where you will attach the thin clients, install two packages and run one command.

Configure your spare interface for the thin clients to have the IP 192.168.0.1, then follow the instructions below.

**sudo apt-get install ltsp-server-standalone openssh-server**

Now create your Thin Client environment on the server with.

**sudo ltsp-build-client**


after the comand "sudo ltsp-build-client", i got this error.


lsaguilos@trialserver:/opt/ltsp$ sudo ltsp-build-client
NOTE: adding default dist and components to security mirror:
[http://security.ubuntu.com//ubuntu](http://security.ubuntu.com//ubuntu) feisty main restricted
I: Retrieving Release
E: Failed getting release file [http://archive.ubuntu.com/ubuntu/dists/feisty/Release](http://archive.ubuntu.com/ubuntu/dists/feisty/Release)
error: LTSP client installation ended abnormally


please help.

---

### Post by phidia on 2007-07-10
I don't know anything about the ltsp package but that error message i.e > E: Failed getting release file [http://archive.ubuntu.com/ubuntu/dists/feisty/Release](http://archive.ubuntu.com/ubuntu/dists/feisty/Release)
error: LTSP client installation ended abnormally
 could be because apt needs updating? Try "sudo apt-get update" and then the build command again.
I could be wrong though-just a guess.

---

### Post by c2y on 2007-07-10
i try "sudo apt-get update" and do the build command but still i got the same error..


help please...

---

### Post by DaveEaseman on 2007-07-31
I also had this problem; are you running behind a proxy?

Although I had defined a proxy on the ubuntu install, and apt-get was working OK, I remembered something about proxy settings for apt-get. This error seemed to be a similar proxy problem so I hunted about and found this:-

[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

At command line I entered:-

export http_proxy=http://username:password@proxyserver.net:port/

(check the article; you don't need to specify the username:password@ part if your proxy is not configured with a username and password)

e.g.

export http_proxy=http://sample.com:8080/

sudo ltsp-build-client then worked OK.

---

### Post by mredmond on 2007-10-26
I was able to use ltsp-build-client  with no problem on feisty 7.04, but I had this hang on gutsy 7.10. Using the export fixed the problem...so thanks very much for that. 

Is this a bug that should be fixed in gutsy? It seems to recur from version to version, so it must be something that requires an active, custom intervention to correct. Probably something that is forgotten from one release to the next. It is a real hassle..first install required that I get on a net without a firewall...dangerous..

Mike R.

---

> **DaveEaseman said:**
> I also had this problem; are you running behind a proxy?

Although I had defined a proxy on the ubuntu install, and apt-get was working OK, I remembered something about proxy settings for apt-get. This error seemed to be a similar proxy problem so I hunted about and found this:-

[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

At command line I entered:-

export http_proxy=http://username:password@proxyserver.net:port/

(check the article; you don't need to specify the username:password@ part if your proxy is not configured with a username and password)

e.g.

export http_proxy=http://sample.com:8080/

sudo ltsp-build-client then worked OK.

---

### Post by mredmond on 2007-10-26
The "permanent" solution to this is to add two lines to  the end of /etc/bash.bashrc:

export http_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.netport/

On subsequent sessions, your proxys will work with apt-get. I was surprised that the "global" proxy settings did not seem to apply to some terminal session operations, like apt-get.

Mike
---
> **DaveEaseman said:**
> I also had this problem; are you running behind a proxy?

Although I had defined a proxy on the ubuntu install, and apt-get was working OK, I remembered something about proxy settings for apt-get. This error seemed to be a similar proxy problem so I hunted about and found this:-

[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

At command line I entered:-

export http_proxy=http://username:password@proxyserver.net:port/

(check the article; you don't need to specify the username:password@ part if your proxy is not configured with a username and password)

e.g.

export http_proxy=http://sample.com:8080/

sudo ltsp-build-client then worked OK.

---

### Post by mrprowse on 2008-03-13
Nice work! This put an end to hours of frustration! THANK YOU! (I don't know how to give your "Thanks" count a +1, or I would have!)

:-j

---

