---
title: "Compatibility Problems?"
date: 2012-03-25
forum: Installation &amp; Upgrades
---

### Post by Somnium91 on 2012-03-25
Hello, first of all, and I do appologize if I posted this in the wrong section but I can't seem to get anything right the past 2 days.

I'm using Ubuntu 11.10 as a standalone OS.

So, the problem is the compatibility o Wine (I have the 1.3 release) with the WoW client, patched up to 3.5.5. I've read the config files and the support on the site, and it does say it's fully supported.

Graphics came out positive and the config files are set to run the game with openGL instead of DX.

However, for some reason, the game just won't start. I don't get any errors or anything like people that use windows partitions do, but Wine loader just starts up, I see the icon on the taskbar and then closes without an error or any warning.

Also, I've copied the WoW folder to a pendrive and just transferred it to my /home folder.

Any thoughts would be appreciated.

---

### Post by dino99 on 2012-03-25
- use the latest wine (update/upgrade your packages via synaptic)
- rename actual .wine (inside /home, unhide it with ctrl+h)
- reinstall wine1.4 to get a fresh .wine
- reinstall wow (see winehq url appsbase about wow)

---

