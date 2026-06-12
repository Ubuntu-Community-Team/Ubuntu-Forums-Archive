---
title: "Can't get past &quot;Welcome to your new Ubuntu system!&quot;"
date: 2004-12-11
forum: Installation &amp; Upgrades
---

### Post by marc_ on 2004-12-11
I have just installed Ubuntu onto a free partion on my Dell machine.  It installs fine, but when I reboot and try to run it for the first time, I get to a screen that says:
"Welcome to your new Ubuntu system!  This program will now walk you through the process of setting up your newly installed system." etc.  

There is a little red Ok 'button' below the text, but when I press Enter or space, I just get a cursor at the bottom of the screen, like it's just a text editor.  I can boot in 'recovery' mode and get the shell prompt, but then don't know what to do!

Has anyone seen this before?

The machine is:
Dell 2.8Ghz intel pentium 4
1 Gb ram
Radeon 300x 128mb graphics card
80 Gb hard drive (12 Gb for the Ubuntu partition, 0.5Gb for swap partition)
USB mouse
USB keyboard


Thanks

---

### Post by az on 2004-12-11
From recovery mode, try:
sudo apt-get -f install

---

### Post by orphennui on 2004-12-17
This doesn't work for me.  Apt-get just prints:

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by SurreaL on 2005-02-10
This is exactly what just happened to me.. I had set up a partition on my workstation at work to try installing ubuntu on (along w/ a Swap partition), and went through the install process. I got the same thing.. install was ok, then reboot, then I get to a ""Welcome to your new Ubuntu system!" screen, but as soon as I press enter it just shifts the screen up, just like the 'usual' behaviour of pressing enter on a console.. This is very annoying, as now my WinXP will not boot either, so I basically have a dead workstation :/

Fortunately there isn't THAT much important stuff on the workstation HD.. so I wouldn't have problems with just trying the install again and wiping the drive completely clean, but I don't think this particular issue is related to a partitioning or dual booting issue.. It seems to be a problem w/ NCurses (Is that what it's called?) Or whatever the system configuration menu program is..

Any other ideas?

---

