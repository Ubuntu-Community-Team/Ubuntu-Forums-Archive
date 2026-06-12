---
title: "Package Manager Crashes"
date: 2012-01-01
forum: Installation &amp; Upgrades
---

### Post by amira-uk on 2012-01-01
Little bit of background:

Installed Kubuntu 11.04 on my netbook, booted up, loaded package manager to do updates (using an ethernet connection), after a while I realized the package manager had frozen so turned the machine off. Rebooted and now have an error message on boot and another error after KDE loads.

It says "Warning: Cannot open ConsoleKit session: Unable to open session: The permission of the setuid helper is not correct" before KDE loads and then says "The audio playback device HDA Intel (ALC269 Analog) does not work. Falling back to." when KDE loads up.

Installed Kubuntu 11.04 on my PC, booted up, loaded package manager for updates (on wireless) exactly the same thing happened as above and after rebooting the wireless was unavailable and I couldn't get it to come back (not that I really understand what I'm doing.) The error message relating to the audio is a different code on the PC, presumably as its different hardware.

Thought never mind, burned 11.10 and have now installed that on my PC however the Muon package manager has now been stuck on "Running dpkg" for half an hour to an hour and I'm getting annoyed because this will be the same problem for the third time in 2 days.

I ran Kubuntu 11.04 and then 11.10 on my netbook for about 6 months before I had to reinstall, I've had multiple problems but never with the package manager so I'm at a loss as to why this has all started and what to do with it. I'm going to ;leave the PC on overnight as its bed time for me now but I don't think its going to sort itself out but if I reboot it will probably mess up like it has the last two times.

Does anyone have any ideas or info about this please, I've googled but can't seem to find what I need.


Just to add, I've just clicked on the start menu (for want of a better name) and when I click on Applications all I now get offered is System, under which there isn't anything. Then loaded Dolphin and there are no folders showing up in any of the directories either.

---

### Post by inobe on 2012-01-01
try running the updates from terminal.

```
sudo apt-get update
```

and 

```
sudo apt-get upgrade
```

you should then see an update description, type **y** and press enter to proceed.

after that update, you should not have a problem using muon package manager.

---

### Post by amira-uk on 2012-01-04
Sorry for the late reply, only just got around to trying to sort it out. Thanks very much, it seems to have worked fine. Its been nearly 10 years since I last attempted to use Linux so what little I did learn back then is all forgotten ;)

---

### Post by bluexrider on 2012-01-04
I would recommend not turning the computer off during the session. 

If you need to kill a program try Alt+F2 type xkill and direct you mouse to the app and click-to-kill.

You can also Ctrl+Alt+Backspace to kill the session then log back in.

---

