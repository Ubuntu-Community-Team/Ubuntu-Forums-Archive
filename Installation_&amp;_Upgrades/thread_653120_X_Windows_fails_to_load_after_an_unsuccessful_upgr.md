---
title: "X Windows fails to load after an unsuccessful upgrade to Gusty"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by lordfkiller on 2007-12-29
Hi everyone.

I installed all updates and started network upgrade, but it failed because of an external repo. I removed that repo and restarted my PC as Synaptic recommended. But when it loaded again, X server no more worked.

[INDENT]... Error: API mismatch: This NVIDIA driver component has version 100.14.19, but NVIDIA  kernel modules version does not match. Please make sure that ...[/INDENT]

By the way, I have installed some softwares from source code(mono). Should I have removed them first?'

How can I have X server work again? Please help!

Thanks for ANY help.

---

### Post by taurus on 2007-12-29
Press <Ctrl><Alt>F2 and log in with your username and password.  Then, reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, restart X with <Ctrl><Alt>Backspace.

---

### Post by lordfkiller on 2007-12-30
It does not accept my username and password. (Login Incorrect) I am sure the username and password are both correct.

---

### Post by lordfkiller on 2007-12-30
Any idea?

---

### Post by lordfkiller on 2007-12-30
Caps Lock didn't work there! I used shift and logged in.

I chose vesa and it is up now. Now what should I do? Go through upgrade process again or setup my nvidia driver or ...?

btw, do I need to uninstall my current Compiz Fusion(from veraptor.info repos)? What else should I remove?

Any help is appreciated.

---

### Post by taurus on 2007-12-30
Upgrade first and again, make sure you either comment out or remove those 3rd party repos that you've added to your /etc/apt/sources.list.

Once everything is working after upgrading, then install a driver for your graphic card from System -> Administration -> Restricted Drivers Manager.

---

