---
title: "Ubuntu 8.10 (before I install question)"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by MichaelLerch on 2008-04-08
I see the 8.10 beta is nearing an official release.  Any idea when the official date is?  If not, here's my question.  If I install the beta now, will it upgrade within OS or would I need to download the latest ISO and upgrade/reinstall from there?

Also, does anyone know if this build installs properly with Vista?  I have Windows Vista already installed, and I really don't feel like doing a full format of anything except that 500GB drive I'm going to be installing Ubuntu onto.. so, does this build actually set up the bootsector with GRUB so I can select Vista or Ubuntu, or will I have to set it up manually like last time...

---

### Post by JDorfler on 2008-04-08
I'm pretty sure you mean 8.04 Beta.  Okay, you don't have to reinstall everything.  Right click on Applications and select Edit Menus.  From there on the right menu select Administration.  In the right menu find Update Manager and right click.  Select Properties.  At the end of the line that says Command add -d at the end of the written command.  It should like something like this, "/usr/bin/update-manager -d".  Now just hit update.  You should get a little message saying that 8.04 is available.  Go ahead and hit Install.  This will also auto update you from beta to release when the actual release comes out.  Good luck.

---

### Post by MichaelLerch on 2008-04-08
Thank you sir =]

---

### Post by JDorfler on 2008-04-08
No problem.  Also, if you just let this ride, when 8.10 starts to come out you will soon get the option to upgrade to 8.10 as well.  I wouldn't check this option until you feel you are ready.  Early Alpha releases can be a pain.

---

### Post by muteXe on 2008-04-08
i think the release date is 24th April 08.

mute

---

