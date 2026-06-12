---
title: "Collectd upgrade failing"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by richardfarrar on 2010-05-30
Hi,

I've just upgraded from Ubuntu 9.10 Server to 10.4 and am having trouble restarting/upgrading **collectd**, and am getting the following errors. Any help would be greatly appreciated: 

 **Upgrading all packages with command apt-get -y -f upgrade ..**
 
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up collectd-core (4.8.2-1) ...
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Starting statistics collection and monitoring daemon: collectd/etc/init.d/collectd: line 67:  7269 Segmentation fault      $DAEMON -t -C "$CONFIGFILE"
invoke-rc.d: initscript collectd, action "start" failed.
dpkg: error processing collectd-core (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of collectd:
 collectd depends on collectd-core; however:
  Package collectd-core is not configured yet.
dpkg: error processing collectd (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 collectd-core
 collectd
E: Sub-process /usr/bin/dpkg returned an error code (1)


Regards,

Richard

---

### Post by richardfarrar on 2010-05-31
I seem to have fixed it, but more by a bodge by commenting out the contents of **check_config() **in **/etc/init.d/collectd** and forcing it to return 0.

I've now got collectd working of a fashion, but can't seem to get it to recognise MySQL or Apache anymore, yet all other things seem to be working. :(

I can't remember what the original contents of check_config() should have been to try reinstating to see if it works now I've got the packages loaded.

Anyone got any clues?

Richard

---

