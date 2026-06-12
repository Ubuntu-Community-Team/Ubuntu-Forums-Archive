---
title: "Distribution upgrade stopped unexpected"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2013-05-01
I attempt to upgrade from 12.10 to 13.04 and the upgrade showed me twice errors, but continued:

Could not install '/var/cache/apt/archives/python-wxgtk2.8_2.8.12.1-11ubuntu4_amd64.deb'

The upgrade will continue but the '/var/cache/apt/archives/python-wxgtk2.8_2.8.12.1-11ubuntu4_amd64.deb' package may not be in a working state. Please consider submitting a bug report about it.

symbolic link '/usr/lib/python2.7/dist-packages/wx-2.8-gtk2-unicode/wx/lib/pubsub/core/kwargs/publishermixin.py' size has changed from 105 to 64

----------------------------------------------


Could not install 'python-wxgtk2.8'

The upgrade will continue but the 'python-wxgtk2.8' package may not be in a working state. Please consider submitting a bug report about it.

package python-wxgtk2.8 is already installed and configured

----------------------------------------------



then after a while I got upgrade stopped unexpected.

When I try to restart   sudo update-manager    I am not offered to upgrade to 13.04, but that it wants to install the already downloaded package python-wxgtk2.8   - which gives over and over an error.



In the terminal I can see:

sudo update-manager 
[sudo] password for ronald: 

(update-manager:10395): IBUS-WARNING **: The owner of /home/ronald/.config/ibus/bus is not root!
gpg: /tmp/tmp6y5uc4/trustdb.gpg: trustdb created
gpg: /tmp/tmpdqhgzo/trustdb.gpg: trustdb created
ronald@ronald-Desktop:/etc/X11$ sudo update-manager 

(update-manager:10742): IBUS-WARNING **: The owner of /home/ronald/.config/ibus/bus is not root!
ronald@ronald-Desktop:/etc/X11$ sudo update-manager 
gpg: /tmp/tmpygdsye/trustdb.gpg: trustdb created

(software-properties-gtk:11083): IBUS-WARNING **: The owner of /home/ronald/.config/ibus/bus is not root!



So, what am I going to do now?
How to finish the upgrade???

---

### Post by ELMIT on 2013-05-02
How can I continue to upgrade????

---

### Post by grahammechanical on 2013-05-02
This is a link to apt-get commands. You may be able to make use of them. You can fix broken packages, remove. Stuff like that. Do not run dist-upgrade as it does not upgrade one version of Ubuntu to the next. The command to do that is

```
sudo apt-get do-release-upgrade
```

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Try to fix or remove the broken package before running apt-get do-release-upgrade.

[https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)

Regards.

---

