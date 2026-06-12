---
title: "GUFW looking weird &amp; Gdebi"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by slumbergod on 2011-10-14
Hi all,

just installed Xubuntu 11.10. 

Just curious if anyone else has experienced problems with GUFW or Gdebi.

Both GUFW and Gdebi look like completely unlike they usually do. Is there some library I need to install?

And Gdebi keeps complaining about broken repos or something yet # apt-get install -f does not fix it. Any ideas?

---

### Post by slumbergod on 2011-10-14
There's something really weird going on with synaptic and its retrieval of dependencies.

First thing I do when I perform a clean install of a new xubuntu version is to get rid of software center and put synaptic and gdebi back on.

But dependencies are not be satisfied. For example, gigolo was not letting me mount a samba share. Why? Because gvfs-backends is not listed as a dependency yet it is needed for gigolo to work

Haven't had this many issues for many ubuntu releases. Getting close to migrating to debian.

---

### Post by marquinos on 2011-10-14
Hi!
You have the dependencies here:
[http://packages.ubuntu.com/oneiric/gufw](http://packages.ubuntu.com/oneiric/gufw)
Did you ask the system about packages not downloaded? If yes, I think you must change the repository sources to another repository, today the servers must be saturated :P
Best regards!

---

### Post by slumbergod on 2011-10-14
Hmm I am not sure what is going on. 
Other applications also see to have really retro looking windows.
I've attached another for file-roller. It has never looked like this.
The pop up settings window for synaptic is another that looks like something from 1990.

---

