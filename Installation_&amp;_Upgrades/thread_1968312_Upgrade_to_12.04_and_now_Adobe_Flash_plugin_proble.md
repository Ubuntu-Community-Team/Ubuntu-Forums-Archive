---
title: "Upgrade to 12.04 and now Adobe Flash plugin problem"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by JohnBK on 2012-04-28
After upgrade, Adobe Flash in Firefox would not work. I tried uninstalling and re-installing Firefox, but there is an Adobe plugin that will not uninstall. Now I can't even get Firefox back. Here is the message:


E: adobe-flashplugin: subprocess installed pre-removal script returned error exit status 2

(Reading database ... 567264 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by ubuntu27 on 2012-04-28
Perhaps this will be fixed by using Flash-Aid:

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by JohnBK on 2012-04-29
[QUOTE=ubuntu27;11885922]Perhaps this will be fixed by using Flash-Aid:

I would try it, but I no longer have Firefox and can't reload it!

---

### Post by dino99 on 2012-04-29
sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it)

---

### Post by JohnBK on 2012-04-29
Did not work. Same result: 


(Reading database ... 567264 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by JohnBK on 2012-04-30
Solved!
Just ran:  sudo apt-get remove adobe-flashplugin

---

