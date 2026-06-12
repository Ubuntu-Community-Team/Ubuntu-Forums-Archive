---
title: "Fresh installation of 17.10 results in several failures"
date: 2018-02-16
forum: Installation &amp; Upgrades
---

### Post by serapis5 on 2018-02-16
Just did a fresh installation from DVD of 17.10 and have run into several problems:

1:  GEDIT will not open using the SUDO command, only the READ0ONLY option works so I cannot modify system files such as /etc/hosts or /etc/hostname
2:  CUPS no longer works for remote printing even though it is shared and showing up on remote computers also running 17.10.  As a side note it also doesn't work for Android CUPS print.
3:  Synaptic Package Manager will not open even though it is installed.
4:  Backups no longer recognizes my old backup files telling me that none exist even though I can see them in my backup location.

Any help would be greatly appreciated.

---

### Post by mörgæs on 2018-02-17
It sounds like you are running in Wayland mode. Have you tried X11?

---

### Post by Impavidus on 2018-02-17
Also see [https://ubuntuforums.org/showthread.php?t=2375077](https://ubuntuforums.org/showthread.php?t=2375077)

And you can use a terminal-based text editor. They work fine with sudo and wayland.

---

### Post by serapis5 on 2018-02-17
That was the problem.  I reinstalled 5 times but that turned out to be the problem.  I've been using Linux for 15 years and never thought about that.  Boy do I feel like an idiot.  Thanks for your help!

---

### Post by vasa1 on 2018-02-17
> **serapis5 said:**
> ...

1:  GEDIT will not open using the SUDO command...
*sudo* isn't to be used with GUI-based applications. Try *sudo -H gedit* instead at least for X11.

---

