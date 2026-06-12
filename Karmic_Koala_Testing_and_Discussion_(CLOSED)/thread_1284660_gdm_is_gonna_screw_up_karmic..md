---
title: "gdm is gonna screw up karmic."
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by schmolch on 2009-10-06
I use karmic on 3 machines and the new gdm is still a horrible mess.
It often remains on the Desktop far too long or even keeps X's cpu-usage at 100% forever.
There is no way that gdm will be working reliably in only 2 weeks.

Please delay Karmic until it works, Jaunty was bad enough.

---

### Post by 3rdalbum on 2009-10-06
Is this a known bug, i.e. is it in Launchpad? I didn't notice it when I was running Karmic.

---

### Post by nhasian on 2009-10-06
yes i didnt notice any problems either.  I have karmic running on two HP laptops and the new gdm is working fine for me.  one is set to auto-login and the other uses the default settings.

---

### Post by MKdx on 2009-10-07
It runs perfectly fine on my machine, and faster than Hardy which I had before. The only problem I have with it is the colours, but that's different issue.

---

### Post by autocrosser on 2009-10-07
> **schmolch said:**
> I use karmic on 3 machines and the new gdm is still a horrible mess.
It often remains on the Desktop far too long or even keeps X's cpu-usage at 100% forever.
There is no way that gdm will be working reliably in only 2 weeks.

Please delay Karmic until it works, Jaunty was bad enough.

Check my bug report & see if it is your problem, if so--add to it: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)

The problem is most likely grub2 instead of gdm, verify if the grub menu is taking too long or gdm login screen.

---

### Post by ikisham on 2009-10-07
Note that this is officially risky...
but you could try to update the system.

Besides the warnings about partial upgrades (they can brake the system), I did one before I read the warning (a few days ago - from the beta torrent alternative cd image, which still hadn't the new gdm theme) and it actually improved something the boot process.
The GRUB2 version here is 1.97something, so its newer than the one in the bug report.

---

