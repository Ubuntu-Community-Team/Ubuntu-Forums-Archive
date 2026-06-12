---
title: "cannot purge blockcontrol.  Messing up automatic updating.  Cannot rid it!"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by ciscoman10 on 2010-11-23
[IMG]http://ubuntuforums.org/images/icons/icon11.gif[/IMG] **Re: **** moblock!** 
I have searched around a bit and am having difficulty purging blockcontrol off my system. I am running Ubuntu 10.04 LTS i686 version. I have been able to remove some of the programs attached to blockcontrol but cannot remove blockcontrol. The synaptics package manager and console root access will not rip out blockcontrol. I want the entire Moblock/Blockcontrol set off the system.
root@computer-desktop:/home/nas# sudo apt-get install -f
Reading package lists... Done
Building dependency tree 
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up blockcontrol (1.6.13-1~lucid) ...
/etc/blockcontrol/blockcontrol.conf: 15: Syntax error: Unterminated quoted string
dpkg: error processing blockcontrol (--configure):
subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
blockcontrol
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@computer-desktop:/home/nas# 
 
then I tried to remove blockcontrol via the synaptic package manager and got the following popup
E: blockcontrol: subprocess installed pre-removal script returned error exit status 2
 
 
please help... I have too much setup on this system to just blow it all out and start again.
 
:wink:

---

### Post by jre on 2010-11-24
Just for the record, I answered here: [http://ubuntuforums.org/showpost.php?p=10153404&postcount=5](http://ubuntuforums.org/showpost.php?p=10153404&postcount=5)

So fix /etc/blockcontrol/blockcontrol.conf or just delete it. It only contains custom configuration.

---

### Post by ciscoman10 on 2010-11-29
thanks JRE.  It now appears to be gone and the synaptic package manager also appears to be satisfied.  You probably already guessed but I am new to Ubuntu, this is my first serious install as I configured a home NAS server.

Again, thanks

---

