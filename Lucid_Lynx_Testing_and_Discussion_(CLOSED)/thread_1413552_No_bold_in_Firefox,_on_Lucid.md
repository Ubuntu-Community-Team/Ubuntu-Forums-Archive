---
title: "No bold in Firefox, on Lucid?"
date: 2010-02-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2010-02-22
Hello,

My Firefox doesn't display bold fonts in my browser, is this happening to anyone else? It is the most noticeable on Facebook.

If it isn't, please could someone post a screenshot of the default fonts in Lucid (appearance pref) and Firefox fonts please, so I can make sure I've got the right settings.

Thank you,

Lee

---

### Post by Darkshade on 2010-02-22
I do see bold fonts. Ugly fonts that make your eyes bleed but bold.

I'm pretty sure the default fonts in Lucid have the same old settings - Sans 10 regular for everything except Sans 10 bold in titlebar and Monospace 10 for fixed width. Slight hinting.

See the attachment for default Firefox font settings.

---

### Post by go7Ul1ai on 2010-02-22
Thank you for the reply, I think my whole fonts system is messed up, the right settings are in place on my system, yet I still can't see bold fonts. I can't select Monospace as it isn't listed (in the firefox fonts menu, but listed in appearance window), but on this reply box here, the font is monospace. Any ideas on how I can get this returned to normal state?

---

### Post by psyke83 on 2010-02-22
Firefox is not currently using the proper font rendering settings (it uses an internal version of cairo which doesn't support the potentially patent-encumbered font smoothing algorithms).

[http://ubuntuforums.org/showthread.php?t=1412751](http://ubuntuforums.org/showthread.php?t=1412751)

---

### Post by caeroe on 2010-02-27
> **lee.jarratt said:**
> Hello,

My Firefox doesn't display bold fonts in my browser, is this happening to anyone else? It is the most noticeable on Facebook.


Font rendering seems fine in Chrome though, both using Freesans.  Been using Chrome for that very reason, hope it's fixed in Firefox soon though, as I want to use some of my add-ons.

---

### Post by inigoml on 2010-04-09
I have the same problem.

I've been waiting until Beta2 release but problem continues both Chrome and Firefox.
I can solve it in Firefox by forcing system fonts.

My problem does not happen with all pages. At this moment I've only experienced this problem with Zimbra webmail.

Prior to 10.04 upgrade there was no problem (chrome and firefox)

---

