---
title: "[SOLVED] update problem, repository connection failures"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by fethio on 2007-08-14
Switched from XP to kubuntu recently. I used to use Debian when I was a student in the States many years ago. 

I'm having a problem with my repository connection. First I noticed it using adept, the kubuntu package manager, and I thought it was the problem, so I decided to use apt-get instead. But, when I used apt-get install I had a similar problem. Here's the output of apt-get when I run the command:

fethi@desktop-A709:/$sudo apt-get install synaptic
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  docbook-xml libvte-common libvte9 scrollkeeper sgml-data
Suggested packages:
  docbook docbook-doc docbook-dsssl docbook-xsl perlsgml doc-html-w3 opensp libxml2-utils dwww
Recommended packages:
  gksu deborphan libgnome2-perl
The following NEW packages will be installed:
  docbook-xml libvte-common libvte9 scrollkeeper sgml-data synaptic
0 upgraded, 6 newly installed, 0 to remove and 106 not upgraded.
3 not fully installed or removed.
Need to get 2973kB of archives.
After unpacking 16.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main sgml-data 2.0.3 [279kB]
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main docbook-xml 4.4-5
  Bad header line [IP: 91.189.89.8 80]
Get:2 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main libvte-common 1:0.16.1-0ubuntu1 [122kB]
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main libvte-common 1:0.16.1-0ubuntu1
  Error reading from server. Remote end closed connection [IP: 91.189.89.6 80]
Get:3 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main libvte9 1:0.16.1-0ubuntu1 [736kB]
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main libvte9 1:0.16.1-0ubuntu1
  Error reading from server. Remote end closed connection [IP: 91.189.89.6 80]
Get:4 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main scrollkeeper 0.3.14-11ubuntu7 [187kB]
Get:5 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main synaptic 0.57.11.1ubuntu14 [1310kB]
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main synaptic 0.57.11.1ubuntu14
  Error reading from server. Remote end closed connection [IP: 91.189.89.6 80]
Fetched 466kB in 4m9s (1869B/s)
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/pool/main/s/sgml-data/sgml-data_2.0.3_all.deb](http://tr.archive.ubuntu.com/ubuntu/pool/main/s/sgml-data/sgml-data_2.0.3_all.deb)  MD5Sum mismatch
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/pool/main/d/docbook-xml/docbook-xml_4.4-5_all.deb](http://tr.archive.ubuntu.com/ubuntu/pool/main/d/docbook-xml/docbook-xml_4.4-5_all.deb)  Bad header line [IP: 91.189.           89.8 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte-common_0.16.1-0ubuntu1_all.deb](http://tr.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte-common_0.16.1-0ubuntu1_all.deb)  Error reading from serve           r. Remote end closed connection [IP: 91.189.89.6 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte9_0.16.1-0ubuntu1_i386.deb](http://tr.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte9_0.16.1-0ubuntu1_i386.deb)  Error reading from server. Re           mote end closed connection [IP: 91.189.89.6 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/pool/main/s/synaptic/synaptic_0.57.11.1ubuntu14_i386.deb](http://tr.archive.ubuntu.com/ubuntu/pool/main/s/synaptic/synaptic_0.57.11.1ubuntu14_i386.deb)  Error reading from se           rver. Remote end closed connection [IP: 91.189.89.6 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ll synaptic


I've looked at the following posts which report similar problems due to proxy configurations, but found out that in my case, I have no proxies set, and I connect to the internet directly, so their solution didn't work for me..

[http://ubuntuforums.org/showthread.php?t=266590](http://ubuntuforums.org/showthread.php?t=266590)   Connection Fails to Repositories

[http://ubuntuforums.org/showthread.php?t=257988&page=2](http://ubuntuforums.org/showthread.php?t=257988&page=2)   Connection Fails to Repositories

[http://thread.gmane.org/gmane.linux.ubuntu.user/76867/focus=80212](http://thread.gmane.org/gmane.linux.ubuntu.user/76867/focus=80212)  Synaptec connection problem


Could anyone help me with this please?

fethi

---

