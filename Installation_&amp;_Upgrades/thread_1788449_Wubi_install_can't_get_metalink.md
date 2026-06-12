---
title: "Wubi install: can't get metalink ?"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by Name141 on 2011-06-22
[http://paste.ubuntu.com/630931/](http://paste.ubuntu.com/630931/)

It comes up to that and errors.  Any ideas ?

---

### Post by Rubi1200 on 2011-06-22
Try this link:
[http://releases.ubuntu.com/10.04.2/wubi.exe](http://releases.ubuntu.com/10.04.2/wubi.exe)

Place the wubi.exe and downloaded ISO in the same folder and then run the executable.

---

### Post by Name141 on 2011-06-22
> **Rubi1200 said:**
> Try this link:
[http://releases.ubuntu.com/10.04.2/wubi.exe](http://releases.ubuntu.com/10.04.2/wubi.exe)

Will this preserve the ISO's information?  I'm on limited bandwidth now (unlimited hours are 1-6 AM (when I downloaded the ISO)) and only have 425 MBs to work with per "rolling 24 hours" (stupid hughesnet.. )

Edit: Simply replacing the Wubi.exe came up with the same error (replacing wubi.exe in the ISO's extract folder).

Edit2: Running wubi.exe outside of the ISO extract produced the same error also.

---

### Post by bcbc on 2011-06-22
Don't open the ISO as an archive. Copy the wubi.exe into your downloads folder along with the ISO (file). You can copy the wubi.exe from the ISO and paste it into the downloads folder or download the version Rubi1200 pointed to.

Then run Wubi from your downloads folder, select Xubuntu,  and it will find and use the Xubuntu ISO in there (provided the ISO is valid).

If you want to run directly from the ISO you have to "mount" it (but this is not necessary) or burn it to CD first.

---

### Post by Name141 on 2011-06-22
> **bcbc said:**
> Don't open the ISO as an archive. Copy the wubi.exe into your downloads folder along with the ISO (file). You can copy the wubi.exe from the ISO and paste it into the downloads folder or download the version Rubi1200 pointed to.

Then run Wubi from your downloads folder, select Xubuntu,  and it will find and use the Xubuntu ISO in there (provided the ISO is valid).

If you want to run directly from the ISO you have to "mount" it (but this is not necessary) or burn it to CD first.

That worked, using the ISO and Wubi.exe without extracting the ISO and then using the ISO's wubi, but rather just running Wubi.exe with the ISO there in the same folder worked.

---

### Post by bcbc on 2011-06-22
> **Name141 said:**
> That worked, using the ISO and Wubi.exe without extracting the ISO and then using the ISO's wubi, but rather just running Wubi.exe with the ISO there in the same folder worked.
If I understood you correctly, it worked. That's great :) 

Please mark the thread as solved using the Thread Tools at the top of the page.

---

### Post by Rubi1200 on 2011-06-23
Sorry for the delayed response. I am also pleased this worked for you.

Good luck and enjoy :)

---

