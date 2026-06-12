---
title: "Trouble Installing Tor on 6.10 Edgy"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by Geomas on 2006-11-02
After upgrading from Dapper to Edgy, I was no longer able to run Tor. So I uninstalled it and tried re-installing it. However, I find I am unable to do so. Here is what the terminal reports:

> geomas@geomas-desktop:~$ sudo apt-get install tor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mixmaster mixminion anon-proxy
Recommended packages:
  socat
The following NEW packages will be installed
  tor
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/782kB of archives.
After unpacking 1593kB of additional disk space will be used.
Selecting previously deselected package tor.
(Reading database ... 128514 files and directories currently installed.)
Unpacking tor (from .../tor_0.1.1.23-1_i386.deb) ...
Setting up tor (0.1.1.23-1) ...
debian-tor uid check: ok
debian-tor homedir check: ok
Raising maximum number of filedescriptors (ulimit -n) to 8192.
Starting tor daemon: tor...
Nov 02 16:56:06.106 [notice] Tor v0.1.1.23. This is experimental software. Do not rely on it for strong anonymity.
Nov 02 16:56:06.109 [notice] Initialized libevent version 1.1a using method epoll. Good.
Nov 02 16:56:06.117 [warn] /var/lib/tor is not owned by this user (debian-tor, 116) but by root (0). Perhaps you are running Tor as the wrong user?
Nov 02 16:56:06.117 [warn] Failed to parse/validate config: Couldn't access/create private data directory "/var/lib/tor"
Nov 02 16:56:06.117 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.
invoke-rc.d: initscript tor, action "start" failed.
dpkg: error processing tor (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tor
E: Sub-process /usr/bin/dpkg returned an error code (1)
geomas@geomas-desktop:~$ 


I am rather new to Linux and am having trouble making head or tail of this. Any insight into what the problem might be, and how to go about resolving it?

---

### Post by j-strap2 on 2006-11-04
Firstly, use the latest Tor ubuntu packages from the Tor people themselves. Instructions to amend your repository sources list to do this are on their page here:

[http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian](http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian)

I had problems with the Tor Edgy packages, so to get it to work I used the Breezy packages even though I am running Edgy. (That is, I entered 'breezy' for the distribution.)

---

### Post by lo_mein_dreams on 2006-11-05
I tried what you said j-strap2, but I still get the same error as Geomas. I am sure that my modification to sources.list worked, but it just won't install itself correctly. I also tried installing with it set to edgy, and that did not work.

I made a thread about this as well (before I saw this one) [http://ubuntuforums.org/showthread.php?t=293620](http://ubuntuforums.org/showthread.php?t=293620) maybe someone will answer it here as well.

---

### Post by tabbe on 2006-11-07
I installerd Tor and Privoxy using Synaptic.
Then I followed this:
> Once you've installed Privoxy (either from package or from source), you will need to configure Privoxy to use Tor. Open Privoxy's "config" file (look in /etc/privoxy/ or /usr/local/etc/) and add the line 
*forward-socks4a / localhost:9050 .*
to the top of the config file. Don't forget to add the dot at the end. 

Privoxy keeps a log file of everything passed through it. In order to stop this you will need to comment out three lines by inserting a # before the line. The three lines are:
*logfile logfile*
and the line 
*jarfile jarfile*
and (on some systems) the line 
*debug 1 # show each GET/POST/CONNECT request*


You'll need to restart Privoxy for the changes to take effect.



And it worked great :)

---

### Post by j-strap2 on 2006-11-07
lo_mein_dreams said on another thread that he/she fixed the problem.

There are so many Tor threads here, it gets confusing. Be best if we could have a single Tor thread for problems.

---

### Post by Geomas on 2006-11-13
Thanks to all who replied! I ultimately succeeded in getting Tor working again using essentially the same technique that lo_mein_dreams mentions in the thread he/she referenced. First, I changed the owner of /var/lib/tor to debian-tor:

sudo chown debian-tor /var/lib/tor

Next, I re-installed Tor (using the repository provided by the Tor developers, which I had been using all along):

sudo apt-get install tor

---

