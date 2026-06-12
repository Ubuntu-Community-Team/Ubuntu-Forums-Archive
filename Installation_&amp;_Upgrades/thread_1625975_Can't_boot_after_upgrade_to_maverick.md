---
title: "Can't boot after upgrade to maverick"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by skamarla on 2010-11-19
Hi,

I just upgraded my old laptop to Maverick, and something went wrong. The update process crashed near the end. I had to kill the window. Tried to do a dist-upgrade but nothing happened, so I rebooted. After the reboot, I got a black screen, showing "Disconnected from Plymouth", and a login prompt. But the keyboard is disabled, so I can't even log in. If I try the recovery mode, I get a menu with options to get to a command line, but the keyboard is still disabled (only Ctrl-Alt-Del works).

I already had a similar error in Lucid: the black screen with the Plymouth error showed up, but after a few seconds X started anyway and everything went fine. Now I'm stuck.

Help me please!

---

### Post by skamarla on 2010-11-19
Got it. I finally managed to ssh into the machine by booting in normal mode.

Then I did the following from [this]("http://wwww.ubuntuforums.org/showthread.php?t=1592268") thread:

sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a
sudo dpkg-reconfigure plymouth

And it finally booted.

---

