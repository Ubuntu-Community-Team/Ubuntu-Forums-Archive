---
title: "Installing updates failing consistently"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by patcc2 on 2011-07-22
Hi, I installed Ubuntu onto my computer about 6 months ago but just started switching to the OS.  I wanted to install Kubuntu plasma desktop from the software from the center but it kept failing.  First guess was that the machine wasn't updated so sure enough around 100 updates need to be installed on the machine.  I hit install and about half way through i get this error "Failed to download package files    Check your Internet connection."  I hit details and that reads 
```
 Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-user-docs/gnome-user-guide_3.0.0+git20110406ubuntu9_all.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.8.13.2ubuntu3_i386.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.8.13.2ubuntu3_i386.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.8.13.2ubuntu3_i386.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector-gnome_0.34.1_all.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector-common_0.34.1_all.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevdocument3_2.32.0-0ubuntu12.1_i386.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevview3_2.32.0-0ubuntu12.1_i386.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince-common_2.32.0-0ubuntu12.1_all.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_2.32.0-0ubuntu12.1_i386.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_4.0.1+build1+nobinonly-0ubuntu0.11.04.2_i386.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_4.0.1+build1+nobinonly-0ubuntu0.11.04.2_i386.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_4.0.1+build1+nobinonly-0ubuntu0.11.04.2_i386.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nux/libnux-0.9-0_0.9.48-0ubuntu1_i386.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nux/libnux-0.9-common_0.9.48-0ubuntu1_all.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nux/nux-tools_0.9.48-0ubuntu1_i386.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/papyon/python-papyon_0.5.5-1ubuntu1.1_all.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_4.0.1_all.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity/unity_3.8.12-0ubuntu1_i386.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity/unity-common_3.8.12-0ubuntu1_all.deb 404  Not Found [IP: 91.189.88.45 80]
 
```

Also just as a note if this matters when I go to install the Kubuntu plasma desktop I get the same plain error with details of.
```
 Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector-gnome_0.34.1_all.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector-common_0.34.1_all.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xml_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-dbus_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-script_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xmlpatterns_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-declarative_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-designer_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-qt3support_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql-mysql_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-help_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-scripttools_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-test_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector-kde_0.34.1_all.deb 404  Not Found [IP: 91.189.92.169 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql-sqlite_4.7.2-0ubuntu6.1_i386.deb 404  Not Found [IP: 91.189.92.169 80]
 
```

Thanks for any help

---

