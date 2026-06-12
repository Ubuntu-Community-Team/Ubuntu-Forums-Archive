---
title: "Unable to apt-get remove for a server with no internet access"
date: 2020-08-27
forum: Installation &amp; Upgrades
---

### Post by z080236 on 2020-08-27
I am trying to remove some unused components.

apt-get remove pulseaudio

You might want to run apt --fix-broken install to correct these.

The following packages have unmet dependencies:
dbus-x11
grub-efi-amd64-bin
.....
I have tried all commands even fix-broken install and auto-remove but didn't work

tried all of these, didn't work.

[https://linuxhint.com/uninstall-debian-packages/](https://linuxhint.com/uninstall-debian-packages/)


Note that this is for a server without internet access.

---

### Post by z080236 on 2020-08-27
in the end I used this method to remove

[https://askubuntu.com/questions/17745/how-to-remove-a-deb-without-removing-its-dependencies](https://askubuntu.com/questions/17745/how-to-remove-a-deb-without-removing-its-dependencies)

---

