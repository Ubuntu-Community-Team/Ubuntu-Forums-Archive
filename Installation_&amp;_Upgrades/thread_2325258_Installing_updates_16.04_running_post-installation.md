---
title: "Installing updates 16.04 running post-installation trigger dpkg-exec seems frozen"
date: 2016-05-20
forum: Installation &amp; Upgrades
---

### Post by moot2 on 2016-05-20
I have been using the new 16.04 (from fresh install) and has been working. I decided to do the updates because while I was trying to get the wireless-info (trying to fix wireless issue).

So now Software Installer window shows Installing updates..., the progress bar is 100%, Running post-installation trigger dpkg-exec
The Details drop-down does not work...
The spinner is on the screen...
The display will dim and turn off at the set times... turns on when mouse is moved...
I can open other apps/programs...

Is there a terminal command or utility I can run to see if anything is going on with dpkg-exec? i.e., disk i/o's, cpu usage by app/process

So I ended up doing a reboot. When the Desktop came back up I went to Terminal and ran the sudo get-app, then sudo get-app dist-upgrade which completed without error. I then did a reboot.

-----------------------------------------------------------------------------------------
You can lead a horse to water... but you can't make 'em think

---

