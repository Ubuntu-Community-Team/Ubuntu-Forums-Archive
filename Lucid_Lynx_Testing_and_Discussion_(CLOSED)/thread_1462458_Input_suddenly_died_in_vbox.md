---
title: "Input suddenly died in vbox"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by null_pointer_us on 2010-04-25
Host: Windows 7 x64
VM: VirtualBox 3.1.6 (puel)
Guest: Ubuntu 10.04 RC (amd64)
Guest Additions Installed: Yes

I was working in Firefox, Monodevelop, and had Rhythmbox streaming audio from last.fm. While using the scrollwheel in Monodevelop, my mouse and keyboard suddenly stopped working.

No matter where I moved the mouse, the cursor remained as the text selection bar. Music kept playing normally and the screen continued (e.g. system monitors graphs) as if there was absolutely no problem.

When this happened, the only keyboard shortcuts that would work were the virtual terminals (e.g. ALT+F2), but the screen on the virtual terminals just showed a portion of the desktop. Trying to login blindly and execute [COLOR="Sienna"]sudo reboot[/COLOR] had no effect.

Sending the ACPI shutdown signal normally works, but this time it had no effect.

Ultimately, I made the VM do a hard reset on the guest.

What failed, and how do I gather information about it?

---

