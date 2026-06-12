---
title: "Fork GNOME?"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kaldor on 2010-03-28
It's been on my mind a bit lately; Ubuntu makes many changes to the basic elements of the gnome desktop during each release. It isn't major, but it's noticeable. 

Does anyone think it would be an advantage, or could forsee Canonical creating their own fork of GNOME and making Ubuntu a unique DE?

---

### Post by Dayofswords on 2010-03-28
:-k

beats me

---

### Post by iduppe on 2010-03-28
I'm not quite sure, but for example the notifications, fedora has them now too...

I think ubuntu just improves, but it gives back to gnome too.. .at least on that situation.

On the other hand, some changes are not on other distros.. but I don't think changes are *that* big to call it a fork.

---

### Post by praveenmarkandu on 2010-03-28
i dont see how canonicals work on ayatana is going to fit into gnome3. its gonna be a train wreck if you ask me

---

### Post by Sophont on 2010-03-28
The customizations for Ubuntu are no reason to fork.

But Gnome-shell and the increasing removal of options might make a fork necessary.

I'm trying to keep an open mind about gnome-shell - but so far I'm not convinced it's a good direction. There are good ideas there but it's way too much about handling workspaces and having exactly this one cool way of doing workspaces is not what's important to have IMHO.

And while I'm happy with the relatively few options that gnome offered (most of the defaults are to my taste and I don't mind doing 2-3 changes after each install - for example setting toolbars to icons only) the few options are important.

Removing the interface tab from appearences was a step too far IMHO. I can easily fix those settings via gconf-editor and have already written a small python script to take care of that, but it's an indication that gnome seems to be bent on enforcing a single oversimplified policy.

I preferred gnome over KDE because KDE overloaded the GUI with options and clunky details (IMHO - matter of taste of course).
But there is too much of a good thing. Removing the button that toggles between breadcrump and path entry in Nautilus was a mistake.
While my script can set path entry - I still don't have a button that simply toggles. I mostly need path entry, but sometimes want the breadcrump. Opening gconf-editor every time I want to toggle that would be silly - so I'm loosing functionality here.

I see this as a regression.

In a world where KDE still tries to offer every option imaginable and gnome soon will be a my-way-or-the-highway no-options solution I'll be looking for a sane in-between desktop.

Pretty much what we already had with Gnome until now. A desktop UI with sane defaults. Not in the way, simple to get in to. Accessible to beginners and sufficiently modifiable for some special purposes. With cool options like Docky or a wide selection of Compiz effects.

What Gnome needed was some cleanup and optimization in old libraries and incorporating some effects and getting better theme support.

Instead we're getting an overpurified DE with Mac envy and too much focus on one way to do workspaces that most of the future target user base won't even care about. And keeping out Compiz is just crazy. Youtube is full of cool vids and XP users comments that the Cube made them switch OS.

---

### Post by emarkay on 2010-03-28
Spohont,

Sort of what I have been saying, in a way; A "gee whiz, no-brain-needed, MS Windows-like, one-button does all" version, and then a  "Get down to business minimalist GUI, with a plethora of options and configurations.  

This way those whining for "Pretty and Easy, Snazzy, New and Improved" " get their load of cake, and those who like text-not-icons, no frilly things, extreme performance and stability, and, who can read a manual and figure out how to "tweak" can grab their snack.

Things in this realm, and most other products these days, seem to be moving away from "user friendly" (configurations and setting options). Whether it's good or bad is only an opinion, but IMHO there needs to be an outpouring of educated and conscious users who demand the ability to both configure and secure their GUI.

Maybe it's time for a fresh rethink?  
Anyone up for "Dwarf" or "Hobbit", or "Lawn Jockey"?   :)

---

### Post by joey-elijah on 2010-03-28
It'd be a massive decision to fork it but I wouldn't say it'd be a *bad* decision. I'm not entirely sure if Gnome-Shell should be introduced in 10.10/11.04 (can't remember precisely when it's due) so less a fork and more a 'maintaining' of 'normal' GNOME wouldn't be out of the question...

...but in reality the GNOME development team is huge. Would Canonical/Ubuntu really be able to get enough developers to make a fork workable, progress-able and not just maintainable? That I don't think so. 

GNOME-Shell has its merits but I'm yet to remain convinced personally.

---

### Post by jfernyhough on 2010-03-28
> **Sophont said:**
> But there is too much of a good thing. Removing the button that toggles between breadcrump and path entry in Nautilus was a mistake.
While my script can set path entry - I still don't have a button that simply toggles. I mostly need path entry, but sometimes want the breadcrump. Opening gconf-editor every time I want to toggle that would be silly - so I'm loosing functionality here.I know this doesn't fix the problem but you can also get text entry by pressing CTRL-L (like getting into the URL bar in Firefox).

---

### Post by dinamic1 on 2010-03-28
i'm in :D let's fork gnome :popcorn:

---

### Post by Schendje on 2010-03-28
I agree with Joey-Elijah.

It's a shame all of Canonical's work will be lost if we suddenly switch to GNOME Shell. Moreover, it'd be a shame to lose all of GNOME's awesome work so far. Like someone said, a train wreck.

But forking? It's way to big. You can fork the software, but you don't create such a huge community from nothing. Never mind the Foundation, the paid developers from other companies, the hackfests, the conferences, etc, etc... That's just impossible.

---

### Post by zengeos on 2010-03-28
hmm...

I wasn't aware that Gnome was a huge organization.  I was sorta under the impression that it was a small team of a dozen or so.  It seems like KDE is aq much larger organization....

---

### Post by Regenweald on 2010-03-28
Considering the shell is really just an overlay, It would simply be Canonical maintaining a heavily customized panel+file manager+ 'whatever else' interface. They would still have the advantage of Gnome's leaner architecture and new features like Zeitgiest to leverage. I prefer Ubuntu's direction in terms of looks and interface to the shell. 

I expect some kind of announcement in the coming months. The social from the start thing is actually beginning to work for me, It's a lot more convenient to simply have empathy log in to gmail chat and operate discretely from the task bar than having to launch a browser and go to gmail.

---

### Post by kurros on 2010-03-28
> **praveenmarkandu said:**
> i dont see how canonicals work on ayatana is going to fit into gnome3. its gonna be a train wreck if you ask me

Huh? notify-osd and the indicator-applet framework can work with gnome-shell just fine. gnome-shell already copies some indicator-applet concepts, and code could be written to make gnome-shell compatible with the framework pretty easily. And notify-osd is unrelated to the window manager.

This is assuming gnome-shell actually does replace metacity on capable hardware, which isn't a sure thing. I don't think any distro is going to have to want to maintain two desktop environments for separate hardware at this point. I think gnome-shell is just going to stay an option until it reaches an adoption tipping point, or there is some serious reworking of metacity/gnome-panel/etc to make it look like gnome-shell.

Most of what is defined by the 3.0 label is about reorganizing the libraries and getting rid of antiquated code and concepts, much of this is already in Gnome 2.30.

---

