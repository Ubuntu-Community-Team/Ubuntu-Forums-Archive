---
title: "dust theme changes"
date: 2010-03-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by montini on 2010-03-04
am i the only one to notice that recent updates of lucid totally wasted the gorgeous look of dust theme? the new design now features the bold grey window edges and nautilus location bar is inconsistent with the menu and main bar colors. Am I the only one to be disappointed with it?

this is how it looked in karmic koala:
[[IMG]http://img291.imageshack.us/img291/3482/screenshotky.th.png[/IMG]](http://img291.imageshack.us/i/screenshotky.png/)

and this is how it looks now:
[[IMG]http://img444.imageshack.us/img444/7669/screenshotlucid.th.png[/IMG]](http://img444.imageshack.us/i/screenshotlucid.png/)

---

### Post by brucemartin on 2010-03-04
i didn't try Dust in Lucid so I don't know if it's a recent update or if  it was like this all along (in Lucid I mean), but maybe it has  something to do with the changes in Nautilus (dual pane, tabs on the bottom, etc.)? 

the window borders can't be right... but from what i see, even the preview in the Appearance Preferences has those borders

---

### Post by Milos_SD on 2010-03-04
I noticed that too. It is like that even when I download theme from wiki and install it on Karmic. It is very ugly. We want old Dust theme look back!!! :)

---

### Post by pferraro on 2010-03-04
The grey metacity side borders must be a bug - I can't imagine that was intentional.  To get the old borders, customize the theme, and switch the Window Border to "Dust Borderless".
I, for one, appreciate the replacement of the ugly pixmap scrollbars with native murrine scrollbars.
The new "even more subdued" highlight color is nice too - though some of the highlights have an ugly brown border.
As for the nautilus changes - I think this is a limitation of the new design (relocation of the breadcrumb).  It would be awkward to keep the dark background for the breadcrumb, while still keeping a light background for the "Places" side pane header (as it was before).

---

### Post by montini on 2010-03-04
> **brucemartin said:**
> i didn't try Dust in Lucid so I don't know if it's a recent update or if  it was like this all along (in Lucid I mean)

It's recent changes - like a week or less ago it changed to that, before it was ok.

---

### Post by Digikid on 2010-03-04
> **Milos_SD said:**
> It is very ugly. We want old Dust theme look back!!! :)

Or better yet.....stick to the code and stop changing things that we do NOT want changed or do not NEED to be changed!

---

### Post by geojorg on 2010-03-04
Try 

Alt + f2
nautilus -q


It seems to be a bug in nautilus.

---

### Post by pkkid on 2010-03-09
I saw this about 2 weeks ago.  I can't imagine this was a conscious design decision unless the designer was smoking.  It looks like its pulling the borders from another theme (maybe missing files in an update?).

