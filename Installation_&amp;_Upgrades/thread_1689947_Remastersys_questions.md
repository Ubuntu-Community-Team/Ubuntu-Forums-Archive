---
title: "Remastersys questions"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by wormyblackburny on 2011-02-17
I had a couple dumb questions that I'm sure a little Google-fu could solve, but figured I'd ask if anyone has actually used it and their experience with it, so here goes:

1) Fairly obvious: does custom distributable iso have all of the additional software that I have installed on my machine (ie Skype, Chrome etc...)?

2) Will the installed image maintain all of the Compiz and other desktop settings on the new install including menus, menu bar setup, dockbar-x etc...?

3) If Samba, Apache, etc... are configured, will it carry over the conf files or just install the base applications?

Again, I'm not looking to backup my system as that will obviously maintain all of my settings/files/etc.., I am looking to make a distro for my friends or other personal machines that will have all the "spiffy" programs I have installed and the gnome configuration of my desktop (or at least have all of the tools to configure it so I can write a script to automatically set all of the menu/compiz settings...

Cheers, and thanks for any input :)

---

### Post by wormyblackburny on 2011-02-17
Ok, I've already answered most of my stupid questions and think i have found most of what I need, so let me simplify what else I am curious about:

Have any of you created your own custom distro/setup, and if so which tools did you use (or if you are too lazy to want to get into specifics, how was your experience with the process? Any potential pitfalls that can be avoided?)

---

### Post by wormyblackburny on 2011-03-10
In answer to my own questions:

Yes, it will include all programs and settings. If you want to maintain desktop settings and menu's/themes in a custom sharable iso, make a test user, configure the desktop, and copy the relevant .profile files from /home/(user) to /etc/skel (make sure to chmod -R root:root /etc/skel after copying files to it). I successfully copied desktop, background, theme, icon theme, gnomenu theme, compiz effects, firefox plugins/home page, and menu options via trial and error.

---

