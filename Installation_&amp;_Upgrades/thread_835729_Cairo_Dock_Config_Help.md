---
title: "Cairo Dock Config Help"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by SammerHammer on 2008-06-20
Hello all, I am relatively new to Ubuntu -and Linux- and have installed Cairo Dock (1.5.6) recently. The only problem is, in the Configurations, for the Keyboard combination feature, I typed in <Control>hide. Now Cairo Dock won't show on my screen even if I type Ctrl+hide. I have tried uninstalling and reinstalling many times, but it still won't show. In the end, I think I can fix the problem if I can **completely** -configuration files and all- remove C.D from my computer and re-install. If that's not possible, where can I find the original configuration files for it so that I can replace my current ones with the originals.

Any help is appreciated,
Sam

---

### Post by onero on 2008-06-23
> **SammerHammer said:**
> Hello all, I am relatively new to Ubuntu -and Linux- and have installed Cairo Dock (1.5.6) recently. The only problem is, in the Configurations, for the Keyboard combination feature, I typed in <Control>hide. Now Cairo Dock won't show on my screen even if I type Ctrl+hide. I have tried uninstalling and reinstalling many times, but it still won't show. In the end, I think I can fix the problem if I can **completely** -configuration files and all- remove C.D from my computer and re-install. If that's not possible, where can I find the original configuration files for it so that I can replace my current ones with the originals.

Any help is appreciated,
Sam

Just delete the .cairo-dock folder in your home directory; that should reset the configuration. Then just kill and relaunch cairo-dock, and the Themes dialog should show up. :)

---

### Post by fabounet on 2008-06-24
that's a bit excessive ^_^
type "cairo-dock --maintenance" in a terminal, and remove the shortcut you added.
<Control>hide is not a valid shortcut I think, did you use the "grab" button ?

---

