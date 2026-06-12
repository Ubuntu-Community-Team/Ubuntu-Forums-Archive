---
title: "xinetd won't start on boot"
date: 2017-03-19
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2017-03-19
Xinetd does not start on boot. I can start it running the script in /etc/init.d
When I run dpkg -- configure xinetd this is what I get:

> root@hamlet:/etc/init.d# dpkg --configure xinetd
Setting up xinetd (1:2.3.15-6) ...
insserv: warning: script 'K02alamin-server' missing LSB tags and overrides
insserv: warning: script 'K02apache-ssl' missing LSB tags and overrides
insserv: warning: script 'K02apache' missing LSB tags and overrides
insserv: warning: script 'K02cyrus21' missing LSB tags and overrides
insserv: warning: script 'K02hotkey-setup' missing LSB tags and overrides
insserv: warning: script 'S03powernowd.early' missing LSB tags and overrides
insserv: warning: script 'S07stop-readahead' missing LSB tags and overrides
insserv: warning: script 'S03xserver-xorg-input-wacom' missing LSB tags and overrides
insserv: warning: script 'S08readahead' missing LSB tags and overrides
insserv: warning: script 'S05ifrename' missing LSB tags and overrides
insserv: warning: script 'S05readahead-desktop' missing LSB tags and overrides
insserv: script xinetd: service inetd already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package xinetd (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 xinetd

This seems to indicate that xinetd is already configured.

I've purged inetd and reinstalled it but haven't gotten it work quite right yet.

---

### Post by rsteinmetz70112 on 2017-03-19
I solved it but still don't know what happened. I simply rename /etc/init.d/xinetd and then ran dpkg --configure xinetd then changed the name back. I'm not sure I even had to run dpkg again. It now works. I'm guessing the configuration database got confused.

As for the script warnings. those were the result of either and improper install and a purge and reinstall solved those or they we left over scripts the upgrade did not remove or replace with the correct ones.

---

