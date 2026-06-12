---
title: "Upgrade question re:partitions"
date: 2024-09-24
forum: Installation &amp; Upgrades
---

### Post by operator-error on 2024-09-24
I'm currently running Kubuntu 22.04. I keep my /home directory on a separate partition. I normally do a fresh installation when a new LTS comes out. This time, however, I've decided to try the upgrade path, instead. Can I assume that the upgrade process won't alter my partition structure? I'm assuming it won't but I thought I'd ask the question just to be safe. Thanks in advance for your replies.

---

### Post by deadflowr on 2024-09-24
It won't change the existing partitioning setup.
There may be many things an upgrade does, but changing the existing partitioning has never been one of them.

And if it, somehow against all historical instances and behaviors, did, it would prompt you that a change was needed.
And you'd need to confirm or deny it in order to proceed further.

---

### Post by operator-error on 2024-09-24
Much appreciated. I assumed that was the case but wanted to bounce the question off someone with more experience than me. Thanks.

---

### Post by guiverc on 2024-09-24
This isn't what you're asking, but it maybe useful knowledge as backup.

Kubuntu 22.04 LTS use the `ubiquity` installer which allowed *non-destructive *re-installs, Kubuntu 24.04 LTS uses the `calamares` installer which likewise allows *non-destructive re-installs*.  The replacement for `ubiquity` for Ubuntu Desktop and most *flavors* is `ubuntu-desktop-installer` which does not allow *non-destructive* re-installs for all options the prior `ubiquity` installer allowed for in comparison.

In your case, I'd do the *release-upgrade* IF you have sufficient disk space to allow for it (*as all software is downloaded prior to any installs being performed, quite a bit of free space is required*).

I keep the *non-destructive* re-install as backup, should

- I have problems with the *release-upgrade*; I see it as an easy fix
- if I lack sufficient space for *release-upgrade*, as there is* comparatively limited* download (*packages come from the install media*) this method works with limited disk space
- Lastly if I lack time, as a *non-destructive* time is far faster, I often opt for this just to get it down quicker

If interested in this, I'll provide two links where I talk about it

- [https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533)
- [https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743](https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743)  (*see 'Upgrading using Existing Partition' testcase*) ; Lubuntu QA tested for it up to 24.04

Benefits of a *release-upgrade *(over clean install)

- changes you made to your setup are preserved
- defaults set by prior release will persevere (*ie. your system will act more like it did before*)

Whilst a *non-destructive* re-install will keep some of those benefits, many defaults (*esp. those set by your install media*) will not survive even with a *non-destructive* or *unclean* install that I've talked about here.

Example..  Kubuntu being a *flavor* has different kernel stack defaults to Ubuntu Desktop (20.04 & later, as Ubuntu Desktop changed its default at 20.04; here I'm talking about GA/HWE/OEM); a *release-upgrade* will keep whatever default you installed with (*in this case its packages that determine your default kernel stack*).  A *clean* or *unclean* install will cause the system to use the defaults of the newer install media (*thus initial install media defaults are overwritten*); with only the *release-upgrade* offering the chance to keep the initial defaults your system had.

Re-install, or *release-upgrade* are different options.  The *release-upgrade* option will cause the least change[I].


[/I]FYI:  The *non-destructive* install method is just an install **without format**, it's also an *unclean* or *dirty* re-install as much survives from the prior install. It'll fix package & other type issues, however if you have bad user configs on the system - those will remain untouched (*thus unclean or dirty*) which can mean some problems will survive re-install.  To me its a useful option.

---

