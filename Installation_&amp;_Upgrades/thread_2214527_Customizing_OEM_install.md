---
title: "Customizing OEM install"
date: 2014-04-01
forum: Installation &amp; Upgrades
---

### Post by Kelly_Crabb on 2014-04-01
Hi,

I've been looking for several hours, I hope my googleFu hasn't failed me too bad this time. If it did, I do apologise.

I've been trying to complete the OEM installation of 12.04LTS (it has to be this version for my company). The OEM goes ok, however, any settings I make aren't stored. 
aka :
I have to create the config files for 2 pieces of software and set the time to 24hr, add Launchers for those 2 pieces of software. I've written a lil script to complete this, but alas. 
I've tried to just drop the file creation (of the dot files) in init.d with an executable sh script and using the variable $USER to well - create the files in the users homedir. But this doesn't run. (This was a tip coming from this forum, though I've lost the link.) 

here's my assignment:
- Create a 'base' image for 7 types of laptops (in total about 200 machines) so end-users can pop in the cd, bootup and do the install easily. So I figured I'd use the OEM install option, but I really need to preconfigure our VPN client and VMWare's View Client. For that, I need to get those dot files in the end-users homedir. 

Of course when that is completed, we're in a new zone - creating bootable CD's from that one correct OEM install. I was going to go for CloneZilla, since Remastersys doesn't seem to be active. I've also tried UCK, with which I had the same issue (dot files). Though with UCK I could get a perfectly working iso (for the CD/DVD or USB).

---

### Post by sudodus on 2014-04-03
Welcome to the Ubuntu Forums :-)

I think OEM is a good option for you. Maybe you can let the end user install those dot files themselves. You could append aliases to /etc/bash.bashrc, so that they will be available for the end users, when they start a terminal window. Or must it be fully automatic?

Clonezilla is a good alternative if the target drives are at least as big as the source drive. Avoid proprietary drivers to keep the 'master system' portable.

---

