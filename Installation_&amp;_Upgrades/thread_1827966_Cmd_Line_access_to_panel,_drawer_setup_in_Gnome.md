---
title: "Cmd Line access to panel, drawer setup in Gnome"
date: 2011-08-18
forum: Installation &amp; Upgrades
---

### Post by m.dr on 2011-08-18
hi -

I am looking for a way to programmatically (Python or shell) set up my  panels, drawers, app launchers and stuff.

Just wondering if there is a way to do that - or a standard approach to it and such.

Am using Gnome - the regular install - no extra components or such.

Would it be easier to do it if I was using Gnome 3. Just putting the question out there in case someone is using Gnome 3 and it would be easier to do the automated setup in Gnome 3.

Thanks for your help.

---

### Post by sanderd17 on 2011-08-18
In Gnome-Shell, the layout of everything is done via JavaScript and CSS. So with JavaScript you can do everything, but it might take a little time to think about good code. You can also hack it like you would hack a website with greasemonkey.

In Gnome 2, I would take a look at the gconf-tool, but I don't know if that tool provides access to the placement of the applets.

---

### Post by m.dr on 2011-08-18
Thanks Sanderd.

Is there way to know which files are set by the JavaScript and CSS for the display panels?

I will look at the gconf-tools - however would be great if I could directly access the files and change them programmatically to add my drawers and app  links.

I am trying to write a Python script to do my setup.

---

### Post by sanderd17 on 2011-08-18
For GS, you should best create an extension: [http://live.gnome.org/GnomeShell/Extensions](http://live.gnome.org/GnomeShell/Extensions) , I'm not an extension developer myself, but I guess it's explained quite well. Many of the extensions around are adding or removing what used to be called "applets".

For G2, there is a CLI to gconf: [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/). But gconf is a real mess and the support will stop rather fast.

---

### Post by m.dr on 2011-08-18
Thanks Sanderd. Will check it out. 
Let me see if I can get it to work.

Regards.

---

