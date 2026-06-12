---
title: "Ubuntu Software - OS Updates Never Finishes - Ubuntu 16.04 LTS 64-bit"
date: 2016-12-23
forum: Installation &amp; Upgrades
---

### Post by mrbunney2 on 2016-12-23
I've kept updated, I've already run 'sudo apt-get update && sudo apt-get upgrade' successfully.

However, Ubuntu Software - OS Updates is always asking for a single update:

[ATTACH=CONFIG]272820[/ATTACH]

Does anyone know how to complete this update request from Ubuntu?

I'm on Ubuntu 16.04 LTS 64-bit.

---

### Post by vasa1 on 2016-12-23
Open a terminal and run the following commands and post the entire output between code tags here:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get dist-upgrade
```

You can press "N" after the second and third commands if you're unsure about accepting what is proposed.

---

### Post by howefield on 2016-12-23
Clicking on the text OS Updates should pop up a window showing what is to be installed and clicking the Install button should install them.

I don't use the Ubuntu Software application but tested it out, it took 3 presses of the Install button before it did it's stuff and the "*OS Updates completed installing*" message indicator popped up. 

As far as I can see Ubuntu Software is a bit of a mess right now and I'd trust the Software Updater, unattended-upgrades and the terminal to keep updated.

---

