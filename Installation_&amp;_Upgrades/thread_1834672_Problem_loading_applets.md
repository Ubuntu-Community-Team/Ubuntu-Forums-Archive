---
title: "Problem loading applets"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by dayers on 2011-08-27
I installed latest 10.4 LTS as a guest OS in Windows 7 VMware. When the new OS boots it complains that Panel had problems loading, "OAFIIS: Gnome_FastUserSwitch applet." Also same error for Gnome_IndicatorApplet.

I'm given option of deleting the applets, which I declined,

I see the same problem described in earlier Ubuntu versions, but the "fixes" don't seem to work for me.

The only symptom that I've noticed as an apparent result from the error is that right-clicking on panel does not allow adding to the panel.

Help would be appreciated.

Dave

---

### Post by Hakunka-Matata on 2011-08-27
The panels not loading correctly are a recurring issue, issue these commands to get the default panel back.

```
[INDENT]gconftool-2 --shutdown
 rm -rf ~/.gconf/apps/panel
 pkill gnome-panel
[/INDENT]
```
Caveat, I don't use Wubi installs, so I'm not sure this will work.

---

