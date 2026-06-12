---
title: "Network install problems - januty"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by stimmins on 2009-11-16
Hi,

I'm having problems installing Ubuntu 9.04 over the network into Sun's Virtual box.

I've tried this on 2 VMs on separate machines and on the same with the same result.

Virtual Box 3.0.8 and 3.0.10
Ubuntu 9.04
Both presseed and non preseed installations

First box has a standard 9.04 desktop with dnsmasq for DHCP/tftp, and copies of the relevant desktop CD available as /ubuntu/ on the local web server. it is currently runing on Sun Virtual Box on Windows 7 (I have successfully installed Ubuntu 8.04, 9.04 and 9.10 onto this install before using locally mounts CDs).

If I install off of a local CD it is fine, if I choose a standard Ubuntu mirror it is fine, but if I try to install from a local network copy of ubuntu, it fails.

I can see the system (The one I'm trying to do a network install on) pull the preseed configuration file (when using a preseeded install) and I can see it pull the following files (succesfully) from the webserver on the first box:

/ubuntu/dists/jaunty/Release
/ubuntu/dists/jaunty/Release.gpg

But on the box doing the install I get an error after it pulls these first 2 files from the web server:

"The installer failed to download a file from the mirror ... <lots more text>"

With a selection to Retry, Change mirror or Cancel. If I chose a standard ubuntu mirror it works fine.

In /var/log/syslog I get the following errors (the pid # component of the file name is different each time of course):

Nov 16 13:16:44 anna[2764]: cat: can't open /tmp/net-retriever-2772-deduplicate/*': No such file or directory

All other log entries look fine. Looking in /tmp I see the following files:

net-retriever-2782-Release
net-retriever-2782-Release.gpg

The number in syslog is *always* 10 less than the number in the filenames in /tmp. These are the exact same files mentioned above as being served by the web server (/ubuntu/dists/jaunty/Release and /ubuntu/dists/jaunty/Release.gpg). I have verified the files are correct using md5 sums.

I have tried this using the standard netboot.tar.gz (i.e. with no modifications by myself) and just gone through the menus selecting all the settings manually and I get the same results (i.e. it works with a remote mirror, but not a local one).

I have found people with similar errors here:

[http://ubuntuforums.org/showthread.php?t=1309279](http://ubuntuforums.org/showthread.php?t=1309279)
[http://www.mail-archive.com/ubuntu-installer@lists.ubuntu.com/msg00061.html](http://www.mail-archive.com/ubuntu-installer@lists.ubuntu.com/msg00061.html)

Is this a problem with Virtual Box? Am I missing something or doing something wrong?

I have read a lot of pages about these sort of installs and I can't seem to find anything about this problem other than the 2 URLs above (which have no replies).

Regards,

Sean Timmins

---

### Post by BamsTia on 2010-02-05
i have same problem like this, but it's not have solution yet... i don't know why it still don't be solve... or i'm not get it yet...?????

---

