---
title: "Printer Sharing - Working For Anybody?"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fondle-em on 2009-10-07
On two different computers running Karmic, one 64-bit and one 32-bit, it is proving impossible to share any printers.  Both of the Ubuntu computers can easily see a shared printer on a Macintosh on the network, but neither one can share a printer to the Mac, or to each other - though both claim they're sharing printers, they aren't.

---

### Post by mikeyrb on 2009-10-07
Yup, it works for me from Karmic to an OS X machine.  Verify that CUPS is set up to share the printer by either going to System->Administration->Printing, then Server->Settings... or [http://localhost:631/admin]("http://localhost:631/admin").  Also, post your steps for how you are trying to set up the printer on the other machines.

---

### Post by fondle-em on 2009-10-09
This is working now, or rather, well enough.  After updating today the shared printer on the 32-bit Karmic box is showing up on the 64-bit Karmic laptop.  The Mac still doesn't detect it (and won't print to it even if the printer's address is added manually) but I can live with that, as I don't really need to print from the Mac at this time.  Thanks for the help anyways.

---

### Post by darco on 2009-10-09
I have to restart cups every time I reboot in order for my HP Printer to be detected...
How can I automate this?


darco

---

