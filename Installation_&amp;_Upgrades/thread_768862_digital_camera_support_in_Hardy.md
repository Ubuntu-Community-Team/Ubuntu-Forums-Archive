---
title: "digital camera support in Hardy"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by webtaster on 2008-04-26
I upgraded to Hardy today Many thanks and congratulations to the Ubuntu team !
Just a tip for anyone who (like me) can't seem to get on with the file structure that f-spot saves digital camera images as :($HOME/year/month/date). 

To revert back to the "old" way Gutsy used to manage files do this:
Go to:

System--> Preferences-->Removable files and media
In the digital camera command box replace f-spot with this:
gnome-volume-manager-gthumb %h

All should be as it was before ! :)

Cheers all!

Phil

---

### Post by wickerman1413 on 2008-04-27
I dont mind the file structure imposed by f-spot, though I do change the settings to store my images beneath /data1/Photos/year/month/date

For support of RAW formats in Hardy, I found I had to first install ufraw from Add/Remove.... then do a *sudo apt-get gimp-ufraw* to get the gimp plugin installed.

I do have a problem now with F-Spot's "Open With" menu. For my Nikon raw .NEF files, F-Spot's "Open With" menu reports "No applications available". The application list is populated within MainWindows.cs with a call to Gnome.Vfs.MimeType.GetMimeTypeForUri but I havent been able to find anything related to this other than the Gnome MIME types. 
The Open With list is populated fine in Nautilus which suggests that perhaps f-spot or mono have an old/cached MIME application list generated prior to me installed the gimp-ufraw plugin. 

If anyone has any ideas I would be very happy to hear them!

---

### Post by kmetz on 2008-09-21
I have the same problem wickerman1413 mentioned. Tried many things - including a reinstall (apt-get remove --purge && apt-get install) of f-spot and mono.
F-spot just keeps to show me different options in the "open with" selection list than nautilus does (also for jpeg files).

Since this thread is rather old: Has anyone found a solution?

I also found a somewhat related bug in launchpad: [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/223400](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/223400)

Thanks!
k

---

