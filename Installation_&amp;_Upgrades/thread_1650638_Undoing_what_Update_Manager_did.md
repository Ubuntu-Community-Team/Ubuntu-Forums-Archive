---
title: "Undoing what Update Manager did"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by xtheunknown0 on 2010-12-22
Last night I downloaded and installed 359 "recommended updates" for Lucid and now the Lucid VM in VBox won't go full screen correctly, like it used to. I'm willing to do anything to *restore* the system to the way it was before. What can I do?

TIA,
xtheunknown0

---

### Post by xtheunknown0 on 2010-12-22
bump

---

### Post by xtheunknown0 on 2010-12-23
bump

---

### Post by miegiel on 2010-12-23
> **xtheunknown0 said:**
> Last night I downloaded and installed 359 "recommended updates" for Lucid and now the Lucid VM in VBox won't go full screen correctly, like it used to. I'm willing to do anything to *restore* the system to the way it was before. What can I do?

TIA,
xtheunknown0

I was hoping to learn something new in this thread. I'm a little disappointed to only find bumps.

Anyway, in reply to your post: I think it might not be possible. Or if it is, you'll need to navigate through a minefield of dependencies.

You could check [launchpad]("https://bugs.launchpad.net/") to see if there's a bug reported. And, who knows, help working on a fix.

---

### Post by ottosykora on 2010-12-23
well restore might not be possible unless you have some kind of backup image of the system somewhere.

But if it is just for the case of the virbox, I would just save all virtual machine somewhere separate and simply uninstall the whole virbox. Then install it again from repository.

The problem with the vixbox is, that to each kernel it needs separate modul and it could be that this was somehow missing.

---

### Post by xtheunknown0 on 2010-12-25
> **miegiel said:**
> I was hoping to learn something new in this thread. I'm a little disappointed to only find bumps.

Anyway, in reply to your post: I think it might not be possible. Or if it is, you'll need to navigate through a minefield of dependencies.

You could check [launchpad]("https://bugs.launchpad.net/") to see if there's a bug reported. And, who knows, help working on a fix.

By browsing through launchpad I picked up the keyword 'resolution'. I played around with System->Preferences->Monitor Preferences and I've fixed the problem.

Why can updates to Ubuntu modify the original, working settings to the resolution after Guest Additions?

xtheunknown0

---

### Post by xtheunknown0 on 2010-12-26
bump

---

### Post by xtheunknown0 on 2010-12-30
bump

---

### Post by miegiel on 2010-12-30
> **xtheunknown0 said:**
> ...

Why can updates to Ubuntu modify the original, working settings to the resolution after Guest Additions?

...

Sometimes old configuration files are not compatible with updates and get replaced with a new default configuration. Are you still having problems, or is it solved now?

---

### Post by xtheunknown0 on 2011-01-07
> **miegiel said:**
> Sometimes old configuration files are not compatible with updates and get replaced with a new default configuration. Are you still having problems, or is it solved now?

No problems, it's solved. I was curious, though.

xtheunknown0

---

