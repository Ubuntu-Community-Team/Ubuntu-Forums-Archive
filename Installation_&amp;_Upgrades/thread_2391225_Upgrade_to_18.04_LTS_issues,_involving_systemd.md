---
title: "Upgrade to 18.04 LTS issues, involving systemd"
date: 2018-05-07
forum: Installation &amp; Upgrades
---

### Post by ashleydrees on 2018-05-07
I am running ESXi and trying to upgrade a file/print server from 16.x.lts to 18.x LTS and the upgrade failed. I still have a running system and have not yet rebooted it - i DID run "do-release-upgrade -d" which might be the root of my problem, so if anyone has any wise words for me, i'd be very grateful.

---

### Post by dino99 on 2018-05-07
Be sure systemd is completly installed:  sudo apt-get install --reinstall systemd udev systemd-sys
Do the same with the metapackage (ubuntu-desktop, or the one you should use) to glance at the possible missing packages

Run the sleaning scripts: clean/autoclean/autoremove
Check the sources.list, and if needed, downgrade to genuine version (via ppa-purge)
And browse the output of 'journalctl -b' to find 'warnings (bright lines) & 'errors' (red lines)

---

### Post by ashleydrees on 2018-05-07
Wish i had seen that before i forced a reboot... down to recovery shell now... have to grab a 18.04 LTS ISO and boot into recover.

---

### Post by ashleydrees on 2018-05-07
Ah well.  in the recovery shell, i do not have any desktop installed as it is an ESXi guest, it does not find [COLOR=#000000]systemd-sys only [/COLOR][COLOR=#000000]systemd-sysv but even that will not install.[/COLOR]

---

### Post by ashleydrees on 2018-05-07
Ah well, things are a lot worse now, but also better, thanks for your help, the do-release-upgrade did not seem to do much of what i expected and left me with a halfway house upgrade - my sources.list had not been updated to bionic so the whole system was still at xenial no wonder it was having issues.  Sadly i did not realise this issue quick enough... serves me right for playing mandolin whilst updating...

---

