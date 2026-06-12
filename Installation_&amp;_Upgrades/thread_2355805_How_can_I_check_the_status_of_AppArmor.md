---
title: "How can I check the status of AppArmor?"
date: 2017-03-16
forum: Installation &amp; Upgrades
---

### Post by AbleTassie on 2017-03-16
I would like to use AppArmor, since it is recommended as a security tool in the Ubuntu basic security page, but I am unsure if it is even installed. I recently installed Lubuntu 16.04 on m PC, but I did not check the box to "allow third party software installation" when I did the initial installation of Lubuntu.  I am using the Firefox webbrowser.  

How can I check the status of AppArmor?    

Thanks,  A.

---

### Post by vasa1 on 2017-03-16
```
apt policy apparmor
apparmor:
  **_Installed_**: 2.10.95-0ubuntu2.5
  Candidate: 2.10.95-0ubuntu2.5
  Version table:
 *** 2.10.95-0ubuntu2.5 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.10.95-0ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

I had some apparmor notes but I can't find them right now!

Edit:
Try```
sudo aa-status
```

I get```
sudo aa-status
[sudo] password for vasa1: 
apparmor module is loaded.
27 profiles are loaded.
20 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/NetworkManager/nm-dhcp-helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/lib/snapd/snap-confine
   /usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/sbin/cupsd
   /usr/sbin/cupsd//third_party
   /usr/sbin/ntpd
   /usr/sbin/tcpdump
   snap.core.hook.configure
7 profiles are in complain mode.
   snap.libreoffice.base
   snap.libreoffice.calc
   snap.libreoffice.draw
   snap.libreoffice.impress
   snap.libreoffice.libreoffice
   snap.libreoffice.math
   snap.libreoffice.writer
3 processes have profiles defined.
3 processes are in enforce mode.
   /sbin/dhclient (1339) 
   /usr/sbin/cupsd (2814) 
   /usr/sbin/ntpd (1651) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

```

---

### Post by deadflowr on 2017-03-16
```
sudo aa-status
```
will give you the current state of your apparmor profiles.
fur what it's worth

I'm unclear if there is any flavor of Ubuntu that does not come with apparmor installed with a number of preset profiles.

ninja'd

---

### Post by AbleTassie on 2017-03-17
Thanks vasa1 and deadflowr,

I ran the terminal commands you gave me and AppArmor is definitely working and has current settings. I will just have to learn more about interacting with AppArmor.

A.

---

