---
title: "upgraded and cds &amp; dvds no longer auto mount"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by poadshaw on 2010-06-03
Ubuntu Experts

My system:  Ubuntu 10.04 fully updated

Ok This is the first time I've had an issue like this.  When I put a cd or DVD into my drive I see the the device being read (blinking lights on my cd-rom drive) but it seems nothing happens in Ubuntu.  No programs can use the cd.  For instance Brasero will not begin burning a blank CDR  

After further investigation I find if I open Places -> Computer  The CD is there... After I click on it it will appear on my desktop. Once this is accomplished All programs "see" the disk and can access it just fine.

This is quite an inconvenience to have an additional step every time I try and use my cd-rom drive.

I am still solidly in the intermediate Linux user stage.  so please list out commands and not just say what is in you fstab or whatever  :)  thank you so much for your help!

---

### Post by Jeroensum on 2010-06-03
Open up your Configuration Editor (In menu system tools) or via the terminal by executing: gconf-editor
Now lookup the automount tickbox:
/apps/nautilus/preferences/media_automount
If it's not ticked, tick it! :)

Also you might want to take a look at how nautilus handles your media:
Open nautilus -> Edit (menu) -> Media tab  for CD/DVD you can set specific actions, the default should be to ask you what to do.

---

### Post by poadshaw on 2010-06-03
in the Configuration Editor - Preferences

Media_automount & media_aoutomount_open are both ckecked.

Everything in Nautilus media tab is "ask every time" except for software which is "open autorun prompt"

These settings look fine to me, so the problem must be somewhere else.  Thank you for your responce, but it did not fix my problem.

Any other thoughts?

---

### Post by Jeroensum on 2010-06-08
Open nautilus -> Edit (menu) -> Media tab

On the bottom there are 2 tickboxes, make sure the one named *Browse media when inserted* has a tick and the one beginning with *Never prompt* has **not** been ticked.

That's about all I can figure out that could be wrong. Hopefully this fixes your prob :)

---

