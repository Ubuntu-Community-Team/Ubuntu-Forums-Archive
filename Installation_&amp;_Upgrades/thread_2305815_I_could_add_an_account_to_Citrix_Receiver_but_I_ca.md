---
title: "I could add an account to Citrix Receiver but I can't start it"
date: 2015-12-09
forum: Installation &amp; Upgrades
---

### Post by deme2 on 2015-12-09
I just installed successfully Citrix Receiver in Ubuntu 14.04 64 bits by following [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo). I added the same account I am using successfully in Windows machine by via [COLOR=#333333][FONT=UbuntuMono]/opt/Citrix/ICAClient/util/configmgr &[/FONT][/COLOR]. Nevertheless, I can't start it. I am quite new to Ubuntu. I tried these:
1 - browse to /usr/share/applications, find selfservice.desktop, right-click and click in run
2 - search applications, find Citrix Receiver and launch it
3 - check if there is "-" missed in [COLOR=#333333][FONT=UbuntuMono]/usr/share/applications/selfservice.desktop as suggested in [/FONT][/COLOR]http://discussions.citrix.com/topic/358076-deb-package-uses-icaroot-instead-of-icaroot-spelling-error/#entry1844542
4 - try start selfservice.desktop via terminal:
deme@PC:/usr/share/applications$ sudo ./selfservice.desktop
[sudo] password for deme: 
sudo: ./selfservice.desktop: command not found
5 - try start selfservice via terminal:
deme@PC:/opt/Citrix/ICAClient$ sudo ./selfservice
libwebkit: libwebkit-1.0.so: cannot open shared object file: No such file or dir

---

