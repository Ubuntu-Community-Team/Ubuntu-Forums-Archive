---
title: "[Lucid] All panel applets locked"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dbcoolio on 2010-03-29
I just upgraded to the Lucid Beta 1 (Netbook Remix), and everything is working except that I can't move/change/add any applets on my gnome-panel. The right-click menus appear, but the 'Remove From Panel', 'Move', and 'Lock To Panel' options are all grayed out.  I opened up gconf-editor and in the app->panel area, the entire panel is not locked (when it is, the options don't even appear in the right-click menus) but each of the applets has a locked boolean key that is set to true and is not writeable.  I tried deleting the keys and creating new ones, as well as editing the XML directly, and whatever changes I made were immediately overwritten and reverted to locked=true.

Here's a screenshot:
[IMG]http://7839255702295085338-a-1802744773732722657-s-sites.googlegroups.com/site/derrickbowen/home/Home/gconf-keynoteditable-Screenshot.png?attachauth=ANoY7cr8Hdyc4gY3blGDAJKQ6OUwwxHmJn8-S2Xa1-hrTtWLplDpoFSrJF4ecK6hD19KOSy4ZszPWQkY4k2sCLTHqfqWni6d2lzLgSVMFh4HpmOCnbsOvoiwO9HrgSQvV-F4Ue4bxoEDK9kIkZBLDsO5fWhoDg5gouDtF4-XLLkVkdFmdNzDbSukybrpvkYYmvgJ0Y6mz7xJrKIQ2qMRy5qZ0c8E-JR0kt02tdnnL-4SiHwYWFSFVmQDf_qPoAv9OMx9aDYPYH8N&attredirects=0[/IMG]

---

### Post by NightwishFan on 2010-03-29
Try this in a terminal:
```
gconftool-2 --recursive-unset /apps/panel
```

---

### Post by dionblundell on 2010-03-29
_NightwishFan_ thanks for the hint, that did not work for me, anymore ideas?

---

### Post by overdrank on 2010-03-29
Moved to Lucid Lynx Testing and Discussion

---

### Post by NightwishFan on 2010-03-29
Make backups of these files/folders first! Copy them to the desktop.

Back up your email in evolution (if you use it) and delete the .gconf .gconfd and .gnome2 directories located hidden in your home folder. ONLY delete those. Then log out and back in. If it works, great. If not, delete the new ones and copy the old ones back.

---

### Post by dbcoolio on 2010-03-29
neither of those things worked for me.

---

### Post by NightwishFan on 2010-03-29
Then it is not a configuration issue, it has to be something you did as root or a package.

Try reinstall gnome-panel and gnome-panel-data.

---

### Post by Anxious Nut on 2010-03-30
same problem here, lucid netbook remix, but fresh install, compaq mini 110c

---

### Post by chrisccoulson on 2010-03-30
This is a design decision due to unfortunate technical limitations of gconf. The desktop team wanted to make it possible to install the UNE desktop in parallel with the standard Ubuntu GNOME desktop, but the UNE environment has different configuration for things like the gnome-panel etc. The issue with that the desktop components write user-specific configuration either when they run or when you modify settings, so the only way to allow you to have UNE in parallel with the standard desktop without the 2 environments screwing each other up is to implement some of the UNE specific configuration using mandatory keys (so that they override the user-specific configuration that's written in the standard GNOME environment).

The unfortunate side effect of this is that there are some things you can't configure in the UNE session.

This is ok though, as the UNE session is meant to provide you with the out-of-the-box Ubuntu Netbook experience. If you want a UNE-type session where you can configure settings and have more freedom to change things, then you can configure your standard GNOME environment to be more like UNE instead.

---

### Post by jnetman1 on 2010-03-30
Oh c'mon - that's just silly! Panels always worked in prior releases in both desktop interfaces. This looks more to me like some sort of purist ideal at the expense of end user flexibility.

---

### Post by victor9098 on 2010-03-30
Log out and in the GDM screen on the bottom right choose the Gnome option from the menus. Then log in. In that session you should be allowed to make alterations, then log back into UNE session when done.

I do not like either, damned stupid.

Try these two thread for more answers/instructions:

[Can't unlock panel in UNE]("http://ubuntuforums.org/showthread.php?t=1416560")
[UNE - Do you want your panel apps fixed?]("http://ubuntuforums.org/showthread.php?t=1429426")

---

### Post by chrisccoulson on 2010-03-30
> **jnetman1 said:**
> Oh c'mon - that's just silly! Panels always worked in prior releases in both desktop interfaces. This looks more to me like some sort of purist ideal at the expense of end user flexibility.

The last sentence is absolutely not true. And it was very different in Karmic - you couldn't install the UNE session and run it side-by-side with the standard GNOME session. In Lucid, you can pick the type of session you want to log in to at the log-in screen

---

### Post by NightwishFan on 2010-03-30
The panels are supposed to work I think. Someone should report this as a bug. If it is intended then.. what?

---

### Post by victor9098 on 2010-03-30
> **NightwishFan said:**
> The panels are supposed to work I think. Someone should report this as a bug. If it is intended then.. what?

It is the intent of the developers to keep them locked from [DesktopTeam/Specs/Lucid/DesktopUNESession]("https://wiki.ubuntu.com/DesktopTeam/Specs/Lucid/DesktopUNESession")

> Stay like this, calling it the "UNE experience" where you can't change any applets. This is what I first chose, (as mostly gnome shell take that path too). But we need then to take some shields against community feedbacks (no casual user where we don't expect to change this)

---

### Post by jnetman1 on 2010-03-30
Yep, if you delete the panel dir entries in /var/lib/gconf/une.mandatory/%gconf-tree.xml you can have your panels back and editable, which is the way it should be. Alternatively, you can add and remove from the list manually. Did I say silly? Oh yes, I did. Don't think there are many netbook users who care about being able to select a desktop at login.

---

### Post by kitrule on 2010-03-31
I did a dist-upgrade earlier (been using lucid since alpha 2/3) and it removed gnome-panels. i saw gnome panels in the list of remove packages with a dozen other gnome packages and figured, hey, maybe they've been replaced with/combined in to another package. they haven't. gdm just logged me in to an xterm. bizarre.

---

### Post by washburnello on 2010-04-03
I understand the logic used to make this decision but I really think it's a bad move. I'm using a Dell mini 9 and love the UNE interface. I would never consider using a standard gnome desktop on this small of a screen. Dual desktops had never come to my mind. Is the standard gnome desktop included with a UNE install? If not, then why is a basic config option locked down in favor of a potential (IMHO unlikely ) dual desktop setup.
This causes a real headache on my mini 9 as it does not have a caps-lock LED. I've always relied on putting an indicator on the panel to keep track of this. Now I have to type some text to see if caps-lock is on.
Like I said, I understand the explanation but totally disagree. If anything, it should be the gnome desktop that should be locked down on a UNE install IF both desktop environments are installed. There just HAS to be a better way.
I'm not mad, just disappointed. I still love Ubuntu but might need to try something different on my netbook if this doesn't change.

---

