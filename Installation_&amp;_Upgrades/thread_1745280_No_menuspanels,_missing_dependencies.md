---
title: "No menus/panels, missing dependencies"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by cosmic_cow on 2011-04-30
Hey guys,
I've got a bit of a problem. My laptop crashed while updating from 10.10 to 11.04. When I tried booting, it brought my straight to a prompt. I ran dpkg -a or whatever it is to finish the installation. When it booted, it said Unity wasn't compatible with my hardware (nVidia 260GTM with 1GB RAM). I tried using the 'killall Xorg' trick I've seen, to no avail. So I ran that command again and set my login pref to Ubuntu Classic. Still didn't help. If I right-click on my desktop, the only options I get are "Create Folder/Launcher...Document, Organize Desktop by Name, Keep Aligned, Past, and Change Desktop Background.' 'Create Launcher...' does nothing. If I try manually launch gnome-panel from terminal, it says it doesn't exist. I saw one suggestion to remove then reinstall ubuntu-desktop, that didn't work because it said ubuntu-desktop isn't there. I saw a suggestion to try removing gnome configs, that didn't work. That also removed my wifi settings, and now I'm having trouble getting connected, so I can't try just apt-get update or upgrade. 
I suspect I have some dependencies that got trashed in the crash. (I like the flow of the sentence, even if it is unfortunate.)
Please, please help. I really don't want to have to wipe everything out and reinstall.
Thanks,
Colin

---

