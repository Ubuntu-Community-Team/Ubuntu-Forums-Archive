---
title: "Can't auto-maximize windows in 16.04"
date: 2017-04-13
forum: Installation &amp; Upgrades
---

### Post by ruberad on 2017-04-13
Upgraded 14.04-->16.04 (reinstalled actually), and I lost my ability to maximize or half-maximize windows by banging the title bar against the left or right or top edges of the screen. (I can still, however, double-click on the title-bar to full-screen maximize)

Is there a setting somewhere I can turn that back on?

FWIW, my installation procedure was 'do something else' so I could reformat and install onto an OS-only partition, and not touch my /data and /home partitions, but mount them back up after I was done. So my entire home directory is untouched, there might be settings in there that are causing conflict. Any ideas about what I might delete/clean out?

---

### Post by llightsey-gmail on 2017-04-13
Try the Unity Tweak Tool --> Select Window Snapping and make sure its ' On ', Under Behaviour, set it how you would it to maximize.
I don't really understand your second question?

---

### Post by ruberad on 2017-04-14
second question was basically whether I am having this problem because after installing 16.04 I still have my home directory unchanged with all dot-subdirectories full of history/config etc.

---

### Post by ruberad on 2017-04-14
OK, after accidentally first downloading the GNome Tweak tool, I found the Unity Tweak Tool and turned on snapping.

I don't recall having to do anything special to activate snapping in 14.04, wasn't (isn't) that a native capability?

---

### Post by deadflowr on 2017-04-14
It's part of the compiz plugin known as grid.
You can adjust it a little more in the compizconfig-settings-manager, or ccsm.
(Would need to be installed)

> second question was basically whether I am having this problem because after installing 16.04 I still have my home directory unchanged with all dot-subdirectories full of history/config etc.
Of course it would be possible.
Was it the cause is unknown.

---

