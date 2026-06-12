---
title: "Applications inaccessible"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by eunix1 on 2011-06-29
:confused:   One hundred and two applications inaccessible via 11.04 on Dell Inspiron 1525 running Gnome 2.32.1.
There is a fault with the way the GUI works on my machine does anyone have a work-arround please.

---

### Post by dabl on 2011-06-29
> **eunix1 said:**
>   One hundred and two applications inaccessible

What does this "inaccessible" mean?  Where are you getting that information, and what would be some examples of the inaccessible packages?

---

### Post by eunix1 on 2011-06-29
Thanks for your reply dabl.

At the left of the screen (laptop) there is an icon for applications (amongst others). clicking on this icon brings up a window: 'Most frequently used', 'Installed (see 117 more results)' and 'Apps available for download'.
5 icons are displayed for each section.  Clicking on the '(see 117 more results)' brings up 10 more icons to fill the screen.  'About me' to 'CD creator'.
There is no way to scroll down the screen to display the majority of the installed apps.  It looks like the window is not locked to the left of the screen although the sidebar is visible in shadow.
I much prefer 'pull-down menues' ala 10.10 - old fashioned I know but I'm alowed because I'm ancient ;)

---

### Post by dabl on 2011-06-29
OK, no problem, I'm fairly ancient myself.  :)

I'm a KDE desktop user, not a Gnome desktop user, so I don't know all the particulars of your laptop display with Ubuntu.  However, let me offer you this encouragement:

You have a graphical viewer with which to view your installed and available software packages -- it is called "Synaptic".  If you do Alt-F2 "gksudo synaptic" you will be able to start it.  With this viewer, you can see all the packages in the Ubuntu repositories, including which ones are installed on your system.  If you want additional packages, just check them and the "Apply" the changes, and they will be installed.

---

### Post by eunix1 on 2011-06-30
Thanks for that.  I used the 'Synaptic package manager' to re-install Gnome.  Your suggestion of using 'Alt-F2' ...... would be fine if the search function worked - it does not.  I think that is part of the problem with the 'Applications' window.  I'm not a coder but I think that there is a bug in the display functions, Gnome or other.  I hav'nt replaced X11 as the other display functions work fine.
Do you think I should report this as a bug even though it hasn't generated an error report?:confused:  
If you can believe it, this is the first problem I've had with Linux that was not either my fault (operator finger trouble) or my hardware.  At the moment this version is just too flaky to install on my desktop.  I am amazed that no-one else has a similar problem - the display is fine except for the 'Applications' and 'Files and folders' windows.

---

