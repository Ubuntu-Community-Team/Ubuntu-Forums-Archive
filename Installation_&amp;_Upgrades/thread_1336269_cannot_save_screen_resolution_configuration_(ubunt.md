---
title: "cannot save screen resolution configuration (ubuntu 9.10)"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by y10linux on 2009-11-24
Hi all,

I recently upgraded to ubuntu 9.10 and have a small problem.

Every time I start the computer, screen resolution is set to 800x600.

I can change screen resolution by doing the following:

1) system ->preferences->display

A message appears saying that

> It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?2) I answer yes (by the way, I have an nvidia gforce gtx card with its proprietary driver correctly installed) and then I can change screen configuration using "nvidia xserver settings"

3) The screen resolution changes correctly but when I try to save the changes I made in 

/etc/X11/xorg.conf

I get the following message 

> Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'.I thought this might have to do with me not having permission and tried to "sudo" the whole process. I opened a terminal, erased the old backup file, changed the name of the current file to .backup and then created a new file with the new configuration  ("nvidia xserver settings" allows you to preview it).

Unfortunately, once I restart the computer the screen is wrong again. More specifically, the resolution looks correct untill I enter my user name and password, and then it changes to 800x600.

Edit: I also tried this:

[http://ubuntuforums.org/showthread.php?t=1321327](http://ubuntuforums.org/showthread.php?t=1321327)

I followed the instructions with just a "minor" problem, after : 

> cd /etc/X11 && sudo mv xorg.conf xorg.conf.backup && sudo nvidia-xconfig


I got this output:

> WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'


Here I got no error messages when saving files, but still the resolution is wrong when I restart the computer.

Any ideas?

---

### Post by ktsteel on 2009-11-24
Following your post I have the same issue and tried all the same fixes. I had this box on a different monitor when setting up the system and now switched to a dell LCD monitor and this issue appeared.

---

