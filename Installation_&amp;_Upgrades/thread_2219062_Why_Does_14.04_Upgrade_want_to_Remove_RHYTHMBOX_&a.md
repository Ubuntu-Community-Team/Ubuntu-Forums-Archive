---
title: "Why Does 14.04 Upgrade want to Remove RHYTHMBOX &amp; GNOME CLASSIC &amp; Can I Stop That?"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by OzzyFrank on 2014-04-22
Hi. My system has various desktop environments and currently am using KDE, in which running the 14.04 upgrader I'm informed that 76 packages will be removed, among them Rhythmbox and all its plugins, and also gnome-session-fallback. I've checked that among the 320+ new packages to be installed these aren't in there with slightly different names, and of course they're not in the huge list of packages to be upgraded (otherwise they wouldn't be in the list of packages being removed). Besides not understanding why many other apps like 2mandvd need to be totally removed, I'm at even more of a loss to understand why everything to do with Rhythmbox needs to be uninstalled, and also why Gnome "Classic" needs to be removed. Anyone know anything about this? And is there a way to continue the upgrade without removing these, as I'm only going to have to reinstall them again anyway. Many thanks in advance.

---

### Post by ian-weisser on 2014-04-23
Is Rhythmbox marked as automatically installed or manually installed?

```
apt-mark showauto rhythmbox
apt-mark showmanual rhythmbox
```

If Rhythmbox is automatically installed, then the *buntu-desktop dependency (the default application) changed. Try changing Rhythmbox to manually-installed to prevent autoremoval.
```
sudo apt-mark manual rhythmbox
```

---

### Post by OzzyFrank on 2014-04-23
Hi, and thanks for your reply. OK, the first command shows nothing in the terminal, while the 2nd comes up with **rhythmbox** as the output. I should also add that a few months back I did in fact add the developer's PPA and install the very latest version that way, basically so I could get all the plugins (which are slowly being rewritten for the 3.x series). So I guess that makes it "manual"... so will the 3rd command still work, or it that only if Rhythmbox was automatically installed? And if it does work, I guess I'd have to do the same for the various plugins that the system wants to remove?

As for gnome-session-fallback, I guess you could say I manually installed that, as an upgrade or two ago it was removed, so I had to reinstall it, though just the usual way through the standard repos, no PPA or anything. Anyone have any ideas why the 14.04 upgrade wants to remove this too?

---

### Post by OzzyFrank on 2014-04-23
I've been reading up a bit on **apt-mark**, so thanks for alerting me to its existence. One option that seemed promising is **unmarkauto**, but then it seems like it is just another way of setting to **manual**? Anyway, I just ran the upgrader again to see if it still wants to remove rhythmbox, which is definitely set to manual now, if it wasn't already, and sure enough it still wants to remove it. I can understand, perhaps, Ubuntu wanting to upgrade Rhythmbox to the supported version from one I manually installed, but not why it would want to remove it and all its plugins, especially as I gather Rhythmbox is still the default music player in 14.04(?). Anyway, I'll try again later with **apt-mark hold**, and see if that prevents Rhythmbox from being added to the list of apps to be removed.

---

### Post by ian-weisser on 2014-04-24
If you installed Rhythmbox (and it's dependencies) from a PPA, then it's understandable. Many PPA authors are imperfect at correctly naming or versioning the dependencies for future upgrades. A human may understand that libfoo_a and libfoo_2.3 are merely different versions of libfoo, but dpkg strictly expects proper debian naming.

---

