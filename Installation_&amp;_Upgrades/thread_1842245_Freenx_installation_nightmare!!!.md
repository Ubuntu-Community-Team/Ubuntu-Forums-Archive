---
title: "Freenx installation nightmare!!!"
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by diamond_D on 2011-09-11
I recently took on the project of installing Freenx on Natty as per the instructions on Wilson's blog
[http://notepad2.blogspot.com/2011/05/install-freenx-server-on-ubuntu-1004.html](http://notepad2.blogspot.com/2011/05/install-freenx-server-on-ubuntu-1004.html)

I could never get connected remotely from my Windows 7 box with the nomachine client as I kept getting the dreaded  error:

> NX> 203 NXSSH running with pid: 2328
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.20 on port: 6019
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.I tried reinstalling, uninstalling modifying the ssh and the app config files. I verified that the generated keys were the nomachine default.....still no luck! And 'yes' my ssh connection is working. I can putty in over port 6019.

I decided to do some cleanup and delete some of the 'stay behind' files so I purged the following.

/var/lib/nxserver
/usr/bin/nxserver

Now I can no longer reinstall.

I follow the instructions from Wilson's blog again but when I run the nxsetup installer I get and error.

> delslige@ubuntu-P5K:/usr/lib/nx$ sudo ./nxsetup --install
[sudo] password for delslige:
------> It is recommended that you use the NoMachine key for
        easier setup. If you answer "y", FreeNX creates a custom
        KeyPair and expects you to setup your clients manually.
        "N" is default and uses the NoMachine key for installation.

 Do you want to use your own custom KeyPair? [y/N]
**./nxsetup: line 140: .: filename argument required**
[B].: usage: . filename [arguments]
Setting up  ...mkdir: missing operand[/B]
Try `mkdir --help' for more information.I've spent the better part of 2 days on this. Any suggestions?

---

### Post by diamond_D on 2011-09-11
Maybe a hint. I tried to uninstall freenx from the software centre and I get a message that the "package system is broken."

> freenx-session-launcher:depends:nxnode but it is not installedI'm not a linux guru so if somebody could give me a suggestion on how to fix so I can run the installer again it would be greatly appreciated.

---

### Post by diamond_D on 2011-09-11
After a reboot I was able to repair the reinstall the freenx package 0.7.3.git110520.3884279-0ubuntu1ppa4

Now back to the reinstall. After all the pain of going through this time I went looking for **/etc/nxserver/node.conf**   - This file does not exist.

I only have an empty directory node.conf.d

What exactly am I missing?

---

