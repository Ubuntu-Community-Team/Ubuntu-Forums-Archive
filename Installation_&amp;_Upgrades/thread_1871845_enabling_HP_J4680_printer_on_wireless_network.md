---
title: "enabling HP J4680 printer on wireless network?"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by Bobrm2 on 2011-10-29
For some reason I've lost the ability to communicate with the HP J4680 networked printer.  Within System/Administration/printing/properties/state there is a box to be checked that enables the printer(?). A click in the box briefly marks the box then disappears.  Network has been identified correctly. System functioned correctly (Ubuntu 10.10) as a wireless connection, until upgrading the other computer on this home network to 11.10. That computer identifies and prints correctly?

---

### Post by Bobrm2 on 2011-10-29
It seems that the HPcups backend is the problem:

Error Message: Printer State  Idle - /usr/lib/cups/backend/hp failed.

Have gone into Synaptic Package manager trying to download/upgrade HP, but I need to get into the backend and download hpcups 3.11.1

Hp 3.10.1 is the HP cups installed.

How do I?

Thanks 

Bob

---

