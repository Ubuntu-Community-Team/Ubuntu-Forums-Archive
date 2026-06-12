---
title: "Updating When Power Cut Out"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by Kodeine on 2012-12-19
So after finishing several updates to such things as the kernel and graphics driver I left the computer running to go down stairs. When I left it had finished installing everything and was just waiting for me to restart. But in my absence the electricity went out in the house. So although the installation of the updates weren't heeded the computer didn't have a clean reboot.

Steam refuses to come on citing in terminal that it has 'not shutdown cleanly' (Asked on steam forums). My unity panel has changed colour (not sure if one of the updates was for unity) and there seems to be a rather considerable performance regression. Typing ten or so characters into the dash leaves it playing catch up as it fairly slowly displays what I typed and videos seem to play fine when in fullscreen but seem to be every so slightly laggy when not in fullscreen.

How could I fix this? Is it possible to find what packages were updated recently and reinstall them?

---

### Post by CharlesA on 2012-12-19
I don't use update manager, so I don't know if there is a log for which packages are installed.

Have you already tried shutting the machine down and bringing it back up so it starts off on a clean slate?

---

### Post by Kodeine on 2012-12-19
> **CharlesA said:**
> I don't use update manager, so I don't know if there is a log for which packages are installed.

Have you already tried shutting the machine down and bringing it back up so it starts off on a clean slate?

I've restarted but nothings changed.

*** I had a third party PPA that provided updates for my Intel graphics. I've reverted back to the stock Ubuntu drivers and now everything works much better. Seems the latest drivers have some performance woes.

---

### Post by CharlesA on 2012-12-19
If there is a way to find out the installed date, you could try checking that. Maybe Synaptic has something like that, but I rarely use GUI package managers.

---

### Post by ajgreeny on 2012-12-19
Try ```
grep -iw upgrade /var/log/dpkg.log.1 && grep -iw upgrade /var/log/dpkg.log
``` which in 10.04 lists everything recently upgraded.

Change the word ***upgrade*** to ***install*** or ***remove*** for those actions.

I've not tried this in versions above 10.04, but I can't imagine dpkg has changed so much that it no longer works.

Note to self: must try it in Lubuntu 12.04 as soon as possible!

---

### Post by CharlesA on 2012-12-19
> **Kodeine said:**
> I've restarted but nothings changed.

*** I had a third party PPA that provided updates for my Intel graphics. I've reverted back to the stock Ubuntu drivers and now everything works much better. Seems the latest drivers have some performance woes.

Glad you got it working. :)

What a pain!

---

