---
title: "Upgrade to final version of ubuntu 10.10 not possible, only rc is available"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by atahu on 2010-10-11
Hi,

I try to upgrade from ubuntu 10.04 to 10.10, but there is no final version available when I press Alt + F2, only the release candidate. What is the problem here and what can I do?

---

### Post by lupe on 2010-10-11
Use the menu in System->Administration->Software Sources, Tab "Updates", under "Release upgrade" to select "Normal releases" rather than "Long term support releases only".

---

### Post by atahu on 2010-10-11
I ve changed it, but there is still only the rc available, very strange. Or should I reboot my computer?

---

### Post by atahu on 2010-10-11
Now it works when I press system - > updates from the menu, but it doesnt work with alt + f2. thank you for help

---

### Post by PattiMan on 2010-10-11
I have the same problem. I've set Release to "Normal", but still I don't get an update notification. There are 4 updates available which I can't select or update. Maybe that's the problem?

---

### Post by illusioniz on 2010-10-14
Try alt+f2, then run **update-manager** but without the -d option. It works for me :)

---

### Post by garvinrick4 on 2010-10-14
Some of the mirrors are behind by a week or more and some are up to date, some have larger band-width and their are over 300 mirrors to choose from.  In Software sources you can change, maybe you are all using mirrors that are behind. Notice Download from in screenshot.
[https://edge.launchpad.net/ubuntu/+archivemirrors](https://edge.launchpad.net/ubuntu/+archivemirrors)

---

