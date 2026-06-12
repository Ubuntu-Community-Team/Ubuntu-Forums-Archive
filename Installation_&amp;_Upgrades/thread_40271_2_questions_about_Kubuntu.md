---
title: "2 questions about Kubuntu"
date: 2005-06-08
forum: Installation &amp; Upgrades
---

### Post by Uta on 2005-06-08
First let me say how much I like Kubuntu and the Ubuntu OS. I have successfully stripped out a Dell C800 Latitude laptop and made it a Kubuntu box. The install went fine and I have a solid Internet connect, and video and sound works great. My 2 issues are printing and CD burning. The CD Kreator wants me to install 'the cdrdao package' where would I find this? The printer issue is a little more complicated. I have a Linksys Wireless-G print server which when I open up Print manager I get the error message 'IPP request failed for an unknown reason'. Additionally it is set to use CUPS and it displays, Server: 192.168.0.100:631 which is the IP address of my print server (192.168.0.100) but when I go to print a document it's not listed and nothing gets printed. Any help would be greatly appreciated.  The other computers on the network are all running Mac OS X and printer sharing is turned on... Thanks!

---

### Post by mingus on 2005-06-08
It's a kcontrol module.  See:

[http://www.ubuntulinux.org/wiki/HowToInstallK3b](http://www.ubuntulinux.org/wiki/HowToInstallK3b)
[http://www.ubuntulinux.org/wiki/K3BHowto](http://www.ubuntulinux.org/wiki/K3BHowto)

(wiki search useful tool)

Re the printer:
Not alot of help to offer.  IPP is a protocol, among several that the devices can possibly use to communicate with CUPS.  To see more of the CUPS configuration, in your browser try the IP of your computer followed by :631 (the CUPS port).  I have a similar setup to yours, but use TCP instead.  I'd also check out Linksys support for config hints.

---

### Post by Uta on 2005-06-08
Thanks for the info concerning the cd burning missing file, I have edited the sources.list and was able to install the missing file...everything works now... the printing issue is still with me. I had previously read the Linksys info and it seemed a little 'complicated and vague at the same time' if I don't use CUPS how do I set it up to use TCP/IP? Again thanks.

---

### Post by mingus on 2005-06-08
Like I said, not a whole lot to offer.  IPP is a printing protocol, while TCP is a device network protocol.  My setup is similar to yours, except that the printer has its own print server rather than the router.  So the IPP socket points to CUPS like yours, the device socket to the printer itself (socket://192.168.0.101:9100 - where 101 is the printer and 9100 is the default printer port).   Take a look at KDE Menu - Utilities - Printing - Print Manager (not sure if this is the menu in Kubuntu, working from memory my SuSE KDE).   You may also need to do something in the print server config.  Like I said, don't know much on this one.

---

