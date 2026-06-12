---
title: "Restore all nautilus associations"
date: 2009-02-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-02-19
Well I've got my system into a bit of a mess. I've installed various things, upgraded twice and nautilus just plain doesn't know what to open things with.

It's fine for most things but there's a lot of craft (open with menu containing apps that don't exist) and executable scripts only have a (Open with text editor) assoc.

I'd like to either find out how to go through all the assocs and clean up or find a script that purges them all and finds out what apps still exist and which files they should open.

---

### Post by kurros on 2009-02-19
I don't know about purging but you can right click on a file and choose Properties and add or remove programs from the Open With tab for all files of that Type.

Sounds like you already know this though.

---

### Post by OliW on 2009-02-19
Yup.

My problem is mainly with old setting crufting everything up. For example, Crossover Professional (uninstalled many aeons back now) is still the default execution method for .exes. No matter how much I kick the computer, I can't make Wine show up as the default.

And executable bash scripts are locked to gedit. Fairly annoying but not annoying enough for me to want to scrub my whole user account (where I imagine these settings are saved).

---

### Post by taavikko on 2009-02-19
Yep.

Settings are stored in hidden folders/files in your ~/

they contain the information how your system works.

---

### Post by mc4man on 2009-02-19
Haven't tried jaunty yet, maybe this weekend.
If nothing drastically changed from 8.04-10 in this regard then you'll find your r.click associations (among other things) stored as userapp.desktops in ~/.local/share/applications (blue diamonds

In ~/.local/share/applications/mimeapps.list will be the various individual lines for mimetypes and apps that have been associated with them.
Generally speaking the first listed is the default, you are free to edit in both area's, for mimeapps.list just kept to the formatting, no spaces, end with a ;

For instance this is for .exe
application/x-ms-dos-executable

for scripts
application/x-shellscript

ect.

---

### Post by OliW on 2009-02-25
I've looked through that dir and the mimeapps.list file but I still can't seem to remove CrossOver from the default .exe handler or associate shell scripts with the run/edit dialogue.

---

### Post by OliW on 2009-03-17
Well things are getting more and more botched the more I try and fix things. Folders launched from the Places menu or other applications (with the exception of the desktop which *is* nautilus), try to open with Phatch (a batch image processing tool).

Needless to say, this is getting silly. Any more ideas?

---

### Post by taavikko on 2009-03-17
Create new user, then login with that account,
If everything works, it just your setup that's corrupted
If not, it's system settings...

Just to rule out stuff...

---

### Post by nyarnon on 2009-03-17
> **OliW said:**
> Well things are getting more and more botched the more I try and fix things. Folders launched from the Places menu or other applications (with the exception of the desktop which *is* nautilus), try to open with Phatch (a batch image processing tool).

Needless to say, this is getting silly. Any more ideas?

Wanna get radical? Just move .gnome, .gnome2 and .gnome_private to a save location and restart with ctrl-sysrq-k. This will create a new gnome config.
But it will also destroy old settings.

---

### Post by taavikko on 2009-03-17
> **nyarnon said:**
>  .gnome, .gnome2 and .gnome_private 

Don't forget .gconf/

---

### Post by OliW on 2009-03-17
> **taavikko said:**
> Create new user, then login with that account,
If everything works, it just your setup that's corrupted
If not, it's system settings...

Just to rule out stuff...

Good call. Yup. Everything works for the new user. I guess that's what almost two years of tweaking three major alpha versions of Ubuntu does to a system.

I'd rather not have to destroy my account completely -- we're very attached. Do you know which settings files I should copy over from the new user account?

---

### Post by OliW on 2009-03-17
> **nyarnon said:**
> Wanna get radical? Just move .gnome, .gnome2 and .gnome_private to a save location and restart with ctrl-sysrq-k. This will create a new gnome config.
But it will also destroy old settings.

I actually did that last week (including gconf). While it did fix some things (hooray), it had no (zero, none, zilch) effect on my associations :(

---

### Post by taavikko on 2009-03-17
move few files to different location, and resstart sesion

```
cd; mkdir backups; mv .gconf/ .local/ .gnome2/ .config/ -t backups/
```

Does it help?
This way you can copy them back and restore your previous settings

---

### Post by OliW on 2009-03-17
> **taavikko said:**
> move few files to different location, and resstart sesion

```
cd; mkdir backups; mv .gconf/ .local/ .gnome2/ .config/ -t backups/
```

Does it help?
This way you can copy them back and restore your previous settings

I just moved .local and .config out the way and one of those did the job with the added bonus of cleaning up a whole load more cruft at the same time.

Thank you!

---

### Post by sdowney717 on 2009-03-17
I think you could open synaptic and do a total remove with configurations.
Then reinstall and it would be back to normal.

I had setup PCMan file manager to take over Nautilus. When I removed and reinstalled Nautilus, Nautilus was opening everything again.
PCMan file manager is so fast compared to Nautilus. I almost cant stand Nautilus anymore.

---

### Post by OliW on 2009-03-17
I was under the impression (or delusion if I'm incorrect) that removing config didn't remove user config (~/....), but only system config (/etc/...).

---

### Post by taavikko on 2009-03-17
> **OliW said:**
> I was under the impression (or delusion if I'm incorrect) that removing config didn't remove user config (~/....), but only system config (/etc/...).

Yes, reinstall or purge doesn't effect ~/

---

