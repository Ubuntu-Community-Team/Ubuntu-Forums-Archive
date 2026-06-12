---
title: "Lucid-2 Desktop questions I think are new."
date: 2010-02-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-02-13
On attached screencap, I have the Desktop Icons' font intentionally large for this example, but how can I increase th2 horizontal space for the text/ the horizontal spacing between Icons.  I recall in Karmic I could "Clean up by name" and that would happen; it doesn't now.

Also, I used to be able to just show Text only, not Icons or "Icons and Text" here in Nautilus.  I don't see that option any more.  How can I get text only?

Thanks

---

### Post by emarkay on 2010-02-14
Anyone?

---

### Post by jpeddicord on 2010-02-14
Unsure about the first part, but:
> **emarkay said:**
> Also, I used to be able to just show Text only, not Icons or "Icons and Text" here in Nautilus.  I don't see that option any more.  How can I get text only?

I believe the settings interface for that was removed as it was mostly unused by the majority of users. All of the settings are still available in the GConf database, however. To change it open gconf-editor (from terminal or Alt-F2), and navigate to /desktop/gnome/interface and look for toolbar_style on the right pane. Try out the settings listed on the bottom: "both" is for icons and text, "both-horiz" is for how it is now, and the others should be self-explanatory.

---

### Post by emarkay on 2010-02-15
> **jpeddicord said:**
> Unsure about the first part, but:

I believe the settings interface for that was removed as it was mostly unused by the majority of users. All of the settings are still available in the GConf database, however. To change it open gconf-editor (from terminal or Alt-F2), and navigate to /desktop/gnome/interface and look for toolbar_style on the right pane. Try out the settings listed on the bottom: "both" is for icons and text, "both-horiz" is for how it is now, and the others should be self-explanatory.


OK, I see that config area - what is te eoption name for " no icons, only text"??

Also something is really wrong, it's getting worse - the horizontal space for text and icons on teh desktop is **shrinking!!**  See new screen cap.
OH NOO!!!  :)

---

### Post by jpeddicord on 2010-02-15
> **emarkay said:**
> OK, I see that config area - what is te eoption name for " no icons, only text"??

That'd be "text"

---

### Post by uBeer on 2010-02-15
And what it does has nothing to do with your desktop icons.
It has got to do with the buttons in toolbars (like in Rhythmbox). It configures whether you want only icons or you want text or both.

---

### Post by jpeddicord on 2010-02-15
> **uBeer said:**
> And what it does has nothing to do with your desktop icons.
It has got to do with the buttons in toolbars (like in Rhythmbox). It configures whether you want only icons or you want text or both.

Ack - wow, I misread the question.

---

### Post by emarkay on 2010-02-15
Urgh - I registered at the GNOME forums, as I couldn't find any info in their Docs on "Icon Text"  or "Icon Spacing" - 

[http://gnomesupport.org/forums/viewtopic.php?p=59233#59233](http://gnomesupport.org/forums/viewtopic.php?p=59233#59233)

---

### Post by emarkay on 2010-02-18
Surely SOMEONE knows how to change this... :(

---

### Post by pferraro on 2010-02-18
> **emarkay said:**
> OK, I see that config area - what is te eoption name for " no icons, only text"??

Also something is really wrong, it's getting worse - the horizontal space for text and icons on teh desktop is **shrinking!!**  See new screen cap.
OH NOO!!!  :)

[LIST=1]
[*]Open up Nautilus.
[*]Edit->Preferences->Views (tab)
[*]In "Icon View Defaults" section, uncheck "Use compact layout"
[/LIST]

---

### Post by emarkay on 2010-02-18
Nope, tried all those settings - it's all on "List view" and zoom was set for 50%.  
Now set to 100% - hmmm, a clue, a small change, but let me mess around with this...

Aha! Wow, how totally unintuitive and restrictive...

Places>Desktop>Edit>Preferences>"Icon View Defaults"
Change "Default Zoom Level" to 100% or greater.

Of course 100% is too small and the next choice, 150% is too large.
This is one time I can honestly say, MS Windows is better in allowing more configurations of the desktop...

Any additional info I can use to configure this?

---

### Post by pferraro on 2010-02-18
> **emarkay said:**
> Nope, tried all those settings - it's all on "List view" and zoom was set for 50%.  
Now set to 100% - hmmm, a clue, a small change, but let me mess around with this...

Aha! Wow, how totally unintuitive and restrictive...

Places>Desktop>Edit>Preferences>"Icon View Defaults"
Change "Default Zoom Level" to 100% or greater.

Of course 100% is too small and the next choice, 150% is too large.
This is one time I can honestly say, MS Windows is better in allowing more configurations of the desktop...

Any additional info I can use to configure this?

The relevant settings for the desktop are under "Icon View" - regardless of the view specified under "Default View".
You still have "Use compact layout" checked.  Turn this off and your desktop icon labels won't wrap so aggressively.

---

