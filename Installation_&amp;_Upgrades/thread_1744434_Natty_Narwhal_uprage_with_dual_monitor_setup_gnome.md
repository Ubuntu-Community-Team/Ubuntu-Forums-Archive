---
title: "Natty Narwhal uprage with dual monitor setup gnome panel can't load applets"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by roadkilla on 2011-04-30
I upgraded to Natty from Maverick and I'm using the Ubuntu Classic interface with effects disabled.

the issue is like this gnome-panel is not loading applets on my secondary monitor
whenever I try to load an applet I'm receive the error message
"Applet Name" has quit unexpectedly.
Reload Don't Reload

I tried resetting the panel using
```
rm -rf ~/.gconf/apps/panel
gconftool --recursive-unset /apps/panel
pkill gnome-panel

```
which did reset the panel but did not helped me getting my applets loaded,as I said previously this issue only happens on my secondary monitor
the primary monitor has gnome-panel working as it should loading whatever applet I like without errors.

I seek help in solving or debugging the issue.

Thanks,
Roger

---

### Post by jcoffland on 2011-04-30
I have the same problem.  I've got dual Nvidia monitors with dual X servers not TwinView.  TwinView does not work well with my monitors.

Anyone know how to fix this?

I've created this bug report: [#774427]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/774427")

---

### Post by roadkilla on 2011-05-01
I'm using Nvidia too I tried to use Nouveau at first but the issue was present there too, same exact setup separated X screen.

---

### Post by jcoffland on 2011-05-01
@roadkilla If you haven't already you should create a launchpad account and mark the bug as "affecting you" in order to increase its priority and likelihood of being fixed.

---

### Post by roadkilla on 2011-05-02
> **jcoffland said:**
> @roadkilla If you haven't already you should create a launchpad account and mark the bug as "affecting you" in order to increase its priority and likelihood of being fixed.

I already did :)

---

### Post by Fabucci on 2011-05-02
Is there a way I can add "me too" to his ticket?

---

### Post by CoatedMoose on 2011-05-15
I had this exact problem. To fix I searched gnome in synaptic package manager and reinstalled anything with a green box and upgraded anything that needed it. It seems with the upgrade to 11.04 that a bunch of packages didn't update.

---

