---
title: "Rewriting MBR and then reloading GRUB2"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by benjihall on 2010-02-12
Hi.  

I'm new to Linux and the forum.  I did a search for this and think I know what I have to do but wanted to check first before I started messing around with my MBR.

Originally was running XP and installed WUBI 9.10 to play around with Ubuntu before doing a proper install.  Got home from work tonight and removed WUBI leaving edited MBR with WUBI boot loader.  I thought I might have to run fixmbr before installing Ubuntu but I assumed Ubuntu would write over WUBI edited MBR.  Installed Ubuntu 9.10 and everything is fine but when I select XP from first boot option (Ububtu) it then takes me to another boot option which was from the WUBI install.

Basically to get to XP, I have to select it twice.

It's not a big issue but I know that this will annoy me and one day or another I will try and remove the second unnecessary option to boot into XP.

So if I have this correct I will need to run fixmbr from XP disc and then install Grub 2.0 from Ubuntu disc somehow?

Is this right?  Is there another way I can delete the second boot option screen?


Thanks in advance.

---

### Post by darkod on 2010-02-12
Boot XP and open C:\boot.ini (it's probably a hidden file). Just delete the whole line where the ubuntu (wubi) entry is. NOTHING ELSE!
This will get rid of the left over wubi-ubuntu entry.
This was supposed to be done before installing ubuntu so I'm not sure but it should pick up the change and stop the two-stage booting process.
After doing the above and checking if XP is booting fine, boot ubuntu and in terminal do:

sudo update-grub

Maybe only after that the two-stage boot will be removed, not exactly sure.

---

