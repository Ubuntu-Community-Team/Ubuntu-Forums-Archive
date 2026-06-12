---
title: "Update/upgrade: karmic development version? What did I do, and how do I un-do it?"
date: 2009-07-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mander on 2009-07-13
Ok, I just installed Jaunty from the Live CD a few days ago.  Everything was fine, after getting the various drivers, tweaks, etc. fixed.

Earlier today, while installing some programs with Synaptic, I realized that I hadn't seen an update notification icon in the panel, and went investigating.  I found the instructions to restore the previous behavior (gconftool -s --type bool /apps/update-notifier/auto_launch false), after which there were a ton of updates showing.

I had already changed the preferences in Synaptic to only show LTS release upgrades.  However, I clicked on highlight all updates, then clicked apply, then walked away.  After it installed tons of stuff, it asked whether I wanted to replace gdm.conf and menu.lst, which I suppose should have been my clue that something wasn't quite right.

When I restarted, the only entries I have in grub are for the Karmic development version of Ubuntu (and Vista, which I am using now).  I tried one of the recovery modes, but it didn't seem to have any useful options for this circumstance.  I can only log into the text consoles in Ubuntu; the graphical log-in screen never appears.  I tried to do 

sudo /etc/init.d/gdm start

but it doesn't work, just gives me a black screen with a blinking cursor.

How can I roll back to normal Jaunty?  Or do I have to start all over again with a clean install?  How do I figure out what I did wrong in the first place, so that I can avoid that mistake in the future?

---

### Post by csabo2 on 2009-07-13
While i'm not sure this would work. I would say first ensure your sources are correct for Jaunty (nano /etc/apt/sources.list) then do an update (sudo apt-get update) and then, apt-cache search for kernels, and then lastly install one :) as for the Grub entries I would just delete them.

---

### Post by Mander on 2009-07-17
I'm still not sure what happened, but in the end I decided that it was going to be easier to just re-install.  Fortunately it had only been a few days since I upgraded so backing up new settings was a minimal project.

I must have put the wrong deb line into my sources list or something, somewhere.  I didn't find it, though.

---

