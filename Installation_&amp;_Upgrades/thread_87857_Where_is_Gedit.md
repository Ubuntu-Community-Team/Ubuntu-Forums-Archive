---
title: "Where is Gedit?"
date: 2005-11-09
forum: Installation &amp; Upgrades
---

### Post by WBC on 2005-11-09
Hi all, I am trying to set up a server but need a text editor like **Gedit** as I am in the command line mode.  I tried to run Gedit and it was not there.  I then tried to use "apt-get install gedit" but it was not found?  I am new to this distro and have about a month of experiance with Linux in general.  I set up Samba in Suse 9.3 but want to have a faster and leaner server system using Ubuntu Breezy Badger.  I have no idea how or if a GUI can be temporarily run to configure things using Ubuntu Breezy Badger?

Any help to find distro's I need would help.  :???: 

WBC

---

### Post by gruepig on 2005-11-09
You can install a GUI, but that will install a lot of packages and may take awhile to set up.

There are numerous console/terminal-based (that is, non-GUI) text editors, and I'd highly recommend getting comfortable using one of you'll be running a server.  That way you can use it for any maintenance tasks (including remotely) you'll need to perform without having all the X and gnome/kde stuff around.

Probably the two most popular editors are vi (and variants such as vim) and emacs.  However, both can be pretty time-consuming to learn.  Try nano, which is a very basic editor.  It may already be installed; if not, 'apt-get install nano'.  When you run nano (e.g., 'nano myfile.txt'), you're in the editor and can type as needed.  The bottom two lines display available commands.  The '^' character means hold down the control key and type the following letter.  When you are done editting, type 'control-X' to exit; you'll be prompted to save your changes.

Enjoy!

---

### Post by WBC on 2005-11-09
[QUOTE=gruepig]You can install a GUI, but that will install a lot of packages and may take awhile to set up.

There are numerous console/terminal-based (that is, non-GUI) text editors, and I'd highly recommend getting comfortable using one of you'll be running a server.  That way you can use it for any maintenance tasks (including remotely) you'll need to perform without having all the X and gnome/kde stuff around.

Probably the two most popular editors are vi (and variants such as vim) and emacs.  However, both can be pretty time-consuming to learn.  Try nano, which is a very basic editor.  It may already be installed; if not, 'apt-get install nano'.  When you run nano (e.g., 'nano myfile.txt'), you're in the editor and can type as needed.  The bottom two lines display available commands.  The '^' character means hold down the control key and type the following letter.  When you are done editting, type 'control-X' to exit; you'll be prompted to save your changes.

Enjoy![/QUOTE]
Hi and thanks for the help.  You would think that Ubuntu would have an editor already in there for use?  Every help file says use gedit but it is not included in the apps.  I don;t know but just by it's name I would think it is a graphical editor?

WBC

---

### Post by kvidell on 2005-11-09
It is. All of the manuals here assume the user is running their Ubuntu install as a desktop, or some other system with a graphical display.
VIM should already be installed on your system, run it with "vim".

It's my editor of choice, if you get good with it's shortcuts it's very powerful... though extremely non-intuitive at first glance.

If you just want a basic editor, that doesn't have a lot of feature-set, go with Nano.
- K

---

