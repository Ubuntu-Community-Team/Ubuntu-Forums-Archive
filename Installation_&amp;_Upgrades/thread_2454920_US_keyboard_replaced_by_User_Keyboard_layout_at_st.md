---
title: "US keyboard replaced by User Keyboard layout at startup cryptsetup prompt"
date: 2020-12-08
forum: Installation &amp; Upgrades
---

### Post by gilles9 on 2020-12-08
I don't know how but the default language that I use to enter my  cryptsetup password has switch with the one that i'm using on my Ubuntu  session during an update.
I tried the solution from this thread [https://askubuntu.com/questions/232656/how-to-change-keyboard-layout-for-startup-passphrase-prompt](https://askubuntu.com/questions/232656/how-to-change-keyboard-layout-for-startup-passphrase-prompt)
It seems that happened after trying to install some dependencies from the followings packages : libproxy1-plugin-networkmanager gnome-shell-extension-system-monitor. but I'm not so sure.

So I did :

echo "KEYMAP=Y" | sudo tee -a /etc/initramfs-tools/initramfs.conf
update-initramfs -u

I even tried many times.
but unfortunately, it didn't work. It is still the same keyboard map in prompt at startup. 
It is the second time that I have this isues.
Any idea ?

Thx in advance.

---

### Post by CelticWarrior on 2020-12-08
Strange problems seem to follow you...

[https://askubuntu.com/questions/810984/keyboard-layout-ignored-in-initramfs-since-kernel-4-4-0-34-how-to-use-non-us-la](https://askubuntu.com/questions/810984/keyboard-layout-ignored-in-initramfs-since-kernel-4-4-0-34-how-to-use-non-us-la)

---

### Post by gilles9 on 2020-12-09
Thank you very much Celtic Warrior. 
the command : "sudo dpkg-reconfigure keyboard-configuration" have resolved the problem. Now I have the US layout keyboard at my startup promt. Great Thanks !
Wish you a merry Christmas and a happy new year.

---

### Post by gilles9 on 2020-12-09
It changed also my layout on login screen. So I could not enter my password in my language (fr). It has switched X.org to US as well. 
I found a way to manage it by adding fr and fr bepo  languages with localectl using this command :
sudo localectl --no-convert set-x11-keymap fr,fr "" oss,bepo grp:alt_caps_toggle,grp_led:scroll

but when I tried to have only fr bepo, : 
localectl --no-convert set-x11-keymap fr bepo

I went back to qwerty.

Any idea ?

---

### Post by gilles9 on 2020-12-09
This command is working :  sudo localectl --no-convert set-x11-keymap fr "" bepo 
Hope this could help someone else.
Cheers

---

