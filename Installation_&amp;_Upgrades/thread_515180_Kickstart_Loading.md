---
title: "Kickstart Loading"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by talktechnow on 2007-08-01
Hey, this is my setup, have a server running a tftp server. This allows clients to boot up and load the ubuntu setup. Thats all fine and dandy.

However once loading the Ubuntu Installer, and the kickstart file, which loads Ubuntu files from an FTP Server. 

Now after auto configuring the network, it says it cannot retrieve Packages.gz, the address of the file is /Ubuntu/dists/feisty/restricted/debian-installer/binary-i386/Packages.gz

However on the Ubuntu CD, the folder layout does not include 'debian-installer' folder. 
I have created this folder, and symbolicly linked the binary-i386 folder to the original folder.

If I load the address in Firefox/IE I can find the file and download it.

Here is a portion of /var/log/syslog that shows the error:

> Aug  2 10:32:59 netcfg[6826]: INFO: DHCP hostname: "ubuntu" 
Aug  2 10:32:59 main-menu[5734]: (process:6825): Internet Software Consortium DHCP Client 2.0pl5 
Aug  2 10:32:59 main-menu[5734]: (process:6825): Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium. 
Aug  2 10:32:59 main-menu[5734]: (process:6825): All rights reserved. 
Aug  2 10:32:59 main-menu[5734]: (process:6825):  
Aug  2 10:32:59 main-menu[5734]: (process:6825): Please contribute if you find this software useful. 
Aug  2 10:32:59 main-menu[5734]: (process:6825): For info, please visit [http://www.isc.org/dhcp-contrib.html](http://www.isc.org/dhcp-contrib.html) 
Aug  2 10:32:59 main-menu[5734]: (process:6825):  
Aug  2 10:32:59 main-menu[5734]: (process:6825): Listening on LPF/eth0/00:08:02:5c:7a:90 
Aug  2 10:32:59 main-menu[5734]: (process:6825): Sending on   LPF/eth0/00:08:02:5c:7a:90 
Aug  2 10:32:59 main-menu[5734]: (process:6825): Sending on   Socket/fallback/fallback-net 
Aug  2 10:32:59 main-menu[5734]: (process:6825): DHCPREQUEST on eth0 to 255.255.255.255 port 67 
Aug  2 10:32:59 main-menu[5734]: (process:6825): DHCPACK from 10.0.2.251 
Aug  2 10:32:59 main-menu[5734]: (process:6825): bound to 10.0.2.145 -- renewal in 43200 seconds. 
Aug  2 10:32:59 main-menu[5734]: (process:6825):  
Aug  2 10:32:59 main-menu[5734]: DEBUG: resolver (libc6): package doesn't exist (ignored) 
Aug  2 10:32:59 main-menu[5734]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Aug  2 10:32:59 main-menu[5734]: INFO: Falling back to the package description for console-setup-udeb 
Aug  2 10:32:59 main-menu[5734]: INFO: Falling back to the package description for console-setup-udeb 
Aug  2 10:32:59 main-menu[5734]: INFO: Menu item 'choose-mirror' selected 
Aug  2 10:32:59 anna-install: Queueing udeb apt-mirror-setup for later installation
Aug  2 10:32:59 choose-mirror[6906]: DEBUG: command: cat /proc/sys/net/ipv4/tcp_syn_retries 
Aug  2 10:32:59 choose-mirror[6906]: DEBUG: command: echo 1 > /proc/sys/net/ipv4/tcp_syn_retries 
Aug  2 10:32:59 choose-mirror[6906]: DEBUG: command: wget -q [http://archive.ubuntu.com/ubuntu/dists/feisty/Release](http://archive.ubuntu.com/ubuntu/dists/feisty/Release) -O - | grep ^Suite: | cut -d' ' -f 2 
Aug  2 10:32:59 choose-mirror[6906]: DEBUG: command: echo 5  > /proc/sys/net/ipv4/tcp_syn_retries 
Aug  2 10:32:59 choose-mirror[6906]: DEBUG: command: wget -q [ftp://server-rot/Ubuntu//dists/feisty/Release](ftp://server-rot/Ubuntu//dists/feisty/Release) -O - | grep ^Suite: | cut -d' ' -f 2 
Aug  2 10:32:59 choose-mirror[6906]: DEBUG: command: wget -q [ftp://server-rot/Ubuntu//dists/feisty/Release](ftp://server-rot/Ubuntu//dists/feisty/Release) -O - | grep ^Codename: | cut -d' ' -f 2 
Aug  2 10:32:59 choose-mirror[6906]: INFO: codename set to: feisty 
Aug  2 10:32:59 choose-mirror[6906]: DEBUG: command: wget -q [ftp://server-rot/Ubuntu//dists/feisty/main/binary-i386/Release](ftp://server-rot/Ubuntu//dists/feisty/main/binary-i386/Release) -O - | grep Architecture 
Aug  2 10:32:59 anna-install: Queueing udeb feisty-support for later installation
Aug  2 10:32:59 main-menu[5734]: DEBUG: resolver (libc6): package doesn't exist (ignored) 
Aug  2 10:32:59 main-menu[5734]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Aug  2 10:32:59 main-menu[5734]: INFO: Falling back to the package description for console-setup-udeb 
Aug  2 10:32:59 main-menu[5734]: INFO: Falling back to the package description for console-setup-udeb 
Aug  2 10:32:59 main-menu[5734]: INFO: Menu item 'download-installer' selected 
Aug  2 10:33:00 net-retriever: gpgv: Signature made Sun Apr 15 13:52:01 2007 UTC using DSA key ID FBB75451
Aug  2 10:33:00 net-retriever: gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Aug  2 10:33:00 anna[6958]: wget:  
Aug  2 10:33:00 anna[6958]: RETR: /Ubuntu/dists/feisty/main/debian-installer/binary-i386/Packages.gz: No such file or directory 
Aug  2 10:33:00 anna[6958]:  
Aug  2 10:33:00 anna[6958]: wget:  
Aug  2 10:33:00 anna[6958]: RETR: /Ubuntu/dists/feisty/main/debian-installer/binary-i386/Packages: No such file or directory 
Aug  2 10:33:00 anna[6958]:  
Aug  2 10:33:00 net-retriever: error: restricted/debian-installer/binary-i386/Packages.gz not found in /tmp/net-retriever-6974-Rel

I think the problem is 
> Aug  2 10:33:00 anna[6958]: RETR: /Ubuntu/dists/feisty/main/debian-installer/binary-i386/Packages: No such file or directory  not putting the server address in front of the file name. 

However I need someone else's opinion. Any ideas would be much appreciated.

---

### Post by talktechnow on 2007-08-01
Sorted it, changed the Ubuntu to folder to the alternative CD laoyout. Worked first time.

---

