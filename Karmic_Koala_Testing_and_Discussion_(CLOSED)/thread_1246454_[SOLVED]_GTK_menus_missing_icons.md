---
title: "[SOLVED] GTK menus missing icons"
date: 2009-08-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by durand on 2009-08-21
None of the menus in my gtk applications have icons in their menus. I have no idea what updates caused this because I updated after 3 weeks so it could be any of the 600 packages that were updated :S Does anyone else have this problem? I've tried using other themes but nothing's changed.

Screenshots attached.

---

### Post by durand on 2009-08-21
Just remembered that there was an option to remove menu icons so I checked those settings and for some reason, it was unticked. I really have no idea why that is the case because I can't remember unticking it...

Anyway, fixed :D

---

### Post by mejy on 2009-08-21
It's the new Gnome default, the developers have decreed it less cluttered.

---

### Post by durand on 2009-08-21
Oh. But everything looks more boring without them :(

---

### Post by fballem on 2009-08-22
And for those who may not now how to turn the Menu icons on:

[LIST=1]
[*]Select System > Preferences > Appearance from the menu.
[*]This displays a tabbed panel, labeled 'Appearance Preferences'.
[*]Select the tab, as shown in the Attached Screenshot.
[*]Select Close.
[*]The menu icons should be back.
[/LIST]

Hope this helps,

---

### Post by forumache on 2009-08-22
@fballem, many thanks!

---

### Post by durand on 2009-08-22
Thanks fballem, I should have given instructions myself but I thought that I was the only one with the problem.

---

### Post by Mr. Picklesworth on 2009-08-22
> **durand said:**
> Oh. But everything looks more boring without them :(

The plan is to have icons for all objects like files, applications and bookmarks, but no icons for actions (like Undo, Copy and Save). Keep an eye out for offenders. I'm not sure what the process is here, but at some point bug reports would probably be appreciated :)

---

### Post by durand on 2009-08-22
So basically no icons inside an application? Wow, I really hope this is optional...

---

### Post by tghe-retford on 2009-08-22
> **durand said:**
> So basically no icons inside an application? Wow, I really hope this is optional...
Well, yes (for now). However, there is discussion that the Interface tab that fballem referred to may be removed before too long, which will prevent people turning icons back on that way.

It may be better to post the command line options to be on the safe side (although reading through the Gnome bug report, these options could be removed too - I started a thread on this same issue in the past and things got heated):

To restore icons in menus:
```
gconftool-2 --type bool --set /desktop/gnome/interface/menus_have_icons true

```

To restore icons on buttons:
```

gconftool-2 --type bool --set /desktop/gnome/interface/buttons_have_icons true
```

---

### Post by durand on 2009-08-22
Yeah, you can do that at the moment but I'm thinking about the future.

---

### Post by tghe-retford on 2009-08-22
> **durand said:**
> Yeah, you can do that at the moment but I'm thinking about the future.
From what I can ascertain from the Gnome bug reports, Launchpad and previous discussion, these changes (described well by Mr. Picklesworth) will be a permanent move to remove "clutter". Although one article I have seen says that icons can be restored, I have seen discussion with Gnome developers which state that the Interface tab and the gconf options to restore icons to buttons and menus will be removed, which essentially means its their way or the highway.

It's not just Ubuntu which will implement this, OpenSUSE is considering it for their distribution (when I last checked).

More info in this news article and links to the important articles and bug reports: [http://www.osnews.com/story/21935/GNOME_To_Drop_Icons_in_Buttons_Menus](http://www.osnews.com/story/21935/GNOME_To_Drop_Icons_in_Buttons_Menus)

---

### Post by durand on 2009-08-22
Hmm, I really don't understand why people don't like those small icons. If I want a minimal desktop, I use openbox. I like how gnome uses icons everywhere. It's what makes gnome interesting to use, not some corporate desktop with all the fun sucked out of it.

---

