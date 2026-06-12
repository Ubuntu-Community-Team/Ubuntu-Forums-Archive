---
title: "Natty: Workspace Switcher Not Working"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2011-04-30
Hi,

I just upgraded to Natty, from Maverick and I can't get *'Workspace-Switcher'* to work.:confused:

As a matter-of-fact, I was completely dumbfounded when Natty launched for the first time, and I was presented with 'no' menus.  What I got instead was some black-screen with some very attractive icons on it; but the icons had no organization to them that I could comprehend, and the categories that were presented didn't make any sense, based on the applications that I had installed. Apparently the designers of Unity thought that it would be a good idea for me to go *'fish'* for my applications.  Also, the most frequently used applications that I had pinned to gnome-panel disappeared, and I couldn't even rebuild them.  The 3D menu, on the left, that combined my desktop icons, with the icons that were *'formerly'* pinned to gnome-panel was also very attractive; but provided me with no useful functionality, other than complete disorientation and confusion.  The scrolling was also slower than poo.  All-in-all a very beautiful *'boat-anchor.'*  This distro should probably be renamed ***'Virtual-Vista.'***  Fortunately, when I reenabled 'Desktop-Cube' and 'Rotate-Cube' and I think some other options related to Gnome, I got my menus and icons back.  *What a relief!!!*  I'm a power-user, and I have something on the order of 100 applications loaded.  I just 'can't' go looking all-over-creation to find them...

Unfortunately, Workspace-Switcher could not be activated by clicking on it, only by <ctrl-alt-left/right arrow keys>.  Also, unfortunately, all the desktops displayed the same applications.  Definitetly 'not' a ready for prime-time player.

I assume that this is a bug?  Is there a work-around for this?  If so, can someone please share it with me?  For now I'm stuck with a *ruptured-duck* that can't swim.  I usually have all four desktops populated, and switch between them whenever I have to wait on an application that's busy, or I get tired.  I really 'need' this functionality.

Any help greatly appreciated.



Thanks, Hannibal


P.S., It's more than Ok with me that a distro not be released, if it's not ready. I'd certainly prefer that to ***'shock-and-awe.'***

---

### Post by coljohnhannibalsmith on 2011-05-01
Well after getting my forehead all bloodied, beating it on my desktop, I think I may have found the correct settings to get Workspace-Switcher to work properly...

In *'compizconfig-settings-manager,*' this assumes you've installed it, which you'll need to, you'll have to select:

Category > General > General Options > Desktop Size

*Then set **"Number of Desktops"** to **"1.*****"**

Then right-click on Workspace-Switcher and select preferences; and set *'columns'* to the number of workspaces you want, and *'rows'* to '1,' unless you want to stack them for some reason...  After I did this Workspace-Switcher functioned normally.

Jesus, Unity is pretty; and everyone knows that Ubuntu has been lacking in the 'skins' department; but good-grief, why ***force ***this change on unsuspecting users, especially when the code appears to be in the Alpha state.  ***"It just locks-up on many users, myself included."***  I did read that Natty was going to be a ***stretch***-release.  I just didn't know it was going to be ***'me'*** that was going to get *stretched!!!*

All seriousness aside, in my opinion Unity should not have been enabled by default..  There should have been some kind of *'very-obvious'* on-off switch for Unity, which would have allowed a user to switch between both modes easily, and without getting lost.


Just one ***irate*** customer's opinion.:rolleyes:




Hannibal

---

### Post by TrotskyIcepick on 2011-06-22
Hmmm, glad you got this to work, I just did a complete fresh install of 11.04 into an Oracle VBox on a Windoze Vista host, had same problem....tried your solution.....and bingo, stuck with problem.

I'm just running Ubuntu in "Classic" mode, and have tried removing and re-adding the workspace switcher to no avail.

---

### Post by gareththomasnz on 2011-09-02
doesnt work in classic mode and nor does ctrl-alt for cube

---

