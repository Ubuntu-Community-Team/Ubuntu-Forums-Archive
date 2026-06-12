---
title: "Deluge installs but won't run"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by patik on 2007-09-09
I've gotten Deluge to run just fine in the past (0.1, 0.2, etc). At some point it stopped working -- it installs just fine (both through apt-get and the .deb from their website) but it won't start up. When I click on the link in the Applications menu, I see "Starting Deluge..." show up on my window bar (just like when most programs are starting to run) but then it disappears; if I alt-F2 "deluge", nothing happens. I've tried uninstalling and reinstalling to no avail. Any ideas?

I'm running Feisty with Gnome.

---

### Post by tripokey on 2007-09-09
[LIST=1]
[*]Start the terminal.
[*]Type: cd .config
[*]Type: rm -r deluge 
[*]done
[/LIST]

---

### Post by patik on 2007-09-09
> **tripokey said:**
> [LIST=1]
[*]Start the terminal.
[*]Type: cd .config
[*]Type: rm -r deluge 
[*]done
[/LIST]
Thanks, but it's still not working. I uninstalled it, then apt-get autoclean, deleted that directory, rebooted for good measure, then installed again. It still shows on the window bar for about 5 seconds before disappearing. This time I kept System Monitor open and I saw the process "deluge" appear for a couple seconds before vanishing.

Also, is it just me or is this package not in the repositories? I thought there was an older version in there.

Edit: Stupid me, I should be asking in the Deluge forums...

---

