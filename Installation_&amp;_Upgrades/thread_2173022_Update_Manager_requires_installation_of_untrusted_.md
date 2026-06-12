---
title: "Update Manager requires installation of untrusted packages"
date: 2013-09-07
forum: Installation &amp; Upgrades
---

### Post by ayesharaziahmed on 2013-09-07
I'm new to Ubuntu and just tried running a simple "required" update through the Update Manager but got this message:

[ERROR]  "Requires installation of untrusted packages:
The action would require the installation of packages from not authenticated sources."

details:

apparmor apport apport-gtk base-files dosfstools firefox firefox-globalmenu firefox-locale-en gir1.2-dbusmenu-glib-0.4 gir1.2-dbusmenu-gtk-0.4 gnome-control-center gnome-control-center-data initramfs-tools initramfs-tools-bin jockey-common jockey-gtk libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4 libgnome-control-center1 libnm-glib-vpn1 libnm-glib4 libnm-util2 libpci3 linux-generic linux-headers-3.2.0-52 linux-headers-3.2.0-52-generic linux-headers-generic linux-image-3.2.0-52-generic linux-image-generic linux-libc-dev lsb-base lsb-release network-manager pciutils python-apport python-problem-report remmina remmina-common remmina-plugin-rdp remmina-plugin-vnc thunderbird thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-gb thunderbird-locale-en-us whoopsie xul-ext-ubufox

and it only has a "Close" button.
What do I do?
I use Ubuntu on Asus laptop x201e

---

### Post by ibjsb4 on 2013-09-07
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

and

```
sudo apt-get upgrade
```

And please post any errors.

---

### Post by ayesharaziahmed on 2013-09-08
Wow that was awesome and thank you for being so fast!
 everything is in working order now! 
even the update manager works! 
that was so cool it looked like the matrix!
Is there some way i can give you a five star rating?
I'm new to all this.....
THANK YOU!!!

---

### Post by ibjsb4 on 2013-09-08
And welcome to the forums :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

