---
title: "Install issues on Lenovo Ideacentre 200-01IBW"
date: 2017-05-06
forum: Installation &amp; Upgrades
---

### Post by hnipen on 2017-05-06
I just bought a Lenovo Ideacentre that comes bundled with Win 10 Home

I made an Ubuntu 17.04 Desktop 64 on a USB stick from which I am trying to install Ubuntu on the above machine. It boots, but screen goes blue, which I reckon is an issue with graphics card detection, or maybe screen resolution is set too high for monitor. I should be ok up to at least 1920×1080, but I assume graphics card support way above this.

There is an Intel(R) HD Graphics controller.

Tried to check some docs but found no solution that works with me, need to set screen resolution, say to 1280 x 1024 during installation, how to do this?
(Don't have any hi-rez monitors available at the moment)

---

### Post by hnipen on 2017-05-06
Found it, the bootup dialogs changed a bit, but on 16 and 17 I managed by editing meny, taking away one dash and add vga=791, and then press f10

[IMG]https://help.ubuntu.com/community/BootOptions?action=AttachFile&do=get&target=Boot-F6-Other-Manual.png[/IMG]

---

