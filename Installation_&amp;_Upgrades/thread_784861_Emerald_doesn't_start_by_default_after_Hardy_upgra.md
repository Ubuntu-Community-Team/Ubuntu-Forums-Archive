---
title: "Emerald doesn't start by default after Hardy upgrade"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by peter.marks on 2008-05-06
Since upgrading to Hardy, my desktop opens with Metacity on login rather than Emerald as it did before. I can switch to Emerald with ```
emerald --replace &
``` from a terminal window, but how do I det it back to being the default?

TIA


Peter

---

### Post by chewearn on 2008-05-07
Install CCSM (if you have done so):
```
sudo apt-get install compizconfig-settings-manager
```


Go to:
Top Panel Menu > System > Preferences > Advanced Desktop Effects Settings

Find Window decorations plug-in.  Add "emerald" in the command field.

See here for details:
[http://wiki.compiz-fusion.org/Plugins/Decoration](http://wiki.compiz-fusion.org/Plugins/Decoration)

---

### Post by peter.marks on 2008-05-07
AstalaVista,

Thanks for this. Following you suggestion, I found the default setting is to call /usr/bin/compiz-decorator. In that script file there is a setting USE_EMERALD="no". Changing this to "yes" fixes the problem, and also supports fallback if Emerald fails.

Cheers


Peter

---

