---
title: "[SOLVED] Connectivity after upgrade"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by ~cyrus~ on 2007-10-22
Greetings,

Upgraded my desktop from 7.04 and had no problem. 

To get Firefox working, I had to disable ipv6 through about:config and I can now browse.

However, cannot log into Pidgin, cannot system update through console or manager, cannot FTP. Disabling ipv6 system wide did not help. I get timeouts.

My desktop is connected with a D-Link usb adapter dwl-g122 with a rt73 driver to a router shared with a laptop, and there's no problem there. Tried the live cd on my laptop, and the same issue there as well.

What could have changed from 7.04 to 7.10 to prevent connectivity from my end for updates, pidgin, ftp, etc.?

Advice appreciated.

---

### Post by ~cyrus~ on 2007-10-23
Have tried the following, but no joy.

1. Disabling ipv6 computer wide. (Have disabled in Firefox which enabled me to access web pages only)

2. Tried prepend domain name servers in /etc/dhcp3. This did not work as well.

Back to square one...cannot login to Pidgin, cannot system update through console or manager, cannot FTP.

Regards,

cyrus

---

### Post by ~cyrus~ on 2007-10-24
Have reverted back to square one. 

The only change after upgrade is disabling ipv6 in Firefox only, through about:config

1. I can login to irc.freenode.com only **after** right I ping it from System Tools. If I don't ping the exact address I am trying to connect to, I get a time out.

2. The same with system upgrades. If I ping the archive that I am trying to connect to, I get a connection immediately after the ping, and can subsequently keep my system upto date. If I don't ping the archives, I get a timeout.

3. I just cannot establish a connection with Pidgin to my msn account.

4. gFTP also only connects **after** I ping ftp.mysite.com. If I don't, I get a timeout

5. I seem to be able to ssh into a server alright.

Appreciate any advice.

Regards,

cyrus

---

### Post by ~cyrus~ on 2007-10-29
Thanks to [this post]("http://ubuntuforums.org/showpost.php?p=3654324&postcount=109"), all the above problems were sorted out.

Obviously my problem was that "DNS resolves everything to 1.0.0.0 intermittently on some ADSL Routers."

:popcorn:

---

