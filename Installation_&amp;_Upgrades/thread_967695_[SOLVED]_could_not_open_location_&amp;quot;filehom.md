---
title: "[SOLVED] could not open location &amp;quot;file:///home/username"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by swells5 on 2008-11-02
after upgrading to intrepid ibex when I click Places>Home Folder I get the following error message.
"Failed to execute child process "avscan" (No such file or directory)"

prior to upgrading to 8.10 clean install - I created a new partition for my home folder using the instructions at
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

In 8.04 I had clamav and avscan installed.
My home folder is accessible via the command line.
I also have a shortcut on my Desktop that opens the home folder without problem - the properties of the shortcut are simply name=home command= nautilus location=/home/username/Desktop

apt does not find avscan in 8.10 and from googling it sounds like avscan should not be installed in 8.10.

all of the links on the Places menu from >home to > videos give the same error message - from >computer down the rest of the links work normally.
I have removed all references to avscan and endeavour2 including hidden files from my computer, installed and uninstall clamav and still have the problem.

Thank you for any ideas
Steve

---

### Post by swells5 on 2008-11-02
i have found one more reference to avscan in the home/username/.local file and removed that file and now everything works without problems.
Steve

---

