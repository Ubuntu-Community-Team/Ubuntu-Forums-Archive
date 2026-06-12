---
title: "[SOLVED] Cannot upgrade to Seamonkey 1.1.11"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by gwoodruff on 2008-07-17
Howdy, I am trying to upgrade to the latest Seamonkey. When I try to launch the installer I get the error:

./seamonkey-installer-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I have tried as normal user and with gksudo / sudo with no success!

Please help

thanks, Gary

---

### Post by gwoodruff on 2008-07-17
bump

---

### Post by Sef on 2008-07-17
Please don't bump your thread unless 24 hours has gone by.  We are all volunteers, so sometimes your problem can be quickly resolved and sometimes, it takes a while.  Continued pre-24 hour bumping will result in an infraction.

---

### Post by gwoodruff on 2008-07-18
bump

---

### Post by chrisTGc on 2008-07-24
> **gwoodruff said:**
> Howdy, I am trying to upgrade to the latest Seamonkey. When I try to launch the installer I get the error:

./seamonkey-installer-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I have tried as normal user and with gksudo / sudo with no success!

Please help

thanks, Gary

Start synaptic the package manager and click on search,enter libstdc and return.That should list libstdc.Look for version 5 and install.This will inlude the missing dependancy.

Or make a link named libstdc++.so.5 to libstd++.so.6 which is installed in Ubuntu.This may or may not work,not tried it,but it should be OK.

While you will need sudo or gksu to complete the install of seamonkey please do not start seamonkey with sudo (eg in order to install the calendar/or other extensions).That will screw the .mozilla hidden file.Instead type sudo su at the terminal and enter you password.Then type  cd  /root.Now you can call up seamonkey from the command line as root to install extensions.That will create a separate .mozilla fie under /root.You can install seamonkey themes as the normal user but not extensions.

The seamonkey executable is at;
 /usr/local/seamonkey/seamonkey
I would suggest you also right click a blank patch of the top panel to arrange a start up link/icon.Choose add to panel>custom application launcher.Name it SeaMonkey and suggest 'THE BEST OF THEM ALL' as a comment !,my opinion anyway!.

If you also want the calendar extension then post again and i will post a link for it.

Good Luck,Chris.

---

### Post by gwoodruff on 2008-07-28
Howdy, Thanks all for the help. I found that I had multiple copies of Seamonkey. One of the installers placed a copy in the opt directory. I removed all versions and installed fresh by downloading the tar.gz. Unpacked into usr/local and then just added my plugins.

---

### Post by chrisTGc on 2008-07-28
> **gwoodruff said:**
> Howdy, Thanks all for the help. I found that I had multiple copies of Seamonkey. One of the installers placed a copy in the opt directory. I removed all versions and installed fresh by downloading the tar.gz. Unpacked into usr/local and then just added my plugins.

Yup.And thats another way to install it.Libstdc is needed by the instaler  only.Hope you enjoy seaMonkey,it's a good un.

Best Wishes Chris.

---

