---
title: "Feisty not showing up in Update Manager"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by JimMattingly on 2007-04-22
I tried to use the: "System->Administration->Update Manager"  method and then the: gksu "update manager -c" method, but for some reason I can't see the window that allows you to just press the "upgrade' button inside Update Manager.

I did see it when I first opened Update Manager, but had to exit because not enough space was available.  So I cleared out enough disc space, tried the gksu method and accidentally closed out the terminal.  After that, the update box would not show up for either method.

Ideas?

Thanks! JM

Dell Latitude C Family (Model: PPX)
Pentium III (Coppermine)
Memory: 255MB
Battery: Dell Battery Module (Type: 75UYF)
O.S.: Ubuntu 6.10
Using Gnome

---

### Post by Artemis3 on 2007-04-22
[https://bugs.launchpad.net/update-manager/+bug/108541](https://bugs.launchpad.net/update-manager/+bug/108541)

---

### Post by JimMattingly on 2007-04-22
From the bug report:
> So I have downgraded the package update-manager to the previous 0.45.2 version and now the upgrade button is again displayed.

So how do I downgrade update-manager?

---

### Post by Artemis3 on 2007-04-22
To downgrade a package from synaptic, select it and right click to choose "force version".

---

### Post by Jonas_Henricsson on 2007-04-23
Um, I have update-manager v. 0.45.2 and I still don't see the upgrade... I tried downgrading it to 0.45 but I couldn't see it anyway...

Any ideas?

---

### Post by mvo on 2007-04-23
The bug in 0.45.3 should be fixed with the recent 0.45.4 upload, see
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/109216](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/109216)

If people still see no button, please file a bug in launchpad and include the ~/.update-manager/meta-release file there.

Thanks,
 Michael

---

