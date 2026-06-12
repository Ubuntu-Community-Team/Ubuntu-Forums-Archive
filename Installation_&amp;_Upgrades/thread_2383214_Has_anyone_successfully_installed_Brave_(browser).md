---
title: "Has anyone successfully installed Brave (browser)"
date: 2018-01-22
forum: Installation &amp; Upgrades
---

### Post by pingnan2 on 2018-01-22
I tried to install Brave in command mode but failed. Here is what I got:
```
dpkg: error processing package brave:amd64 (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Errors were encountered while processing:
 brave:amd64
```

---

### Post by cruzer001 on 2018-01-22
Hello

Please provide the download link and post the output of:

```
inxi -S
```

---

### Post by Impavidus on 2018-01-22
It may be useful if you provide the exact command you tried and the full output if gave. Right now we're guessing.

---

### Post by vasa1 on 2018-01-23
> **Impavidus said:**
> It may be useful if you provide the exact command you tried and the full output if gave. Right now we're guessing.
+1.

And because you're using the command-line, that information should be in *$HOME/.bash_history*.

If you haven't done a lot in the terminal subsequently, use something like:
```
tail -50 $HOME/.bash_history
```to give you, for example, the last fifty lines.

Also helpful would be the complete terminal output from first running
```
sudo apt-get update
```and then running```
sudo apt-get upgrade
```

---

