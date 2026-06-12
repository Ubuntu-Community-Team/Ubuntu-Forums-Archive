---
title: "Ubuntu-terminal-app on unity7 (17.04)"
date: 2017-04-11
forum: Installation &amp; Upgrades
---

### Post by yuhuanknot on 2017-04-11
Hello all,

I've always had Ubuntu on my computer, up until yesterday I had Ubuntu 16.04 Gnome. I've decided to try 17.04 because I couldn't make my RTL8821AE wifi card work without the signal dropping to zero constantly (even thought it is still connected). The problem wasn't solved.

But I'm here because I want to have ubuntu-terminal-app working on 17.04 but on unity7. Unity8 works awfully for me, always crashing, etc. but I had a glimpse on that terminal, and I really need it. Thing is: I thought i had to install it when logging in with unity7. I've tried through snap, and it said it was already installed but I can't find it nowhere (reinstall does not work either) and I've tried the .deb package from [http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-terminal-app/](http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-terminal-app/) which does install it (even though the icon is nowhere to be found either) but i can call it on the terminal(gnome-terminal) but then I get the following message:
```
dazev@duarte-pc:~/Downloads$ ubuntu-terminal-app 

(process:24102): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "unity-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
int main(int, char**) Running on non-MIR desktop, not requiring authentication by default
Trying to load QML from: "/snap/ubuntu-terminal-app/99/usr/bin/qml/ubuntu-terminal-app.qml"
Trying to load QML from: "/home/dazev/Downloads/qml/ubuntu-terminal-app.qml"
Trying to load QML from: "/home/dazev/snap/ubuntu-terminal-app/99/.local/share/terminal/qml/ubuntu-terminal-app.qml"
Trying to load QML from: "/home/dazev/snap/ubuntu-terminal-app/99/.local/share/terminal/qml/ubuntu-terminal-app.qml"
Trying to load QML from: "/home/dazev/snap/ubuntu-terminal-app/99/terminal/qml/ubuntu-terminal-app.qml"
Trying to load QML from: "/snap/ubuntu-terminal-app/99/usr/share/terminal/qml/ubuntu-terminal-app.qml"
Retrieving default keyboard profiles from folder:  "/snap/ubuntu-terminal-app/99/usr/share/terminal/qml/KeyboardRows/Layouts/"
Retrieving keyboard profiles from folder:  "/home/dazev/.config/ubuntu-terminal-app/Layouts/"
Retrieving keyboard profiles from folder:  "/snap/ubuntu-terminal-app/99/etc/xdg/ubuntu-terminal-app/Layouts/"
Retrieving keyboard profiles from folder:  "/snap/ubuntu-terminal-app/99/usr/xdg/ubuntu-terminal-app/Layouts/"
Retrieving keyboard profiles from folder:  "/snap/ubuntu-terminal-app/99/ubuntu-app-platform/etc/xdg/ubuntu-terminal-app/Layouts/"
Retrieving keyboard profiles from folder:  "/snap/ubuntu-terminal-app/99/ubuntu-app-platform/usr/xdg/ubuntu-terminal-app/Layouts/"
Retrieving keyboard profiles from folder:  "/etc/xdg/xdg-ubuntu/ubuntu-terminal-app/Layouts/"
Retrieving keyboard profiles from folder:  "/etc/xdg/ubuntu-terminal-app/Layouts/"
using main qml file from: "/snap/ubuntu-terminal-app/99/usr/share/terminal/qml/ubuntu-terminal-app.qml"
QQmlApplicationEngine failed to load component
file:///snap/ubuntu-terminal-app/99/usr/share/terminal/qml/ubuntu-terminal-app.qml:20 plugin cannot be loaded for module "QtSystemInfo": Cannot load library /snap/ubuntu-terminal-app/99/ubuntu-app-platform/usr/lib/x86_64-linux-gnu/qt5/qml/QtSystemInfo/libdeclarative_systeminfo.so: (libmirclient.so.9: cannot open shared object file: No such file or directory)
```

I think the problem might be the fact that I had to install Qt4 because of TexStudio (wouldn't work with qt5, problem with mir, don't really remember). I just wanted to make sure of it before doing any further move, because i need texstudio to be working.

If it is needed some more information, please ask.

---

### Post by ofletcher on 2017-05-06
Yeah man I just started dualbooting with 16.04 with the same wireless card and am having the same issue with the wifi. It has a signal, but comes in extremely spotty reception, while windows has a perfect connect even to 5ghz. 
I can't really offer much help with the issue you're having unfortunately, because I just started using linux. But did switching to 17.04 help with your wireless issues?

---

### Post by Frogs Hair on 2017-05-06
The ubuntu-terminal-app maybe native to Unity 8 which is more of a tech preview than a working desktop.I had no trouble installing it but only see the following in Unity 7. I removed U8 because development by Canonical has ceased. 
```
ubuntu-terminal-app: command not found


```

---

