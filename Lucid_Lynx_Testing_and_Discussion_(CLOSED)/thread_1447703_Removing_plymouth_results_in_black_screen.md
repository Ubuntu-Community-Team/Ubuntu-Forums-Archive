---
title: "Removing plymouth results in black screen"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by null_pointer_us on 2010-04-05
Ubuntu 10.04 beta 1 (AMD64) on VirtualBox 3.1.6

My system booted successfully, but I get random crash notifications (frequently) about plymouthd and (rarely) xorg. So I opened the software center app and told it to remove plymouth (main) package, which it apparently did. Part of the way through the removal process, the screen went black although the hard drive light remained quite active.

Eventually the hard drive light stopped completely. The system was unresponsive at this point. CTRL+ALT+Fn for the virtual terminals 1-7 did absolutely nothing. Then I tried using the VM's ACPI power button to tell the OS to shutdown. No change. Finally, I reset the machine.

The next attempted boot produced this:
```
error: file not found.
error: file not found.
error: you need to load the kernel first.

  Failed to boot both default and fallback entries.

Press any key to continue...
```

Pressing any key just prints another copy of the above message.

I'm guessing my grub config is broken. My searches on the forum and using Google turned up nothing.

(This VM has a snapshot before removing plymouth; it can be restored to a working state.)

What is the proper procedure for removing plymouth?

Yes, this is a beta and such issues are expected. I'm not complaining. It's just that clicking a button in the software center app shouldn't break the system, so something needs to be changed before release.


EDIT:

After using [COLOR="Sienna"]sudo /etc/init.d/gdm stop[/COLOR] to drop the system out of gnome and into a cli, I checked out the result of [COLOR="Sienna"]sudo aptitude remove plymouth[/COLOR]. The problem is that it removes the kernel, too. Yet the software center allows this with a single click (i.e. no warning!), which seems like a bug.

Should this be reported as an software center bug?

---

### Post by Jordanwb on 2010-04-05
They made plymouth a dependency for literally everything. If all you want to do is disable plymouth try removing "splash" from the kernel params.

[Edit]

If that works, you'll need to edit /etc/default/grub, find "splash" and remove it.

---

### Post by null_pointer_us on 2010-04-05
Thank you!

Disabling plymouth (by removing [COLOR="Sienna"]splash[/COLOR] kernel parameter) appears to fix:

 - auto eth0 disabled even though it's configured to auto connect
 - random crash reports about plymouthd and xorg at startup

I'm still seeing messages about a failure to read bytes, but that appears to be an unrelated open bug with plenty of attention in launchpad.

---

### Post by Korcia on 2010-04-06
> **Jordanwb said:**
> They made plymouth a dependency for literally everything. 



What!!!! OMG, this is becoming the new Windows.

This is really sad.

---

### Post by hikaricore on 2010-04-06
> **Korcia said:**
> What!!!! OMG, this is becoming the new Windows.

This is really sad.

It's not quite that bad but it is a pain in the ***.
There are several ways to fix this issue but none are really easy for new users.
Hopefully they'll fix the problem or remove the dependency issue.

---

