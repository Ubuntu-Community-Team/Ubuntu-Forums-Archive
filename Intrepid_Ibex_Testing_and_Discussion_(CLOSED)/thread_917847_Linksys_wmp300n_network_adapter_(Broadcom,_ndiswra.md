---
title: "Linksys wmp300n network adapter (Broadcom, ndiswrapper) in Intrepid"
date: 2008-09-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by berman56 on 2008-09-12
Wondering if anyone has had success getting their broadcom network adapter working in Intrepid.  In Hardy, I've been using my Linksys WMP300N adapter using ndiswrapper and the windows driver.  As has been discussed in other threads, performance is poor compared to windows.  I thought I might give the new Linux kernel 2.6.27 a try in Intrepid alpha 5.  Ndiswrapper appears to recognize and install the driver but the wireless adapter doesn't work at all.  The system doesn't register it in iwconfig. Nothing in network manager.

Hopefully this will be sorted out in one of the upcoming releases.  Anyone have any success with a broadcom adapter in Intrepid?  Thanks!

---

### Post by TSupra88 on 2008-09-12
try this: [http://tsupra88.blogspot.com](http://tsupra88.blogspot.com)

(I've written a quick, but clear tutorial that will help you install broadcom cards and I've provided links to the necessary drivers/firmware.)

---

### Post by TSupra88 on 2008-09-12
delete

---

### Post by berman56 on 2008-10-07
I am solved my performance issue with, who would think, a different driver.  The linksys wmp300n driver (any version) gives consistently poor performance in linux when compared to windows.  However, I hunted down a broadcom driver that is compatible with this adapter (see attached).  This driver is far far more stable in both linux and windows :)

Install with ndiswrapper.  And by the way, I haven't been able to get this driver to work with any version Intrepid yet (including beta).  Only seems to work with Hardy (32 and 64-bit!).

---

### Post by berman56 on 2008-10-07
Sorry, the attachment didn't upload.  Here it is.

---

### Post by Brainal on 2008-10-13
Sorry to bump this thread, but after I upgraded to the Intrepid beta, I get the same problem. I tried the walkthrough that helped me get it to work in Hardy, but no prevail in Intrepid. Also, in the restricted hardware option (whatever it's called), it says for the driver of it but I don't know if it works since I don't have an internet connection. Is there any update on this?

---

### Post by woodhome on 2008-10-30
Don't know how or why but this my wmp300n wireless adapter is working fine for me now under intrepid after having nothing but trouble until tonight.  I have a bedtime story to read to a little boy first, then I'll post the details but basically I extracted the newest XP driver from the Linksys file (Oct 17, 2007) and set up ndiswrapper using ndisgtk, Just as I'd tried three times before. But all is now working now at about the same level I got under Hardy.

---

