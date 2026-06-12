---
title: "Anyone able to get Cairo Dock to display?"
date: 2017-10-19
forum: Installation &amp; Upgrades
---

### Post by JoelParke on 2017-10-19
HI,

I upgraded from 17.04 -> 17.10. 
Now my Cairo Dock shows as running, but I can't close it, and it does not show anywhere.  
If I run it again, it shows that two instances are running.
BUT if I right click on the icon, and click on 'Quit 2 WIndows' it does NOTHING!

Has anyone gotten Cairo dock to work properly?

also I noticed that it took a few reboots and attempts for Ubuntu to access my google accounts.

Thanks,
Joel

---

### Post by JoelParke on 2017-10-20
After deleting the ~/.config/cairo-dock directory.
And re-running cairo-dock and configuring  -- it is better.
BUT setting the display to the bottom, causing the dock to show up near the top of the display!

If anyone has been able to get the configuration to function properly,  please let me know.

---

### Post by leunam12 on 2017-10-20
I have been using cairo-dock for many years and I have never had a problem with it. All I do is install it and set it to auto start on boot. No extra configuration needed other than pinning your favorite programs to the dock. What are you trying to do? Is this a problem related to 17.10 or have you had problems before?

---

### Post by JoelParke on 2017-10-20
It seems only related to 17.10.  In the past, I needed to rebuild from the source in order to get the weather extension working.  That is no longer needed.  
I believe the issue I am seeing is related to a problem with understanding the vertical positioning.  Selecting top or right works as expected.  Please let me know if bottom selection for position works for you.

I will also check if there are any pieces of my build from source left on my system.
I have uninstalled cairo-dock and it's dependencies.
And reinstalled - but this was not help.
Thanks!

---

### Post by orangereaper on 2017-10-21
HI Guys, Confirm that I have the same problem here.

> [COLOR=#000000]deleting the ~/.config/cairo-dock directory.[/COLOR]
[COLOR=#000000]And re-running cairo-dock and configuring.[/COLOR]

Made no difference for me. Any help here would be gratefully received. TIA. ;)

---

### Post by JonPaul on 2017-10-21
Try logging out and logging back in with Ubuntu on xorg. Click on the cog by the password box.

---

### Post by orangereaper on 2017-10-21
Thanks a million. That fixed it straight away! :guitar:

---

