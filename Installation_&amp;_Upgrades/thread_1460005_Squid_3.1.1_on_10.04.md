---
title: "Squid 3.1.1 on 10.04"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by wightman.p on 2010-04-22
As Squid 3.1 is not part of 10.04 Beta 2 (64), I'm assuming it's not going to make it into the LTS release.

I have found a pretty good procedure at [http://www.sput.nl/software/squid31-lenny.html]("http://www.sput.nl/software/squid31-lenny.html")

There is a typo in the prerequisites - libxml2-de should read libxml2-dev

I did a fresh install of Ubuntu 10.04 beta 2 (64) this morning into a VM, followed the instructions and all went well.  I did install the build_essential package before I started the procedure, but otherwise, all cool, including startup / shutdown / restart scripts for squid3.

I'm busy with a server build that will eventually include the following:

Ubuntu 10.04 (64) LTS
OCSInventory
GLPI
Nagios3
Munin
Squid3.1.1
Firewall
Postfix (local only!)
VirtualBox hosting a Windows 2008 R2 domain controller
Samba (AD authentication to the 2008 box)
Fileshares for the windoze users (the 2008 box will only do DC and WSUS roles)
Drupal6 for Intranet
OpenVPN Client / Server
PPtP client
MySAR (Squid report analysis)
CUPS
Webmin . . .

I'd almost given up on the Squid 3.1.1 / Ubuntu integration, tried FreeBSD 8.0, but that road leads to madness, especially if you want to run virtualisation!

26 April 2010 - Added attachment with beginnings of procedure.  Hope this helps someone.  Most of the squid stuff comes from the link as noted above.  The rest comes from all over the Internet, with a little bit of my own mods thrown in.

---

### Post by dcasteel on 2010-06-16
Thanks for your documentation. I found it helpful and it gave me some confidence that I was working in the right direction. I am new Ubuntu and Linux in general. I am a Windows server admin by trade. I am trying just to install Webmin on LTS 10.04. I have libmd5-perl_2.03-1_all.deb (the lastest I found on the ftp site you pointed out) and webmin_1.510-2_all.deb. Both seem to install correctly. I can not find libnet-ssleay-perl anywhere. I receive an error that reads:
 
*Package libnet-ssleay-perl is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source.*
*E: Package libnet-ssleay-perl has no installation candidate*
 
Any help or direction in finding the libnet file would be greatly appreciated. It seems to be the last step in getting Webmin to go.

---

### Post by dcasteel on 2010-06-17
Thanks again. I re-read your documentation and found I had missed a step in the install of the OS. I reinstalled and Webmin is running great. Thanks for all your help.

---

### Post by wightman.p on 2010-09-04
I'm glad I was able to put something back into the community!!  Done my fair share of taking ;)  I'll soon be revising the document, there are quite a few changes I'd like to incorporate!

---

### Post by leetkrew on 2011-05-12
i successfully installed squid 3.1.1 but it seems that i am having a hard time accessing websites hosted on our lan. I searched for possible solution and it seems that it has been fixed on version 3.1.4 so I installed 3.1.6. I followed your tutorial and it works... thanks

---

