---
title: "Just let Ubuntu upgrade to 23.04 and two problems"
date: 2023-04-21
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2023-04-21
PC is DELL Precision 7720 laptop.

Everything working well before upgrade from 22.10, although it would take several reboots at times to get sound to work (pipewire and wireplumber).  Now no sound, but more importantly System Settings will not launch from Unity launcher.  System Settings will run from CL but only shows network configuration.  CL shows the following:

john@john-Precision-7720:~$ systemsettings
kf.kirigami: Failed to find a Kirigami platform plugin
file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/ScrollablePage.qml:200:9: QML MouseArea: Binding loop detected for property "width"
file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/ScrollablePage.qml:200:9: QML MouseArea: Binding loop detected for property "width"
kf.kirigami: Failed to find a Kirigami platform plugin

Please let me know what is going on and how to get System Settings back?

Thank you,

John

---

### Post by cigtoxdoc on 2023-04-21
First, an upgrade on a second machine Lenovo M83 went perfectly, and I am using that machine to reply to the message above on problems with Dell Precision 7720 laptop after upgrading to 23.04.  The remainder of this post deals with the 7720

The next step after the upgrade was to check if 23.04 had installed the correct video driver.  It had installed the nouveau driver so I installed the correct nVidia driver (525).  When I rebooted, the machine stalled before getting to the Ubuntu login.  Doing as Ctrl-Alt-F2 got me to tty2.  I logged in and immediately go the following errors:

[33.113078] snd_hda_codec_generic hdaudioC002: Unable to sync register 0x2f0d00. -5

Several more lines saying the same thing followed, only with slightly different numbers at the beginning of the error messages, and the hdaudio ended in D0.

How do I fix this?

Thank you,

John

---

### Post by cigtoxdoc on 2023-04-25
I fixed this by dowloading the Ubuntu 23.04 Unity install program and putting it on thumb drive.  I had the installer replace the existing 23.04 installation and then everything worked correctly.

---

### Post by ActionParsnip on 2023-04-25
Please mark as solved if there is no more issue

---

