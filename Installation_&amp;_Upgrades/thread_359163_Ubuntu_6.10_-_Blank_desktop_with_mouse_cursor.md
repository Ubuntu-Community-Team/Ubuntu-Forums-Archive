---
title: "Ubuntu 6.10 - Blank desktop with mouse cursor"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by drknow on 2007-02-11
Hi i really hope that someone can help.

When i try to start GDM it comes up like it is suppose to. But when i enter my username and password, and gnome is suppose to boot it just shows me a blank desktop. And after a while a grey box appears - nothing else.

I have made a screenshot of what i looks like [here]("http://www.doop.dk/log/screenshot.jpg"): 

If i try to start the Gnome Failsafe it is the same thing. But if i try with a failsafe terminal the terminal comes up ok.

Right now i cant use my system for anything, and would really like some help.

I have a Intel d845GVSR motherboard, and are using the i810 driver module for X.

Files:
[xorg.conf]("http://www.doop.dk/log/xorg.conf")
[gdm log]("http://www.doop.dk/log/gdm.0.log")
[lspci]("http://www.doop.dk/log/lspci") 
[xorg log]("http://www.doop.dk/log/Xorg.0.log") 
[xsession-errors]("http://www.doop.dk/log/xsession-errors")

---

### Post by GrumpySmurf on 2007-02-14
I am having this exact same problem. 

Last night, gnome-terminal wasn't displaying anything in the window. The title bar would draw, the window borders would draw, but no contents. 

I was rebooting anyway to check something out in Windows first, then when Ubuntu started up, the problem you describe happened. This is driving me nuts. I can't get anything GNOME to display. I can start up Fluxbox or Window Maker window managers, but gnome-panel, terminal and others won't display at all, or display only the window title bar.

---

### Post by GrumpySmurf on 2007-02-14
After digging through more of the forums here, I cam across [this post](http://www.ubuntuforums.org/showthread.php?t=357121). Something that he said triggered my memory.

[quote="John E"]The last update I did was yesterday morning when I did apt-get install alsa-tools-gui ...[/quote]

I too had installed alsa-tools-gui prior to the problem on my system. I deleted that package (--purge with extreme prejudice!), removed all the gconf and orbit files in /tmp, and tried to log in via GDM again.

Success!

Except - my sound no longer works. Now I have a nice long rant in store for ALSA. I hates me some ALSA. Sound on Linux in general. Its almost as bad as Wireless.

---

### Post by drknow on 2007-02-15
It worked for me aswell, ALSA was the problem. 

But it is a bit booring wathing movies on a comp. with no sound :guitar:

---

### Post by GrumpySmurf on 2007-02-18
Well, I do not seem to have actually resolved the problem on my end. I'm not sure what the issue is at this point. I'm still having the blank desktop when logging in with GNOME. Enlightenment, Fluxbox and Window Maker all start properly. Even with a fully cleaned out home directory, root can't even log in, so its not a permission issue.

I'm thinking a bug report should be filed on this one. Or, I'll at least look at the bugtraq for 6.10 and see what is going on here.

---

