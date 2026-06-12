---
title: "Where are my installed programs?"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by m5b on 2008-02-21
Where can I find my stalled programs that do not show up on the Applications Menu? How can I put them on the Applications Menu? How can I run them when they are not on the Applications Menu?

---

### Post by Partyboi2 on 2008-02-21
To add programs to the Applications menu you need to go to system>preferences>main menu and add your program to the menu list.

---

### Post by m5b on 2008-02-22
That doesn't work. What you suggest works only to put into the Applications Menu those programs that are shown as already installed.

I have installed a number of programs that seem to have simply disappeared. I can't get to them, either to put into the Applications Menu or to run. Or to delete, for that matter.

Any ideas?

---

### Post by Ecclesia on 2008-02-22
How did you install the programs?  Did you install them via synaptic, a deb file, or source?  Have you tried typing the name of the program into the terminal (or pressing alt-F2 to bring up a run command)?

---

### Post by m5b on 2008-02-22
I install3e them via Synaptic Package Manager. When I hit Alt-F2 the programs don't show up. So far I have not been able to run the programs by typing their names, in some cases due to the fact that I don't remember their precise names, but in other cases (where I do remember) the programs still don't run.

---

### Post by Ecclesia on 2008-02-22
What programs have you installed that you're trying to run?  Most of the larger programs that are installed under synaptic place themselves into the menu, others run from the command line.  If this is a large graphical package like Banshee or The Gimp, then it's some sort of bug or it wasn't installed correctly.  If it's a command line program then you probably need to run it from the terminal and look into the man pages to figure out how to make this work.

Just list the programs and we'll go from there.

---

### Post by Arrgoss on 2008-02-22
Hi,

I have the same problem. I know that the "Configuration Editor" is installed, but I can't find it in my Applications-->System Tools menu.

EDIT:
I found it in /usr/bin, where I found out most of the applications are sitting.

---

### Post by oldos2er on 2008-02-22
In Synaptic, go to Status, Installed; right-click on a package, choose Properties, Installed Files.

---

### Post by m5b on 2008-02-24
I found most of them using a combination of Synaptic File Manager and Places/Find Files.

I could run most, but not all, from the terminal after navigating to the appropriate directory.

Is there a way, though, to manually place the programs into the Applications Menu?

---

