---
title: "Another log in problem"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by Alexi.S on 2011-02-15
Ï installed ubuntu studio 10.10 to an old computer I'm not familiar with. However I'm not able to log in. The log in screen is not grafical. It says in the first line "ubuntu 10.10 (computer name) tty1. Then I enter the username and it asks for password. However I cannot write anything to that line, so I'll never be logged in unless you have answeres. I don't believe this is one of those NVidia-cases, for I tried "sudo rm /etc/x11/xorg.conf" tips and others as well.
Thanks for yor help.

---

### Post by sikander3786 on 2011-02-15
Welcome to the forums :-)

The command you mentioned above is not correct. Linux is case sensitive and the X for 'X11' needs to be capital. Please follow the commands below, same case as mentioned here.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bad
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo reboot now
```

---

### Post by Alexi.S on 2011-02-15
It says that "phigh" is not installed, and that no info is avaivable etc. That is after typing "sudo dpkg-re-configure -phigh xserver-xorg" and entering.

---

### Post by sikander3786 on 2011-02-15
I suspect you mistyped the commands. Anyways, try this one.

```
sudo dpkg-reconfigure xserver-xorg
```

And then reboot.

---

