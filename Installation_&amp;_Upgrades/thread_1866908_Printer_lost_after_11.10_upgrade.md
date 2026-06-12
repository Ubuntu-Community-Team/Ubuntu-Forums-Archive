---
title: "Printer lost after 11.10 upgrade"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by raysa on 2011-10-22
Upgraded to 11.10 and all seems OK except I can't print any more.
The job appears as "pending" in the job list but nothing happens.
In the printer app the correct printer is shown ticked and the status reads "Processing, waiting for printer to become available."
Thanks for any help please.

---

### Post by satanselbow on 2011-10-22
Sinclair ZX Spectrum thermal printers are no longer supported (if they ever were) or do you have something else?

---

### Post by raysa on 2011-10-22
Sorry, should have mentioned the printer. 
It's an Epsom Stylus Photo R340.

With no jobs pending, the printer app says "Idle - Waiting for printer to become available.".  Then when you send it a job this changes very briefly to "Printing" and then to "Processing - Waiting for printer to become available."

The printer is properly identified in the app window but the computer doesn't seem able to sent the job to it. It worked without fail under 10.04 and I have not changed any leads or printer set-up. The USB sockets work fine with anything else.

How can I make the printer "available" again?

I now think the printer app was just remembering the Epson details from the 11.04 installation rather than recognising it now. I uninstalled the printer app and reinstalled it, and now there's no sign of the connected printer at all!

Anything happening about these printer problems? The developers surely can't be content to leave so many people unable to use their printers after upgrading to 11.10

C'mon chaps ... Any instructions on how to get our printers working again?

---

### Post by masgeeks on 2011-10-22
Can you do a clean install...???

---

### Post by raysa on 2011-10-22
I'd need help ... do you mean the printer, the printer app, or the entire OS? (The latter would seem a bit drastic as this is the only prob I've found so far). But I must have printing, so ...

---

### Post by rohnadams on 2011-10-29
I have this same issue. I have tried uninstalling and reinstalling cups to no avail. It still will no detect my usb Epson Photo R340. I can see that is connect via lsusb. Printer worked (if not always flawlessly via network) in Ubuntu 11.04. Is this somehow due to 11.10 using the new Cups 1.5? I couldn't figure out a way to revert to the old cups using Software Center.

---

