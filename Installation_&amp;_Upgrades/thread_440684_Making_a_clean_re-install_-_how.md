---
title: "Making a clean re-install - how ?"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by jellyfisharepretty on 2007-05-11
My Ubuntu box at work is breaking apart -  the result of too many upgrades since breezy but mostly the result of me trying to customize everything !

I want to do a clean re-install of feisty.  My plan is to backup my home folder completely on another computer.  Then I'll install feisty and any additional programs I need and copy over my home folder.  Hopefully most of the applications will read their hidden directory (for example wine will read .wine) and the settings will be restored to just the way I like.

I would also keep a copy of my xorg.conf and my repository list file and place them appropriately on my new system.

Is this a good plan ?  What would you suggest for doing a re-install without losing application settings ?

More generally, your strategy for doing a re-install ?

---

### Post by starcraft.man on 2007-05-11
Well I guess the general steps I would do it is:

1) Reinstall from Live/alternate, with a home partition of right size.
2) Replace your sources file and update/upgrade all things installed.
3) Install all the drivers you are missing, and reconfigure your Xorg accordingly at each step. I wouldn't back it up its not so hard to do modify it the few times you need to, and if you don't install all your drivers/modifications then the xorg will be wrong and might fail to load your xserver.
4) Reinstall all the applications you had before (wine for instance).
5) Copy over the contents of the old folders into the new ones individually and just replace whats there.
6) Reboot and cross fingers everything is fine :D

Should be fine though, if you do everything in that order I think.

---

### Post by jellyfisharepretty on 2007-05-11
That seems like a good procedure. Thanks a lot !

I'm definitely keeping my xorg.conf, maybe just so I can refer to the nvidia driver settings section.  Maybe I won't copy it over entirely.

However, the thought just occurred to me... might there be a way to make apt install everything there is now on my computer on the new system.

For example, I backup a file from apt that lists all the installed applications, copy that file over to the new system, run apt-get update, apt-get upgrade (or something) and all the missing applications are installed ?

No doubt this is NOT a recommended procedure.  I was just wondering if there might be a way to do something of the sort.

---

