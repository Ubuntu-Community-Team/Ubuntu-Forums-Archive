---
title: "New Natty install - can't run printer or load Gramps files"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by Buster95 on 2011-08-14
Installed Natty on a Windows machine via a dual boot. Two issues arising:
1 Brother HL-2040 printer just spits out all the paper without printing anything. I checked the printer application. It correctly identified the printer as HL-2040 but loaded the "recommended" HL-2060 driver. I noticed from my searches that others have had this problem but I don't understand whether (or how) they fixed it.

2 Loaded Gramps onto the "new" install (via Synaptic). Exported my Gramps file from another machine onto an external drive and tried to import the file to the new install. Tried opening Gramps to see if it would attempt to import the file, but there didn't seem to be a selection to recover the backup nor did it seem to be visible to the program. Also tried selecting the backup file and "Open with Gramps" - didn't work either. Also unloaded and reloaded Gramps via Synaptic but no change.

Any thoughts on either or both?

Thanks

---

### Post by Buster95 on 2011-08-16
Re: HL-2040 printer problem - fixed it by loading the HL-2060 foomatic hl1250 PPD option instead of the recommended PPD. Can't explain it- must be magic!

Still struggling with the Gramps problem

---

### Post by lkraemer on 2011-08-17
If you just copy the Gramps data file to a USB Flash Drive and then insert that USB Flash Drive in the new computer running Gramps, you should be able to access the data, and save it on the Hard Drive.

Why EXPORT the file and then try to IMPORT it.  All you need to do is access the data.

lk

---

### Post by Buster95 on 2011-08-20
> **lkraemer said:**
> If you just copy the Gramps data file to a USB Flash Drive and then insert that USB Flash Drive in the new computer running Gramps, you should be able to access the data, and save it on the Hard Drive.

Why EXPORT the file and then try to IMPORT it.  All you need to do is access the data.

lk

I first tried creating and exporting a gpkg.media file (in accordance with Gramps documentation on migrating between machines). I saved it on an external portable drive. That seemed OK.
When I started Gramps, there was no import option available, even though the manual says "select family tree -> Import".

When that didn't work, I tried what you suggested above. I went to the saved file and selected "open with ...Gramps". After a delay, nothing happened.

The only thing I can think of now is to repeat the whole process again, just in case some sort of file corruption occurred.

Any other thoughts would be appreciated.

---

### Post by lkraemer on 2011-08-20
When you created your initial database it was located at:
```

/home/loginname/.gramps/grampsdb/randomnumberfolder/several-files

```
Assuming you are running the same version of gramps, if you copy the
grampsdb/randomnumberfolder to the second computer you should be able to access your database.

NOTE:  the .gramps subdirectory is hidden, but CNTL H (Toggle) will allow you to see it.

Or you can export the database in one of the several formats:
Comma Separated Values (CSV)
GEDCOM
GeneWeb
Gramps XML
Gramps XML Package
Web Family Tree
vCalendar
vCard

Filtered by what you want/need.

LK

---

### Post by Buster95 on 2011-09-12
Reloaded Gramps - At first I thought that there was no change but after around 10 minutes!! of grinding through the "load file' process, it worked.
Gramps now loads the file quickly and normally.
I'm at a loss to explain what happened and why, so this thread will be of little use to other troubleshooters.

---

