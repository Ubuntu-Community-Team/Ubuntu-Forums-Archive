---
title: "Install issue for 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by 1slackr on 2010-04-30
I have an IBM X40 laptop running  9.10.  Went through 4 plus hours of upgrade. After reboot, new Ubuntu splash screen come up, then blank screen, then everything stops. Is there a way to get back to 9.10 after the upgrade?

---

### Post by doktorOblivion on 2010-04-30
What I normally do when this occurs is do a pristine install of the former version, but, choosing full manual partition control so that you can keep your old /home partition around.  If you did not make it a separate partition, you might be in trouble.  If you chose to remove the old packages, this may be your only way out.  If you haven't and they are still around, there might be something you can do by getting into single user mode and use dpkg or synaptic to backout the new system, but I doubt it.

Good luck.

---

### Post by 1slackr on 2010-04-30
Thanks Dr. .I can boot from the 9.10 CD and all my files are still there. .Ill try running thru the install. MS

---

