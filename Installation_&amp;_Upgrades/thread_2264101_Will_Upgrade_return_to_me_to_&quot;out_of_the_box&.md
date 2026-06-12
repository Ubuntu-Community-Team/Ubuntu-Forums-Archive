---
title: "Will Upgrade return to me to &quot;out of the box&quot;"
date: 2015-02-05
forum: Installation &amp; Upgrades
---

### Post by danjswade on 2015-02-05
Ok, title probably says it all. If I upgrade my current 14.04 to 14.10, will that remove the packages I've currently installed (like xampp primarily)? Does it essentially hit reset and you start afresh and have to reinstall packages? Will it also delete my personal files such as pictures, music etc.

---

### Post by ian-weisser on 2015-02-05
> **danjswade said:**
> If I upgrade my current 14.04 to 14.10, will that remove the packages I've currently installed (like xampp primarily)?
No. It will, however, upgrade xampp (and everything else) to a newer version.

 > **danjswade said:**
> Does it essentially hit reset and you start afresh and have to reinstall packages?
No. A release-upgrade is not a reinstall.

 > **danjswade said:**
> Will it also delete my personal files such as pictures, music etc.
No. Even a reinstall will _try_ to preserve your /home dir. It may not succeed. The user may have made /home impossible to preserve (by damage, formatting, renaming, etc.)
Always backup your data before a reinstall or a release-upgrade. After all, it's your stuff.

---

### Post by danjswade on 2015-02-05
Cool, thanks for that!

So a reinstall WOULD delete everything (except for /home dir) but an upgrade will do just that, upgrade stuff?

---

### Post by grahammechanical on 2015-02-05
> [COLOR=#000000](except for /home dir)[/COLOR]

I do not agree with that. A re-install will act like a new install and format the partition if we tick the box "Format the partition" To re-install we 

1) use the Something Else option.
2) we select the partition and click "Change."
3) we fill in the dialog box
a) change "Use as" to Ext4
b) do not tick the box "Format the partition." I repeat. We do not tick the box "Format the partition."
c) select the mount point as /
d) be sure in our own mind that the default location (sda) for the installation of the boot loader is the loacation we want.
e) click "OK."

If we format the partition we will loose everything in /home. This is one of those matters that only become obvious after we have made the mistake. I am speaking from experience.

Regards.

---

### Post by danjswade on 2015-02-05
Ok, so a reinstall will (unless stated otherwise) wipe EVERYTHING! Got it.

I made another post ([http://ubuntuforums.org/showthread.php?t=2262948](http://ubuntuforums.org/showthread.php?t=2262948)) about changing the gdm after tinkering with Gnome. As my gdm seems to be broken, would an upgrade fix this or would I need a reinstall?

---

### Post by ian-weisser on 2015-02-05
> **danjswade said:**
> Ok, so a reinstall will (unless stated otherwise) wipe EVERYTHING! Got it.

That's NOT what grahammechanical wrote.
He was clear about _how_ to get a reinstall to wipe everything...and how some users do it by mistake.

---

### Post by danjswade on 2015-02-05
Ah ok, sorry for misunderstanding. Thanks for clarifying

---

### Post by craig10x on 2015-02-05
If you select the automatic option on the iso's install list to remove your current system and install the new one, it will wipe clean the entire drive and then install everything fresh....nothing will be saved from your current install...
So, if that's what you would prefer to do, then that would be the best way to do it...

---

