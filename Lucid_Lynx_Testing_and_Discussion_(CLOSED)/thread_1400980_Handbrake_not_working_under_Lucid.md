---
title: "Handbrake not working under Lucid"
date: 2010-02-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zykotick9 on 2010-02-07
HandBrake the video encoder from [http://handbrake.fr/](http://handbrake.fr/) is non-functional under Lucid Alpha 2.

HandBrake will start up fine, and can scan DVD source for titles, but issues with the interface prevent any actual encoding.

The HandBrake developers are aware of the issue, as it has been raised on Handbrake's forum at:

[http://forum.handbrake.fr/viewtopic.php?f=13&t=14879&p=71050&hilit=10.04#p71050](http://forum.handbrake.fr/viewtopic.php?f=13&t=14879&p=71050&hilit=10.04#p71050)

Just hoping someone resolves/fixes/finds-work-around to the issue soon.

---

### Post by JohnAStebbins on 2010-02-22
Fixed [http://trac.handbrake.fr/changeset/3135](http://trac.handbrake.fr/changeset/3135)

---

### Post by haydoni on 2010-02-27
I've just put on lucid alpha 3, handbrake DOES allow encoding HOWEVER the only quantifier is the "constant quality" as a percentage, I'd prefer to use total video size/bitrate but these are both blanked out/ fixed at 700MB/1500kbps respectively (they are editable/working in 9.10).

Does anyone else have this issue?

Thanks, I really like handbrake- it's so fast!

---

### Post by haydoni on 2010-02-27
This problem appears to be known as a problem with (of) Lucid.
[http://forum.handbrake.fr/viewtopic.php?f=13&t=14879](http://forum.handbrake.fr/viewtopic.php?f=13&t=14879)

The CLI version is apparently working fine.

---

### Post by zykotick9 on 2010-03-01
@haydoni - I can certainly confirm that the cli version works just fine

@JohnAstebbins - have you applied this patch and successfully built the source?  If yes, feel like sharing any details?

---

### Post by JohnAStebbins on 2010-03-01
The changeset I linked to fixes the problems in the gui.  That code is in svn and all reports indicate it fixes all those lucid issues. The specific issue that caused all the problems is a change in GtkBuilder.  It no longer stores object id's in the widget name, but instead stores them in a new property.  The handbrake gui used the object id's as the key in a hashtable the contains all the settings, so this change broke things badly.

---

