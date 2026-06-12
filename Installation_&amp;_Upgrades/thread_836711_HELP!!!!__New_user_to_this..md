---
title: "HELP!!!!  New user to this."
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by limsungbae on 2008-06-21
hi,  i am brand spanking new to linux.  i need help to install drivers and programs that i frequently use.  i've tried to double-click and right-click all over the place but no joy.  the programs are things like wireless card from linksys, nero, gom player, etc.  i'm a windows user at work and have never worked with linux until now.  can anyone help?

---

### Post by cpetercarter on 2008-06-21
Installing programmes in Linux is quitedifferent from Windows. Start by reading this :
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by ad_267 on 2008-06-21
Nero has a Linux version but why would you want it when you have Brasero by default in Ubuntu? For most applications you use in Windows you can find a suitable alternative. Go to Applications - Add/Remove and search for what you want. I'm not sure what gom player is but there should be something similar. If you find you need something only available for windows you will have to install it using WINE.

---

### Post by limsungbae on 2008-06-21
what is wine?  and thanks guys for the help.  i know there a lot of things out there to do to the OS to make it very personnal.  where could i go do that?  isn't there a thing that i can do like 3 different desktops?  and how do i mess with that part of it?

---

### Post by ad_267 on 2008-06-21
For the three different desktops thing I think you're thinking of workspaces. If you're using default Ubuntu there should be a workspace switcher in the bottom right corner. You can click on different workspaces to change. You can right click on it and select preferences to change the number of workspaces (I think you can have as many as you want).

This explains what wine is: [http://www.winehq.org/](http://www.winehq.org/)
You can install it from Add/Remove programs or from System - Administration - Synaptic Package manager.
I have found that I don't need wine at all as every application I need is available for Ubuntu/Linux.

This explains some of the ways you can customize your desktop: [http://justanothertechblog.blogspot.com/2007/03/quick-guide-on-customizing-ubuntu.html](http://justanothertechblog.blogspot.com/2007/03/quick-guide-on-customizing-ubuntu.html)
Also have a look at this thread: [http://ubuntuforums.org/showthread.php?t=812943](http://ubuntuforums.org/showthread.php?t=812943)

If you want to customize with more advanced desktop effects have a look here: [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by cpetercarter on 2008-06-21
Wine is a programme which allows you to run some Windows programmes more or less successfully in Linux. You can download and install it using Synaptic Package Manager. Details of what it can do are at [http://www.winehq.org/]("http://www.winehq.org/")
Seriously, though, it is best to start with the simple stuff - downloading a few native Linux programmes and trying them out, navigating round the files on your computer with Nautilus, learning about the mysterious "sudo" thing, trying some simple stuff in the terminal. Just don't expect that Linux is like Windows - it does a lot of things differently. Good luck.

---

### Post by pietjanjaap on 2008-06-22
Read more the things you are asking are all written down.
search forums, ubuntu howto sites etc.
You need to read a lot in the beginning.

[http://computertip.googlepages.com/ubuntulinux](http://computertip.googlepages.com/ubuntulinux)
[http://onlyubuntu.blogspot.com/](http://onlyubuntu.blogspot.com/)
[http://www.ubuntu-unleashed.com/](http://www.ubuntu-unleashed.com/)
[http://www.ubuntu1501.com/](http://www.ubuntu1501.com/)
[http://www.tuxmachines.org/](http://www.tuxmachines.org/)
[http://polishlinux.org/howtos/truecrypt-howto/](http://polishlinux.org/howtos/truecrypt-howto/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
[http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/)
[http://www.ubuntux.org/](http://www.ubuntux.org/)
[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)




[http://www.linuxalt.com/](http://www.linuxalt.com/)
[http://www.openinhoud.nl/zoeken](http://www.openinhoud.nl/zoeken)
[http://www.osalt.com/](http://www.osalt.com/)
[http://linuxappfinder.com/alternatives?page=1](http://linuxappfinder.com/alternatives?page=1)

the best:
[http://damen.dommel.be/Ubuntu.html](http://damen.dommel.be/Ubuntu.html)

the gimp     -   very good photoshop
gfslicer     -  splitter joiner
Q7z+7z       -   archiver
hellanzb- downloaden nzb van usenet
kget - download program
Inkscape Vector Graphics Editor
Klibido- to look in usenet groups and nzb download
dvdfab in wine- the only thing i can't find in linux.

---

### Post by limsungbae on 2008-06-23
alright now i have a problem.  i am new but in System-Preferences-theme?

there is no theme?

what's up with that?

---

### Post by oldos2er on 2008-06-23
I think you're looking for System, Preferences, Appearance, Theme.

---

### Post by ad_267 on 2008-06-23
> **limsungbae said:**
> alright now i have a problem.  i am new but in System-Preferences-theme?

there is no theme?

what's up with that?

Do you mean System - Preferences - Appearance?

There should be quite a few themes listed there. You can also install themes from [http://www.gnome-look.org](http://www.gnome-look.org). Does everything look ok normally. Do you have window borders and the applications don't look ugly?

Edit: Oh I thought you meant there were no themes listed. Yeah go to System - Preferences - Appearance.

---

### Post by limsungbae on 2008-06-24
alright, got some things figured out but...
1.  can't make the cube thing for the desktop.  not in the theme or appearance thing.
2.  it's not recognizing the HD i put in here for storage.  i have a lot of music and stuff.  what's up with that?

---

### Post by ad_267 on 2008-06-24
> **limsungbae said:**
> alright, got some things figured out but...
1.  can't make the cube thing for the desktop.  not in the theme or appearance thing.
2.  it's not recognizing the HD i put in here for storage.  i have a lot of music and stuff.  what's up with that?

1. Please do some research. It's all explained here: [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695) and in many other places.
2. Is this an external drive or what? Did you give it a mount point when you installed Ubuntu? Can you post the output of "sudo fdisk -l"

---

