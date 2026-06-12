---
title: "Error with hylafax during upgrade, now interfering with application installation"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by titania177 on 2010-04-30
I just upgraded through the Upgrade Manager to Lucid, and at the end of the installation of the upgrade I got an error message about "hylafax" and after I agree to report this bug, the upgrade installation didn't finish, there was no "cleaning up" and no restart. When i restarted, everything seemed to be working fine, but now whenever I try and install a new application through Synaptic, I get an error related to hylafax. The new app installs, though, and seems to be working. The latest error was:

"E: hylafax-client: subprocess installed post-installation script returned error exit status 1
E: hylafax-server: dependency problems - leaving unconfigured
"

Do I need to do something about this? What is hylafax? 

I am using a Dell M1330. Not sure what other info you might need. 

Thanks!

---

### Post by nolo on 2010-05-24
Hylafax is a fax program allowing incoming and outgoing faxes via a faxmodem.  If you don't use it, you can remove it either with synaptic or apt-get.  You will need to uninstall the client and the server.  If you wish to use Hylafax and have the proper drivers for your faxmodem, I suggest reinstalling with apt-get install.

Hope this reply hasn't come too late to do you any good.

Nolo

---

