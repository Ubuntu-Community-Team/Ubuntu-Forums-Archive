---
title: "X problems after upgrade"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by maclaud on 2006-10-30
Hello 
gksu "update-manager -c" was about to finish and i was all expactation to boot into my new edgy, sudenly it ask me if i want to remove or keep the obsoletes packages, i choose for the remove option thinking that if any thing will be neede then i can reinstall.
after that i reboot the machine and get the login screen  but the X was reseting itself saying that my session last less than 10 seconds and refering me to the .xsession-errors:
[HTML]
/etc/gdm/Xsession: Beginning session setup...
Xlib: connection to ":0.0" refused by server
Xlib: Protocol not supported by server


(x-session-manager:5144): Gtk-WARNING **: cannot open display:[/HTML]

[COLOR="Red"]after digging a lilte more i found that if i stop gdm i can startx and it work so probably it is a permissions issue but i still dont dont where
[/COLOR]

i search for help here in the forums but i dindt find any post that help me so here i'm.
a secondary and far less important problem is that the grub menu.lst have not my chiced image as  default but that i can edit manually
thnx in advance 
Maclaud

---

