---
title: "Can't find Trac install package"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by steenbras on 2007-11-02
Hi - I'm running Gutsy on a VMWARE guest, hosted on a Win 2003 Server box. I can't install the Trac application doing a sudo apt-get install trac - result is "E: Couldn't find package trac"

The sources.list is as per original distribution, and I have successfully installed other packages (subversion, webdav, etc). Can anyone help please?

---

### Post by arkara on 2007-11-02
open up a terminal and type: sudo synaptic
then click on the search button and on the search dialog type trac or whatever program you  want to install.
synaptic tool will find many packages. from there install whatever you need.
maybe you can't find it because it's not on the repositories.

---

### Post by steenbras on 2007-11-02
Thanks for the reply, but as this is a server installation, there is no UI available to me. All I have is a command shell.

---

### Post by steenbras on 2007-11-02
SOLVED - After speaking to a network admin here, the issue was the nameserver(s) in /etc/resolv.conf

Modified these to what he told me and it all works fine now!

---

### Post by arkara on 2007-11-02
glad i gave a try..

---