I will be eagerly awaiting a fix.  Doesn't look like there is a bug filed yet either..
[https://bugs.launchpad.net/dusttheme/+bugs?orderby=-heat&field.status:list=NEW&field.status:list=INCOMPLETE_WITH_RESPONSE&field.status:list=INCOMPLETE_WITHOUT_RESPONSE&field.status:list=CONFIRMED&field.status:list=TRIAGED&field.status:list=INPROGRESS&field.status:list=FIXCOMMITTED&field.omit_dupes=on](https://bugs.launchpad.net/dusttheme/+bugs?orderby=-heat&field.status:list=NEW&field.status:list=INCOMPLETE_WITH_RESPONSE&field.status:list=INCOMPLETE_WITHOUT_RESPONSE&field.status:list=CONFIRMED&field.status:list=TRIAGED&field.status:list=INPROGRESS&field.status:list=FIXCOMMITTED&field.omit_dupes=on)

EDIT: Trying to fix this, I don't see a "Dust Borderless" option in Customize Theme >> Window Border.

---

### Post by pferraro on 2010-03-10
> **pkkid said:**
> I saw this about 2 weeks ago.  I can't imagine this was a conscious design decision unless the designer was smoking.  It looks like its pulling the borders from another theme (maybe missing files in an update?).

I will be eagerly awaiting a fix.  Doesn't look like there is a bug filed yet either..
[https://bugs.launchpad.net/dusttheme/+bugs?orderby=-heat&field.status:list=NEW&field.status:list=INCOMPLETE_WITH_RESPONSE&field.status:list=INCOMPLETE_WITHOUT_RESPONSE&field.status:list=CONFIRMED&field.status:list=TRIAGED&field.status:list=INPROGRESS&field.status:list=FIXCOMMITTED&field.omit_dupes=on](https://bugs.launchpad.net/dusttheme/+bugs?orderby=-heat&field.status:list=NEW&field.status:list=INCOMPLETE_WITH_RESPONSE&field.status:list=INCOMPLETE_WITHOUT_RESPONSE&field.status:list=CONFIRMED&field.status:list=TRIAGED&field.status:list=INPROGRESS&field.status:list=FIXCOMMITTED&field.omit_dupes=on)

EDIT: Trying to fix this, I don't see a "Dust Borderless" option in Customize Theme >> Window Border.

You can find this in the dust-extras tarball:
[http://launchpad.net/dusttheme/0.5/0.5.0/+download/Dust-extras-0.5.tar.gz](http://launchpad.net/dusttheme/0.5/0.5.0/+download/Dust-extras-0.5.tar.gz)

---

### Post by cyberkilla on 2010-03-10
I had installed Dust manually, so I didn't immediately notice this change. I'm not keen; it looks like the author was experimenting with side borders not dissimilar to the wooden ones on OS X's Garageband.

It doesn't really work when it isn't on a high DPI screen, perfectly antialiased and made of wood texture though:p

That's my guess anyway:D

---

### Post by kmseven on 2010-03-14
Hi! It was a fairly recent update. The side borders were placed to:
(1) make resizing from any side easier. The 1px border is really hard to hit.
(2) have a larger border; not everyone has compositing, so we can't rely on window shadows to differentiate between windows.

About the nautilus breadcrumb thing, as said earlier, it was moved so I don't think I can do much about it.

You should have filed a bug, as I just got to this page by chance (I don't go to ubuntu forums often).

---

### Post by Longinus00 on 2010-03-14
> **kmseven said:**
> Hi! It was a fairly recent update. The side borders were placed to:
(1) make resizing from any side easier. The 1px border is really hard to hit.
(2) have a larger border; not everyone has compositing, so we can't rely on window shadows to differentiate between windows.

About the nautilus breadcrumb thing, as said earlier, it was moved so I don't think I can do much about it.

You should have filed a bug, as I just got to this page by chance (I don't go to ubuntu forums often).

I actually prefer having the wider window borders for the reason you mentioned but I think they would be more acceptable if they are the same color/look as the titlebar area (i.e. black).

---

### Post by kmseven on 2010-03-15
Like this?
[[IMG]http://img188.imageshack.us/img188/21/screenshotnsg.th.png[/IMG]](http://img188.imageshack.us/i/screenshotnsg.png/)

---

### Post by Longinus00 on 2010-03-15
> **kmseven said:**
> Like this?
[[IMG]http://img188.imageshack.us/img188/21/screenshotnsg.th.png[/IMG]](http://img188.imageshack.us/i/screenshotnsg.png/)

I was thinking something more like this.
[[IMG]http://img694.imageshack.us/img694/21/screenshotnsg.th.png[/IMG]](http://img694.imageshack.us/i/screenshotnsg.png/)

I'm not a graphic artist so it's a bit rough but you can see that I copied the motif from the top border onto the left side border. I also reduced the size of the border by a pixel because I felt as though your side borders were a touch too large.

The reason I did this is because I feel that the motif of the top/bottom and side borders should be similar. I feel that when you have the side borders look very different from the top/bottom it makes the final look raw and unrefined.

I think your design is good enough that it could actually surround the window on all four sides.
[[IMG]http://img24.imageshack.us/img24/2938/screenshotnsg2.th.png[/IMG]](http://img24.imageshack.us/i/screenshotnsg2.png/)

---

### Post by ffi on 2010-03-15
It is this bug, please read the last comments
[https://bugzilla.gnome.org/show_bug.cgi?id=605704](https://bugzilla.gnome.org/show_bug.cgi?id=605704)

---

### Post by Atermoon on 2010-03-15
> **ffi said:**
> It is this bug, please read the last comments
[https://bugzilla.gnome.org/show_bug.cgi?id=605704](https://bugzilla.gnome.org/show_bug.cgi?id=605704)

It has nothing to do with this bug.

---

### Post by ffi on 2010-03-15
> **Atermoon said:**
> It has nothing to do with this bug.

You are wrong, it's the same bug...

---

### Post by Atermoon on 2010-03-15
> **ffi said:**
> You are wrong, it's the same bug...

Uh... no. This is the nautilus bug that draws a border around the desktop. The thread is about the new Dust metacity theme.

---

### Post by ffi on 2010-03-15
I told you to read the last comments, read comments 14 to 16

---

