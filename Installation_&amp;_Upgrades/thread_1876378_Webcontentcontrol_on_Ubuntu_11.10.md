---
title: "Webcontentcontrol on Ubuntu 11.10"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by Archangelos on 2011-11-06
Hi, I'm trying to install Webcontentcontrol 1.3.7 on Ubuntu 11.10. I can't use the i386.deb because I'm using amd64 architecture and would need an amd64.deb. So I'm installing from the tar.gz.

However, I'm getting a few errors. I can do a successful ./configure. But when I come to 'make' I get the following error:

```
-->webcontentcontrol_GUI/webcontentcontrol_GUI.gambas target called
-->all target called
WCC_CONFIG=yes
WCC_PROXY=tinyproxy
cd ./webcontentcontrol_GUI && gbc2 && gba2
/home/archangelos/Downloads/webcontentcontrol-1.3.7/webcontentcontrol_GUI/FMain.class:943: Unknown identifier: WebBrowser
make: *** [all] Error 1

```

And if I do a 'make install' I get the following errors:

```
Updating menus
/bin/bash: line 10: update-menus: command not found
make[2]: *** [install-data-hook] Error 127
make[2]: Leaving directory `/home/archangelos/Downloads/webcontentcontrol-1.3.7'
make[1]: *** [install-data-am] Error 2
make[1]: Leaving directory `/home/archangelos/Downloads/webcontentcontrol-1.3.7'
make: *** [install-am] Error 2

```

After installation, the app works, but the icon will not start up the GUI. What am I doing wrong? I've followed the instructions perfectly and still get these errors. Thanks. :confused:

---

### Post by dino99 on 2011-11-06
if you are using Firefox, then add the desired plugins instead of using a third app like webcontentcontrol.

firefox -> tools -> addons menu

[https://addons.mozilla.org/z/fr/firefox/extensions/privacy-security/](https://addons.mozilla.org/z/fr/firefox/extensions/privacy-security/)

you can add url filtering too:

[https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

---

### Post by Archangelos on 2011-11-06
Umm..thanks. That doesn't exactly address the question, though.

I need a system wide solution as people use several browsers on the system. :???:

---

