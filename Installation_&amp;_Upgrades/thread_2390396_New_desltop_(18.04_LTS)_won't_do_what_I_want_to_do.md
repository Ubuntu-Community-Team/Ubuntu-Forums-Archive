---
title: "New desltop (18.04 LTS) won't do what I want to do"
date: 2018-04-28
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2018-04-28
Problems:

1. One one of my most-used program is PDFStudioPro12 (the equivalent of Adobe Acrobat Pro DC for Windows 10).  I want to keep it as a favorite, and I want it to be there on the "Show Applications" desktop.

2.  Icons seem to change from the real ones to the generic ones.

3.  There appears to be no way of getting rid of programs on "Show Applications desktop that I don't want to see.  I don't want to remove the programs, I just don't want to see them.

4.  All of this important because I need to move my secretary's PC from 16.04 to 18.04.  I don't want to waste her time (and my money) trying to solve problems that should not be there.

Please note that I am a long-time Ubuntu user and that my scientific consulting business runs on Ubuntu.

John

---

### Post by vanadium on 2018-04-29
> **cigtoxdoc said:**
> Problems:

1. One one of my most-used program is PDFStudioPro12 (the equivalent of Adobe Acrobat Pro DC for Windows 10).  I want to keep it as a favorite, and I want it to be there on the "Show Applications" desktop.

For having it as a favourite on your dash, run it, then right-click and select "Add to favourites". This is similar to how this worked in Unity.
> 
2.  Icons seem to change from the real ones to the generic ones.

Not clear what you mean with this. The application vendor should ship the correct icons and install them in the appropriate system locations. The icon must be referred to in the application´s .desktop file under /usr/share/applications.
> 
3.  There appears to be no way of getting rid of programs on "Show Applications desktop that I don't want to see.  I don't want to remove the programs, I just don't want to see them.

There is no gui way indeed. Was not there in Unity as well. I believe you may however use the older utility Alacarte to indicate programs you want to hide. Behind the scenes, that utility modifies the .desktop files to indicate they should not be shown. The same mechanism is still applicable in gnome shell.
> 
4.  All of this important because I need to move my secretary's PC from 16.04 to 18.04.  I don't want to waste her time (and my money) trying to solve problems that should not be there.

Problems are subjective. I did not hear much real problems except for the wrong icon appearing. To some extend, you have to adhere to the workflow proposed by your desktop environment, or choose another one that fits your desired workflow more. Alternatively, Linux permits you very much to build your system exactly as you want it.

---

### Post by willfoot on 2018-04-29
Yeah or leave your secretary on 16.04

---

### Post by mc4man on 2018-04-29
> 3. There appears to be no way of getting rid of programs on "Show Applications desktop that I don't want to see. I don't want to remove the programs, I just don't want to see them.
If you want some apps to not be visible then that can be done by editing that app's .desktop file. Note that the app will also not be searchable though can be started from cli or the run command (alt+F2) & still can be pinned to a dock.
Just add to the app's .desktop a line or if already there with false then change to true.
```
NoDisplay=true
```

Usually better to copy an app's .desktop to the user's ~/.local/share/applications folder & edit there without root .

---

### Post by cigtoxdoc on 2018-04-29
Thank you for your replies.

1.  PDFStudioPro12 problem was solved by creating a link to the program in /usr/local/bin

2.  The change in icons occurs with programs from Ubuntu Software, Nemo, in particular.  I have Nemo set as default file manager.  I also have it in start-up applications.

3.  I have given alacarte a brief try.  I got rid of a few icons.  Still have more work to do.

4.  The success of Ubuntu depends on increasing its user base, particularly in small business.  It should be easy to configure.

John

---

### Post by vanadium on 2018-04-29
> **cigtoxdoc said:**
> Thank you for your replies.
2.  The change in icons occurs with programs from Ubuntu Software, Nemo, in particular.  I have Nemo set as default file manager.  I also have it in start-up applications.

Are you now referring to icons in the file manager? I was understanding you referred to icons in the application menu.
> 
3.  I have given alacarte a brief try.  I got rid of a few icons.  Still have more work to do.

You may also consider removing installed software, unless there are users on the system that need the software.
> 
4.  The success of Ubuntu depends on increasing its user base, particularly in small business.  It should be easy to configure.

Small and large businesses are served with a system that can be deployed with minimal alterations. Configuration options should be limited to avoid users breaking their system and minimize help desk interference. That is exactly what Canonical tries to provide with Ubuntu.

---

### Post by ubfan1 on 2018-04-29
The Unity desktop is still available in Ubuntu 18.04.  If you don't want to change, you don't have to, just install it.

---

### Post by cigtoxdoc on 2018-04-29
Thank you very, very much for your suggestion.  Just have to remember to select lightdm for the display manager.  Going with the Unity desktop saves much grief.  John

---

### Post by cigtoxdoc on 2018-04-29
Thank you very, very much for your suggestion.  Just have to remember to select lightdm for the display manager.  Going with the Unity desktop saves much grief.  John

---

