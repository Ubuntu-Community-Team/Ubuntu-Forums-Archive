---
title: "Installing GDM Themes in 9.10 Karmic Koala?"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by klausner on 2009-10-15
How can I install a new login screen in 9.10? The old method of System->Administration->Login Screen no longer has any option for managing artwork. Where have they moved it?

---

### Post by P4man on 2009-10-16
please post in the appropriate forum:
[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

But before posting there, have a look, there are already a gazillion threads about the new gdm and how to customize it.

---

### Post by klausner on 2009-10-16
I was going to apologize for mis-posting, but a little investigation has changed my mind! 

First of all, the Koala discussion is buried four layers deep, and unless you already know the section is there, it is not visible from either the forum homepage or the advanced search engine.

Second, I also repeated my search, and if there is anything addressing this, I can't find it.

---

### Post by Exry on 2009-10-16
I want to know this too. As I find it really irritating that they removed "gdmsetup". Grr. :mad:

Must exist an easy way.

---

### Post by fmfrisch on 2009-10-16
THere is no way to "theme" your GDM with 9.10. THat feature has been removed. However you can make some changes by editing a script. The changes you can make are minor though, like background and icons. You can read about how to go about this here:

[http://www.lathund.nu/2009/10/16/anvand-samma-tema-i-gdm-som-for-gnome-i-ubuntu-9-10/](http://www.lathund.nu/2009/10/16/anvand-samma-tema-i-gdm-som-for-gnome-i-ubuntu-9-10/)

(The article is in swedish.)

---

### Post by shafin on 2009-10-16
> **Exry said:**
> I want to know this too. As I find it really irritating that they removed "gdmsetup". Grr. :mad:

Must exist an easy way.
*gksudo -u gdm dbus-launch gnome-appearance-properties *

---

### Post by P4man on 2009-10-16
> **klausner said:**
> I was going to apologize for mis-posting, but a little investigation has changed my mind! 

First of all, the Koala discussion is buried four layers deep, and unless you already know the section is there, it is not visible from either the forum homepage or the advanced search engine.

Second, I also repeated my search, and if there is anything addressing this, I can't find it.

My point wasn't to have you apologize, just to inform you :) After all, I only found out about that section after one of my posts was moved by a moderator, so I concur about the relative invisibility of the karmic forum.

I disagree about the lack of threads on the subject though. here is a small selection just from the last few days:

[http://ubuntuforums.org/showthread.php?t=1277030](http://ubuntuforums.org/showthread.php?t=1277030)
[http://ubuntuforums.org/showthread.php?t=1281134](http://ubuntuforums.org/showthread.php?t=1281134) (12 page thread on new gdm)
[http://ubuntuforums.org/showthread.php?t=1289748](http://ubuntuforums.org/showthread.php?t=1289748)
[http://ubuntuforums.org/showthread.php?t=1289748](http://ubuntuforums.org/showthread.php?t=1289748)
[http://ubuntuforums.org/showthread.php?t=1286955](http://ubuntuforums.org/showthread.php?t=1286955)
...

Long story short: its work in progress. The gdm is brand new, and there isn't much of a GUI yet to customize it, but its being worked on.

---

### Post by klausner on 2009-10-16
> **P4man said:**
> My point wasn't to have you apologize, just to inform you :) After all, I only found out about that section after one of my posts was moved by a moderator, so I concur about the relative invisibility of the karmic forum.

I disagree about the lack of threads on the subject though. here is a small selection just from the last few days:

...

Long story short: its work in progress. The gdm is brand new, and there isn't much of a GUI yet to customize it, but its being worked on.

Thanks. I looked through those, but my answer is not there. The fault is partly mine, in using an inexact subject for this thread. I'm looking to change the LOGIN screen, not the splash or the desktop theme (for which the "old" tools still work).

---

### Post by P4man on 2009-10-17
gdm=log in screen

---

### Post by klausner on 2009-10-27
OK, so its bad netiquette to solve my own thread, but no one else did so.....

The solution turns out to be [[COLOR="Navy"]here[/COLOR]]("http://wiki.archlinux.org/index.php/Gnome_2.28_Changes#Configuring_gdm_2.28"). The bad news is that pre-2.28 themes won't work anymore. Unless you want to revert to an older version of GDM.

Or... maybe someone knows where there are some new GDM themes available??

---

### Post by MacUntu on 2009-10-27
> **fmfrisch said:**
> THat feature has been removed.

That sounds like 'those evil developers have taken away our lollypops', but you cannot remove what's never been there - it's just a new GDM version that doesn't support theming like the old one (yet there are still many things you can customize, see links above).

---

### Post by joey-elijah on 2009-10-27
> **MacUntu said:**
> That sounds like 'those evil developers have taken away our lollypops', but you cannot remove what's never been there - **it's just a new GDM version that doesn't support theming like the old one **(yet there are still many things you can customize, see links above).

It doesn't support themeing ***YET***.

---

### Post by klausner on 2009-10-27
> **MacUntu said:**
> That sounds like 'those evil developers have taken away our lollypops', but you cannot remove what's never been there - it's just a new GDM version that doesn't support theming like the old one (yet there are still many things you can customize, see links above).

I used theme in it's broadest sense. I meant things like changing the login wallpaper, the menu choices on the login page, and the location of the dialog box(es). That's sort of a theme.

---

### Post by XDevHald on 2009-10-28
BUMP - Need to know the resolution on this as I am not aware of how to change this as well, unless the devs are waiting for full release.

---

### Post by klausner on 2009-10-28
> **XDevHald said:**
> BUMP - Need to know the resolution on this as I am not aware of how to change this as well, unless the devs are waiting for full release.

See the link in [this earlier message]("http://ubuntuforums.org/showpost.php?p=8173341&postcount=10") in the thread for the solution. Unfortunately, as that message notes, there are still issues.

---

### Post by .haNk on 2009-10-29
well this is a major let down.

---

