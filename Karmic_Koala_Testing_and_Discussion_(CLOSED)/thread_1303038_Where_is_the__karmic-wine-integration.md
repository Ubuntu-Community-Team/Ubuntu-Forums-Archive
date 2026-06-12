---
title: "Where is the  karmic-wine-integration?"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Ric_NYC on 2009-10-27
I didn't notice anything different.
When I uninstall applications their entries stay in the Wine menu.

---

### Post by zekopeko on 2009-10-27
> **Ric_NYC said:**
> I didn't notice anything different.
When I uninstall applications their entries stay in the Wine menu.

It's not in Karmic...

---

### Post by Ric_NYC on 2009-10-27
I thought it was "official".
What changed?

[https://wiki.ubuntu.com/karmic-wine-integration](https://wiki.ubuntu.com/karmic-wine-integration)

---

### Post by Doctor Debian on 2009-10-28
I've recently read a blog post that stated that Karmic Koala would have increased wine integration, e.g making shortcuts in the right places, adding installed wine applications to add/remove, etc. What happened with this project? I am using the Karmic RC, and although it is handy that you can install the wine development releases from the Software Center, I see no further improvements. Feel free to correct me if I am wrong :)

---

### Post by VMC on 2009-10-28
I forgot all about that project until you mentioned. Hopefully it will see the light of day under L2.

---

### Post by 23meg on 2009-10-28
> **Ric_NYC said:**
> I thought it was "official".
What changed?

[https://wiki.ubuntu.com/karmic-wine-integration](https://wiki.ubuntu.com/karmic-wine-integration)

If you check out the whiteboard in [the Launchpad page]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-wine-integration") of the blueprint, it says what changed:

> pitti, 2009-09-15: Looks we need to defer that, for Karmic it's getting very late


---

### Post by humphreybc on 2009-10-28
Shame, wine integration would be mean. Oh well, Lucid Lynx, here we come!

---

### Post by vinutux on 2009-10-28
Wait for final release.........

---

### Post by flipper9 on 2009-10-28
> **vinutux said:**
> Wait for final release.........
You're implying it's going to get secretly slipped into the final release? :O

---

### Post by 23meg on 2009-10-28
> **vinutux said:**
> Wait for final release.........

Please read the previous posts. It won't be in the final release.

---

### Post by seeker5528 on 2009-10-28
A: Do you have wine installed or wine1.2? 1.2 is the newer stuff.

B: Might also depend on which desktop/window manager environment you are running. On my gnome desktop, the top level of the applications menu has a wine menu with entries to browse the C: drive, configure wine, or uninstall wine software, and there is a 'Programs' submenu showing the menu items created by the installation of windows programs. I assume they use XDG menu entries for this stuff, but how these get treated by the different desktops/panel menu systems may vary.

Later, Seeker

---

### Post by 23meg on 2009-10-28
Threads merged.

---

### Post by Doctor Debian on 2009-10-28
I have 1.2 installed, no changes between versions afaik.

---

### Post by graaant on 2009-10-28
> **23meg said:**
> Please read the previous posts. It won't be in the final release.

Oh, I have to think this guy is just trolling. His "Wait for final release..." pops up all over the place.

---

### Post by vinutux on 2009-10-28
> **graaant said:**
> Oh, I have to think this guy is just trolling. His "Wait for final release..." pops up all over the place.

+1 hopes...

---

### Post by seeker5528 on 2009-10-28
> **Doctor Debian said:**
> I have 1.2 installed, no changes between versions afaik.

Well, for Gnome anyway, there is one more possibility I can think of, the menu item might be hidden by default.

If you right click the menu applet on the panel and choose 'edit menus' does wine show up there? Stuff that does not have a check in it will not show up when you view the menus.

EDIT: I never use the Gnome Control Center so the 'greater integration' thing escaped me. ;) Without that integration seems plenty, but still have plenty of argument for moving the 'Configure Wine' and 'Uninstall Wine Software' menu items to the preferences menu.

Later, Seeker

---

### Post by Doctor Debian on 2009-10-28
> **seeker5528 said:**
> Well, for Gnome anyway, there is one more possibility I can think of, the menu item might be hidden by default.

If you right click the menu applet on the panel and choose 'edit menus' does wine show up there? Stuff that does not have a check in it will not show up when you view the menus.

Later, Seeker

Maybe you misunderstood what this thread is about. This thread is about the greater integration between wine and the OS, such as integrating the wine control panel with gnome-control-center, etc. The problem lies not within the wine menu.

---

