---
title: "new install 22.04.1 - gnome shell extension system-monitor graphs on top bar"
date: 2022-08-14
forum: Installation &amp; Upgrades
---

### Post by Kris_M on 2022-08-14
I haven't done this since 20. Is it still the same?
My notes say:
```
   	 	 	 	   **gnome shell extension system-monitor graphs on top bar**
  Before installing this extension, ensure you have the necessary system packages installed:
 [FONT=Liberation Serif, serif][SIZE=3]do fixes:[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]sudo apt-get install gir1.2-gtop-2.0[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]sudo apt-get update[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]sudo apt-get install gir1.2-nm-1.0:i386 gir1.2-nm-1.0[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]sudo apt install gir1.2-clutter-1.0 gir1.2-clutter-gst-3.0 gir1.2-gtkclutter-1.0[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]check that FF add-ons gnome shell integration is there. (add it in FF)[/SIZE][/FONT]
  [FONT=Liberation Serif, serif][SIZE=3]sudo apt install chrome-gnome-shell[/SIZE][/FONT]
  then
  [FONT=Liberation Serif, serif][SIZE=3]in FF go to:[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3][https://extensions.gnome.org/extension/120/system-monitor/](https://extensions.gnome.org/extension/120/system-monitor/)[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]and turn it on/install (it’s very quick)[/SIZE][/FONT]
  
```

THANKS!

---

### Post by deadflowr on 2022-08-15
Not sure it'll work since the extension is only built up to gnome-shell 40 and Ubuntu 22.04 uses gnome-shell 42.
Gnome is very picky about these things.


Also Ubuntu 22.04 uses a snap for firefox which may or may not have the proper functionality to even use the extension plugins.
See: [https://discourse.ubuntu.com/t/call-for-testing-native-messaging-support-in-the-firefox-snap/29759/32]("https://discourse.ubuntu.com/t/call-for-testing-native-messaging-support-in-the-firefox-snap/29759/32")
on the current progress of getting it working.

In the meantime you would need to use a version of firefox like from the upstream tarball version or from this PPA: 
[https://launchpad.net/~mozillateam/+archive/ubuntu/ppa]("https://launchpad.net/~mozillateam/+archive/ubuntu/ppa")
but for the PPA version you also need to follow a basic guide in order to allow the system to grab that version of firefox or you end up with the snap version,
as Ubuntu ships the snap in a transitional deb package.

See this as a basic guide to install the deb version of fiefox: 
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04]("https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04")

---

### Post by Kris_M on 2022-08-15
Yep, realized that. Forget it.
Thanks!

---

