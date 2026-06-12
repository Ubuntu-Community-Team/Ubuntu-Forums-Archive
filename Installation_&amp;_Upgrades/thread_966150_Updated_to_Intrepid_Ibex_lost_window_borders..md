---
title: "Updated to Intrepid Ibex lost window borders."
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Iztari on 2008-11-01
I just updated my ubuntu hardy heron to intrepid, and after restarting the computer I lost window borders/decorations. The only way to get them back up is deactivating the special effects. I've tried using the nvidia 177 and 173 restricted drivers and neither works. I also tried reinstalling compiz.

Thanks in advance.

---

### Post by denham2010 on 2008-11-01
When your system starts up, try the following.

Press ALT+F2 and enter:

```
emerald --replace

(replace emerald with the window decorator you have selected to use)
```


If this brings your window borders back, it appears that compiz is no longer starting your window decorator when it is loaded.

If this is the case, start CompizConfig Settings Manager and go to the Window Decoration plugin.

Ensure the command for starting your window decorator is present and the plugin is activated.

If they are already set, you may just need to force a reset of them (sometimes during an upgrade some settings can be lost but the configuration shows they are still there). To do this, remove the command and disable the plugin. Restart your system then reactivate the plugin and enter the command again.

All going well, when you restart again, your window borders should be present again.

Cheers.

---

### Post by Iztari on 2008-11-01
Thanks, the command wasn't set in compiz config. It works perfectly now.

---

