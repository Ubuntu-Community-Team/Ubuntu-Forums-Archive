---
title: "control modifier ignored by vncviewer"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by jcrockett70 on 2006-10-13
I currently run Gnome environment on Ubuntu Edgy. 

I used to be able to use vncviewer to connect to vncservers on other machines and have all my keypresses go to the server. Lately, all my vncviewers (xvnc4viewer, xtightvncviewer, xrealvncviewer) have the behavior of ignoring the CTRL or ALT modifier. I hit Ctrl-p to go up a line, and it inserts a "p". This makes it impossible for me to edit -- I use control characters for everything (emacs user...). 

Does anyone know why this is happening? I've searched in GNOME settings for anything, but to no avail. 

Please help!

---

### Post by r_stevenz on 2007-12-17
I just ran into this exact same problem.  

In my case, it turns out that the locate pointer option was enabled in Gnome, and this was intercepting my control-key presses before they reached vnc.

I fixed the problem by changing /desktop/gnome/peripherals/mouse/locate_pointer to the OFF status using the Configuration Editor.

---

### Post by pvravi on 2007-12-17
> **jcrockett70 said:**
> I currently run Gnome environment on Ubuntu Edgy. 

I used to be able to use vncviewer to connect to vncservers on other machines and have all my keypresses go to the server. Lately, all my vncviewers (xvnc4viewer, xtightvncviewer, xrealvncviewer) have the behavior of ignoring the CTRL or ALT modifier. I hit Ctrl-p to go up a line, and it inserts a "p". This makes it impossible for me to edit -- I use control characters for everything (emacs user...). 

Does anyone know why this is happening? I've searched in GNOME settings for anything, but to no avail. 

Please help!

Same problem. Locate pointer is false. (Don't think this is a problem anyway, but..).

I use Gutsy, and connect to Solaris through VNC. Ctrl is very important to me and although sequences such as Ctrl-C work, holding the Ctrl button to select multiple items does not work. 

Appreciate any help

---

### Post by agibby5 on 2008-06-04
Don't mean to resurrect the dead, but this functionality is of great importance to me as well.  Any ideas?

---

