---
title: "nvidia-glx-new conflicts/requires nvidia-glx"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by Kajong on 2008-02-09
Before I install nvidia-glx:

[IMG]http://i12.photobucket.com/albums/a248/kajong1/Screenshot-PackageInstaller-nvidia-.png[/IMG]


After I install nvidia-glx:

[IMG]http://i12.photobucket.com/albums/a248/kajong1/Screenshot-PackageInstaller-nvid-1.png[/IMG]


nvidia-glx-new requires nvidia-glx but then it conflicts with it. what am i doing wrong?
I have AMD64 and an hp laptop dv2315nr with nvidia Geforce Go 6150

I know I need this driver for my nvidia graphics card to work (this is a snapshot of the restricted drivers manager when i try to activate nvidia):
[IMG]http://i12.photobucket.com/albums/a248/kajong1/Screenshot-restricted-manager.png[/IMG]

---

### Post by The Avatar of Time on 2008-02-09
I don't believe that nvidia-glx is in any way needed for nvidia-glx-new. They are two seperate drivers as is the. Generall if I am in Gnome or KDE i use restricted drivers manager and just enable the only option. Always works fine. However when in Fluxbox I do this from terminal: (this is assuming that you need the glx-new driver, and I would also recommend that you uninstall any driver you have already installed first)

sudo aptitude install nvidia-glx-new linux-restricted-modules  

then:

sudo nvidia-xconfig

Course you could always install Envy and use it. Hope this helps.

---

### Post by Kajong on 2008-02-09
the first command you told me worked, but "sudo nvidia-xconfig" returned the error:

"sudo: nvidia-xconfig: command not found"



Now i am trying envy...

EDIT

It works!!! Thank you!

---

