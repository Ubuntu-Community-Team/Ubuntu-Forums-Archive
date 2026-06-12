---
title: "&quot;Open with Other Application&quot; on folders!?"
date: 2010-03-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cyberkilla on 2010-03-01
Hello,

This has been annoying me for months now, so I thought I'd post it here...

Folders (when you right click in Nautilus) have the option "Open with Other Application". It allows you to choose an application to handle folders.

Unfortunately, if you are stupid enough to use it, you can NOT remove them! On normal files, there is a tab on Right Click/Properties called "Open With" which allows you to remove them.

On folders, there is no such tab (at least for me).

In summary:
- You can add an "Open With" handler to folders, but you cannot remove it without directly editing mimeapps.list.
- Even after removing the handlers, you still have "Open with Other Application" on the folder's context menu. Why have it there at all, if it is a trap!

There is enough junk on the context menus for files and folders - it would be great if this could be sorted out, because the option really is idiotic to have on a folder if you can't remove them later on.

---

### Post by shafin on 2010-03-01
Here is a post on your requirements. :)
BTW, default application for directory opening is defined in /etc/gnome/defaults.list. look for keys x-directory/normal and inode/directory

---

### Post by cyberkilla on 2010-03-02
> **shafin said:**
> Here is a post on your requirements. :)
BTW, default application for directory opening is defined in /etc/gnome/defaults.list. look for keys x-directory/normal and inode/directory

Hello,

I can't seem to get anybody to grasp the problem. The original poster on the bug report faired just as poorly.

I don't want "Open With Other Application" to even be on the context menu of a folder, if you can't remove the damned associations without manually editing config files.:D

It seems stupid to me that that option would even be there, because there is no complimentary option to undo what you've done.

On normal files, you can right-click on them, go to Properties and use the Open With tab.

On folders, there is no Open With tab. Basically, you can make folders open with something, but you can't remove the association later.

Does nobody understand me?:P

---

### Post by mc4man on 2010-03-02
> I don't want "Open With Other Application" to even be on the context menu of a folder
Well that's rather silly to suggest and does point to that you're referring to the wrong thing.

The list produced from "Open With Other Application" is not editable 
What you should be referring to is the "open with" area in the r. click menu or the "open with" sub menu.
( The area is limited to 3 entries, one which is reserved for "Open With Other Application", if more than 2 add. entries are created it's all moved to a sub menu.

As a by product of removing the "open with" tab on the properties of dir.'s, you can only remove entries from the "open with" area or sub menu by editing ~/.local/share/applications/mimeapps.list or in some very rare cases also in ~/.local/share/applications/mimeinfo.cache

If you were to file a bug/wishlist it would be to return the "open with" in properties of dir.'s for removing added associations ( or a similar means as the default for dir. shouldn't/can't be changed from the context menu

Personally I think if one knew enough to go to r. click - properties - open with, that they could just as easily go into mimeapps.list to clean up if desired

---

### Post by coffeecat on 2010-03-02
> **mc4man said:**
> Personally I think if one knew enough to go to r. click - properties - open with, that they could just as easily go into mimeapps.list to clean up if desired

I disagree. I think the OP has a point. Practically everyone knows about rt-click > open with for files (for files only it's common to Windows and MacOS as well), so a moderately-experienced gnome user (but one who didn't know where the config file was) might try Rt-click > open-with on a folder and be tempted to experiment, confident that they could "clean-up" afterward as they could with a filetype. Agreed this is an unlikely scenario but I think the OP has found a usability glitch if not exactly a bug.

When I right-click > open with on a folder in Karmic, I am offered Dolphin, Konqueror (yes, I installed some KDE stuff), **VLC** (:-s  :?), and then 'Other Application'.

---

### Post by pferraro on 2010-03-02
Adding Totem to your folder "Open with" list generates an adhoc playlist using the directory contents.  Pretty handy, IMO.

---

### Post by mc4man on 2010-03-02
> I think the OP has a point
To a degree he does, but the solution is not to remove 'open with other application" 

What's interesting is the remove command in (r. click  -> open with other application) is active for userapp-XXXXXX.desktops but not .desktops from normally installed apps

Edit: in essence mimeapps.list is edited for you but only for custom definitions (userappp.desktops), it will not edit out app.desktops from added associations

---

### Post by emarkay on 2010-03-02
OP, I agree, the less unneeded "Stuff" teh better - remember how abso-friggen-lutely-hard it was to edit the Win XP context menus?  Jeez - I spent hours on that, for a simple enhancement; moving the "Delete" entry to the bottom!.

---

### Post by cyberkilla on 2010-03-04
> **mc4man said:**
> To a degree he does, but the solution is not to remove 'open with other application" 

What's interesting is the remove command in (r. click  -> open with other application) is active for userapp-XXXXXX.desktops but not .desktops from normally installed apps

Edit: in essence mimeapps.list is edited for you but only for custom definitions (userappp.desktops), it will not edit out app.desktops from added associations

I'm not questioning the usefulness of the feature.

It is the *inconsistency* that I take exception to. I don't think anyone can possibly argue that it is acceptable to allow users to add "open with" associations but provide no way to remove them. That's all I'm trying to say. The fact that you CAN remove them on normal files, but not on folders (because the Open With tab in properties is removed), is stupid. Am I missing something here?

> Personally I think if one knew enough to go to r. click - properties - open with, that they could just as easily go into mimeapps.list to clean up if desired

That is flawed logic in anyone's book. If you can add something via the GUI, you should be able to remove it again in a similar fashion.

---

### Post by coffeecat on 2010-03-04
> **cyberkilla said:**
> If you can add something via the GUI, you should be able to remove it again in a similar fashion.

Yes, I agree. You've made the point very clearly. Have you filed a bug-report or a paper-cut?

---

### Post by cyberkilla on 2010-03-04
> **coffeecat said:**
> Yes, I agree. You've made the point very clearly. Have you filed a bug-report or a paper-cut?

I haven't yet, no. I'll report it tonight if I have a minute.:)

---

### Post by ffi on 2010-03-04
> **cyberkilla said:**
> . Why have it there at all, if it is a trap!


It can be very handy, I use it a lot with audacious, unfortunately the implementation is very half baked in that indeed the mimeapp.list gets screwed up.

---

### Post by Jordanwb on 2010-03-04
I'd like to see VLC try and play a folder. Wait, that could actually make sense. VLC would detect that it's a folder, and play all the media in that folder.

---

### Post by coffeecat on 2010-03-04
> **Jordanwb said:**
> I'd like to see VLC try and play a folder. Wait, that could actually make sense. VLC would detect that it's a folder, and play all the media in that folder.

When I first saw VLC as a choice for opening folders on my system, I wondered - what does a folder sound like? :wink: Then I realised that VLC will "play" a VIDEO-TS folder and all its contents as though it's a DVD - menu as well. So the choice is a logical one - if a little unexpected.

But after the problem the OP has identified, I'm still going to open VLC first and then Media > Open Directory from its menu.

---

### Post by ffi on 2010-03-08
> **Jordanwb said:**
> I'd like to see VLC try and play a folder. Wait, that could actually make sense. VLC would detect that it's a folder, and play all the media in that folder.

This works in windows for most media player actually :-\"

---

