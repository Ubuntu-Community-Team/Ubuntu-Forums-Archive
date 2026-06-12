---
title: "Installed using Instlux, stuck in command shell, please help..."
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by dsp82 on 2006-03-05
I finally found a way to install ubuntu om my x31 using the automatic installer(Instlux) from here: 

[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)

I won't boot to gnome, only the command shell.

I have a few guesses why it's happening. Since all files are downloaded from the net and then installed, im guessing it choses the smallest ubuntu size possible leaving out stuff such as gnome, openoffice etc.

I think the problem lies in choosing the the ubuntu mirror. Is there any mirror, that will install all the software including gnome, openoffice etc.? Or maybe a way to refer to the image of ubuntu i allready have on a fat32 partion of my harddrive?

---

### Post by roshan.s on 2006-03-05
After it boots, try typing ```
sudo apt-get install ubuntu-base ubuntu-desktop
```

---

