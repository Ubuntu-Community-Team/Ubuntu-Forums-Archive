---
title: "Update-manager PROBLEM!!! Ghostly Mysterious Upgrades"
date: 2008-10-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by american.swan on 2008-10-30
update-manger gives me three updates.   kdeedu-data, libkcddb1, libkdegames1
update-manger refuses to remove them from the list of possible updates.  Why do I want them removed?  Because synaptic says I have NO possible updates!!!  

How do I get update-manager and synaptic to AGREE.  I even REINSTALLED the three packages and update-manager still doesn't listen or know.

HELP!!

---

### Post by Yashiro on 2008-10-30
Perhaps there is confusion over versions because you have some 3rd party repositories enabled?

Open /etc/apt/sources.list ([COLOR="Green"]gedit /etc/apt/sources.list[/COLOR])

Any url's pointing to domains that are not ubuntu.com or canonical.com are ones you have added.

---

### Post by american.swan on 2008-10-30
I commented out ALL non Intrepid related upgrades and it might have fix the problem.

---

