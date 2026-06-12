---
title: "error in installation"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by bijipseemon on 2011-03-25
:(when i want to install kubuntu desktop,me getting the error as follows..W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdewebkit5_4.5.1-0ubuntu8_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdewebkit5_4.5.1-0ubuntu8_i386.deb)
  Could not connect to in.archive.ubuntu.com:80 (111.91.91.37). - connect (110: Connection timed out):(

---

### Post by bijipseemon on 2011-03-25
when i want to install kubuntu desktop,me getting the error as follows..W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...untu8_i386.deb](http://in.archive.ubuntu.com/ubuntu/...untu8_i386.deb)
Could not connect to in.archive.ubuntu.com:80 (111.91.91.37). - connect (110: Connection timed out)


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/q/qca2/libqca2_2.0.2-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/q/qca2/libqca2_2.0.2-1ubuntu2_i386.deb)
  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.7.0-0ubuntu4.2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.7.0-0ubuntu4.2_i386.deb)
  Unable to connect to in.archive.ubuntu.com:http:


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-script_4.7.0-0ubuntu4.2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-script_4.7.0-0ubuntu4.2_i386.deb)
  Unable to connect to in.archive.ubuntu.com:http:

---

### Post by Old_Grey_Wolf on 2011-03-25
It appears the server you are trying to download from is not responding.

Go to the menu System > Administration > Synaptic Package Manager. 

When the window opens use the menu Settings > Repositories.

When the window opens use the Download From: pull-down to select Other...

Then select your country and a different server in your country.

Then click on the choose server button.

Click on the Reload button on the top left of the Synaptic Package Manager window.

Then try downloading the desktop package again.

---

