---
title: "uninstalling the Desktop through CLI"
date: 2016-01-21
forum: Installation &amp; Upgrades
---

### Post by lance317 on 2016-01-21
I'm somewhat of an Ubuntu novice, and as a test I installed the Gnome desktop to my VPS "testing" web server through the CLI, and am looking how to get rid of it and just use CLI. I'm aware of the basic uninstall command, but a bit freaked out that it will wind up breaking something else!

---

### Post by papibe on 2016-01-21
Hi lance317. Welcome to the forums ):P

If you haven't done anything important with your VPS, I think it would be easier to just create a clean droplet/instance.

If you don't want to go that route, and assuming you installed Gnome using this command:
```
sudo apt-get install ubuntu-gnome-desktop
```
You could remove it by running:
```
sudo apt-get purge ubuntu-default-settings

sudo apt-get purge ubuntu-desktop

sudo apt-get autoremove
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by lance317 on 2016-01-21
Hi Papibe, and thanks for responding so quickly! I will try your suggestion after work this evening...

---

### Post by lance317 on 2016-01-22
Hi Papibe,

I ran some of your commands, and I don't believe it worked - or at least not all of it - please see a screenshot below, thanks!

[IMG]http://i.imgur.com/9zhoBnf.png[/IMG]

---

