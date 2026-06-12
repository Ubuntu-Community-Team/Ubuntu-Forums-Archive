---
title: "Cryptic Error Message During Update"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by Ashejoe on 2008-07-26
For the past week, when I attempt to update my Ubuntu 8.04 install, the update refuses to happen.  

Instead, I get this cryptic error message which I don't understand, let alone, know how to resolve.  Can anyone help ?
---------------------------------------
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
----------------------------------------
I do have a portable hard disk attached to my system via USB port.  But, it's never been a problem in the past.  Only in the past week have I been encountering this issue.

Also, (assuming this error message refers to that portable hard drive), I can still access it.

(forgive me if this has already been addressed.  I didn't know what to search for.)

Thanks

---

### Post by avtolle on 2008-07-26
That message appears when another package manager is in use, such as Synaptic, Add/Remove Programs, or when apt is being used from the command line. Be sure that none of these are open, and try again.

---

### Post by Ashejoe on 2008-07-26
Well... as far as I know Avtolle, there is no other package manager running ??  But I'll check... (if I can figure out how to)

I boot up into Ubuntu, and when my desktop loads, the first thing I notice is the task bar icon notifying me that updates are available for download.

Before I do anything else, I attempt to download and install the updates.  And that's when I get the error message I reported.

Could it be that I don't have to "click the icon" ?  That Ubuntu is already in the process of downloading automatically ?  Maybe that's why I'm getting this error message ???

---

### Post by avtolle on 2008-07-26
Not sure why you are getting the error message, then; unless you have enabled the "Install Security updates without confirmation" or "Download all updates in background" choices in Software Sources. 

I know that trying to access update manager, synaptic, etc., when the notifier is grayed out in the panel will give me an error like that (it appears to be doing some background work when grayed out), but just clicking on the orange cog wheel/red arrow when it appears doesn't; but I don't have either of the two options mentioned above selected, either.

---

### Post by Ashejoe on 2008-07-27
You know... I think that's it !  You're right, now that I think about it, the task bar icon IS grey and not orange.  And also, I think I do have it set for automatic download of security updates.  Actually, the more I ponder what you said, when the icon is orange, I don't ever recall having that error message.  I think you've solved my riddle.  Thanks !!:guitar:

---

