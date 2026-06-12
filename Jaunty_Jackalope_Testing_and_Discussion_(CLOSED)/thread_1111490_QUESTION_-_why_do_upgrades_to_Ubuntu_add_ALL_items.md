---
title: "QUESTION - why do upgrades to Ubuntu add ALL items, instead of what's installed?"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-03-30
For example, the Malaysia, Lao and Arabic fonts, and things that I have uninstalled, like Evolution, Bluetooth support, Tomboy, Tracker, etc.?

I would expect a new install to have all this as a default, this, but is there a reason why and upgrade can't "see" what you have and use that as a baseline?

No big deal, just curious.

---

### Post by darkstaar on 2009-03-30
If it did that, you'd never see any new features.

---

### Post by emarkay on 2009-03-30
No, not even mentioning new features, just those that were deselected in prior version so as not to be selected in new version - Presuming anything new  beyond those items would be installed normally.

---

### Post by KhaaL on 2009-03-30
I agree with OP. I have to re-run a command that uninstalls a bunch of stuff i never use, so why shove them down on us again?

---

### Post by emarkay on 2009-04-03
Anyone???

---

### Post by xebian on 2009-04-03
How did you upgrade?  In synaptics, make sure unmark the box that says '..recommends as dependencies..'.  Any recommended that's going to be installed will also install everything that it recommends..and so on..

If through aptitude, pass the argument  --without-recommends.

---

### Post by Flywaver on 2009-04-03
> **xebian said:**
> How did you upgrade?  In synaptics, make sure unmark the box that says '..recommends as dependencies..'.  Any recommended that's going to be installed will also install everything that it recommends..and so on..

Is this the same as unchecking Recommended Updates (Jaunty Updates) in Software Sources / Updates ??

---

### Post by ronacc on 2009-04-03
no it is a different thing , in synaptic go to settings>preferences and uncheck "consider recomended packages as dependencies" .

---

### Post by xebian on 2009-04-03
> **Flywaver said:**
> Is this the same as unchecking Recommended Updates (Jaunty Updates) in Software Sources / Updates ??

I don't think so.  You are talking about the repositories which is totally different.

A debian package has a list of dependencies which are required.  Then they have what are 'recommended' and 'suggested' which are not required for the package to work.

---

### Post by Flywaver on 2009-04-03
ok...thanks for the infos! :)
Cheers!

---

### Post by phenest on 2009-04-04
There is a permanent way round this. Open Synaptic and go to the package you want to keep uninstalled, i.e Evolution. Hi-lite it (click on it), click Package (menu bar) > Lock Version. You will then have a new entry on the left called 'Pinned'. This is a list of packages that will not be upgraded.

---

