---
title: "Coming home ..... !"
date: 2020-02-22
forum: Installation &amp; Upgrades
---

### Post by michael351 on 2020-02-22
I'm writing this here because I don't want to offend our friends over at the Centos forum .... but Centos is terrible.

I inherited a server with two nodes on it. It came with an old version of Centos and so I thought rather than mess with installing Ubuntu over it (like I have on my other systems), I'd keep it, update and play with Centos for awhile. I updated it to Centos 8, the current version. The server is used for media serving over a LAN (Plex) and elsewhere. Updating Centos works on one node, but not the other (dnf update + something about "no more mirrors to try ... "). So this is finished can't update. And help on the forum is limited to what I can tell - is one guy.

On the other node, I have this zombie process with changing PID's cropping up - java - and uses 130% CPU (multiple procs & threads) - heck if I can find what the parent process is and KILL IT. I can't figure out how this java process got created in the first place and chewing up my cpu like it is. Even filezilla is giving me problems on this system (constantly disconnecting re-connecting - firewall? over a LAN?).

Nevertheless - Ubuntu is so much simpler and better supported and has all of you! I have a Kodi box with Ubuntu under the hood that I have used for YEARS - it just works. I update Ubuntu regularly - add all sorts of new packages from time to time and otherwise love the environment. No mysteries - it just works.

Question - what is the best way to migrate over to Ubuntu from Centos? Should I just do a fresh install and say bye-bye to Centos? Dual boot? I'm asking because I have a lot of media files stored on the Centos system disks and would hate to have to reload it all (from backups). And I serve them up to family/friends and re-configuring will take some time.

Again, I don't want to offend our friends on Centos, there is just so few of them.

---

### Post by dragonfly41 on 2020-02-22
I can offer no advice on Centos since I only use Ubuntu. But I see that Stacer (which I use to monitor Ubuntu processes) can also install on Centos.

[https://linoxide.com/linux-how-to/install-stacer-monitoring-optimising-tool-linux/](https://linoxide.com/linux-how-to/install-stacer-monitoring-optimising-tool-linux/)

This might at least give you a handle on taming the system before you migrate.

---

### Post by michael351 on 2020-02-22
Thanks dragonfly! I'll take a look.

---

