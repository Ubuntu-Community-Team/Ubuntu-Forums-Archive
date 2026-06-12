---
title: "Volume icon disappears when &quot;Envelope&quot; is removed"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-03-21
I hated to file a bug on something this trivial, but Audio, and its manipulation is a core OS component, while some mail feature is not.

[https://bugs.launchpad.net/indicator-applet/+bug/543592](https://bugs.launchpad.net/indicator-applet/+bug/543592)

---

### Post by 23meg on 2010-03-21
If you want the "envelope" gone only, remove the indicator-messages package, and keep indicator-sound (which is for the volume) and indicator-application installed. Don't remove indicator-applet, which is the host applet that all of the above plug into.

---

### Post by emarkay on 2010-03-21
> **23meg said:**
> If you want the "envelope" gone only, remove the indicator-messages package, and keep indicator-sound (which is for the volume) and indicator-application installed. Don't remove indicator-applet, which is the host applet that all of the above plug into.

Thanks!
That is what I heard on the bug report - Just that this is new behaviour and wanted to post it for others.  :)

---

