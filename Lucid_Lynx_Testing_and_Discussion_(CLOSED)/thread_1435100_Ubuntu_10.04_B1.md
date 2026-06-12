---
title: "Ubuntu 10.04 B1"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by filip007 on 2010-03-21
I have try new Ubuntu and i think that user interface need a little bit more changes not just move things around and enable that and disable that. Blocking icons from System menu it's a bit dumb, add at lest one icon that menu will be proper size, well at lest you fixed icon for Examples folder. If Ubuntu will be using this industrial look than use it don't brake consistency with some random changes like not full size menus and window title is not in window center. If you remove something than make installer icon in menu that will open Ubuntu Software center with that app. Yes some users are lazy probably but don't make OS dumb just for them, Ubuntu is here to give and share knowledge and wisdom and not take from user if self! You can add ads for your special devices with Ubuntu why not at lest the user will know what where and how to get Ubuntu system i support that, that's the way the W. world works all this time anyhow.

---

### Post by And1945 on 2010-03-21
The only thing I am not pleased about is the location of the close/maximize/minimize buttons.

How do I change that, so they can come back, where they belong?

EDIT:
And another thing. Why has gnome-apt been removed completely from the respositories?

---

### Post by geirha on 2010-03-21
> **And1945 said:**
> The only thing I am not pleased about is the location of the close/maximize/minimize buttons.

How do I change that, so they can come back, where they belong?

Just change the theme to one that has those buttons on the rhs. System -> Preferences -> Appearance.

---

### Post by And1945 on 2010-03-21
> **geirha said:**
> Just change the theme to one that has those buttons on the rhs. System -> Preferences -> Appearance.

Strangely, that does not seem to work.

We can agree that "dust" have buttons on the right side, right? Does not do the job.

---

### Post by geirha on 2010-03-21
> **And1945 said:**
> Strangely, that does not seem to work.

We can agree that "dust" have buttons on the right side, right? Does not do the job.

You are right, I mistakenly assumed that that was controlled by the theme.

Alt+F2 -> gconf-editor -> /apps/metacity/general

Change the value of button_layout from 

**maximize,minimize,close:** to **:maximize,minimize,close** (moving the colon from right to left)

I couldn't find any way to do that from the menus :/

---

