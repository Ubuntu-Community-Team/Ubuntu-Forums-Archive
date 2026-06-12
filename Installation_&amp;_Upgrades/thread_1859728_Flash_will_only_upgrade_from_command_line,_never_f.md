---
title: "Flash will only upgrade from command line, never from software updater."
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by marek_online on 2011-10-14
This one has bugged me for several releases, and I've never understood it.

Whenever there's an update for flashplugin-installer, it will fail to update from within the software updater (I use Kubuntu).

However, if I run
```
sudo apt-get upgrade
```from a command line it downloads and updates perfectly.

Because I've always just used the command line I've never bothered to try to solve the problem, but last night this issue seemed to crash my upgrade to Oneiric (thankfully could be fixed easily with a "dpkg --configure -a" from the command line after reboot).

So I'm curious, can anyone tell me what might  be going on?

Aside from this one issue, and my wireless USB stick triggering two working drivers (so I had to blacklist one), my most painless upgrade ever. Very pleased.

---

