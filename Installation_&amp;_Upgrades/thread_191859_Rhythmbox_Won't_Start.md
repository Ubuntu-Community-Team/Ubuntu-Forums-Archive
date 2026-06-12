---
title: "Rhythmbox Won't Start"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by dr3wster on 2006-06-08
Hello everyone.  I just upgraded to dapper and now my rhythmbox won't start.  I uninstalled/reinstalled it using synaptic, and installed gstreamer0.10-plugins-ugly like synaptic recommended. However, when I click to run rhythmbox, it says it's loading but it never opens.  Running it in the terminal yields the following: 
"
rhythmbox: error while loading shared libraries: libtotem-plparser.so.0: cannot open shared object file: No such file or directory
"
I checked synaptic and the libtotem-plparser0 package is no longer available.  I've seen that other people can use rhythmbox, why can't I?  Any help would be greatly appreciated.  Thanks!

---

### Post by Ivan Matveich on 2006-06-08
You sure you're fully upgraded? Run:

sudo apt-get update
sudo apt-get dist-upgrade

If that does not work, use synaptic to remove rhythmbox and then reinstall it...

---

