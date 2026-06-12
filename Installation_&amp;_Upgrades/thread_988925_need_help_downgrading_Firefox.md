---
title: "need help downgrading Firefox"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by akahige on 2008-11-21
Running Hardy on amd64. After upgrading to Firefox 3.0.4, the browser is chewing so much of my available CPU cycles that the desktop keeps freezing. (CPU only; not memory or swap.) I'd like to try dropping back to the previous version (3.0.3) to see if that fixes the problem -- but I haven't been able to figure out how.

Remarkably, it doesn't seem to have anything to do with Flash, since I killed npviewer.bin and it had no effect.

Can anyone help me out here...?

---

### Post by frankleeee on 2008-11-21
> **akahige said:**
> Running Hardy on amd64. After upgrading to Firefox 3.0.4, the browser is chewing so much of my available CPU cycles that the desktop keeps freezing. (CPU only; not memory or swap.) I'd like to try dropping back to the previous version (3.0.3) to see if that fixes the problem -- but I haven't been able to figure out how.

Remarkably, it doesn't seem to have anything to do with Flash, since I killed npviewer.bin and it had no effect.

Can anyone help me out here...?

I think you can do a force to the previous in synaptic. Yes just look up FF have package open preferences-general-tick package properties in main window click on FF3 and click on packages then force.

---

### Post by akahige on 2008-11-21
There is an option for "force version" in Synaptic -- but the only available options are the current version, and the original 3.0-b5 package. None of the intervening releases are listed.

Is there another repo (that I could add) that might have them?

---

### Post by cariboo on 2008-11-21
Instead of trying to down grade, have you tried creating a new profile to see if that will make any difference. If you keep the same profile while downgrading you may run into the same problem. The profile is located in ~/.mozilla, it is a hidden directory. To view the hidden files nad directories, open PLaces-->Home Folder and press Ctrl-h.

Jim

---

### Post by frankleeee on 2008-11-21
> **akahige said:**
> There is an option for "force version" in Synaptic -- but the only available options are the current version, and the original 3.0-b5 package. None of the intervening releases are listed.

Is there another repo (that I could add) that might have them? Did you tick the preferences-general show package properties in main window so that you see below the package lists 5 choices description, common, dependencies, installed files versions. On my 3 computers if versions is ticked it shows FF 3.03 which you would click on then force. I believe it will reload it but you have to get to the preferences to expose these 5 choices below the package lists.

---

### Post by akahige on 2008-11-21
> **frankleeee said:**
> Did you tick the preferences-general show package properties in main window so that you see below the package lists 5 choices description, common, dependencies, installed files versions. On my 3 computers if versions is ticked it shows FF 3.03 which you would click on then force. I believe it will reload it but you have to get to the preferences to expose these 5 choices below the package lists.

I didn't know about the show package properties option. That's pretty cool. Thanks for the tip.

However, I'm not seeing versions different from the two that I mentioned in the earlier post.


[quote=cariboo907]Instead of trying to down grade, have you tried creating a new profile to see if that will make any difference. If you keep the same profile while downgrading you may run into the same problem.[/quote]
The new profile thing is pretty obvious -- but I have to admit, I didn't try it before posting. I haven't had any problems with profile corruption on linux, or on FF3, but you were right. It IS a profile corruption issue, so I guess I need to rebuild the thing.

Thanks!

---

