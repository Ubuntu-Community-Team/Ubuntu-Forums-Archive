---
title: "aptitude install vim-full, listing too many packages to install"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by succhi on 2008-11-13
I am trying to install vim-full on an Ubuntu 8.04 LTS remote server. It is the only way I know to get the use of arrows working. I recently upgraded vim with aptitude but it still doesn't recognise arrows.

What I would like to know is why I get so many packages listed to automatically install, please see below. I obviously don't want sound on a server install.

```

sudo aptitude install vim-full
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  acl consolekit dbus dbus-x11 esound-clients esound-common gamin gconf2 gconf2-common gnome-keyring gnome-mime-data 
  gnome-mount hal hal-info libart-2.0-2 libasound2 libaudiofile0 libavahi-client3 libavahi-common-data libavahi-common3 
  libavahi-glib1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libdbus-glib-1-2 libenchant1c2a 
  libesd-alsa0 libgail-common libgail18 libgamin0 libgconf2-4 libglade2-0 libgnome-keyring0 libgnome2-0 libgnome2-common 
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common 
  libgnomevfs2-extra libhal-storage1 libhal1 libhunspell-1.1-0 libidl0 libnotify1 liborbit2 libpam-ck-connector 
  libpam-gnome-keyring libpolkit-dbus2 libpolkit-gnome0 libpolkit-grant2 libpolkit2 libsexy2 libsmbclient libsmbios-bin 
  libsmbios1 libsmbiosxml1 libstartup-notification0 libwnck-common libwnck22 libx86-1 libxres1 notification-daemon pm-utils 
  policykit policykit-gnome powermgmt-base radeontool shared-mime-info uswsusp vbetool vim-gnome vim-gui-common 
The following NEW packages will be installed:
  acl consolekit dbus dbus-x11 esound-clients esound-common gamin gconf2 gconf2-common gnome-keyring gnome-mime-data 
  gnome-mount hal hal-info libart-2.0-2 libasound2 libaudiofile0 libavahi-client3 libavahi-common-data libavahi-common3 
  libavahi-glib1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libdbus-glib-1-2 libenchant1c2a 
  libesd-alsa0 libgail-common libgail18 libgamin0 libgconf2-4 libglade2-0 libgnome-keyring0 libgnome2-0 libgnome2-common 
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common 
  libgnomevfs2-extra libhal-storage1 libhal1 libhunspell-1.1-0 libidl0 libnotify1 liborbit2 libpam-ck-connector 
  libpam-gnome-keyring libpolkit-dbus2 libpolkit-gnome0 libpolkit-grant2 libpolkit2 libsexy2 libsmbclient libsmbios-bin 
  libsmbios1 libsmbiosxml1 libstartup-notification0 libwnck-common libwnck22 libx86-1 libxres1 notification-daemon pm-utils 
  policykit policykit-gnome powermgmt-base radeontool shared-mime-info uswsusp vbetool vim-full vim-gnome vim-gui-common 
0 packages upgraded, 77 newly installed, 0 to remove and 0 not upgraded.
Need to get 9661kB/9740kB of archives. After unpacking 63.4MB will be used.
Do you want to continue? [Y/n/?]
```

Any thoughts?
Thank you

---

### Post by shadanan on 2008-11-13
Don't install vim-full. That includes the X version of vim. Just do:

sudo apt-get install vim

---

### Post by succhi on 2008-11-13
I see. But I did that already and I still can't use the arrow keys, which is why I was trying vim-full.

That does at least explain why there are so many packages it wanted to install.

So I guess I just need to look for a way to get arrow keys to work

Cheers,
Stuart

---

